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
