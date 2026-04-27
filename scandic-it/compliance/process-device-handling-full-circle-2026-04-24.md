# Device Handling — Full-Circle Process

**Document ID:** QMS-PROC-010
**Version:** 1.0
**Effective:** 2026-04-24
**Owner:** Mike Andersen (Operations)
**Next review:** 2026-10-24 or upon significant change
**Classification:** Internal
**Standard alignment:** ISO/IEC 27001:2022 (A.5.9, A.5.28, A.7.10, A.7.14, A.8.10) · ISO 9001:2015 Clause 8 (Operation)

---

## 1. Purpose

This process describes the end-to-end handling of a customer device from initial collection request to final disposition and reporting. It is the master operational flow that the more detailed procedures (Device Reception, Data Erasure, Diagnostics & QC, Shipping & Logistics) sit beneath.

## 2. Scope

All customer devices received into Scandic IT's Tarmvej 8 facility for ITAD handling — including laptops, desktops, mobile phones, servers, and storage media — regardless of customer type or engagement model.

## 3. Roles

| Role | Responsibility |
|---|---|
| **Operations lead (Mike)** | End-to-end accountability for the process; sign-off on final disposition reports |
| **Warehouse technician** | Physical handling, intake, erasure, destruction; chain-of-custody signing |
| **Quality technician** | Diagnostics, grading; second set of eyes on erasure certificates |
| **Management rep (Kasper)** | Commercial interface with customer; onboarding new customers into the flow |

## 4. Process flow

```
┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
│  1. Request   │→ │  2. Pickup    │→ │  3. Transit   │→ │  4. Receipt   │
└───────────────┘  └───────────────┘  └───────────────┘  └───────────────┘
        ↓                                                        ↓
┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
│ 12. Archive   │← │ 11. Reporting │← │ 10. Disposition│← │  5. Intake    │
└───────────────┘  └───────────────┘  └───────────────┘  └───────────────┘
                                                                 ↓
                   ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
                   │ 9. Destruction│← │ 8. Erasure    │← │ 6-7. Diagnost │
                   │ (if required) │  │               │  │   + Grading   │
                   └───────────────┘  └───────────────┘  └───────────────┘
```

### Step 1 — Collection request
- Customer raises request via email, phone, or direct contact with account manager
- Request captured internally (subject, volume estimate, device types, pickup address, urgency)
- Operations confirms feasibility and quotes timing
- **Output:** request logged; commercial confirmation sent to customer

### Step 2 — Pickup scheduling
- Carrier (DHL or customer-specified) booked
- Pickup date confirmed with customer
- Sealed containers / packaging guidance sent to customer if required
- Chain-of-custody form issued (if used for the engagement)
- **Output:** booking reference, scheduled pickup date

### Step 3 — Transit
- Carrier collects from customer site
- Shipping insurance per carrier terms; high-value consignments insured additionally
- Tracking number captured; status monitored
- **Output:** tracking reference, ETA to Scandic IT

### Step 4 — Receipt at warehouse
- Delivery received at Tarmvej 8
- External inspection of packaging for damage or tampering
- Count verified against customer's declared quantity
- Discrepancies flagged and communicated to customer within same business day
- **Refers to:** Device Reception Procedure
- **Output:** receipt confirmation, discrepancy note if any

### Step 5 — Intake & registration
- Each device logged individually
- Serial number, model, visible condition captured
- Devices assigned to job/batch in tracking system
- Chain-of-custody transfer recorded (carrier → Scandic IT)
- Status: *Received* → workflow begins
- **Output:** per-device intake record, job batch created

### Step 6 — Diagnostics
- Device powered on (if safe and applicable)
- Aiken/Piceasoft diagnostic run
- Hardware health captured (boot, disk SMART, memory, battery if laptop)
- **Refers to:** Diagnostics & Quality Control Procedure
- **Output:** diagnostic report per device

### Step 7 — Grading
- Device assigned grade A / B / C / D based on:
  - Cosmetic condition
  - Functional condition per diagnostics
  - Age and serviceability
- Grade determines disposition path (refurbish / resell / recycle)
- **Output:** grade assigned, disposition path chosen

### Step 8 — Data erasure
- Device booted from Certus PXE server on isolated erasure VLAN
- Erasure performed to **NIST SP 800-88 Rev 2** and **IEEE 2883-2022** aligned standards
- Certificate generated per device (PDF, serial-matched)
- Erasure verified by quality technician before sign-off
- **Refers to:** Data Erasure Procedure
- **Output:** erasure certificate per device, stored in Certus portal and exported to customer record

### Step 9 — Physical destruction (if erasure fails or customer requires it)
- OMS900 shredder used for HDDs/SSDs
- Destruction record logged (date, serial, technician)
- Recycling partner (Stena / El-Recycling) collects shredded material
- **Output:** destruction certificate, chain transferred to recycler

### Step 10 — Disposition
- Based on grade and contractual terms:
  - **A/B grade + refurb scope:** prepare for resale or customer redeployment
  - **C/D grade:** recycle via Stena / El-Recycling
  - **Customer-return:** package and ship back per agreement
- Status updated in tracking system
- **Output:** disposition confirmation per device

### Step 11 — Reporting & certificate delivery
- Summary report generated per job:
  - Devices processed, per-device certificates, disposition outcomes
  - Resale value (if applicable) and revenue-share breakdown
- Delivered to customer via email and/or portal
- **Output:** customer-facing report + individual erasure/destruction certificates

### Step 12 — Archive & close
- All records retained per Data Classification Policy retention requirements
- Certus portal retains per-device certificates (long-term retention)
- Chain-of-custody, commercial, and processing records archived in M365 per document control
- Job closed; feedback loop to Customer Satisfaction cycle (see §6)
- **Output:** closed job, records archived

## 5. Records generated (Cellar layer)

| Record | Generated at step | Retained in |
|---|---|---|
| Collection request log | 1 | Internal workflow system |
| Carrier booking and tracking | 2-3 | Internal workflow + carrier system |
| Chain-of-custody handover | 4-5, 9 | Physical signed form + M365 |
| Intake record (per device) | 5 | Workflow + Asset Inventory (customer-device category) |
| Diagnostic report | 6 | Aiken/Piceasoft |
| Grade assignment | 7 | Workflow |
| Erasure certificate | 8 | Certus portal |
| Destruction record | 9 | Workflow + OMS900 log |
| Disposition record | 10 | Workflow |
| Customer job report | 11 | M365 + sent to customer |

## 6. Customer feedback and continual improvement

- Customer satisfaction survey sent **annually** (updated from quarterly in response to Stage 1 audit 2026-04-24)
- Feedback captured and reviewed at Management Review
- Any non-conformity raised in the job flow tracked via the Corrective Action Procedure
- **Refers to:** Customer Satisfaction Procedure, Corrective Action Procedure

## 7. Cross-references

- **Policies:** Acceptable Use Policy, Asset Management Policy, Data Classification Policy, Physical Security Policy, Access Control Policy
- **Procedures:** Device Reception, Data Erasure, Diagnostics & Quality Control, Shipping & Logistics
- **Records:** Asset Inventory (customer-devices-in-processing category), Corrective Action Log

## 8. Approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Operations Owner | Mike Andersen | ______________________ | 2026-04-24 |
| Management Representative | Kasper Horn | ______________________ | 2026-04-24 |

## 9. Change log

| Version | Date | Changes | Responsible |
|---|---|---|---|
| 1.0 | 2026-04-24 | Initial document; created during Stage 1 audit to close Floor 2 (Processes) gap | Mike Andersen |
