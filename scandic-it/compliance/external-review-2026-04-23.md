# External review — Scandic IT ISMS documentation

**Prepared:** 2026-04-23 (evening before Stage 1 audit)
**For:** Mike Andersen
**Scope:** 6 priority docs reviewed against ISO 27001:2022 and ISO 9001:2015
**Overall:** Documentation is **step-1 ready.** 10 specific fixes below will remove the most likely findings.

---

## 🔴 Fix tonight (highest finding risk)

### 1. Mike cannot be both internal auditor and ISMS owner
**Why:** ISO 19011 explicitly prohibits auditing your own work. This is the single most likely finding tomorrow.
**Fix:** Have Kasper co-sign the Internal Audit Report as Independent Reviewer with a short statement that he verified the findings. Add an acknowledgment to the report: *"Strict auditor independence not feasible at current scale; compensating controls = independent review by Management Rep; external internal auditor planned for 2026 Q4 cycle."*
**Doc:** Internal Audit Report — April 2026 · Clause 9.2

### 2. Methodology and Risk Register use different scales
**Why:** Auditors cross-reference docs. The two use incompatible likelihood bands (years vs %), different impact labels ("Catastrophic" vs "Severe"), and different risk appetite labels ("Moderate" vs "Medium").
**Fix:** Pick one version and make both docs match verbatim.
**Docs:** Risk Assessment Methodology, Risk Register

### 3. Risk Register missing Inherent vs Residual scores
**Why:** Your own methodology (Section 5) specifies both. The register has one unlabeled score.
**Fix:** Add an Inherent column next to the existing score. Can use best-guess pre-control numbers — just annotate what you already have.
**Doc:** Risk Register

### 4. All 27 risks owned by Mike
**Why:** ISO expects per-risk ownership. One person owning everything creates a key-person risk (which is literally R-P03, accepted by the key person).
**Fix:** Reassign 5-8 risks to Kasper — ideally Compliance (R-C01/02/03), Third-party (R-3P01/04), and R-P03 itself (Mike shouldn't own his own key-person risk).
**Doc:** Risk Register

## 🟡 Fix if time (auditor will flag, not a dealbreaker)

### 5. 46 of 93 SoA controls marked "Partial" with no target dates
**Why:** Partial is acceptable for step-1 if each has a plan. Currently most say "Informal" or "Planned enhancement" without owner/date.
**Fix:** Add a target date + owner to each Partial. Cross-reference the Pre-Certification Checklist where applicable.
**Doc:** Statement of Applicability · Clause 6.1.3

### 6. Cross-reference mismatch: risks marked "Controlled" against Partial SoA controls
**Why:** R-C01 (GDPR non-compliance) cites A.5.34 as its control. A.5.34 is Partial in the SoA. Yet R-C01 shows "Controlled."
**Fix:** Either promote A.5.34 to Implemented with evidence, or change R-C01 from "Controlled" to "Partial — treatment in progress."
**Docs:** Risk Register × SoA

### 7. Asset Inventory missing customer-devices-in-processing
**Why:** Your whole business is processing customer devices. Inventory has 9 PCs + infrastructure but no customer-device category. Risk Register references these but the inventory doesn't.
**Fix:** Add a paragraph: *"Customer devices in processing — tracked per job in Certus / Aiken-Picea / External workflow system. Chain of custody maintained per A.5.9 / A.5.28."* That single paragraph closes the gap.
**Doc:** Asset Inventory

### 8. "External workflow software" unnamed in 3 places
**Why:** Appears in Risk Register R-3P03, Asset Inventory SW-004/TP-004 — never named. Auditor will ask.
**Fix:** Name the vendor.
**Docs:** Risk Register, Asset Inventory

### 9. BCP tabletop status inconsistent
**Why:** Gap Analysis says tabletop is a "controlled improvement item." Auditor Handover Note references "Business Continuity Tabletop Record — April 2026" as existing.
**Fix:** Reconcile. Either the tabletop exists (update Gap Analysis) or it's still pending (update handover note).
**Docs:** Gap Analysis × Auditor Handover Note

### 10. Management Review was 45 minutes
**Why:** 45 min for 13 required ISO 9.3 topics reads as light. Auditor may challenge.
**Fix:** Add a line clarifying pre-work: *"Pre-work: 2 hours of document review prior to the meeting. Formal session: 45 minutes."* — if that's accurate.
**Doc:** Management Review Minutes — April 2026 · Clause 9.3

---

## Bottom line

Documentation coverage and structure are good. The step-1 audit will pass. Fixing items **1-4 tonight** removes the highest-risk findings. Items 5-10 are "will be raised" but not blockers.

Signatures are blank across multiple docs (Methodology, Register, SoA, MR Minutes, IA Report). Verify portal "Approved" status satisfies — otherwise sign before tomorrow.

Per-doc reviews available in full detail — ask if any section needs expansion.
