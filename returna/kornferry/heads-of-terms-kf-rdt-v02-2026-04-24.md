# Heads of Terms — Kornferry × RDT

**Version:** 0.2 (draft)
**Date:** 2026-04-24
**Status:** For discussion
**Parties:**
- **Kornferry** ("KF") — client
- **RedeployIT Ltd** ("RDT") — supplier

---

## 1 · Contract structure

- Contract based on RFP; SOW signed by both parties
- 15-month minimum term: 12-month lock-in + 3-month notice (RDT ROI)
- If KF doesn't cancel, yearly review 3 months before renewal — SOW + pricing adjustment
- SLA penalties in place
- Formal change request process
- Contracting entity — which KF entity signs, which RDT entity signs
- Governing law — EU seat vs UK vs neutral
- Right-to-publicise — logo use / case study / reference

## 2 · Commercial model

- 60-day payment terms
- Minimum spend commitment over 15 months
- Pricing structure — service fee, per-device rate, volume tiers
- Currency &amp; FX — EUR / GBP / USD at spot pricing on monthly invoice
- Billing cadence — monthly vs quarterly; late-payment interest
- Termination economics — early exit fee schedule

## 3 · Scope

- **Device categories** — laptops confirmed; confirm desktops / mobiles / monitors / servers / peripherals
- **Geographic coverage** — EU and UK first, followed by NA (USA + Canada), then APAC / LATAM via verified Return Hubs in the network. Where volumes do not justify an RDT-operated site, approved partner Hubs are used.
- **Services in scope** — deployment, returns, in-life swap, image refresh, repairs (in-warranty and out-of-warranty), disposal, erasure certificate, redeployment
- **Out-of-scope** — consumables, desk phones, anything KF does not want RDT to handle
- **Volume forecast** — devices/month by region; seasonality may affect pricing

## 4 · SLA matrix

- Deployment SLA — KF order → laptop in user's hands (by region)
- Return / pickup SLA — ticket raised → collection scheduled
- Processing SLA — receipt → erasure + disposition
- Certificate SLA — certificate produced within agreed business days per SLA
- Exception SLA — mitigated by defined hold times for damaged / missing devices
- Reporting SLA — monthly by day N, quarterly by day N
- Penalty mechanics — service credits (% of monthly fee) vs liquidated damages; cap per quarter

## 5 · Operational governance

- Operational and service quarterly reviews
- Onboarding plan — 30 / 60 / 90 day milestones, named contacts both sides
- Monthly operational call — volumes, exceptions, roadmap
- Quarterly business review — KPIs, strategic direction, pricing
- Annual executive sponsor meeting — commercial / renewal
- Tooling &amp; reporting portal — platform for ticketing, asset register, status, certificates, reporting
- Escalation path — operator / manager / executive on both sides

## 6 · Technical &amp; integration

- RDT permissions in KF's Intune environment
- Image available upfront with RDT
- Test plan understanding KF requirements
- Intune / Autopilot enrolment — RDT acts on behalf of KF; Azure AD scope, least-privilege
- ITSM integration — KF ITSM ↔ platform ticketing
- Image governance — owner, versioning, update cadence, sign-off
- Encryption verification — every returned device's state confirmed and logged
- Data wipe certificate — aligned to **NIST SP 800-88 Rev 2** and **IEEE 2883-2022**; PDF + API; serial-matched
- Asset tag standard — barcoding, cross-reference to KF's register
- API / webhook — platform endpoints via the RDT contract

## 7 · Data protection &amp; compliance

