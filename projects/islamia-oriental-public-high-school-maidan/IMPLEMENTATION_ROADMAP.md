# Codeedge Dedicated School OS — Implementation & Acceptance Roadmap (Draft)

**School:** Islamia Oriental Public High School Maidan  
**Coordinator:** Wasif / Codeedge Pakistan  
**Status:** PLAN ONLY. Requirements and roadmap preparation, **NO CODING OR LIVE ACTIVATION AUTHORIZED**.  
**Date:** 2026-10-29  
**Main inputs:** [Portals & Workflows](PORTALS_AND_WORKFLOWS.md) · [WhatsApp/SMS Automation](COMMUNICATIONS_AUTOMATION.md) · [Project Scope](README.md)

## Executive objective

Deliver one **school-owned, school-controlled dedicated management system** for pupil/teacher attendance (including appropriately safeguarded fingerprint reader integration), fee collection, auditable accounting, Parent Portal, School Portal with principal/teacher/cashier/accountant role views, parent-teacher appointment workflows and school-owned WhatsApp/SMS automated messaging, campaigns and inbound auto-handling. Use one authoritative school data store; present different permission-scoped screens, not independent conflicting copies of records.

The school must retain admin control, portability/export, backups and infrastructure credentials. No Codeedge central operator access or shared customer-data dashboards. Codeedge technical support only through explicitly granted, expiring, audited school permission. Work in a **separate private implementation repository** after later authorization; the public Wasif-project remains a documentation index only.

### Original six confirmed priority modules

1. Fingerprint device and trusted attendance event ingestion (pupils and staff, subject to child privacy gates).
2. Fee schedule, monthly invoices, collection, receipts, paid/partially-paid/unpaid/overdue.
3. Accounting ledger, bank/cash reconciliation, expenses, approvals and reports.
4. Daily/weekly/monthly teacher and student attendance from fingerprint, card or human verification.
5. Dual portal experience: Parent Portal and School Portal, with distinct principal, class-teacher, cashier/accountant permissions.
6. WhatsApp / SMS automation: scheduled notices, opt-in bulk campaigns, guardian alerts, inbound WhatsApp automated replies, secure handover to human.

## Architectural overview (proposal, subject to school approval)

```text
School-owned domain / authenticated HTTPS
  |
  +-- Parent Portal (child-scoped guardian views)
  |      | fees / receipts / dues / attendance / meetings / notifications
  |
  +-- School Portal (role-specific staff views)
  |      +-- Principal: whole-school reports, approvals, security
  |      +-- Teacher: assigned classes, verified attendance, meetings
  |      +-- Finance: invoice, collection, receipt, accounting
  |      +-- Office: admissions, data entry, operational workflows
  |
  +-- School-only API + permissions + MFA + audit logs
          |
          +-- School-dedicated PostgreSQL database & object storage
          |      +-- student / guardian / teacher / class
          |      +-- fee schedules / invoices / payments / allocations
          |      +-- balanced accounting journals / reconciliation
          |      +-- attendance events / daily verified records
          |      +-- meetings / notice history / consent / audit
          |
          +-- School-owned background jobs + event/outbox queues
          |      +-- validated billing / attendance automations
          |      +-- consent-aware SMS / WhatsApp templates
          |      +-- inbound WhatsApp webhook + staff handoff
          |
          +-- Authenticated local gateway (LAN) for fingerprint terminals
                 +-- staff/pupil approved device-local fingerprint match
                 +-- signed or otherwise authenticated event IDs
                 +-- offline cache, dedupe, clock sync, fallback attendance
```

Architecture choice: dedicated school-owned cloud + secure on-site attendance gateway is one practical *candidate*, especially if browser access from home is desired. Alternatively choose school-owned on-premises or hybrid deployment after site survey of power, internet, available IT support, safeguarding and costs. Never expose fingerprint terminals directly to the public Internet.

