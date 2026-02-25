# Autopilot Detection — API Research

*Research date: 2026-02-24*
*For: Returna warehouse module feature*

---

## Executive Summary

**Udfordring:** Der findes INGEN offentlig Microsoft API til at checke "er denne device registreret i Autopilot hos en anden organisation?"

**Løsninger:**
1. Microsoft Graph API — kun for egen tenant
2. Microsoft Partner Center — kræver CSP-partnership + kunde-consent
3. OEM APIs — kun for devices de har solgt
4. Boot-time detection — teknisk workaround

---

## 1. Microsoft Partner Center API

### Hvad det er
CSP (Cloud Solution Provider) partnere kan registrere/deregistrere Autopilot devices på vegne af kunder.

### Krav
- **CSP Partnership** med Microsoft
- **Kunde consent** — hver enterprise-kunde skal godkende
- Kun adgang til devices for **egne kunder**

### API Capabilities
```
Partner Center API:
- Add devices to Autopilot (for kunde)
- Remove devices from Autopilot (for kunde)
- List devices (for kunde)
```

### Limitation
❌ Kan IKKE checke om en device tilhører en **anden** organisations tenant

### Hvordan Returna kan bruge det
- Hvis Returna bliver CSP partner
- Og enterprise-kunden giver consent
- Så kan Returna se/fjerne devices fra kundens Autopilot

**Fordel:** Kan automatisere deregistrering som del af ITAD-flow

---

## 2. Microsoft Graph API (Intune)

### Endpoint
```
GET /deviceManagement/windowsAutopilotDeviceIdentities
GET /deviceManagement/windowsAutopilotDeviceIdentities/{id}
```

### Hvad det returnerer
```json
{
  "serialNumber": "ABC123",
  "manufacturer": "Dell Inc.",
  "model": "Latitude 5520",
  "enrollmentState": "enrolled",
  "lastContactedDateTime": "2026-02-24T10:00:00Z",
  "azureActiveDirectoryDeviceId": "...",
  "managedDeviceId": "..."
}
```

### Krav
- Azure AD app registration
- Intune license
- `DeviceManagementServiceConfig.ReadWrite.All` permission

### Limitation
❌ Kun adgang til **egen tenant** — kan ikke se andre organisationers devices

### Hvordan Returna kan bruge det
- Enterprise-kunder kan give Returna delegeret adgang
- Returna kan så liste/deregistrere devices fra kundens tenant
- Kræver OAuth consent flow

---

## 3. OEM APIs (Dell, HP, Lenovo)

### Dell TechDirect API
- **Adgang:** Dell partner program
- **Capabilities:** Support tickets, warranty lookup, parts dispatch
- **Autopilot:** Kan registrere devices ved køb
- ❌ Ingen offentlig "check Autopilot status" endpoint

### HP Partner Portal
- **Adgang:** HP partner program
- **Capabilities:** Order management, warranty
- **Autopilot:** Registration ved salg
- ❌ Ingen offentlig status check

### Lenovo
- **Adgang:** Lenovo partner portal
- **Autopilot:** Via "Windows Autopilot Registration Service"
- ❌ Ingen tredjepartsadgang til status

### OEM Limitation
OEMs kan registrere devices de **sælger** til Autopilot — men de har ikke adgang til at se om en device er registreret i en **anden** organisations tenant.

---

## 4. Boot-Time Detection (Teknisk Workaround)

### Sådan virker det
1. Boot device fra custom environment (USB/PXE)
2. Hent hardware hash fra WMI/BIOS
3. Forsøg at kontakte Microsoft Autopilot service
4. Observer response (clean vs. locked)

### Teknisk implementation
```powershell
# Hent hardware hash
$session = New-CimSession
$hash = (Get-CimInstance -Namespace root/cimv2/mdm/dmmap -Class MDM_DevDetail_Ext01 -CimSession $session).DeviceHardwareData
$serial = (Get-CimInstance -Class Win32_BIOS -CimSession $session).SerialNumber
```

### Hvad TRC/BitRaser/Ziperase gør
- Custom bootable ISO
- Henter hardware hash FØR OOBE
- Checker mod Microsoft's service under boot
- Logger "Clean" eller "Locked"

### Returna implementation
1. **PXE boot** i warehouse
2. Custom script henter hash + serial
3. Forsøger OOBE-lignende check
4. Logger resultat i Returna platform

---

## 5. Anbefalinger for Returna

### Kort sigt (MVP)
| Approach | Effort | Value |
|----------|--------|-------|
| **Manuel check via kundens Intune** | Lav | Medium |
| **CSV upload fra kunde** | Lav | Medium |
| **Instruktion til Return Hub** | Lav | Lav |

### Mellem sigt
| Approach | Effort | Value |
|----------|--------|-------|
| **CSP Partnership** | Medium | Høj |
| **Delegeret Graph API adgang** | Medium | Høj |
| **Integration med kundens Intune** | Medium | Høj |

### Lang sigt
| Approach | Effort | Value |
|----------|--------|-------|
| **Boot-time detection tool** | Høj | Meget høj |
| **Partnership med TRC/BitRaser** | Medium | Høj |
| **OEM partnerships** | Høj | Medium |

---

## 6. Konkrete næste skridt

### 1. CSP Partnership
- [ ] Undersøg Microsoft CSP program krav
- [ ] Vurder om Returna skal være direkte CSP eller via partner
- [ ] Kræver: MPN membership, competency requirements

### 2. Graph API Integration
- [ ] Design OAuth consent flow for enterprise-kunder
- [ ] Kunde giver Returna adgang til deres Intune
- [ ] Returna kan liste + deregistrere devices

### 3. Boot-time Tool (Build vs. Buy)
**Buy:**
- BitRaser Autopilot Detection — licensbaseret
- Ziperase — licensbaseret
- TRC RefurbOS — subscription

**Build:**
- Custom PXE/USB boot environment
- PowerShell script til hash extraction
- Integration med Returna warehouse module

### 4. Partnership
- [ ] Kontakt TRC om integration/licensing
- [ ] Kontakt Blancco (ejer BitRaser)
- [ ] Vurder white-label muligheder

---

## 7. Feature Spec Draft

### User Story
> Som Return Hub operatør vil jeg kunne se Autopilot status på en device ved intake, så jeg kan undgå at spilde tid på låste enheder.

### Flow
```
1. Device ankommer til Return Hub
2. Tekniker scanner serienummer
3. Returna checker Autopilot status:
   a. Hvis kunde har givet Intune-adgang → direkte check
   b. Hvis ikke → "Status ukendt - anbefal kunde-check"
4. Status vises: ✅ Clean | 🔒 Locked | ❓ Unknown
5. Locked devices flagges til kundehenvendelse
```

### Integration Points
- Warehouse module intake screen
- Enterprise dashboard (kunde kan se locked devices)
- Reporting (% locked per batch)

---

## Kilder

- Microsoft Learn: Partner Registration
- Microsoft Graph API: windowsAutopilotDeviceIdentity
- Dell TechDirect API documentation
- BitRaser KB: Check Autopilot Locked Devices
- TRC RefurbOS documentation

---

*Clorius research for Kasper Horn — Returna ApS*
