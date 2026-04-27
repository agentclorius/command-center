# Kornferry × RDT (on Returna platform) — Contract Mechanics Agenda (enriched)

**Prepared:** 2026-04-23 for the management discussion on 2026-04-24
**Scope:** contract, commercial, operational, technical, compliance, and exit terms

> **Structure for phase 1:**
> - **Contracting party to KF = RDT.** RDT already runs office ITAD for KF today and holds ISO 27001 — they're the trusted prime / invoicing entity, effectively an ambassador bringing the Returna-orchestrated service to KF under an existing relationship.
> - **Platform and tooling = Returna.** KF will use Returna's portal, reporting, ITSM integration, and orchestration from day 1 — Returna is a visible platform partner, not hidden. The value Returna adds on top of what RDT does today: orchestration visibility, multi-region scale, and a single-pane-of-glass asset/certificate register.
> - **Execution by region:**
>   - **UK → RDT** (their own facility, under their ISO scope)
>   - **EU / NA / APAC / LATAM → verified Return Hubs** in the Returna network (orchestrated by Returna on RDT's behalf, each operating under their own certifications)
> - **Phase 2 (at renewal, planned):** once Returna is ISO 27001 certified, the contract can be moved from RDT to Returna. RDT's role shifts to **ambassador** — relationship maintainer, rev share, introducer for future deals. KF will be able to use more platform features once invoiced directly through Returna.
>
> In short: "You contract with RDT. You use Returna. Physical work is done by the right local Hub in each region. Same chain of responsibility, one clear path."

Items marked **[D]** come from the existing draft agenda. Items marked **[+]** are additions to get in front of before the meeting.

---

## 1 · Contract structure

- **[D]** Contract based on RFP; SOW signed by both parties
- **[D]** 15 months minimum-term contract: 12-month lock-in, 3-month notice thereafter (RDT ROI)
- **[D]** If KF does not cancel, yearly review 3 months before renewal — SOW and pricing adjustment
- **[D]** SLA penalties in place
- **[D]** Formal change request process
- **[+] Contracting entity** — confirm KF legal entity signing (parent vs. regional subsidiary) and which RDT entity signs
- **[+] Governing law & dispute forum** — EU seat (Denmark / Netherlands / Ireland) vs. UK vs. neutral
- **[+] Right-to-publicise** — can RDT list KF as a customer / include a logo / do a case study?

## 2 · Commercial model

- **[D]** 60-day payment terms
- **[D]** Minimum spend commitment over 15 months
- **[+] Pricing structure** — service fee model; per-device rate; any volume-tier discounts
- **[+] Currency & FX** — contracting currency (EUR / GBP / USD), who bears FX risk
- **[+] Resale revenue share** — split on remarketed equipment (KF / RDT / any marketplace); KF's right to keep 100% or share
- **[+] Billing cadence** — monthly / quarterly; late-payment interest
- **[+] True-up model** — if KF exceeds minimum, how the overage is priced; if under-spend, how minimum is charged
- **[+] Termination economics** — early-termination fee schedule; payment for services already rendered mid-cycle

## 3 · Scope

- **[+] Device categories** — laptops confirmed; confirm desktops, mobiles/tablets, peripherals, monitors, servers, network gear
- **[+] Geographic coverage** — UK via RDT; EU, NA / APAC / LATAM via verified Return Hubs in the Returna network
- **[+] Services in scope** — deployment (new devices out), returns (used devices in), in-life swap/repair, image refresh, disposal, data erasure certificate, refurb+resell, redeployment of refurbed devices to KF
- **[+] Out-of-scope items** — consumables, accessories already with the user, desk phones, anything KF handles elsewhere
- **[+] Volume forecast** — expected devices/month by region; seasonality (hire waves, refresh cycles)

## 4 · SLA matrix (what the penalties enforce)

- **[+] Deployment SLA** — days from KF order to laptop in user's hands (by region)
- **[+] Return / pickup SLA** — from ticket raised to collection scheduled
- **[+] Processing SLA** — from receipt at warehouse to erasure + disposition
- **[+] Data destruction cert delivery SLA** — cert produced within N business days of processing
- **[+] Exception / escalation SLA** — ticket hold times for damaged / missing devices
- **[+] Reporting SLA** — monthly operational report by day N; quarterly review by day N
- **[+] SLA penalty mechanics** — service credits (% of monthly fee) vs. liquidated damages; cap per quarter

## 5 · Operational governance

- **[D]** Operational and service quarterly reviews
- **[+] Onboarding plan** — 30 / 60 / 90 day milestones; dedicated KF point of contact on both sides
- **[+] Monthly operational call** — day-to-day issues, volumes, exceptions, roadmap
- **[+] Quarterly business review (QBR)** — KPIs, strategic direction, pricing adjustments, regional expansion
- **[+] Annual executive sponsor meeting** — commercial / renewal
- **[+] Tooling & reporting portal** — Returna platform (ticketing, asset register, status, certificates, reporting)
- **[+] Escalation path** — named contacts at operator, manager, exec levels on both sides

## 6 · Technical / integration

- **[D]** RDT permissions in KF's Intune environment
- **[D]** Image available upfront with RDT
- **[D]** Test plan understanding KF requirement
- **[+] Intune / Autopilot enrolment** — RDT acts on behalf of KF; Azure AD / Entra app registration scope, conditional access, least-privilege access model
- **[+] ITSM integration** — KF's ITSM (FreshService / ServiceNow / Jira) ↔ **Returna platform** ticketing; ticket flow standard
- **[+] Image governance** — master image owner (KF vs. RDT-maintained), versioning, update cadence, sign-off process
- **[+] BitLocker / encryption verification** — every returned device's encryption state confirmed and logged before wipe
- **[+] Data wipe certificate** — aligned to **NIST SP 800-88 Rev 2** and **IEEE 2883-2022**; certificate delivered per device (PDF + API) through the Returna platform, serial-number-matched
- **[+] Asset tag standard** — KF naming/labelling, barcoding, cross-ref with KF's asset register
- **[+] API / webhook** — Returna platform endpoints KF can pull (device status, certificate retrieval, disposition report); contractually exposed via RDT

## 7 · Data protection & compliance

- **[+] Data Processing Agreement (DPA)** — GDPR + UK GDPR; KF controller, RDT processor
- **[+] Sub-processor list** — **Returna** (platform + orchestration) + the verified Return Hubs active at contract start, carriers, erasure SW vendor, any refurb/remarketing partners; KF approval right on additions, plus flexibility for RDT/Returna to substitute Hubs of equivalent certification without fresh KF consent (standard operational clause)
- **[+] In-region processing by design** — Returna's routing keeps devices and personal data within their region of origin (EU devices processed in EU Hubs, UK in UK, etc.), so cross-border transfers are the exception, not the default. UK ↔ EU is covered by mutual adequacy. SCCs / UK IDTA / DPF clauses included in the DPA as a safety net for any exceptional flows outside the region
- **[+] Security certifications** — RDT holds **ISO 27001** (the reason KF contracts with RDT as prime). Every verified Return Hub in the chain must hold appropriate certifications for its region of operation; Returna's Hub vetting standard is part of the platform. RDT's ISO anchors the contractual chain. Returna's own ISO 27001 is in progress — not required for phase 1; becomes relevant at phase-2 migration. Erasure aligned to **NIST SP 800-88 Rev 2** and **IEEE 2883-2022**; R2 or e-Stewards where applicable
- **[+] Breach notification** — timeline (24h preferred, 72h maximum), designated contacts, template
- **[+] Audit rights** — annual on-site or remote; SOC 2 reports may satisfy in lieu; KF right to audit on reasonable notice
- **[+] Personnel vetting** — background checks for warehouse staff handling KF devices; NDA flow-down to facility staff
- **[+] Record retention** — KF's disposal certificates retained N years, retrievable on request

## 8 · Risk, insurance & liability

- **[D]** Insurance cover for goods and warehouses
- **[D]** Optional insurance during transit for high-value items (new laptop)
- **[+] Insurance limits & certificates** — public liability, product liability, professional indemnity, cyber — min limits KF wants to see
- **[+] Liability cap** — typical 12-month fees; carve-outs (data breach, IP infringement, gross negligence uncapped)
- **[+] Indemnification** — who indemnifies whom for third-party claims (data breach, IP, personal injury)
- **[+] Title & risk transfer** — when does title to the device pass between KF / RDT / resale buyer
- **[+] Business continuity plan** — RDT site outage or unavailability: alternative processing capacity, RTO
- **[+] Force majeure** — scope, notification, mitigation obligations

## 9 · Exit strategy

- **[D]** Zones EU & UK → RDT:
  - **[D]** Send new and used equipment to RDT warehouse
  - **[D]** Used equipment via inbound check list to ensure the laptop is working correctly
- **[+] Transition period** — 60 / 90 / 120 days post-termination; RDT continues operating at BAU pricing during handover
- **[+] Handover deliverables** — final asset register, all outstanding certificates, any KF-held images, service history, open tickets, residual inventory list
- **[+] Return of KF data** — within N days of termination; secure deletion of anything not retained for legal/compliance
- **[+] Data in RDT's custody at termination** — what happens to devices in-flight (in transit, awaiting erasure, awaiting resale)
- **[+] Residual stock** — how KF-owned inventory held at RDT is returned or disposed
- **[+] Onward IP / tooling** — KF keeps its image, user data, asset register; RDT keeps platform / tooling
- **[+] Non-solicit** — limits on RDT hiring KF staff (and vice versa) for a period

---

## Likely KF questions to prepare for

1. **"Who actually touches our laptops?"** — answer = RDT warehouse, named site, vetted staff
2. **"What happens if RDT's primary site goes down?"** — backup capacity, BCP, alternate processing
3. **"How do we know the data is gone?"** — certificate aligned to NIST SP 800-88 Rev 2 and IEEE 2883-2022, serial-matched, API-retrievable
4. **"Can we audit?"** — yes, annual + on reasonable notice; SOC 2 Type II available
5. **"What's my exit if this isn't working?"** — 3-month notice after month 12, clear handover deliverables
6. **"What am I locking into for 15 months?"** — min spend, change request mechanism if scope shifts
7. **"Who's responsible if a laptop with data is lost in transit?"** — insurance, liability cap, breach process
8. **"Can we extend beyond EU+UK?"** — yes; RDT has partner network / capability for additional regions
9. **"What does my portal look like day-to-day?"** — demo of the **Returna platform**; KF contracts with RDT but uses Returna as the daily tool (ticketing, asset register, certificates, reporting)
10. **"How much resale value comes back to us?"** — split model, transparency on proceeds
11. **"Why are we contracting with RDT but using Returna's tools? Is that safe?"** — RDT holds ISO 27001 and is the responsible party; Returna is a named sub-processor inside the DPA. RDT's ISO scope is designed to cover the Returna-orchestrated services so the chain is compliant. Over time, once Returna completes its own ISO certification, we can offer a migration path for you to contract directly with Returna — at your option, at renewal

## Materials to bring to the meeting

- **A one-page pricing summary** (service fee + per-device + min spend) so KF mgmt can see the commercials on one sheet
- **The RDT facility fact-sheet** — ISO 27001 scope, capacity, employees, processes, physical security
- **Sample data destruction certificate** — show them what the artefact looks like
- **A sample monthly operational report** — show them what visibility they'll get
- **Draft SOW table of contents** — not the full SOW, just headings so they see nothing is missed

---

## 🔒 INTERNAL ONLY — not for KF meeting

_The items below are for RDT + Kasper to align on between themselves. Strip before sharing._

**Phase 1 structure (at signing):**
- Contract: KF ↔ RDT (prime, ISO 27001 holder, invoicer)
- Platform: Returna (visible to KF, named sub-processor, used daily)
- Execution: **UK → RDT's facility** · **EU / NA / APAC / LATAM → verified Return Hubs in the Returna network**
- Commercial split RDT ↔ Returna ↔ Hubs: handled in the separate partner agreements, not exposed on the KF SOW

**Phase 2 (at renewal, planned):**
- Trigger: Returna completes ISO 27001 + is formally onboarded as a named contracting entity
- Contract moves from RDT to Returna at renewal. Same Hubs doing the physical work; the name on the invoice changes
- **RDT role shifts to ambassador** — relationship maintainer, earns ongoing rev share as introducer, not prime contractor, not required to run the UK Hub
- **KF upside at phase 2:** access to more Returna platform features that are reserved for direct customers (deeper reporting / automation / multi-region orchestration) — real carrot to motivate the move
- Design implication: the 15-month + 3-month-notice term is sized so the first renewal lands near Returna's likely ISO completion. Worth quietly designing the SOW so the transition is clean (no penalty, pre-agreed mechanism) without flagging it as imminent to KF

**⚠️ EU Hub — substitution risk to map:**
An initial EU Hub may change during the contract term (e.g. through corporate events, partner exit, or capacity reallocation). If a specific Hub is named explicitly in the DPA and later needs to be replaced, KF may need to re-approve a new Hub. Mitigation:
- **Pre-emptive flexibility clause** — DPA allows RDT/Returna to substitute an EU Hub with equivalent certifications without fresh KF approval (notification only). Normalises Hub substitution as a standard operational action.
- Keep KF-facing material generic ("verified Return Hubs in the Returna network") rather than naming specific Hubs.

**Critical items to nail down BEFORE tomorrow's meeting:**
1. **RDT's ISO 27001 scope** — explicitly covers (a) RDT's facility, (b) the processes KF will use, AND (c) its role as the contractual prime over the Returna-orchestrated services. If the scope is narrow, KF's due diligence will catch it
2. **Every named EU Hub holds ISO 27001** (or equivalent) covering the services KF will use. If any named Hub lacks it, the EU chain has a gap
3. **Sub-processor disclosure** — draft DPA list: Returna + current active Hubs + carriers + erasure SW. Confirm KF accepts that chain, with substitution flexibility
4. **RDT ↔ Returna ↔ Hub commercial split** — margins, per-device rates, resale proceeds flow, FX, and the rev-share RDT earns as phase-2 ambassador. Do this before any pricing is presented to KF
5. **Portal branding** — "Returna" (co-branded with RDT) vs. "RDT-powered-by-Returna" vs. white-labelled. Signals different stories
6. **Returna ISO 27001 timeline** — credible target date (Q3 / Q4?) makes phase-2 novation believable
7. **Returna data holdings today** — any KF demo / sales / discovery data already in Returna systems? DPA must cover from day 1
8. **Hub stability review** — confirm current active Hubs are stable for the initial contract period; any planned changes handled under the substitution-flexibility clause

---

_File: `returna/kornferry/agenda-enriched-2026-04-23.md`. Paste directly into a doc or export to PDF._