Suggested technology options, **not approved**: TypeScript web apps with responsive/PWA support, PostgreSQL transactional storage, school-specific auth, protected background job queue, provider-neutral messaging adapters, read-only/controlled bank reconciliation import, and a local hardware bridge using verified vendor SDK. Reuse **reviewed patterns**, not shared tenants or privileged accounts, from Codeedge's existing products. Do not transplant unresolved Supabase restrictions.

## Delivery phases — ordered gates

### Phase 0 — Discovery, governance, policies (NOT STARTED)
Tasks:
- School meeting with principal, accountant, class teachers and office staff.
- Obtain student/staff counts, number of classes and sections, fee heads, annual/term calendar, discount/late fee rules, school timings, sibling mappings, guardian contacts, languages and contact permissions.
- Document current attendance register, fee receipt process, existing cashbook, bank reconciliation and change permissions.
- Confirm current fingerprint device(s), vendor, SDK, supported offline/local matching, import/export/deletion, expected peak scans and electricity/internet reliability.
- Legal/privacy impact and need assessment for pupil fingerprints, informed guardian authorization, child-appropriate choice and equivalent non-biometric alternative.
- Written project scope, acceptance owner, operating/support contract, school-owned infrastructure/admin/key/billing and cost approval.
Deliverables: discovery workbook, process maps, user-role matrix, data retention/consent policy, initial budget envelope, scope baseline.
**Exit gate:** principal approves scope and child-biometric risk review plan. Without this, no real-person biometric enrollment.

### Phase 1 — Security and system design (NOT STARTED)
Tasks:
- Create new **private** school implementation repository **only after explicit authorization**, with isolated CI, dependency review and no real student records.
- Screen/site map; teacher, parent, principal, finance dashboard wireframes; define user stories and acceptance test cases.
- School-specific deployment selection, backups, recovery, MFA, least privilege, import/export, audit trail, encryption, secrets and incident response.
- Data contract: school, academic year, student, guardian link, class, teacher, biometric consent/event (no raw prints), fee assignment/invoice/payment/receipt/ledger, meetings, messages and delivery status.
- Interfaces: school domain services -> neutral provider contracts -> adapters; attendance identity -> validation -> daily record; fees -> double-entry mapping and reporting.
Deliverables: agreed screen designs, secure architecture, schema proposal, integration risk register, deployment/rollback strategy.
**Exit gate:** independently reviewed data/permissions and design sign-off.

### Phase 2 — School Portal and Parent Portal foundations (NOT STARTED)
Tasks:
- School-scoped login, principal/admin MFA, password/passkey recovery, staff role invites and revocation, verified parent/child linking with safe recovery.
- Principal overview scaffold, teacher's assigned classes view, finance workspace shell, guardian mobile-first home/child selector.
- Server and database authorization tests for every query; parent cannot access unrelated child, teacher unrelated class, finance other roles.
- Student, parent, staff, academic term, class and section CRUD with auditable edits and demo data only.
Deliverables: two navigable secure portal experiences and validated role permissions.
**Exit gate:** critical cross-role/cross-child isolation tests pass, with backups and audit.

### Phase 3 — Attendance & fingerprint integration (NOT STARTED)
Tasks:
- Build general attendance first using manual/QR or school-card fallback and school calendar; present/absent/late/excused, correction requests and approvals, leave/exceptions.
- Parent attendance history vs teacher assigned-class roll call vs principal school-wide view; consistent one-source-of-truth status.
- Prototype school-approved terminal with fictional/test accounts, secure local gateway, device ID, signature/authenticated events, offline queue and duplicate/replay blocking.
- Controlled staff biometric pilot if appropriate, followed by separate optional **pupil fingerprint pilot only after safeguarding, legal/privacy and parental/child consent gates**.
- Device withdrawal, terminal-level deletion, account retirement, outages and non-biometric equal treatment.
Deliverables: verified daily attendance and reports; optional approved hardware pilot.
**Exit gate:** devices cannot spoof/duplicate attendance, alternative works, guardian restrictions pass, biometric legal/privacy gate formally cleared.

