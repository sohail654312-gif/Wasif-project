# Dedicated School OS — Urdu + English Language & Communication Requirements

**School:** Islamia Oriental Public High School Maidan  
**Requested:** 2026-10-29  
**Status:** CONFIRMED PRODUCT REQUIREMENT — planning only; NO CODING, MESSAGES OR AUTOMATIONS STARTED.  
**Ownership:** School controls all templates, communications, translations, preferences, access and audit logs. Codeedge has no standing access.

## 1. Confirmed language decision

- **Application interface can remain English-first and English-default** for school staff and parent navigation. No requirement to translate every UI screen at initial release.
- **All person-to-person school communications and case content** must accept and appropriately display **Urdu (اردو) and English**.
- Teacher and administrator can compose school notices, bulk SMS, bulk WhatsApp, meeting requests, attendance alerts, fee reminders and student-concern notices in either language or in a school-approved dual-language layout.
- Parent can submit complaints, read approved responses and submit replies **in Urdu or English**. Staff can read the original and, if needed, an appropriately labelled reviewed translation.
- **School logs and authorized records must render Urdu reliably** as entered, not romanize, replace or drop the original text. Reports and exports preserve source language and formatting.
- This is an additional **cross-cutting requirement** for the existing seven modules, **not a new unrelated product or a requirement to begin coding**.

## 2. Message composition model

The School Portal communication composer provides:
1. **English** — author and send approved English template/text.
2. **اردو** — author and send approved Urdu template/text with correct RTL layout.
3. **Bilingual (Urdu + English)** — two labelled sections, clear separation and preview, only when the school decides both should appear in one message.

The school may choose a **parent preferred language** per verified contact (Urdu / English / Bilingual). Defaults and fallback must be school-approved; if no preference is known, a school-defined bilingual template or neutral invitation to update language preference is safer than guessing. Teacher or authorized office may switch draft language for an allowed one-to-one message, but must respect the recipient's preference, notification policy and approval rules.

**Bulk sending:** School creates approved content in separate English and Urdu variants of one campaign, or approved bilingual text, selects target classes/sections/guardians and previews recipient counts by language. A single school-approved campaign can dispatch the appropriate template to each recipient; do NOT silently mix up language variants, contacts or children.

**WhatsApp:** Store provider-approved language-specific templates and locale codes; send using school-owned authorized WhatsApp Business Platform/BSP with valid opt-in and current policy checks. Do not claim a translation is approved as a WhatsApp template merely because the English version is approved. Non-template auto-replies must obey current conversation rules and human handoff.

**SMS:** Correct Unicode / Urdu script, mixed-direction numbers and Latin school names; test handset readability and delivered text. Unicode messages often use fewer characters per SMS segment than plain English, and long bilingual messages may split into multiple billed segments. Show preview, segment estimate and provider/recipient costs where verified; no promises of free/unlimited SMS.

## 3. Parent Portal language behavior

- Portal UI: English-first; language setting for **messages/notifications and complaints**.
- Parent can view **their own child's** fee alerts, attendance alerts, meeting notices, official school notices and complaint case replies in preferred language when approved version exists.
- Parent can **write complaints and replies in Urdu or English**, including mixed-language content, without losing formatting or characters.
- Parents can view message original language; optionally show "Translated for reading" with human-reviewed translation for sensitive complaints when authorized.
- School-controlled archive of notices available in parent's child scope only; personal finance and conduct details require authenticated guardian authorization beyond WhatsApp sender phone number.
- Parent's language preference never weakens privacy, notification consent, authentication or staff review requirements.

## 4. Teacher, principal, office and complaint portal behavior

- Staff UI in English by default; content editor accepts Urdu or English and handles RTL/LTR line structure.
- Teacher drafts complaint/incident narrative or guardian message in own working language; case record stores *exact original* plus source language.
- Principal/assigned case reviewer sees language indicator, original and an optional **verified review translation**; untranslated text remains authoritative in case of dispute.
- Sensitive allegations, disciplinary communication and safeguarding information must NOT be automatically translated and directly dispatched without a human checking wording and recipient safety. The school uses designated reviewers.
- Complaint search/report filters operate by canonical categories/status IDs, with Urdu/English labels in display. Never equate spelling variations with different case counts.
- Teacher complaint-count analytics separate submitted, duplicate, pending, substantiated/not substantiated and child-safeguarding restricted cases regardless of language.
- Case closure and disciplinary decisions are made by authorized humans, never by a translation model.

## 5. Proposed bilingual sample templates (illustrative; not approved for sending)

### Fee reminder — English
"Dear Parent/Guardian, a school fee payment is due. Please sign in to your parent portal to view the amount, due date and verified receipts. Thank you."

### فیس کی یاد دہانی — اردو
"محترم والدین/سرپرست، اسکول کی فیس کی ادائیگی واجب الادا ہے۔ براہِ کرم واجب الادا رقم، آخری تاریخ اور تصدیق شدہ رسیدیں دیکھنے کے لیے اپنے پیرنٹ پورٹل میں لاگ اِن کریں۔ شکریہ۔"

### Attendance notice — English
"Dear Parent/Guardian, there is an attendance update for your child. Please check your secure school parent portal or contact the school office."

### حاضری کی اطلاع — اردو
"محترم والدین/سرپرست، آپ کے بچے کی حاضری سے متعلق نئی اطلاع موجود ہے۔ براہِ کرم اسکول کے محفوظ پیرنٹ پورٹل میں دیکھیں یا اسکول آفس سے رابطہ کریں۔"

### School meeting notification — English
"Your requested parent–teacher meeting has been confirmed. Please check the parent portal for the scheduled time."

