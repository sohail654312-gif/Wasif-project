# Codeedge Dedicated School OS — Role-Based Portals and Core Workflows

**School:** Islamia Oriental Public High School Maidan  
**Coordinator:** Wasif / Codeedge Pakistan  
**Document status:** REQUIREMENTS DRAFT — NO CODING AUTHORIZED  
**Recorded:** 2026-10-29  
**Owner/operator:** School principal or school-designated administrators  
**Repository:** Public documentation only — never add real child, guardian, staff, accounting, biometric or credential data.

## 0. Explicit client instructions (confirmed)

1. A **dedicated installation** for this school, with control of the data, accounts, infrastructure, approvals and access in the school's hands. Codeedge cannot silently view school data and has **no standing admin access**.
2. The initial five priority domains in this order: **(1) fingerprint attendance, (2) fee collection, (3) accounting, (4) overall attendance, (5) role-based parent and school portals**, all connected.
3. **Two distinct application experiences**: **Parent Portal** and **School Portal** (the school portal contains permission-specific teacher, principal/admin and accountant pages, rather than giving all staff the same privileges).
4. Parent can view their own linked pupil(s)' **fees due, fees paid, payments, receipts and attendance**, in one app; school can manage and view the appropriately authorized corresponding records. Teacher sees own assigned students' attendance; principal sees school-level attendance and authorized summaries.
5. Financial and attendance records are stored **once as the authoritative source of truth**, not copied into separate parent/school ledgers. Each portal displays a scoped, live view of those same records.
6. Capture/plan/document requirements now; **do not start coding, deploy, provision, connect devices, collect real biometrics or change other repositories** without a later instruction.
7. **Sixth confirmed requirement (added 2026-10-29):** school-controlled WhatsApp automation, automated SMS, approved bulk WhatsApp/SMS, and secure inbound WhatsApp auto-handling with staff takeover. [Read the detailed Communications Automation requirements](COMMUNICATIONS_AUTOMATION.md). Parent sees own notifications and school staff control campaigns and inbox according to role. No coding or message sending authorized.

## 1. Product boundaries and portals

### A. Parent Portal (Web/mobile-responsive, with future mobile app optional)
- Secure login and guardian-to-student link established/approved by school.
- Home: child selector (support multiple siblings), relevant child attendance today, monthly attendance summary, current fees due and recent payment summary, school notices and meeting requests.
- **Attendance page:** daily/weekly/monthly history; recorded Present/Absent/Late/Excused statuses and reason/notes approved for parent viewing; alert status; request correction with staff review. No raw fingerprints or other students' attendance.
- **Fees page:** per-child fee structure assigned to that child, fee period, fee heads (tuition/admission/transport/exam if the school uses them), amounts charged, discounts and waivers, receipt numbers, amounts received, balance, dates due, state (Unpaid / Part-paid / Paid / Overdue). Download receipt/statement. Payment option is future/optional and subject to verified gateway integration; initially receipts reflect **school-verified** collections only.
- **Accounting/financial information:** guardian-facing **personal fee account statement only**; NOT the school's full accounting records, cash/bank details, salary ledger or all-student collection reports.
- **Meetings:** see teacher time availability made public to parents, request slot, see confirmation/reschedule/cancel, school notices, request corrections.
- Parent can submit a query or payment-proof claim if allowed, but **cannot post a financial ledger entry, mark a fee Paid, edit attendance or book double slots**.
- Clear language, PKR amounts, receipt print/PDF and privacy controls. Support Urdu/English after school confirmation.