### Phase 4 — Fee collection and parent statement (NOT STARTED)
Tasks:
- Per-student fee plan, academic session, invoice/fee period, sibling discount/concession/waiver and approved policy for arrears.
- Cashier payment recording, cash/bank references, unique receipts, payment allocation to one/multiple fee periods, due/part-paid/paid/overdue, printable statements, audit log and reversals.
- School fee dashboard with collection and unpaid summary; guardian sees only own child charges, verified payment/receipt, due and history.
- Payment screenshots/claims from guardians remain pending; do not turn them into settled transactions without financial verification.
Deliverables: consistent transactional fee balances and school/parent screens.
**Exit gate:** multiple payments, duplicate attempts, overpayments, reversals and two-child guardian example match across both portals.

### Phase 5 — Accounting and financial controls (NOT STARTED)
Tasks:
- Integrate verified fee collection into an auditable receivables/general ledger interface; balanced journals and controlled corrections.
- School income/expenses, petty cash, cashbook/bankbook, cash closing and reconciliation, budget control as approved.
- Principal financial reports/approval flows; accountant/cashier separation of duties; parent still sees child-only fee statement, **NOT school profit or bank data**.
- Evaluate Finance Suite/ERPNext integration **only through neutral adapter**, with explicit isolated licensing/security/acceptance review; no access to prior clients.
Deliverables: reconciled fee-to-ledger reporting and financial administration.
**Exit gate:** every receipt reconciles or is clearly marked pending, trial balance reconciles and corrections never silently delete entries.

### Phase 6 — Meetings, guardian and teacher operational workflows (NOT STARTED)
Tasks:
- Parent meeting request -> teacher availability -> school confirmation -> changes/reminders -> attendance/follow-up.
- Home dashboards integrate verified attendance and fee data. Notification history, school notices, language and accessibility controls.
- Parent portal shows secure child selector, attendance history, fee statement and meeting requests; teachers have only assigned student access.
Deliverables: complete core user journeys and consistent near-real-time or correctly labelled last-synced state.
**Exit gate:** end-to-end tests across guardian, principal, teacher and finance roles pass.

### Phase 7 — WhatsApp, SMS and school inbox automation (NOT STARTED)
Tasks:
- School-owned authorized WhatsApp Business Platform number/account and verified SMS provider; provider-neutral adapter design and school-managed credentials/billing.
- School-authored approved message templates, opt-in/opt-out ledger, class/audience selection, draft-review-approve-send/schedule workflow and delivery/budget reports.
- Transactional triggers: absence/late verification, fee due and confirmed paid, meeting reminder, school-approved announcements.
- Inbound WhatsApp webhook -> duplicate/spoof protection -> classify -> verified public FAQs / secure authenticated portal link -> staff takeover for personal/uncertain/sensitive matters. Payment screenshots never post to ledger automatically.
- Test Meta template/24-hour window, frequency controls, SMS sender rules, human handoff, retries/rate limits and cost cap.
Deliverables: compliant, school-approved bidirectional messaging; bulk WhatsApp/SMS only within consent/platform requirements.
**Exit gate:** no data leaks, no unsolicited blasts, no unauthorized bulk sending, provider tests and owner sign-off.
Reference policy: https://business.whatsapp.com/policy/

### Phase 8 — Independent QA, pilot, handover and operations (NOT STARTED)
Tasks:
- Demo-only seeded school, privacy/authorization/prompt-injection checks, fingerprint outage + alternate attendance, financial reconciliation, duplicate/failed SMS/WhatsApp, payment fraud/duplicate tests.
- School-authorized closed pilot using minimal live data **only after data/privacy acceptance**, sample classes/staff, approval of parent contacts and agreed device testing.
- Fix defects, rerun CI/security/pilot acceptance, load tests at verified enrolment counts and peak school start time.
- School owner admin/MFA, backup/restore test, key ownership, exports, device access, supplier/provider credentials, operating manual, training and emergency rollback.
- Support contract with school-controlled time-limited assistance only; Codeedge retains no hidden operator access or personal data.
Deliverables: signed acceptance record, private infrastructure handover, training and operational runbook.
**Exit gate:** signed school authorization and independent tests pass. Until then mark Pilot/Not Accepted.

