# School-Owned WhatsApp, SMS and Shared Messaging Automation — Requirements Only

**School:** Islamia Oriental Public High School Maidan  
**System:** Dedicated Codeedge School OS (school-controlled, NO shared Codeedge inbox)  
**Requested:** 2026-10-29  
**Stage:** Design / requirements only. NO API provisioning, phone numbers, messaging, coding, data upload or activation authorized.

## Confirmed requested capabilities

1. **WhatsApp automation** from school-owned approved WhatsApp Business Platform account/number.
2. **Automated SMS** via licensed/authorized school-approved SMS provider and sender.
3. **Bulk SMS messaging** to verified school guardian/teacher audiences (class, section, all, selected, fee-overdue, attendance etc.) with approved content and opt-out controls.
4. **Bulk WhatsApp messaging** to approved guardian/teacher segments, only within Meta policy, verified opt-in and permitted template/messaging limits.
5. **Inbound WhatsApp auto-handler** that receives school-related messages, categorizes intent, provides safe replies for verified public FAQs, and securely routes private matters to authenticated workflows or human staff.
6. **Two-role-experience rule:** Parents have their own message/notification history, preferences and requests; school staff have authorized campaign composer, inbox, queues, templates, delivery logs and human escalation. No cross-guardian data disclosure.

## 1. Example outbound automation triggers

- **Fingerprint/teacher-confirmed pupil attendance:** absent/late alert to verified guardian with approved policy and message; include correction/request link, no raw biometric details.
- **Fee billing/collection:** due-date reminders, confirmed paid receipt notice, partial payment acknowledgment, overdue reminders. The authoritative fee ledger controls messages; an incoming screenshot or reply never changes balances automatically.
- **Parent-teacher meetings:** request received, slot confirmation, reschedule/cancel, appointment reminder.
- **School information:** official holidays, exam schedule, approved results published, emergency closure, admission announcements, class notices and safety alerts; only send information approved for the recipient group.
- **Teacher/staff operations:** authorized duty/meeting messages and school notices, without child identifiers unless role requires them.
- **Receipt/fee status updates** must reflect school-verified payments and show child-specific information only after verification.

## 2. Bulk sending — safeguards and experience

School Portal > Communications:
- Compose one message; select **WhatsApp**, **SMS**, or explicitly approved fallback option; select recipients by guardian/student/class/section/status, not uploaded random contact lists.
- Display count, sample render, projected cost (if known), template approval state and excluded/opt-out audience before sending.
- Draft -> review -> school-authorized approval -> schedule or send -> queued -> sent/delivered/failed tracking.
- No bulk messages containing full student rosters, detailed marks, or private financial information; personalization per verified guardian and linked child only when appropriate.
- Respect school quiet hours, reasonable frequency caps, deduplicate guardian contact numbers across multiple children where appropriate, rate limits, provider limits, retries and cost caps.
- Individual provider failure logged with retry/dead-letter queue; prevent duplicate delivery on job restarts and show exact recipient-level state only to authorized staff.
- Undo before dispatch where possible; sent messages cannot be recalled reliably. Emergency communications need a specifically approved override policy.
- Outbound promotional messages are separate from necessary school service notices; enforce opt-in/opt-out and applicable local rules for each.
- No uncontrolled scraping, unsolicited blasts or unofficial WhatsApp automations.

## 3. Inbound WhatsApp handling

School-owned WhatsApp number -> verified provider webhook -> school-only inbox -> intent classification / deterministic workflow / AI-assisted FAQ (optional) -> safe response or human staff handoff.

### Parent requests the system can assist with
- Public FAQs: school hours, office contact (only verified facts), admissions procedure, meeting procedure.
- Fee question: acknowledge and offer authenticated Parent Portal/session verification for own child's due/paid/receipts; never reveal amounts based solely on phone number.
- Attendance question: link to authenticated child's attendance view or secure school staff follow-up.
- Meeting request: gather minimal safe details, check approved appointment options and request confirmation.
- Payment screenshot/claim: create **Pending Verification** ticket; school accountant verifies from trusted payment records before ledger posting.
- Complaint, welfare/safeguarding concern, account/identity dispute or unknown intent: route to appropriate authorized human; avoid AI decisions/claims.
- Human takeover from shared school inbox; staff can assign, tag, resolve, reopen, add internal notes and audit replies.
- Clearly disclose when a message is answered by an automated assistant, when possible offer an immediate way to speak to a person.
- Handle Urdu, English (and other school-approved languages) only after testing; fallback gracefully on uncertainty.

### Inbound safety logic
1. Validate incoming webhook integrity and event id; reject spoofed/duplicate events.
2. Restrict processing to school-owned WhatsApp business account and current approved credentials.
3. Determine if sender is a verified linked guardian; if not, only offer public FAQs and identity verification path.
4. For child, fee, results, or attendance details, require a secure authenticated session and guardian/student authorization; no OTP exchange in open shared WhatsApp threads unless explicitly designed securely.
5. Apply approved WhatsApp conversation service-window/template rules and channel consent/preferences before outbound reply.
6. Keep private student/financial data outside model training, third-party logs and general Codeedge dashboards; minimize prompts.
7. Log classification, messages (per policy), handoff, outcomes and deletion/retention actions for school-authorized review.
8. Protect against prompt injection, spam, abusive messages, high-volume traffic, integration outages and accidental external effects.