### B. School Portal (Single staff-facing application, permission-appropriate pages)
- **Principal/School Owner:** overview of all authorized students, class-by-class and school-wide attendance, fee status/arrears, collection summaries, approved accounting reports, teacher attendance, hardware health, exceptions, changes approvals, messaging and system configuration.
- **Accountant/Cashier:** create authorized fee invoices/charges, collect and allocate cash/bank payments, receipts, waivers and refunds submitted for approval, school ledger, cashbook, reconciliation and collection reports. No pupil biometric templates and no unneeded academic information.
- **Teacher/Class In-charge:** assigned class roster, classroom attendance, teacher-specific attendance view, parent meeting availability, corrections submitted for approval, subject-related academic activities in later scope. No bank ledger, school payroll, or unrelated children.
- **Admissions/Office Staff (optional):** enrolment/class/guardian links, student records within role policy, approved attendance corrections and administrative correspondence. No financial posting except if specifically authorized.
- **Attendance Device Operator (optional):** maintain device mapping/health and retry queues; no general access to biometric templates or family financial information.
- School Owner determines permissions and approval chain, but must preserve separation of duties for risky financial operations and multi-factor authentication for privileged accounts.

### C. Dual-view design rule — apply to EVERY module
- **One verified event / balance / meeting record** shared across the system.
- **Parent view** = their linked child(ren)'s permitted part, generally read-only with requests allowed.
- **School view** = role-scoped operational view, reconciliation, review/approve, reporting and correction with audit.
- If a module is purely internal (general ledger, payroll, bank reconciliation, biometric configuration), parent UI shows **only the relevant derived child-facing information** or **no page**. Never expose internal confidential data merely to satisfy a two-page rule.
- Each view gets a separate authorization check in backend services AND database; UI hiding alone is insufficient.

## 2. Module specifications and ownership

| Module | Parent-facing page | Staff-facing pages / write authority | Shared records and automation |
| --- | --- | --- | --- |
| Fingerprint identity / check-in | Today's arrival and absence status, consent choice and alternative attendance request; never biometric data | Principal/attendance officer sees aggregated events, teacher sees own class, authorized device operator manages terminal, human resolves exceptions | Approved scanner validates identity locally, emits signed/idempotent attendance event; event creates attendance record; permitted parent alert |
| Fee collection | Due/paid/partial/overdue amounts by child and month, verified receipt list and statements; optional payment instructions | Cashier records collections and issues receipt; accountant reconciles; principal approves exceptional adjustments | Validated payment -> allocation to specific invoice/fee period -> ledger entry -> receipt -> instantly refreshed parent and school balances |
| Accounting | Child's personal fee statement only | Accountant journal, chart of accounts, expense vouchers, cashbook/bankbook, financial reports, reconciliation; principal approvals | Invoice receivable, posted collections, refunds/discounts/waivers, reversal entries; reports agree with fee ledger |
| Attendance (academic) | Daily attendance, history, percentage where applicable, excused/late state, absence notifications, dispute/request correction | Teacher assigned-class daily register and review; attendance officer exceptions; principal full approved reports | Scanner/manual/card events -> validated per-school attendance rules -> teacher review when needed -> principal dashboard and permitted parent view |
| Parent meetings | Request, confirmation, cancellation, rescheduling and summary shared by staff | Teacher calendar and requests; office and principal oversight | Availability validation, no double-booking, reminder with approved channel |
| Admission/student information | Own child's approved admission/class information and school notices | School office admits/updates class, handles guardian link and identity verification | School-governed student/guardian IDs, effective-dated enrolment and audit events |
| Results/homework (later) | Child-only approved report card and assignments | Assigned teacher enters, designated academic reviewer approves and publishes | Human-approved result publishing only; no school-wide view for parent |
| School announcements (later) | Own class/school notices | Authorized announcements with review and schedule | Consent/channel controls, delivery logs and opt-outs |

## 3. Core data objects / logical schema (not a database migration)