## Portal completion specification

| Experience | Main pages | Verified permission |
| --- | --- | --- |
| Parent portal | Dashboard, My Children, Daily Attendance, Fee Due/Paid, Receipts, Meetings, School Notices, Account & Consent | Own verified child/children only |
| Principal portal | School Dashboard, Class & Staff Attendance, Fee Summary, Arrears, Financial Reports, Approvals, Messages, Audit, Device Status | School-owned operational access with approvals |
| Teacher dashboard | Today/Class Roster, Attendance Entry/Correction, Timetable, Meetings, approved academic features later | Assigned class/subjects only |
| Cashier/accountant dashboard | Fee Plans, Invoice, Collect Payment, Receipts, Refund Requests, Cashbook, Bank Reconciliation, Journal, Collections | Finance-role scoped with separation of duties |
| Office operations | Admissions, Student/Guardian Verification, Class Transfers, Staff Operations, Communications | Restricted school office rights |

**"Two portals" means Parent Portal and School Portal; the School Portal contains multiple separate role-specific dashboards, not a single unrestricted page.**

## Business rules that must be correct before accepting a build

- Scan -> **validated** attendance event; individual parent, own teacher/class and principal views reconcile to the same approved daily record.
- School posts valid fee payment -> receipt, pupil fee balance, school collection and finance ledger update atomically/idempotently.
- Parent cannot change fee status or attendance; can make review requests.
- No public GitHub real data, credentials or fingerprint images. Even biometric templates require verified device-local protected storage, withdrawal/deletion process and separate risk approval.
- Always allow non-biometric pupil attendance (e.g. school card or teacher confirmation) without penalty.
- All privileged edits, grants, waivers, refunds, attendance corrections and mass communications logged and authorization-controlled.
- SMS and WhatsApp are **notification channels**, not a replacement for secure Parent Portal authentication. A sender's phone number alone does not prove authorization to read a pupil's finances.
- WhatsApp business-initiated outbound requires applicable consent, approved templates and current platform rules, with 24-hour inbound customer-service window and accessible human handoff.
- Demo/Sandbox/Staging/Production separated; failed tests never trigger real message provider actions or real charges.
- School remains owner of all operational accounts and can export data and restore without Codeedge's ongoing participation.

## Recommended implementation order for risk and early value

Design BOTH portals early, but start with **manual/card-based attendance and verified cash-office fee collection**, then student fingerprint only after specific safeguards, then accounting integration, then full parent flows, then messaging activation. Fingerprint is high priority but must **not** block the school from achieving reliable attendance.

## Release gates/checklist (all must pass before final acceptance)

- [ ] School scope and approval recorded
- [ ] Separate approved dedicated deployment and credentials controlled by school
- [ ] School/parent/admin/teacher/finance permissions independently tested
- [ ] Student record linked to only authorized guardian(s)
- [ ] Non-biometric attendance accurate, including outages and corrections
- [ ] Scanner SDK / offline data / consent / deletion / alternative checked; pupil biometric optional and gated
- [ ] Fee balances, partial payments, receipts and corrections verified
- [ ] Double-entry accounting and cash-bank reconciliation approved by accountant
- [ ] School and parent read the same source of truth, with data minimization
- [ ] SMS / WhatsApp vendor approved, sender and templates verified, consent and human takeover tested
- [ ] No sensitive student data in public repositories or centralized Codeedge systems
- [ ] Disaster recovery restore, logs, monitoring and school staff training tested
- [ ] Written school acceptance and Codeedge access revoked by default

