# Returna Non-Negotiable Requirements (Platform Safety & Trust Layer)

_Source: Kasper's ChatGPT draft — R2v3 version, to be adapted to EU-first (ISO 27001, ISO 14001, WEEE)_

These requirements cannot be overridden by enterprises, even if requested. Enterprises may add stricter requirements, but never relax these.

## 1️⃣ Information Security for Data-Bearing Assets

**✅ Rule:** Any ITAD partner handling data-bearing assets must have:
- ISO 27001 certification OR be explicitly covered by a parent company's ISO 27001 scope (documented)
- AND Use a Returna-approved data erasure tool
- Produce device-level erasure certificates
- Map erasure evidence to assets inside Returna

**❌ Not allowed:**
- "We follow ISO practices but are not certified"
- Customer waivers for non-ISO partners
- Manual or unverifiable erasure proof

**Why non-negotiable:** Table-stakes for enterprise risk, audits, and insurance. Returna becomes legally and reputationally exposed otherwise.

**Flexibility:** None for enterprise data-bearing devices. Limited exceptions only for scrap-only assets or verified non-data-bearing equipment.

## 2️⃣ Certified Recycling & Downstream Control

**✅ Rule:** Any ITAD partner performing recycling, destruction, or downstream transfer must have:
- R2v3, e-Stewards, or an equivalent Returna-approved standard
- Documented downstream vendors
- Certified recycling/destruction evidence per asset or batch

**❌ Not allowed:**
- "Local recycler we trust"
- Unverified downstream chains
- Customer opt-outs for certified recycling

**Why non-negotiable:** ESG and environmental liability flows upstream. Downstream risk is invisible until it becomes a scandal.

**Flexibility:** Regional equivalents allowed only if pre-approved by Returna. No ad-hoc customer approvals.

_NOTE: For EU-first version, replace R2v3/e-Stewards with ISO 14001 + WEEE registration as baseline._

## 3️⃣ Evidence & Chain-of-Custody Integrity

**✅ Rule:** All partners must:
- Follow Returna-defined workflow steps
- Produce required evidence at each state transition
- Maintain ≥98% evidence completeness
- Accept auditability and traceability requirements

**❌ Not allowed:**
- "We do it differently"
- Offline or external evidence systems
- Completing tickets with missing proof

**Why non-negotiable:** Returna is a system of record. Without evidence, Returna is just a coordinator.

**Flexibility:** None on evidence presence. Minor flexibility on format (as long as machine-verifiable).

## 4️⃣ Data Erasure Is Mandatory Before Any Other Outcome

**✅ Rule:** For all data-bearing assets, erasure must complete successfully before:
- Repair, Refurbishment, Resale, Redeployment, Recycling

**❌ Not allowed:**
- Repair before erasure
- "Resale with wipe later"
- Customer-directed shortcuts

**Why non-negotiable:** Fundamental ITAD sequencing. Courts, insurers, and auditors all agree on this order.

**Flexibility:** None.

## 5️⃣ Tier Definitions Are Owned by Returna

**✅ Rule:**
- Tier/Category definitions are set by Returna
- Tiers determine eligibility, not preference
- Enterprises cannot redefine tiers

**❌ Not allowed:**
- "Our Tier 1 means something else"
- Custom tier logic per customer

**Why non-negotiable:** Routing, KPIs, and automation depend on tiers. If tiers are subjective, the platform breaks.

**Flexibility:** Enterprises can require minimum tier, higher tier, or specific capabilities within a tier.

## 6️⃣ Performance-Based Routing Overrides

**✅ Rule:** Returna retains the right to pause routing, throttle volume, or reroute tickets based on SLA breaches, KPI degradation, capacity issues, or compliance incidents.

**❌ Not allowed:**
- "Always route to this partner"
- Contractual guarantees that override performance reality

**Why non-negotiable:** Static routing guarantees cause silent failures. Box programs fail without dynamic control.

**Flexibility:** Enterprises can define preferences. Never absolute routing guarantees.

## 7️⃣ Repair & Refurbishment Require Both Skill AND Security

**✅ Rule:** Repair or refurbishment requires:
- ISO 27001 (data handling)
- Approved erasure tooling
- TRC-aligned refurbishment capability (or equivalent)

**❌ Not allowed:**
- TRC without ISO
- ISO without repair competence
- Customer waivers

**Why non-negotiable:** Refurb sits at the intersection of data risk + value recovery. Weakness on either side breaks trust.

**Flexibility:** Skill frameworks (TRC or equivalent) can evolve. Security requirement does not.

## 8️⃣ No Enterprise Opt-Out of Platform Guardrails

**✅ Rule:** Enterprises cannot disable compliance checks, bypass evidence requirements, or override platform safety rules.

**Why non-negotiable:** Returna must be defensible to all enterprises. One exception poisons the well for everyone.

**What Enterprises CAN Control:**
- Require additional certifications
- Restrict partner lists
- Require higher tiers
- Approve partners per country
- Exclude partners they don't trust

**Enterprises CANNOT:**
- Lower the floor
- Redefine safety
- Bypass controls
