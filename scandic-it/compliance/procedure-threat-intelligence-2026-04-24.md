# Threat Intelligence Procedure

**Document ID:** ISMS-PROC-020
**Version:** 1.0
**Effective:** 2026-04-24
**Owner:** Mike Andersen (ISMS Owner)
**Next review:** 2026-10-24 or upon significant change
**Classification:** Internal
**Standard alignment:** ISO/IEC 27001:2022 **A.5.7 Threat Intelligence**

---

## 1. Purpose

Establish a consistent process for collecting, analysing, and acting on information security threat intelligence relevant to Scandic IT's operations, customers, and scope — so that the ISMS remains responsive to the evolving threat landscape.

## 2. Scope

All information security threats potentially affecting Scandic IT ApS's people, facility, systems, customer data, or supply chain.

## 3. Definitions

- **Strategic threat intelligence** — long-term trends: attacker groups, motivations, geopolitical context, industry-specific risks
- **Tactical threat intelligence** — techniques, tactics, procedures, attack tools
- **Operational threat intelligence** — specific campaigns, vulnerabilities, IOCs, active exploitations
- **Threat signal** — any piece of information that may indicate a relevant threat (advisory, news item, incident report, supplier notice)

## 4. Sources

Scandic IT maintains active awareness of information security threats through the following sources, reviewed at the cadences below.

| Category | Sources | Review cadence |
|---|---|---|
| **Vendor-driven advisories** | Microsoft 365 security centre (via Montes), Certus software updates, Piceasoft advisories, Ubiquiti security notices, firewall vendor bulletins, 1Password security updates | Immediately on receipt; weekly review of accumulated notifications |
| **National / governmental** | CFCS (Center for Cybersecurity, DK) alerts · CERT.dk · ENISA bulletins · CISA advisories (for cross-border visibility) | Weekly scan; immediate if flagged critical |
| **Industry / sector** | ITAD industry press · e-waste sector incidents · data-leak / breach disclosures affecting peers · insider-theft / chain-of-custody incident reports | Weekly / as published |
| **Supplier incidents** | Any incident notification from sub-processors (Montes, Certus, Piceasoft, Danløn, carriers) | Immediate |
| **Internal signals** | Incident register, near-miss reports, findings from internal audit, customer-raised concerns | Continuous |

## 5. Severity classification and action pathway

Each threat signal is evaluated against defined criteria and actioned per the matrix below. The severity determines both the response time and the specific actions taken.

| Severity | What qualifies | Response time | Specific actions |
|---|---|---|---|
| **🔴 Critical** | Active exploitation affecting our systems, facility, or data · confirmed breach at a named sub-processor handling our data · imminent and specific threat with high likely impact on customers or operations | Immediate (same day) | 1. Halt affected operation if needed · 2. Apply patch, isolate, or contain · 3. Notify management (Mike + Kasper) · 4. Enter in Incident Register if materialised · 5. Notify affected customers per contract timelines · 6. Update Risk Register · 7. Post-incident review within 7 days |
| **🟠 High** | Newly-published vulnerability in systems we use (M365, Certus, Piceasoft, Ubiquiti, 1Password, firewall) with no active exploitation yet · supplier security advisory requiring action · targeted phishing campaign against similar organisations | Within 48 hours | 1. Apply patch or mitigation · 2. Coordinate with Montes for M365-side work · 3. Document in action log · 4. Brief staff if behavioural change needed · 5. Update Risk Register if new risk identified |
| **🟡 Medium** | Broader threat trend relevant to our sector · newly-disclosed vulnerability in non-primary systems or low-exposure components · industry incident suggesting a pattern worth tracking · minor supplier advisory | Next management review (or within the month) | 1. Discuss impact at next management review · 2. Update Risk Register if applicable · 3. Consider training or policy update · 4. Add to monthly threat-intel summary |
| **🟢 Informational** | General awareness items · updates on threat landscape · educational content · non-urgent regulatory commentary | Monthly summary | 1. Logged in monthly threat-intel summary · 2. Distributed to staff as awareness reading · 3. No direct action |

**Decision guide:**
- *Could this be exploited against us within 24 hours?* → Critical
- *Does this affect a system we actively use, and requires action within days?* → High
- *Does this represent a trend or latent risk we should track but not react to immediately?* → Medium
- *Is this useful context with no action required?* → Informational

## 6. Roles and responsibilities

| Role | Responsibility |
|---|---|
| **ISMS Owner (Mike)** | Primary owner of threat-intel monitoring; weekly review; action decisions |
| **Montes (MSP)** | First-line filter for M365-related advisories; applies patches per SLA; escalates items requiring customer-side action |
| **Management Rep (Kasper)** | Notified of commercial-relevant items (customer-impacting, reputational); signs off on responses that affect customer engagements |
| **All staff** | Report any suspicious signal (phishing attempt, odd behaviour, physical irregularity) per Incident Response Plan |

## 7. Output and reporting

- **Monthly threat-intelligence summary** — brief note covering: feeds scanned, critical/high items actioned, open items, watch-list. Filed with management review inputs.
- **Quarterly management review input** — aggregated themes, risk register updates triggered by threat intel, training or policy implications.
- **Annual review** of sources and cadences — confirm feeds remain relevant, add/remove as the threat landscape evolves.

## 8. Records generated

| Record | Retained in | Retention |
|---|---|---|
| Threat-intel log (monthly summary notes) | M365 ISMS folder | 3 years |
| Critical/High action entries | Corrective Action Log · Incident Register (if materialized) | Per Data Classification Policy |
| Risk register updates triggered by threat intel | Risk Register | Per Risk Assessment Methodology |

## 9. Cross-references

- **Clause / Control:** A.5.7 (primary), A.5.5 (Contact with authorities — CFCS, Datatilsynet), A.5.6 (Contact with special interest groups), A.5.24-A.5.27 (Incident management), A.8.8 (Management of technical vulnerabilities)
- **Procedures:** Incident Response Plan, Risk Assessment Methodology, Corrective Action Procedure
- **Inputs to:** Management Review (quarterly), Risk Register (continuous)

## 10. Approval

| Role | Name | Signature | Date |
|---|---|---|---|
| ISMS Owner | Mike Andersen | ______________________ | 2026-04-24 |
| Management Representative | Kasper Horn | ______________________ | 2026-04-24 |

## 11. Change log

| Version | Date | Changes | Responsible |
|---|---|---|---|
| 1.0 | 2026-04-24 | Initial procedure; created in response to Stage 1 audit feedback to lift A.5.7 from Partial to Implemented | Mike Andersen |
