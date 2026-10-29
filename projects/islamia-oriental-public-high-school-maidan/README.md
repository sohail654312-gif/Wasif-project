# Islamia Oriental Public High School Maidan — School Automation Project

**Parent hub:** [Wasif-project](https://github.com/sohail654312-gif/Wasif-project)  
**Project owner / coordination:** Wasif (Codeedge Pakistan operations)  
**Stage:** Requirements collection — DRAFT (not built, deployed, or configured)  
**Last updated:** 2026-10-29

> اس دستاویز میں صرف ابتدائی ضروریات محفوظ کی گئی ہیں۔ اسکول کی اصل معلومات، فیس کی رقم، پالیسی، برانچز اور رابطہ تفصیلات ابھی تصدیق نہیں ہوئیں۔ مزید ضروریات بعد میں شامل کی جائیں گی۔

## مقصد / Vision

اسلامیہ اورینٹل پبلک ہائی اسکول میدان کے لیے ایک مربوط School Management & Automation System تیار کرنا، تاکہ حاضری، والدین سے رابطہ، والدین/اساتذہ کی میٹنگز، فیس وصولی اور اسکول کی اکاؤنٹنگ ایک محفوظ نظام سے چلیں۔

## 1) Student & Parent Records — بنیادی ڈیٹا

- ہر طالب علم کا منفرد ID، کلاس، سیکشن، داخلے اور فعال/غیرفعال حیثیت۔
- والدین/سرپرست کے مجاز رابطے، ایک یا کئی بچوں سے تعلق۔
- طالب علم کو متعلقہ کلاس، اساتذہ، حاضری، فیس اکاؤنٹ اور ملاقاتوں سے منسلک کرنا۔
- اصل معلومات کی درآمد/استعمال صرف اسکول کی اجازت اور محفوظ ماحول میں۔

## 2) Attendance Automation — حاضری

- کلاس اور تاریخ کے حساب سے اساتذہ حاضری درج کریں: Present / Absent / Late / Excused۔
- روزانہ کی حاضری کے ریکارڈ اور طالب علم کی ماہانہ/مدت وار رپورٹ۔
- غیرحاضری یا مسلسل غیرحاضری کے لیے قواعد پر مبنی الرٹس؛ والدین کو پیغامات **صرف اسکول کے منظور شدہ چینل، رضامندی اور قواعد کے تحت**۔
- غلط اندراج کی اصلاح، تبدیلی کرنے والے شخص اور وقت کا audit trail۔
- ڈپلیکیٹ انٹری، چھٹی، تعطیل، غیر فعال داخلہ اور نیٹ ورک کی ناکامی جیسے حالات کا تحفظ۔

## 3) Parent–Teacher Meetings — والدین کی میٹنگ

- والدین میٹنگ کی درخواست کر سکیں یا اسکول/ٹیچر میٹنگ طے کر سکے۔
- دستیاب وقت، ٹیچر، کلاس، ملاقات کی وجہ (اختیاری) اور طے شدہ وقت۔
- Appointment statuses: Requested / Confirmed / Rescheduled / Cancelled / Completed / No-show۔
- منظور شدہ رابطہ ذریعے سے confirmation/reminder؛ وقت کی تبدیلی پر متعلقہ فریق کو اطلاع۔
- میٹنگ کا محدود رسائی والا نوٹ اور follow-up tasks؛ sensitive notes عوامی طور پر شیئر نہ ہوں۔
- ڈبل بکنگ سے بچاؤ اور دستیابی کی تصدیق۔

## 4) Fee Management — اسکول فیس اور بقایا جات

- ہر طالب علم کے لیے فیس شیڈول، واجب الادا رقم، due date اور billing period۔
- Student-wise status: Paid / Partially Paid / Unpaid / Overdue / Waived (جہاں قابل اطلاق ہو)۔
- Payment methods کی recording: cash / bank / transfer / other approved modes۔
- مکمل یا جزوی ادائیگی، discount، scholarship، waiver، refund، adjustment اور receipt نمبر کا حساب۔
- خودکار receipt، outstanding balance اور overdue summary؛ duplicate payment posting کا تحفظ۔
- اسکول انتظامیہ کو واضح فہرست کہ کس بچے نے فیس دی، کس کی باقی ہے، کتنی رقم باقی ہے اور کس مدت کی۔
- Approved reminder rules with opt-in/channel controls; کوئی خودکار مالی write-off یا sensitive action بغیر مجاز approval نہ ہو۔

## 5) School Accounting — اکاؤنٹنگ

- فیس کے واجبات، وصول شدہ رقم، رعایت اور باقی رقم کا ledger اور accounting reconciliation۔
- Daily / monthly collection reports؛ student-wise اور class-wise summaries۔
- Cash اور bank collection کی علیحدہ رپورٹ اور reconciliation۔
- Journal entries، reversal/adjustment audit، receivables اور basic income/expense tracking۔
- مالی رپورٹ: collected / outstanding / overdue / income / expenses۔
- Finance-only permissions؛ حساس تبدیلیاں authorized accountant/admin approval کے بعد۔
- تفصیلی chart of accounts، payroll، supplier payments اور local reporting rules کے تقاضے **بعد میں طے ہوں گے**۔

## 6) Example Automation Workflows

1. Teacher submits attendance → validate class/date → save record → calculate absence rules → send permitted guardian alert → log delivery result.
2. Parent requests meeting → check teacher availability → request/confirm slot → send confirmation → optional reminder → update meeting status.
3. Monthly fee cycle starts → generate per-student charges → update balances → produce payable lists.
4. Authorized fee payment is recorded → validate receipt and amount → apply to outstanding charges → post ledger entry → issue receipt → refresh paid/unpaid dashboard.
5. Fee due date passes → flag overdue accounts → show admin report → optionally send school-approved reminders.

## 7) User Roles & Safeguards

- School Owner / Principal / Admin
- Accountant / Finance Staff
- Teacher / Class In-charge
- Parent / Guardian (restricted access to own linked children)
- Optional additional roles to define later

**Must-haves:** role-based access, least privilege, authenticated users, student/family privacy, audit trail, backups, secure configuration, payment integrity, human approval for sensitive changes, demo data isolation, and no live messages/payments until approved.

**Public repository warning:** یہ hub Public ہے۔ اس میں حقیقی بچوں کے نام، والدین کے فون نمبر، حاضری، فیس ریکارڈ، بینک تفصیلات، پاس ورڈ یا کوئی ذاتی معلومات commit نہ کی جائیں۔ Production code/data کے لیے علیحدہ **private** repository اور secure database ضروری ہوں گے۔

## 8) Scope & Decisions Not Yet Confirmed

- School logo, actual campus details, classes/sections, academic calendar.
- Number of students, staff and branches.
- Exact fee rules, late fees, scholarships and payment methods.
- Parent communication channel (SMS/WhatsApp/app), consent and provider costs.
- Meeting timing/policies, language preferences and notification templates.
- Deployment, database, hosting and compliance requirements.
- Future modules and final roadmap **pending further input**.

## 9) Implementation Status

| Area | Status |
| --- | --- |
| Initial project brief | Recorded |
| Attendance requirements | Draft |
| Parent meeting requirements | Draft |
| Fee tracking requirements | Draft |
| Accounting requirements | Draft |
| Security/privacy requirements | Draft |
| Full roadmap | Not finalised |
| Database/backend/frontend | Not started |
| Automations and integrations | Not started |
| Deployment | Not started |

**Change policy:** نئی ضروریات اسی دستاویز کے ساتھ ورژن کے مطابق شامل کی جائیں؛ نئی خصوصیات کو implementation کی جگہ draft سمجھا جائے جب تک باقاعدہ test اور acceptance نہ ہو۔

---

## 10) Expanded School OS Discovery Catalog — PROPOSALS, NOT APPROVED SCOPE (2026-10-29)

These are suggested modules for a reusable **Codeedge School OS** product. The school must confirm necessity, policies, available staff and budget. Recording these does **not** approve implementation or mean the capabilities exist.

### Essential school administration
1. **Student information system:** unique IDs, class/section, guardians and sibling relationships, admission history, transfers/withdrawals, enrollment status, identity checks and correction logs.
2. **Admissions CRM:** school enquiry, application, documents, screening, eligibility, waitlist, decision, admission receipt, class allocation; school staff retain final admission decisions.
3. **Attendance:** class/date roll call, leave requests, late/absent, corrections and approvals, guardian notification rules, seasonal/holiday calendar, student/class trends.
4. **Fees and receivables:** annual/monthly/term fees, fee heads, concessions, sibling discounts, arrears, carry-forwards, scholarship/waiver approvals, partial/multiple payments, receipts, aging, refunds and reversals.
5. **Accounting:** cashbook, bankbook, expense vouchers, general ledger, reconciliation, daily closing, authorized adjustments, collections, P&L and outstanding reports; qualified accountant verifies local reporting/tax needs.
6. **Communications:** school notices, class-specific notifications, templates, approved WhatsApp/SMS/email providers, consent and opt-out, delivery statuses, no public exposure of student details.
7. **Principal dashboard:** attendance, fee recovery, overdue balances, unpaid follow-ups, meetings, admissions funnel, upcoming exams, tasks, role-scoped alerts.

### Academic and parent experience
8. **Academics:** academic year, timetable, course/subject allocation, period schedule, holidays, examination seating, substitutes.
9. **Assessments:** exam scheduling, marking, grading rules, teacher review, moderated results, downloadable report cards, promotion after authorized approval.
10. **Homework:** assignments, attachments, submission statuses, teacher comments, due dates, guardian visibility.
11. **Parent-teacher meetings:** availability, appointments, confirmations, rescheduling, authorized notes, follow-up tasks.
12. **Parent portal:** guardian-only children, attendance, homework, notices, fees, receipts, meeting requests, requests/corrections.
13. **Teacher portal:** roster, attendance marking, homework, marks entry, timetable, announcements.
14. **Certificates/documents:** fee clearance, admission confirmation, leaving and transfer certificates, official issuance audit.
15. **Student support:** private safeguarding/escalation workflow, parent contacts, emergency contacts, minimum-necessary sensitive data with strictly restricted access.

### Operations and later additions
16. **Staff HR / payroll:** contracts, staff attendance/leave, salary schedules, payslips, employment audit.
17. **Library and stock:** book lending/returns, late items, inventory, asset tagging, procurement approvals.
18. **Transport:** optional bus routes, assigned guardian/pickup arrangements, driver permissions and safe contact controls.
19. **Website:** admissions and enquiry form, school noticeboard, faculty/contact information with verified content and publication approvals.
20. **AI assistant:** FAQ chatbot for public school information, staff draft assistance and retrieval over approved school knowledge only; no autonomous marks, disciplinary or fee waivers; human handoff and restricted child data.
21. **Multi-school product:** tenant isolation and school-specific configurations once single-school acceptance passes.

### Proposed phased delivery
- **Phase 0 — Discovery and security:** confirm policies, staff/student count, process diagrams, education calendar, privacy, permission matrix, import plan, demo-only data.
- **Phase 1 — Core MVP:** students/guardians/classes, teacher attendance, attendance report, fee schedule and paid/unpaid dashboard, manual payment receipts, basic admin dashboard and CSV exports.
- **Phase 2 — Communication and workflow:** guardian notifications with consent and provider checks, parent meeting bookings, admissions pipeline, roles/audits/backup restore verification.
- **Phase 3 — Academics:** teacher portal, timetable, exams/results, report cards, homework, parent portal.
- **Phase 4 — Financial operations:** full accounting reconciliation, expense controls, periodic closing, supplier payments and optional HR/payroll where approved.
- **Phase 5 — Advanced:** AI FAQ, library, transport, digital payment gateway only after provider review, multi-school SaaS only after independent security acceptance.

### Engineering principles
- Separate new **private** source repository for the deployed application; the public Wasif-project repo is an index/specification only.
- Reuse audited **patterns** from Codeedge Business OS (auth/roles, booking, messaging adapters, external-effect policy, demo separation) and evaluate the Finance Suite/ERPNext/Frappe Education options; avoid modifying frozen existing products.
- Explicit states for development/demo/staging/production. No real student data in GitHub or demos. Secure hosted storage, encrypted backups, retention/deletion policy, least privilege, student-level guardian authorization and admin MFA.
- Restricted, append-only financial history where appropriate, immutable receipts with reversal/void workflows, idempotent payment posting and double-entry reconciliation for accounting.
- Each user-visible academic/financial report is reproducible; mark revisions and approvals; restore backups tested.
- Pakistan-specific needs: Urdu/English UI, PKR, school-specific annual/term cycles, irregular internet connectivity, print-friendly receipts/results, no hard-coded board or fee rules.
- External WhatsApp/SMS messaging requires provider integration, lawful permissions/opt-in and budget; Meta template rules and 24-hour service windows apply.
- Do not claim AI is replacing teachers or administrators. No biometric attendance or face recognition in core MVP.
- **Open decisions:** enrollment counts; branches; grades/sections; fee structures; available staff; classes; parent's preferred channel; language; deployment budget; internet reliability; actual bank/payment method; requirements from principal/accountant; local legal review.

### Commercial model (illustrative; prices to be researched/approved)
One-time implementation/setup + recurring per-school subscription/support, plus separately priced provider consumption (WhatsApp/SMS/telephony/payment fees); optional add-ons for academics, parent portal and AI support. No unverified performance or revenue guarantees.
