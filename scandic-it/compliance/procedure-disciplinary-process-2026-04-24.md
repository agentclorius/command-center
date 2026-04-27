# Disciplinary Process

**Document ID:** ISMS-PROC-021
**Version:** 1.0
**Effective:** 2026-04-24
**Owner:** Mike Andersen (ISMS Owner / HR)
**Next review:** 2026-10-24 or upon significant change
**Classification:** Internal
**Standard alignment:** ISO/IEC 27001:2022 **A.6.4 Disciplinary Process**

---

## 1. Purpose

Establish a formal, proportionate, and documented process for handling information-security policy violations by employees, contractors, and other personnel working within Scandic IT's management-system scope. This procedure implements control **A.6.4** of ISO 27001:2022 and supplements Section 4.4 of the HR Security Policy (ISMS-POL-004).

## 2. Scope

All individuals with access to Scandic IT's information, systems, or facility — including permanent employees, part-time staff, temporary workers, contractors (e.g. the freelance bookkeeper), and any third-party personnel acting under Scandic IT's direction while in scope.

## 3. Principles

Every disciplinary action must be:

- **Fair** — proportionate to the severity and intent of the violation
- **Consistent** — similar violations result in similar outcomes, regardless of individual
- **Documented** — every step is recorded and retained
- **Confidential** — discussed only with those with a legitimate need to know
- **Compliant** — with Danish employment law, GDPR, and Scandic IT's HR Security Policy
- **Evidence-based** — action is never taken on suspicion alone; facts are established first

## 4. Roles and responsibilities

| Role | Responsibility |
|---|---|
| **ISMS Owner / HR (Mike)** | Owns the disciplinary process; receives reports; decides investigation; leads hearings |
| **Management Representative (Kasper)** | Second reviewer on Serious / Gross cases; independent sign-off; customer-impact assessment if relevant |
| **Reporting employee** | Reports observed or suspected violations via the Incident Response Plan or directly to Mike |
| **Affected employee** | Has the right to be heard, to be represented if applicable, and to appeal |
| **External advisor** | Danish employment-law counsel consulted for Serious / Gross cases before termination |

## 5. Severity classification

Severity determines the action taken. Mapped from HR Security Policy §4.4.

| Severity | Qualifying criteria | Examples | Typical action |
|---|---|---|---|
| **🟢 Minor** | Isolated lapse · no customer or data impact · no intent · easily corrected | Unlocked workstation · minor policy oversight · missed training deadline | Verbal warning + coaching + additional training |
| **🟡 Moderate** | Repeated minor violations · sharing of Internal-classified data externally without authorization · breach of procedure with limited impact | Emailing internal documents to personal address · repeated password-hygiene lapses · failure to follow acceptable-use policy | Written warning + mandatory refresher training + documented follow-up |
| **🟠 Serious** | Sharing of Confidential data · deliberate circumvention of security controls · negligence causing real or potential customer-data exposure | Disabling endpoint protection · bypassing access control · sharing customer data outside the authorised chain | Final written warning + access restriction + formal review |
| **🔴 Gross** | Intentional data theft · deliberate sharing of Restricted data · fraud · sabotage · willful breach with malicious intent | Exfiltrating customer data · tampering with erasure certificates · physical theft of customer devices | Termination + potential civil or criminal legal action · regulatory notification if personal data is involved |

## 6. Process steps

### Step 1 — Detection / report
- Violation detected via incident report, internal audit, access-log review, customer complaint, or supplier notification
- Reported to Mike (ISMS Owner) within 24 hours of detection
- For anonymous or whistle-blower reports: route via email or direct conversation; protect reporter identity
- **Record:** entry in the internal incident register

### Step 2 — Initial assessment (within 3 working days)
- Mike assesses whether a potential violation has occurred
- Checks: policy applicability · supporting evidence · severity range
- Outcome: (a) no-case, close with note · (b) formal investigation required
- For Serious / Gross cases: Kasper consulted at this step

### Step 3 — Investigation (within 10 working days of Step 2)
- Evidence gathered: logs, records, witness accounts, physical evidence
- Interviews conducted where appropriate, with two company representatives present
- Subject of investigation informed of the allegation and given the opportunity to respond
- Investigation principles respected (fair, confidential, GDPR-compliant, evidence-based)
- External counsel involved if legal advice required
- **Record:** investigation file (retained per retention policy)