- **SchoolInstance**: dedicated school ID, name, policy settings, time zone, calendar.
- **UserAccount**: login, MFA, status, school ID, role memberships.
- **RolePermission**: actions/scope (school, class/section, student, linked child, finance).
- **Student**: internal unique student ID, school ID, class/section, enrollment state; no real student data in this repository.
- **Guardian** and **GuardianStudentLink**: verified relation, scoped child access, contact permissions.
- **Teacher** and **TeacherClassAssignment**: school staff identity and assigned classes/subjects.
- **Class**, **Section**, **AcademicSession**, **SchoolHolidayCalendar**.
- **BiometricDevice**: school-controlled device ID, firmware, integration status, location, device admin owner; NO biometrics in this model.
- **BiometricEnrollmentConsent**: guardian/staff consent or legally verified basis, scope, alternative, withdrawal, audit and deletion status; template never stored in server app.
- **AttendanceEvent**: pupil/staff ID, school ID, source (fingerprint/card/manual), terminal event ID, local event time, UTC time, signed verification/ingestion, source reference, duplicate-handling status.
- **AttendanceDailyRecord**: student ID, school day, state, source, teacher/admin verification, correction history and rationale; derived from accepted events/manual entry using school policy.
- **FeePlan**, **FeeHead**, **FeeAssignment**: amounts, due rules, enrollment period and child-specific concessions.
- **FeeInvoice**/**Charge**: student ID, period, issue date, due date, ordered line items and amount; statuses derived from outstanding balance and date.
- **Payment**/**PaymentAllocation**: verified payment with method and reference; one payment may cover multiple invoices; no guardian claim posts funds before confirmation.
- **Receipt**: unique immutable school-issued number, allocation references, reprint/void trail.
- **CreditAdjustment**/**Waiver**/**Refund**: approval/actor/reason and correction through auditable reversal, not silent deletion.
- **AccountingJournal**/**JournalLine**, **Account**, **FinancialPeriod**, **Reconciliation**: balanced double-entry posting where full accounting is enabled; cash/bank settlement records and year close.
- **MeetingRequest**/**MeetingSlot**, **Notification**, **NotificationConsent**, **DeliveryLog**, **SupportAccessGrant**, **AuditEvent**.
- Every school-specific record includes school identity and scoped access; access decisions must be server-enforced.

### Fee calculation example — explanatory, fictional data only

A student owes PKR 3,000 for a month; school staff confirms PKR 1,500 paid.
- Parent app: Charged PKR 3,000 / Verified paid PKR 1,500 / Remaining PKR 1,500 / **Part-paid**.
- Cashier app: that payment posted with a unique reference, receipt and correct fee period.
- Principal app: collections and outstanding totals updated from same ledger.
- School accountant: payment matches cash/bank record after reconciliation; unmatched payments flagged, never silently represented as settled.
- A guardian-uploaded screenshot is **not** equivalent to a verified payment or accounting posting.

## 4. Fingerprint + attendance workflows (two related, separate concerns)

**Fingerprint = one possible way to identify a person at arrival/departure.**  
**Attendance = the authoritative daily record**, which also supports teacher-verified manual or card-based records. These must not be conflated.

### Proposed scanner flow
1. Guardian/staff is informed; consent, appropriate legal basis and non-biometric alternative recorded before enrollment.
2. Vetted scanner performs matching **on trusted school-owned device**; server does not receive raw print or stored templates.
3. Authenticated gateway receives time, matched pseudonymous device reference, event ID and validation data; securely maps to school student/staff ID.
4. Event is validated: identity, device, date, school schedule, duplicates/replays, clock drift, offline backlog and whether arrival/exit.
5. Create/adjust proposed attendance event; daily attendance follows school rules and authorized review/exception process.
6. Student's guardian sees only authorized attendance state. Principal sees school level; teacher sees own assigned class only.
7. Optional guardian alert after approved policies and verified messaging permission. Failed delivery cannot erase event.
8. Withdrawal and school-leaving triggers auditable local device template deletion with confirmation, policy-based data retention, and alternative attendance.

### Student safeguards / mandatory deployment gates
- Fingerprint is **requested but not yet approved for use**. Do privacy/legal review, informed guardian consent and child-appropriate agreement; no coercion, ensure equally usable non-biometric method.
- Test device SDK, offline sync, on-device protected templates, tamper-resistance, secure deletion, support and accuracy in actual school conditions.
- If these safeguards cannot be independently verified, do not enroll student prints; attendance works through cards/teacher instead.
- No automatic punitive decisions from a scan mismatch, device outage, or attendance correction claim.
- Never retain raw fingerprint images in GitHub, app logs, analytics, support dashboard or Codeedge storage.