## 4. Parent Portal vs School Portal

| Feature | Parent Portal | School Portal |
| --- | --- | --- |
| Notifications | My child's approved notices, fee/attendance alerts and message history | Draft/approve/schedule/send class and school notices |
| WhatsApp inbound | Ask questions, secure portal links, human escalation | Unified inbox, assign staff, approved replies and bot supervision |
| Bulk campaigns | No bulk send rights | Authorized staff only, school-defined approval |
| Fee and attendance | Own linked pupils' authenticated data | Role-scoped school/class data and authorized edits |
| Preferences | Opt in/out for optional communication channels/categories | School compliance, recipient filters and delivery dashboards |
| Delivery reports | Own message delivery/read status where available | Recipient-level status only for properly authorized school roles |

## 5. Provider model, ownership and Meta conditions

- **School owns** WhatsApp Business Account/number, SMS sender account, messaging credentials and billing where feasible; Codeedge only connects through revocable school-approved provider adapters.
- Use Meta's authorized WhatsApp Business Platform/Cloud API or approved BSP and a compliant SMS gateway; **do not** depend on unofficial WhatsApp Web bulk sender, automated account scraping, or circumvented sending limits.
- Meta WhatsApp Business policy requires business-initiated outreach with approved message templates, with a 24-hour customer service window for non-template replies after a user message; automated response must offer a clear human escalation path. Enforce current Meta documentation at integration time.
- Consent and opt-out must be recorded and respected. Quiet-hours, sender reputation, provider message quotas, template categories, daily budgets and billing reporting configurable by school.
- Cross-channel delivery must not automatically resend the same sensitive message on SMS if WhatsApp fails unless a school-approved fallback rule exists.
- School finances and payment ledger are never modified by AI conversational text, without school-controlled verified payment confirmation and appropriate authorization.
- Private content is kept in dedicated school databases; no Codeedge central storage or access by default.
- The WhatsApp/SMS provider will charge based on usage; per-message and setup costs are **not yet quoted**.

## 6. Proposed logical entities (NOT migrations)

CommunicationChannel, MessagingProviderAdapter, SchoolSenderIdentity, GuardianContactVerification, ChannelConsent, OptOutEvent, NotificationTemplate, TemplateApprovalState, AudienceSegment, Campaign, CampaignApproval, CampaignRecipient, MessageOutbox, DeliveryAttempt, ProviderWebhookEvent, InboundConversation, ConversationMessage, IntentClassification, AutoReplyRule, SecureVerificationTicket, StaffAssignment, HandoffEvent, MessagingCostLedger, AuditEvent, RetentionPolicy.

All data school-scoped, access controlled, auditable. Encryption, backup, retention, export, incident handling and consent withdrawal required.

## 7. Test scenarios (design-time acceptance criteria)

1. Authorized principal creates school closure notice to guardians, previews recipients, approves, sends and sees per-channel delivery results.
2. A guardian with two linked children receives appropriate deduplicated notices without exposing unrelated children.
3. An unpaid/part-paid fee notice is generated from verified ledger, not from a parent screenshot or unverified payment.
4. A parent asks “my fee is how much?” in WhatsApp from an unverified number; bot offers secure login rather than quoting fees.
5. A verified parent gets a secure link to their own child only, and cannot access another child even with a guessed URL.
6. SMS bulk respects opt-out, sender policy, segmentation and duplicates, and shows projected/actual per-provider costs.
7. WhatsApp bulk outside the permitted conversation context requires approved templates and provider limits; no bypass.
8. A complaint or unclear AI answer is assigned to an authorized human, with status visible to the school.
9. Provider down / duplicate webhook / rate limit does not create duplicate messages or bogus attendance/fee postings.
10. Revoked consent immediately excludes future non-essential messaging; safety/mandatory operational messages follow the verified school-approved policy.
11. Codeedge support cannot read/trigger school messages without expiring school-granted access.

## 8. Not yet decided; must ask school later

- Existing school WhatsApp number: whether it is eligible for Business Platform integration and what onboarding is required.
- Pakistan SMS provider, sender ID/registration, costs and approved bulk limits.
- Number of parents/guardians and school message volume, max monthly budget and quiet-hours rules.
- Which messages are essential service notices vs optional promotional broadcasts; precise school consent practice.
- Languages, templates, user verification method and who may approve each campaign.
- Should human messaging begin only during office hours? Which staff handle escalations and urgent issues?
- Hosting and data retention, notification delivery SLAs and school-specific legal requirements.

**Status: documentation only. No actual automation, bulk campaign, messaging provider or AI webhook is active.**

## 9. Case-linked Complaints and Guardian Calling (added 2026-10-29)

See [Complaint Center & Student Concerns](COMPLAINTS_AND_DISCIPLINE.md). Authorized teacher/principal may propose school-approved messages about a child's concern. After consent/policy checks and safety review, the system can send privacy-minimized WhatsApp/SMS to the **verified** linked guardian, record per-case message body/template reference, school approver, attempts, delivery status and human response. Phone contact initially is staff-initiated with a call-log form (attempt timestamp, authorized caller, reached/unreachable, notes and follow-up); integrated school-owned dialing is a separate optional future project. Never silently audio-record calls; review consent and local law first. Child safeguarding matters are handled by designated humans and may require holding parent notification if safety is at risk. **No automatic AI discipline, case closure, provider activation or live messaging.**