### Step 4 — Determination
- Mike (with Kasper for Serious / Gross) reviews evidence
- Determination made: no violation · Minor · Moderate · Serious · Gross
- Rationale documented
- **Record:** written determination with reasoning

### Step 5 — Decision and action
- Action selected per the severity table in §5
- For Serious / Gross: Kasper signs off; external counsel consulted for termination or legal action
- Action implemented:
  - Minor: verbal warning recorded
  - Moderate: written warning + training plan
  - Serious: final warning + access adjustment
  - Gross: termination per Danish employment law + legal process
- **Record:** signed decision letter

### Step 6 — Notification to subject
- Affected employee notified in writing within 3 working days of decision
- Notification states: nature of the violation, evidence, severity, action taken, right to appeal
- Delivered in person where possible; in writing where not
- **Record:** acknowledged copy of notification

### Step 7 — Appeal (if exercised)
- Subject has **10 working days** from notification to appeal in writing
- Appeal reviewed by Kasper (or external advisor if Kasper was involved in Step 5)
- Appeal outcome: upheld · modified · overturned
- Final outcome recorded and communicated within 10 working days
- **Record:** appeal file and outcome letter

### Step 8 — Implementation and follow-up
- Technical actions implemented (access restriction, termination, revocation)
- HR actions implemented (contract termination, final pay, offboarding checklist if applicable)
- Customer notification if personal data was involved (per Incident Response Plan + GDPR breach-notification rules)
- Regulatory notification to Datatilsynet if required

### Step 9 — Closure and lessons learned
- Case formally closed in the incident register
- Systemic factors (was a control missing? did a policy fail?) reviewed
- Corrective action raised if a systemic issue is identified
- Case feeds into management review as trend / learning input
- **Record:** closure note; corrective action entry if relevant

## 7. Timelines (at a glance)

| Step | Target timeline |
|---|---|
| Detection → report | Within 24 hours of detection |
| Initial assessment | Within 3 working days |
| Investigation | Within 10 working days of initial assessment |
| Determination → notification | Within 3 working days of determination |
| Appeal window | 10 working days from notification |
| Appeal review | Within 10 working days of appeal receipt |

Timelines can be extended for complex cases; any extension is documented with rationale.

## 8. Records and retention

All disciplinary case records are stored securely in M365 (restricted HR folder), retained per the Data Classification Policy, and accessible only to:

- ISMS Owner / HR (Mike)
- Management Representative (Kasper)
- External legal counsel (where engaged)

Records include: initial report, investigation file, interview notes, determination, decision letter, notification, appeal file (if any), closure note.

Retention: minimum duration required by Danish employment law and GDPR, or the period stipulated in the Data Classification Policy — whichever is longer.

## 9. Awareness

The disciplinary process is:

- Included in **Security Awareness Training** for all new hires (onboarding)
- Re-confirmed in the **annual refresher**
- Summarised in the **Technician / Employee Onboarding Process** (QMS-PROC-012) at policy-acknowledgment step
- Referenced in employment contracts and NDAs

## 10. Cross-references

- **HR Security Policy** (ISMS-POL-004) Section 4.4 — foundation
- **Incident Response Plan** — channel for reporting violations
- **Access Control Policy** — for access adjustments resulting from disciplinary action
- **Data Classification Policy** — for data-handling severity
- **Offboarding Checklist** — for termination cases
- **Technician / Employee Onboarding Process** (QMS-PROC-012) — for awareness

## 11. Approval

| Role | Name | Signature | Date |
|---|---|---|---|
| ISMS Owner / HR | Mike Andersen | ______________________ | 2026-04-24 |
| Management Representative | Kasper Horn | ______________________ | 2026-04-24 |

## 12. Change log

| Version | Date | Changes | Responsible |
|---|---|---|---|
| 1.0 | 2026-04-24 | Initial procedure; created in response to Stage 1 audit feedback to formalise the disciplinary process previously summarised only in HR Security Policy §4.4 | Mike Andersen |