### Staff safeguards
- Fingerprint check-in/out for teachers with leave/late exception handling, alternate input, staff notices, audits.
- No payroll deductions based solely on scans without authorized policy and human review.

## 5. Fee and accounting workflows

### A. Monthly billing
Principal/finance approves FeePlan + academic period -> issue eligible student charges (stable invoice IDs) -> compute due -> display on parent child portal and school collection queues -> permitted reminders.

### B. Collection
Cashier searches student -> verifies relevant payer/invoice -> accepts payment through allowed method -> receipt -> allocation to appropriate charge -> reconciled or pending reconciliation status clearly shown -> update Parent and School portal views.

### C. Overdue
Due date crossed and outstanding > 0 -> outstanding status -> accountant/principal dashboard and permission-based notices to parent. **Never** auto-punish a child or deny access to class because of a ledger status.

### D. Correction / refund
Authorized request -> approval from principal/finance according to policy -> reversal/credit note/new valid posting -> audit trail and updated statement. Do not overwrite previous receipts/journals.

### E. Reporting
- **Parents:** child-specific statement by month, charges, allocations, balance, receipts, due dates.
- **Cashier:** today's collections, receipt register, students with balances, class-wise counters if authorized.
- **Accountant:** cash/bank reconciliation, receivables aging, journals, expenses, controls.
- **Principal:** total due, total collected, overdue amount, class trend, exceptions, authorized internal financial reports.
- No student names in public analytics and no cross-school reporting to Codeedge.

## 6. Access matrix

| Action / information | Parent | Assigned Teacher | Accountant/Cashier | Principal/Admin | Codeedge |
| --- | --- | --- | --- | --- | --- |
| Own linked child's attendance | Read / request correction | Assigned class read/write within policy | No by default | School read/approve | No default access |
| Scan/fingerprint raw image or template | Never | Never | Never | Not in app; device-controlled enrollment only | Never |
| Staff/pupil biometric attendance exceptions | Request for own child | Review assigned class | None | Authorized review | No default access |
| Own child's fee due/paid + receipt | Read | No | Assigned permitted students | School view | No default access |
| Post fee payment | No (claim only) | No | Yes subject to controls | Override/approval under separation of duties | No |
| General ledger / bank reconciliation | No | No | Finance roles only | Authorized finance overview/approval | No |
| Parent meeting | Request/manage own | Manage assigned appointments | No | Authorized oversight | No |
| Change school policies or users | No | No | No except designated finance policy | School owner only | No |
| Emergency tech support | No | No | No | Grant/revoke auditable time-limited access | Only as granted |

**Two portals, multiple roles, least privilege.** Teacher, accountant and principal may use separate dashboards within the School Portal.

## 7. Suggested IA / screen map (design proposal, not implemented)

```text
DEDICATED SCHOOL SYSTEM
├── Parent Portal (guardian-only authorization)
│   ├── Home (child selector, attendance today, fee balance)
│   ├── My Children
│   │   ├── Attendance History & Correction Requests
│   │   ├── Fees Due / Paid / Receipts / Statements
│   │   └── Results / Homework (future)
│   ├── Meetings and Requests
│   ├── Notices / Notifications
│   └── Profile / Consent / Security
└── School Portal (school-only roles)
    ├── Principal Dashboard
    │   ├── School-wide Attendance / Exceptions
    │   ├── Fee Collections / Outstanding / Approvals
    │   ├── Accounting Summary & Audit
    │   └── School Configuration / Permissions / Device Health
    ├── Teacher Dashboard
    │   ├── Assigned Classes / Roll Call
    │   ├── Scanner Exceptions / Corrections
    │   └── Parent Meetings / Academic Tools (future)
    ├── Finance / Cashier Dashboard
    │   ├── Student Fee Accounts / Invoices
    │   ├── Collect Payment / Issue Receipt
    │   ├── Arrears / Discounts / Refund Approval Requests
    │   └── Cashbook / Journal / Reconciliation (authorized roles)
    └── Office / Attendance Device Management
        ├── Student / Guardian Enrollment
        ├── Calendar & Attendance Exceptions
        └── Device Enrollment / Health / Sync (restricted)
```