- **DPA** — GDPR + UK GDPR; KF controller, RDT processor
- **Sub-processor list** — platform + verified Return Hubs active at contract start + carriers + erasure SW, with substitution-flexibility clause for Hubs of equivalent certification
- **In-region processing by design** — devices and data routed to Hubs within their region (EU stays in EU, UK in UK). UK ↔ EU transfers covered by mutual adequacy. SCCs / UK IDTA / DPF included in the DPA as a safety net for any exceptional flows outside the region
- **Security certifications** — RDT's ISO 27001 anchors the contract; every verified Hub holds region-appropriate certifications under the applicable vetting standard
- **Breach notification** — 24-hour target, 72-hour maximum; named contacts, template
- **Audit rights** — annual plus on-request on reasonable notice; SOC 2 Type II may satisfy in lieu
- **Personnel vetting** — background checks plus NDA flow-down to facility staff
- **Record retention** — certificates retained 3 years, retrievable on request

## 8 · Risk, insurance &amp; liability

- Insurance cover for goods and warehouses — included
- Optional transit insurance for high-value items — charged at 2% of declared value
- Insurance limits &amp; certificates — public liability, product liability, professional indemnity, cyber — with KF minimum limits stated
- Liability cap — typical 12-month fees; carve-outs for data breach, IP infringement, gross negligence
- Indemnification — third-party claims, breach, IP, personal injury
- Title &amp; risk transfer — device title between KF / RDT / onward buyer
- Business continuity — RDT site outage: backup capacity, defined RTO
- Force majeure — scope, notification, mitigation obligations

## 9 · Exit strategy

- EU + UK zone → RDT: new and used equipment to RDT warehouse
- Used equipment: inbound checklist to ensure the device is working correctly
- Transition period — 60 / 90 / 120 days post-termination at BAU pricing
- Handover deliverables — final asset register, all outstanding certificates, images, service history, open tickets, residual inventory
- Return of KF data — within N days; secure deletion of anything not retained for legal / compliance
- Data and devices in-flight at termination — defined handling mid-transit, mid-processing, mid-resale
- Residual stock — KF-owned inventory: return or dispose
- Onward IP — KF retains image, data, asset register; RDT retains platform and tooling
- Non-solicit — staff-hiring limits for a defined period

---

## Likely KF questions — prepared answers

1. **"Who actually touches our laptops?"** — RDT warehouse, named site, vetted staff
2. **"What happens if RDT's site goes down?"** — Backup capacity, BCP, alternate processing
3. **"How do we know the data is gone?"** — Certificate aligned to NIST SP 800-88 Rev 2 and IEEE 2883-2022, serial-matched, API-retrievable
4. **"Can we audit?"** — Annual and on reasonable notice; SOC 2 Type II may satisfy in lieu
5. **"What's the exit?"** — 3-month notice after month 12, with clear handover deliverables
6. **"What am I locking into for 15 months?"** — Minimum spend, change-request mechanism if scope shifts
7. **"Who's responsible if a device is lost?"** — Insurance, liability cap, breach process
8. **"Can we extend beyond your own facilities?"** — Yes. RDT orchestrates additional third-party Hubs under the same framework where volumes do not justify an RDT-operated site
9. **"What does the portal look like day-to-day?"** — Demo of the platform — ticketing, asset register, certificates, reporting

---

## Signatures / next steps

| Party | Name | Role | Signature | Date |
|---|---|---|---|---|
| Kornferry | | | ______________________ | |
| RDT | | | ______________________ | |

### Next steps
1. KF to confirm scope and geographic priorities
2. RDT to issue SOW aligned with these Heads of Terms
3. DPA drafted alongside SOW
4. Signature on full SOW + DPA

---

## Document control

| Version | Date | Changes | Author |
|---|---|---|---|
| 0.1 | 2026-04-23 | Initial draft (agenda format) | AI-assisted for Kasper Horn |
| 0.2 | 2026-04-24 | Converted to Heads of Terms format; incorporated Dennis Frize amendments: de-branded platform references, geographic sequencing (EU/UK → NA → APAC/LATAM), removed resale scope, added repairs (in + out of warranty), specified 3-year cert retention, 2% transit-insurance surcharge, softened SLA specifics to be filled at SOW stage, trimmed KF Q&amp;A | Dennis Frize (RDT) + refinement |
