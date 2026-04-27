# Technician / Employee Onboarding Process

**Document ID:** QMS-PROC-012
**Version:** 1.0
**Effective:** 2026-04-24
**Owner:** Mike Andersen (Operations / HR)
**Next review:** 2026-10-24 or upon significant change
**Classification:** Internal
**Standard alignment:** ISO 9001:2015 Clause 7.2 (Competence) · ISO/IEC 27001:2022 (A.6.1, A.6.2, A.6.3, A.6.6)

---

## 1. Purpose

This process describes how a new technician or employee is brought on board at Scandic IT. It ensures every new joiner is competent, vetted, policy-aware, and safely provisioned with the access needed for their role — before they touch customer data or equipment.

## 2. Scope

All new permanent, part-time, temporary, and contracted staff joining Scandic IT in roles that touch the ISMS / QMS scope. Covers warehouse technicians, quality technicians, administrative staff, and external contractors such as the freelance bookkeeper.

## 3. Roles

| Role | Responsibility |
|---|---|
| **Hiring manager (Mike)** | End-to-end responsibility for a new hire's onboarding |
| **Management Rep (Kasper)** | Sign-off on employment contract; approve access for sensitive roles |
| **ISMS Owner (Mike)** | Ensure security awareness training is completed before access granted |

## 4. Process flow

### Step 1 — Role definition and selection
- Role description documented (responsibilities, required competence, scope of access)
- Interview process conducted
- Selected candidate identified
- **Output:** candidate offer letter

### Step 2 — Reference and background checks
- References contacted for prior employment (minimum one)
- For roles with access to customer data or high-value assets: additional background check proportional to role risk
- **Refers to:** HR Security Policy, control A.6.1 Screening
- **Output:** references log; background check record where applicable

### Step 3 — Employment contract and confidentiality
- Contract signed covering:
  - Role, reporting line, terms
  - Confidentiality obligations (explicit clause)
  - Compliance with Scandic IT policies
  - Post-termination obligations (return of assets, non-disclosure)
- For contractors: separate NDA signed
- **Refers to:** HR Security Policy, control A.6.2, A.6.6
- **Output:** signed contract / NDA on file

### Step 4 — Facility induction
- Physical tour of Tarmvej 8: office, depot, erasure area, shredder area, emergency exits, first aid, fire extinguishers
- Safety briefing: handling of electronics, safe lifting, electrical safety
- Introduction to the team
- **Output:** induction checklist signed

### Step 5 — Security awareness training
- Full Security Awareness Training completed — covers:
  - Information security policies (all 9)
  - Data Classification and handling
  - Password management (1Password)
  - Phishing and social engineering awareness
  - Physical security and chain of custody
  - Incident reporting
- Quiz completed and passed
- **Refers to:** Security Awareness Training Record, Attendance Record, Quiz Record
- **Output:** training + attendance + quiz records

### Step 6 — Policy acknowledgment
- New joiner signs acknowledgment that they have read, understood, and will comply with:
  - Acceptable Use Policy
  - Asset Management Policy
  - Data Classification Policy
  - HR Security Policy
  - Physical Security Policy
  - Access Control Policy
  - Supplier & Third-Party Security Policy (if relevant to role)
- **Output:** signed policy acknowledgment (added to HR file)

### Step 7 — Access provisioning
- **Physical:** biometric depot access configured; visitor policy briefed
- **Logical:** M365 account created by Montes; role-based access applied per Access Control Policy; 1Password vault access if role requires it
- **Operational tools:** Certus, Aiken/Piceasoft, workflow system — access limited to role requirements (least privilege)
- Granted only after steps 3-6 are complete
- **Refers to:** Access Control Policy, control A.5.15, A.5.18
- **Output:** access provisioning record

### Step 8 — Role-specific technical training
- Warehouse technician: Certus erasure workflow, Aiken/Piceasoft diagnostics, OMS900 shredder operation, chain of custody procedures
- Quality technician: grading criteria, certificate verification process
- Admin / commercial: workflow system, reporting formats, customer communication
- Bookkeeper (freelance): M365 financial scope only, Danløn as applicable
- **Output:** role-competence checklist signed by new joiner and hiring manager

### Step 9 — Buddy / shadowing period
- New joiner paired with experienced technician for first 1-2 weeks depending on role complexity
- Independent work authorised only after buddy signs off on core competencies
- **Output:** buddy sign-off record

### Step 10 — Competence confirmation and live status
- Hiring manager confirms new joiner is competent for independent work
- New joiner moves to live status in HR records
- Enrolled in annual refresher training cycle (Security Awareness + role-specific)
- **Output:** competence record filed; annual refresher scheduled

## 5. Records generated

| Record | Step | Retained in |
|---|---|---|
| Offer letter | 1 | HR file (M365) |
| References log / background check record | 2 | HR file (M365, restricted access) |
| Signed employment contract / NDA | 3 | HR file |
| Induction checklist | 4 | HR file |
| Security Awareness Training, Attendance, Quiz records | 5 | Security Awareness Training Record |
| Policy acknowledgment | 6 | HR file |
| Access provisioning record | 7 | Access Control records |
| Role-competence checklist | 8 | Competence & Training Record |
| Buddy sign-off | 9 | Competence & Training Record |
| Live-status competence confirmation | 10 | Competence & Training Record |

## 6. Ongoing obligations after onboarding

- Annual Security Awareness refresher + quiz
- Annual performance / competence review
- Policy re-acknowledgment when any policy is materially updated
- Immediate notification of any access change (role change, additional responsibilities, termination)

## 7. Offboarding linkage

When an employee or contractor leaves, the Offboarding Checklist is triggered. This ensures:
- Physical and logical access removed promptly
- All assets returned
- Confidentiality obligations reinforced in exit discussion
- Access Control Policy followed to closure

**Refers to:** Offboarding Checklist, control A.6.5

## 8. Cross-references

- **Policies:** HR Security Policy, Acceptable Use, Access Control, Physical Security, Data Classification, Supplier & Third-Party Security
- **Procedures:** Competence & Training Procedure, Offboarding Checklist, Security Awareness Training Procedure
- **Records:** All listed in §5 above

## 9. Approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Operations / HR Owner | Mike Andersen | ______________________ | 2026-04-24 |
| Management Representative | Kasper Horn | ______________________ | 2026-04-24 |

## 10. Change log

| Version | Date | Changes | Responsible |
|---|---|---|---|
| 1.0 | 2026-04-24 | Initial document; created during Stage 1 audit | Mike Andersen |