## 8. Shared UI design principles

- Parent and school apps may be separate routes or apps, but MUST enforce role-specific backend/database authorization.
- Parent first screen surfaces child's attendance + current outstanding balance; teacher first screen surfaces today's roster; principal first screen shows aggregated operations.
- Consistent term and currency format, fee period and last-updated indicator, pending/verified status distinctions, receipt export.
- Real-time updates where safe; if offline, show last-synced time, avoid presenting unverified fees as paid.
- All correction requests tracked with states Requested / Under Review / Approved / Denied and author/reason; high-risk changes require human approval.
- Accessible mobile UI, low bandwidth, school-approved Urdu/English language, print-friendly PDF statements and offline queues only where safely supported.

## 9. Acceptance scenarios (to test later; not implemented)

1. Guardian of Student A can view A's daily attendance, dues, verified receipts and no other pupil.
2. Guardian with two children can switch between both with correctly separated fee periods.
3. A teacher can mark or review their assigned class only; cannot see unrelated children, school bank accounts or finance journals.
4. Principal sees school-wide attendance and authorized totals but cannot silently change a fee without authorization and audit.
5. A PKR 3,000 charge + PKR 1,500 verified payment displays PKR 1,500 due in both portals, with matching receipt and ledger.
6. Duplicate scan, offline queue replay, device outage and missing/withdrawn consent never create silent incorrect attendance.
7. Card/teacher manual fallback provides equivalent attendance service without punishing children.
8. Guardian submits a payment claim; portal shows pending review and does not reflect Paid until school verification/posting.
9. Waiver, refunded payment or correction retains complete, traceable history and recalculates balances correctly.
10. Codeedge cannot access personal school data without school-issued time-limited permission; revocation blocks access immediately.
11. Deletion/withdrawal workflows remove fingerprint template from scanner and leave only necessary auditable nonbiometric records under approved retention policy.
12. Student/guardian profiles and payment data remain in the school-controlled infrastructure and are never committed to this public repo.

## 10. Phase / decision status

| Decision | Status |
| --- | --- |
| Dedicated school-controlled system | Confirmed design directive |
| Parent + School portals | Confirmed |
| Fingerprint for teachers and pupils | Requested; dependent on privacy, hardware and safeguarding approval |
| Fee collection + due/paid in both portals | Confirmed functional requirement |
| School accounting + parent fee statement | Confirmed, with strict access separation |
| Attendance visibility: parent, teacher, principal | Confirmed, with scope controls |
| Hardware brand, fee policies, staff/student counts | Undecided |
| Tech stack, hosting/cloud vs on-prem, payment provider | Undecided |
| UI design, database migration, coding, deployment | Not started / not authorized |

**Next step:** Gather additional requirements from the user and school leadership. No implementation is authorized by this document.

## 11. Communications Automation — Sixth confirmed module

[Full WhatsApp, Bulk WhatsApp, SMS, Bulk SMS, Inbound Auto-Handling and School/Parent Portal specification](COMMUNICATIONS_AUTOMATION.md).

- School Portal: message composer, permission-checked recipient segmentation, template preview and approval, scheduling, provider budget, bulk sending, delivery reports, school-owned shared inbox and human handoff.
- Parent Portal: own child notices, receipts/attendance reminders and messages/preferences, with secure authenticated child information only.
- Outbound fee/attendance alerts are driven by validated underlying records; messaging must never automatically set a fee as paid or mark a child present without verified source and authorization.
- WhatsApp inbound bot answers verified school FAQs, routes personal financial/attendance queries to guardian-authenticated access and escalates sensitive or uncertain cases to authorized staff.
- Meta-approved templates/service windows, consent, sender policy, anti-spam, provider fees, child-data protection, support-access restrictions, retries and duplicate suppression are release gates.
- **Not implemented / no provider connected or live messages sent.**
