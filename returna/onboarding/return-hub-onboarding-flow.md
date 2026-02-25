# Return Hub Onboarding Flow

_Version 1.0 — 2026-02-09_

## Overview

This document defines the step-by-step process for onboarding new Return Hub partners from first contact to active hub status.

---

## Onboarding Stages

```
┌──────────┐    ┌───────────┐    ┌──────────┐    ┌─────────┐    ┌────────┐
│ PROSPECT │ → │ QUALIFIED │ → │ CONTRACT │ → │  SETUP  │ → │ ACTIVE │
└──────────┘    └───────────┘    └──────────┘    └─────────┘    └────────┘
   1-2 weeks      1-2 weeks       1-2 weeks      2-4 weeks      Ongoing
```

**Total time to Active: 5-10 weeks**

---

## Stage 1: PROSPECT (1-2 weeks)

### Entry Points
- Inbound via Typeform survey
- Outbound via Returna partner outreach
- Referral from existing partner
- Conference/event meeting

### Actions
1. **Initial contact** — email/call to introduce Returna
2. **Typeform completion** — partner fills out survey
3. **Basic qualification** — automated scoring check
4. **Discovery call scheduled** — if passes initial criteria

### Typeform Data Collected
- Company name, location, website
- Contact person + role
- Services offered (ITAD, refurb, recycling, logistics)
- Certifications held
- Monthly processing capacity
- Geographic coverage
- Current technology stack
- Motivation for joining Returna

### Exit Criteria → QUALIFIED
- [ ] Typeform completed
- [ ] Passes basic scoring threshold (≥60 points)
- [ ] Discovery call scheduled

---

## Stage 2: QUALIFIED (1-2 weeks)

### Actions
1. **Discovery call** — understand capabilities, goals, fit
2. **Capability verification** — validate certifications, facilities
3. **Scoring finalization** — complete partner-scoring-system.md
4. **Tier assignment** — Cat 1/2/3 based on capabilities
5. **Volume discussion** — expected monthly devices
6. **Commercial terms review** — pricing, splits, SLAs

### Discovery Call Agenda (45 min)
1. Introductions (5 min)
2. Returna platform overview (10 min)
3. Partner capabilities deep-dive (15 min)
4. Questions & concerns (10 min)
5. Next steps (5 min)

### Qualification Checklist
- [ ] Confirmed ITAD processing capability
- [ ] Certifications verified (ISO, R2, etc.)
- [ ] Facility location confirmed
- [ ] Processing capacity meets minimum (≥500 devices/month)
- [ ] No competing platform ownership
- [ ] Geographic coverage defined
- [ ] Decision-maker engaged

### Tier Assignment Criteria

| Tier | Category | Capabilities | TRC Level |
|------|----------|--------------|-----------|
| Cat 1 | Basic Processing | Intake, data erasure, basic testing | Level 1 |
| Cat 2 | Data & Diagnostics | + Advanced diagnostics, grading | Level 2 |
| Cat 3 | Full Refurb | + Repair, refurb, box programs | Level 3-4 |

### Exit Criteria → CONTRACT
- [ ] Discovery call completed
- [ ] Score ≥70 points (Priority tier)
- [ ] Tier assigned
- [ ] Commercial terms discussed
- [ ] Internal approval (Kasper/Mike)

---

## Stage 3: CONTRACT (1-2 weeks)

### Actions
1. **Partnership agreement draft** — send standard template
2. **Legal review** — partner reviews with their legal
3. **Negotiation** — adjust terms if needed
4. **Signature** — both parties sign
5. **NDA execution** — if not already in place

### Partnership Agreement Key Terms
- Service scope (which services partner will provide)
- Geographic territory (exclusive/non-exclusive)
- Processing SLAs (turnaround times)
- Pricing structure (execution fees, resale splits)
- Data security requirements
- Compliance obligations (GDPR, certifications maintenance)
- Insurance requirements
- Term and termination
- Liability and indemnification

### Commercial Model Recap
- **Execution fee**: Partner receives 90% (Returna takes 10% platform fee)
- **Resale split**: 70% enterprise / 30% Return Hub
- **Pricing tiers**: Based on volume commitments

### Exit Criteria → SETUP
- [ ] Partnership agreement signed
- [ ] NDA signed (if required)
- [ ] Payment terms confirmed
- [ ] Insurance verified

---

## Stage 4: SETUP (2-4 weeks)