## Schedule and budget — not committed

No credible binding budget or completion date exists without: enrolled student count, peak scans, number of campuses, fingerprints devices/vendor, school network/electricity, data migration quality, fee structure complexity, preferred payment rails, messaging monthly volume and development team capacity. Ask for this at Phase 0. Cost categories include engineering/design/security review; school-owned hosting/backups/domain; biometric hardware installation/support; SMS/WhatsApp and third-party fees; training and ongoing maintenance. Never promise free or unlimited messages.

## Scope control

- This is a **roadmap** and not an instruction to implement, create private repositories, purchase devices, deploy a backend, send WhatsApp/SMS or enroll fingerprints.
- Further user requirements should be added as change requests, classified must-have vs optional and signed off before coding.
- Existing Codeedge repositories remain untouched; Wasif-project may carry public **non-sensitive planning documents only**.

**Roadmap baseline: v0.1 / Awaiting school discovery and approvals.**

## New scope item — Phase insert: Complaint Center & Student Concerns (module 7)

[Full complaint/case requirements](COMPLAINTS_AND_DISCIPLINE.md) are **confirmed as desired functionality** while implementation remains unauthorized. The existing nine phases 0–8 are unchanged in count; expand them as follows:

| Phase | Additions |
| --- | --- |
| 0 Discovery | Complaint handling policies, child safety escalation, subject/alternate reviewer, reporting routes, guardian contact and case retention rules |
| 1 Architecture | Data model for protected cases, allegations versus findings, appeal/reopen, assignment and encrypted communications, permission matrix |
| 2 Portals | Parent Submit/My Complaints; School Principal Case Dashboard; Teacher Report Student Concern; confidential safeguarding lane |
| 6 Workflows | Case intake, triage, investigation, human resolution, child-concern history, teacher-specific counts by status, approved parent response |
| 7 Communications | Case-linked approved WhatsApp/SMS notification, guardian verification, staff phone contact log; future optional telephony after approval |
| 8 Independent QA | Data isolation, case subject conflict of interest, child safeguarding, fair nonpunitive reporting, audit, message and call log acceptance |

**Gate:** Do not publish public teacher complaint rankings, share child sensitive case contents with unverified guardians, or automate disciplinary punishment. Complaint counts distinguish allegations, duplicates and substantiated findings. No real communication without school-approved consent and provider policy. No call audio recording by default. School retains all data and support permission.


## Bilingual acceptance requirement — Urdu + English (confirmed 2026-10-29)

[Detailed bilingual design & examples](BILINGUAL_LANGUAGE_POLICY.md). This is a **cross-cutting requirement** across the existing nine phases, not a new phase and not approval to code.

| Phase | Language deliverable |
| --- | --- |
| 0 Discovery | Parent/teacher language needs, school terminology, approval process for official Urdu/English messages, optional bilingual default |
| 1 Architecture | Urdu Unicode + RTL rendering policy, immutable original-language content, localized versions, signed/approved template mapping and language-aware audit records |
| 2 Portals | English-first navigation, parent language preference, complaint/message editors and content display in Urdu or English |
| 4 Fee | Confirm fee reminders, balances, PKR numbers, receipts and parent notices display correctly in authorized language |
| 6 Meetings & Complaints | Parent/teacher complaints and school replies in Urdu/English; reviewed translations separated from original cases |
| 7 WhatsApp/SMS | Urdu/English/bilingual templates, bulk segmentation by language, inbound language detection/handoff, Unicode SMS cost and provider restrictions |
| 8 QA | End-to-end handset, browser, print/export, privacy, approved translation, consent, template, encoding and recipient-language tests |

Do not auto-translate sensitive child/staff allegations for direct dispatch without human sign-off. UI defaults English, but user-generated communications and complaint records must remain correctly legible in Urdu or English. **No coding or integration activation authorized.**