### ملاقات کی اطلاع — اردو
"آپ کی درخواست کردہ والدین اور استاد کی ملاقات کی تصدیق ہو گئی ہے۔ مقررہ وقت دیکھنے کے لیے پیرنٹ پورٹل استعمال کریں۔"

### Complaint acknowledgment — English
"Your complaint has been received and assigned a case reference. You can check its status in the secure parent portal."

### شکایت موصول ہونے کی تصدیق — اردو
"آپ کی شکایت موصول ہو گئی ہے اور اس کے لیے ایک حوالہ نمبر جاری کیا گیا ہے۔ آپ محفوظ پیرنٹ پورٹل میں اس کی پیش رفت دیکھ سکتے ہیں۔"

### Student concern / parent-contact notification — English
"The school has a private update for you about your child. Please open your verified parent portal or contact an authorized school staff member."

### بچے سے متعلق رابطہ — اردو
"اسکول کی طرف سے آپ کے بچے کے متعلق ایک نجی اطلاع موجود ہے۔ براہِ کرم اپنے تصدیق شدہ پیرنٹ پورٹل میں دیکھیں یا اسکول کے مجاز عملے سے رابطہ کریں۔"

**All content is illustrative** and must be approved by the school prior to any real dispatch. Keep details of complaints/finance behind authenticated portal instead of putting them in a shared SMS/WhatsApp chat.

## 6. Inbound WhatsApp and SMS language-handling requirements

- A school-owned WhatsApp webhook receives parental enquiry in English or Urdu; auto-handler can classify language and reply with correct **approved** language variant when safe.
- For **public FAQs**, answer only from school-verified knowledge; Urdu/English responses must be tested for meaning.
- For a child's fee, attendance or complaint details, offer secure login and verified guardian access instead of disclosing private information based solely on phone number.
- If the model is uncertain, parent changes language mid-thread, message contains ambiguous Roman Urdu, or content is sensitive: ask for language preference or transfer to school human staff. Roman Urdu support is optional and must be separately evaluated.
- Staff takeover preserves original messages, reviewed translations if any, the language used for reply and communication status.
- SMS replies (if provider supports receiving them) are optional and separately verified; outbound SMS is not proof of inbound two-way capability.

## 7. Data model and audit logging — logical concepts only

- `GuardianContactPreference`: guardian and school ID, verified contact, `preferred_language` = `ur` / `en` / `ur-en`, channel preference, consent.
- `LocalizedMessageTemplate`: `template_key`, purpose, version, locale, reviewed_by, approval status, allowed provider/template ID, expiry/withdrawal.
- `CampaignAudience`: one approved campaign + guardian/student authorization, per-recipient chosen locale and variant.
- `OutboundMessage`: original approved text snapshot or immutable template+variables reference, locale sent, Unicode flag, provider ID, scheduled/sent/delivery state, estimated vs verified cost, staff actor and audit.
- `InboundMessage`: raw original content (securely held with retention), detected/declared language, classification, human handoff status; privacy-safe source.
- `ComplaintContentVersion`: exact original and `source_language`, optional separate translated text, `translation_status` (draft/reviewed/approved), reviewer, timestamps; **never silently replace the source text**.
- `AuditEvent`: actor, language selected, before/after template version, approval, send attempts, restricted access, correction; logs shown according to permissions and preserved in valid Urdu Unicode.
- Dates, PKR amounts, student IDs and contact numbers must display clearly in both LTR and RTL sections.

## 8. QA and acceptance tests

1. A parent selects Urdu notifications; school sends a reviewed fee reminder in Urdu, properly displayed and linked to the correct guardian only.
2. Another guardian selects English; the same campaign sends the approved English variant instead of the Urdu one.
3. School explicitly selects **Bilingual** and user receives readable English and Urdu with appropriate Unicode and RTL, not garbled or truncated.
4. Long bilingual SMS shows actual segment count/cost if supported by selected provider; fail gracefully if budget or provider limits reached.
5. Guardian writes complaint in Urdu; complaint system preserves exact characters, links correct case, and staff can view original and optional labelled reviewed translation.
6. Teacher writes an incident in English; parent receives only staff-approved privacy-safe Urdu notice (if preference is Urdu).
7. Teacher and principal complaint analytics count cases correctly regardless of input language or spelling.
8. WhatsApp inbound Urdu/English public FAQ routes to approved answer; private pupil information requires authenticated portal and guardian link.
9. Unauthorized staff cannot view other children's Urdu/English complaint logs or send school-wide campaigns; Codeedge cannot view without time-limited school grant.
10. Urdu/PDF/CSV/print export retains the text, punctuation and logical layout; mixed date/number rendering verified across target phones.
11. A translation error is corrected by new audited version and human review, while original case/message remains preserved under retention rules.
12. Opt-out, sender/template permission, budget, quiet hours and child-safety safeguards apply equally to Urdu and English.

## 9. Phased delivery alignment (still no coding)

- **Phase 0 Discovery:** decide language default, contact-level preference, school vocabulary, template approval staff and whether bilingual notices should be default.
- **Phase 1 Design:** Unicode/RTL strategy, versioned locale templates, data model, secure logs, language-sensitive QA.
- **Phase 2 Portals:** keep navigation English-first but add language preferences, Urdu content entry/display and preview.
- **Phase 4/5 Fees/accounting:** Urdu/English parent fee statements/communications; financial numbers remain authoritative and unchanged.
- **Phase 6 Complaints/meetings:** bilingual intake, responses, case history and safe human review.
- **Phase 7 WhatsApp/SMS:** per-locale approved templates, bulk recipient routing, inbound auto-language handling, cost/segment previews.
- **Phase 8 Acceptance:** Urdu script, mixed layout, SMS encoding, privacy, bilingual content correctness, school sign-off.

**No implementation, live message send, real parent account data or provider changes authorized.**