### Actions
1. **Platform access** — create partner account in Returna
2. **Warehouse module setup** — configure ERP features
3. **Integration configuration** — API, webhooks, carrier integrations
4. **Training sessions** — platform walkthrough, best practices
5. **Test transactions** — pilot devices through system
6. **Go-live preparation** — final checks

### Technical Setup Checklist
- [ ] Partner account created
- [ ] Users added with appropriate roles
- [ ] Warehouse location(s) configured
- [ ] Processing workflows defined
- [ ] Carrier integrations tested (DHL, UPS, etc.)
- [ ] Erasure tool integration (Blancco, etc.)
- [ ] Diagnostics integration (if applicable)
- [ ] Branding/labels configured
- [ ] Reporting access granted

### Training Program
| Session | Duration | Topics |
|---------|----------|--------|
| Platform Overview | 1 hour | Navigation, dashboards, tickets |
| Warehouse Operations | 2 hours | Intake, processing, disposition |
| Logistics & Shipping | 1 hour | Labels, tracking, carriers |
| Reporting & Compliance | 1 hour | Reports, certificates, audit trail |
| Admin & Settings | 30 min | Users, preferences, integrations |

**Total training: ~5.5 hours**

### TRC Certification Pathway (Optional)
Partners wanting to upgrade tier can pursue TRC certification:
- Level 1 Applicator → Cat 1 baseline
- Level 2 Advanced → Cat 2 qualification
- Level 3 Screen Specialist → Cat 3 preparation
- Level 4 Master Refurbisher → Full Cat 3

### Test Transaction Requirements
- [ ] Minimum 10 test devices processed
- [ ] Full workflow completed (intake → erasure → grading → disposition)
- [ ] Certificates generated correctly
- [ ] Reporting accurate
- [ ] No critical issues identified

### Exit Criteria → ACTIVE
- [ ] Platform fully configured
- [ ] Training completed
- [ ] Test transactions successful
- [ ] Partner sign-off received
- [ ] Go-live date confirmed

---

## Stage 5: ACTIVE (Ongoing)

### Go-Live Actions
1. **Announcement** — internal notification to sales team
2. **First real tickets** — route initial enterprise volume
3. **Close monitoring** — watch first 30 days closely
4. **Feedback collection** — weekly check-ins initially

### Ongoing Support
- Dedicated partner success contact
- Slack/Teams channel for real-time support
- Monthly performance reviews
- Quarterly business reviews (QBRs)

### Performance Metrics Tracked
- Devices processed / month
- Average turnaround time
- Data erasure compliance rate
- Resale value recovery rate
- Customer satisfaction scores
- SLA adherence

### Escalation Path
1. Partner success manager
2. Operations team (Mike)
3. Commercial team (Kasper)
4. Executive escalation

---

## Automation Opportunities

### Typeform → Database → Routing (Spec for Christian)

**Flow:**
```
Typeform Submission
       ↓
Webhook to Returna API
       ↓
Auto-create prospect record in database
       ↓
Auto-score based on Typeform responses
       ↓
If score ≥ 60: Notify Kasper for review
If score < 60: Auto-respond with "not a fit" email
       ↓
Kasper approves → Move to QUALIFIED
Kasper rejects → Archive with reason
```

**Database Fields:**
- company_name, website, country, city
- contact_name, contact_email, contact_phone, contact_role
- services[] (array: itad, refurb, recycling, logistics)
- certifications[] (array: ISO27001, ISO14001, R2, etc.)
- monthly_capacity (number)
- coverage_regions[] (array of regions)
- current_tech_stack
- motivation (text)
- score (calculated)
- tier (Cat 1/2/3)
- status (prospect/qualified/contract/setup/active/rejected)
- created_at, updated_at
- notes (text)

**Notifications:**
- New submission → Slack #partner-pipeline
- Score ≥ 80 → Priority alert to Kasper
- Status change → Log to activity feed

---

## Templates Needed

1. **Outreach email templates** — ✅ Already created (6 templates)
2. **Discovery call agenda** — Defined above
3. **Partnership agreement template** — TBD (legal review needed)
4. **NDA template** — TBD (legal review needed)
5. **Training materials** — Platform documentation
6. **Go-live checklist** — Defined above

---

## Appendix: Partner Scoring System

Reference: `/returna/partner-scoring-system.md`

**Quick scoring guide:**
- 85-100: 🟢 Priority — fast-track onboarding
- 70-84: 🟡 Standard — normal process
- 60-69: 🟠 Conditional — needs specific improvements
- <60: 🔴 Not a fit — reject or defer

---

_Document owner: Kasper Horn_
_Last updated: 2026-02-09_
