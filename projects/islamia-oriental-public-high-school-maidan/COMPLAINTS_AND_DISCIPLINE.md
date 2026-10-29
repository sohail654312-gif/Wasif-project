# Codeedge Dedicated School OS — Complaints, Conduct, Guardian Contact & Case Management

**School:** Islamia Oriental Public High School Maidan  
**Requested:** 2026-10-29  
**Status:** Requirement confirmed; planning draft only. **No code, live contact or school records created.**  
**Privacy:** This public repository is for nonsensitive requirements only. Real allegations about teachers or children, documents, contacts, call recordings and safeguarding cases must never be put here.

## 1. Confirmed requirements

A new **seventh core module** in the dedicated school-controlled application:

A. **Parent -> School complaints:** a guardian may file a complaint about a teacher, principal/school administration, classroom issue, behavior, fee error, attendance, or other school service. Guardian sees the complaint's own safe status and school-approved replies. A complaint about the principal must be routed to an authorized alternate school owner/board official, not automatically back to the subject.

B. **School -> Parent concerns:** teacher or principal may record a concern/complaint about an individual student (e.g. repeated lateness or behavior; categories set by school policy), route it to a principal or other designated reviewer where needed, and propose a guardian notification via approved WhatsApp, SMS or direct phone call. Keep a complete school-owned history.

C. **Per-teacher/principal dashboard:** for authorized school leadership, show number of complaints linked to each staff member, categorized by status and outcome, with individual cases, dates, issues, responses, follow-up, evidence and resolved/unresolved totals.

D. **Per-student conduct/concern history:** authorized personnel can view complaint/concern counts, categories, date/time, review outcome, staff author and guardian communication history for a child. Parent sees only safely approved information about their **own child**.

E. **Communication evidence:** for every approved WhatsApp/SMS notification and phone-contact attempt, capture who initiated it, why, intended/verified recipient, timestamp, template/body or safely redacted copy, delivery status/provider reference, follow-up and call disposition. Only record phone audio if lawful consent, retention and school policy are verified; a call log is not automatically an audio recording.

F. **Two-portal model:** Parent Portal has Submit Complaint / My Complaints / Child Concern Notices; School Portal has Complaint Center / Case Assignment / Investigation / Teacher Trends / Student Concern History / Contact Guardian / Case Analytics.

## 2. Recommended complaint intake workflow

1. Guardian signs in and selects one of their linked children (or files a school-wide concern without selecting a child); category, subject staff member (optional), date, issue narrative and permitted attachment.
2. Unique case ID, creation timestamp, confidential access and acknowledgement. Optional anonymity to be assessed by school leadership; confidentiality promised only within policy limits.
3. Rules route to principal, trained investigator or alternate governing authority; **never assign complaint about a staff member to that staff member as the initial decision-maker**.
4. Triage: General, High Priority, Student Safety/Safeguarding. A high-risk allegation triggers restricted human safeguarding escalation promptly, not standard AI reply or broadcast. Any imminent danger requires immediate real-world safeguarding/emergency procedure.
5. Case state: Submitted -> Acknowledged -> Under Review -> Awaiting Input -> Resolved / Closed / Reopened (or Withdrawn); each transition dated, attributed and auditable.
6. Investigator records evidence and findings separately from allegations and offers the relevant party a fair process appropriate to child protection, privacy and school policy.
7. Guardian gets safe case updates and an approved summary. Confidential staff/pupil personal information and unverified allegations are never disclosed to unrelated parties.
8. Closing includes approved resolution, communication outcome, school action if any, reopen route, and retention policy.

## 3. Staff or principal -> guardian concern workflow

1. Assigned teacher/principal selects their authorized student; issue category and descriptive incident report (time, place, observations rather than assumptions or derogatory labels).
2. Create a StudentConcernCase linked to school and student; designate staff author, witnesses/evidence (restricted), supervisor review status and recommended follow-up.
3. Depending on school policy, authorized reviewer approves guardian notification; sensitive child safety cases **must not automatically alert a guardian when doing so could risk the child's safety**. Escalate to trained safeguarding staff instead.
4. For normal, approved concerns choose **WhatsApp**, **SMS**, or **Phone** (with provider integration or staff-initiated call), send minimal/privacy-preserving language and optionally a safe portal link.
5. Record outbound attempt, channel, date/time, exact approved safe template or content reference, sender, school-owned sender identity, provider delivery result or staff-entered call outcome, and next action.
6. Guardian can view approved concern summary about own child, request meeting/reply, and optionally contest an error.
7. School retains event chronology (drafts, approvals, sent message IDs, retries, human calls, case updates). Corrections create audit records rather than silently overwrite original history.

### Important distinction for phone calls

- Phase A: manual school staff **click-to-call / phone number view** with a mandatory call-log form (called, reached, no answer, left message, follow-up needed), timestamps and staff identity.
- Phase B (optional, after cost/legal check): integrated school-owned telephony, outbound dialing, call event reconciliation and automated reminders/escalation. **No unattended AI voice calls or recording without later explicit authorization, consent, provider capability verification and applicable-law review.**
- If call audio is lawfully recorded, keep encrypted, tightly restricted, retention-bound and accessible only to authorized investigation staff; call metadata alone is default.

## 4. Portals and authorization

| Capability | Parent Portal | Teacher Portal | Principal/authorized case manager | Accountant / Codeedge |
| --- | --- | --- | --- | --- |
| Complaint about teacher or school | Submit/see own case status; safe responses | Cannot browse complaints made against them unless school-approved procedural disclosure | Restricted full case handling, routing and case outcomes; alternate investigator for complaint against principal | No default access |
| Report concern about student | Can see only own child's school-approved summary and reply | Draft for assigned pupils, view own authorized submissions | Triage/approve contact and case action | No default access |
| Complaints count per teacher | None | Own case notices when authorized, not rankings of coworkers | Only leadership; counts split by submitted/duplicate/withdrawn/under-review/substantiated/unsubstantiated, with date filters | No |
| Concern count per student | Only own child cases approved for display | Assigned pupils under relevant policy | Authorized scoped oversight | No |
| Send WhatsApp/SMS to guardian | Reply/receive, opt-in/preferences per policy | Prepare request; send only within explicit school policy | Approve/dispatch sensitive contact, audit all sends | No |
| Call parent and log | Submit callback request | Authorized staff member logs call attempt | Assign, escalate and inspect approved logs | No |
| Child safeguarding allegation | Report secure concern | Confidential report only | Designated trained safeguarding officers, alternate school governance when implicated | No |
| Close/resolve complaint | Can request reopen | Cannot close complaint against self | Designated reviewer separate from subject where possible | No |

All access checked server-side and at data layer. School administration holds accounts; Codeedge has no standing access.

## 5. Teacher complaint analytics (to meet requested reporting)

Leadership report by **teacher, school term, class, issue category and status**, including:
- Total submissions and distinct cases in selected period;
- Pending acknowledgement, under review, closed and reopened;
- Duplicates/invalid submissions separately flagged;
- Findings when adjudicated: substantiated / not substantiated / inconclusive / withdrawn;
- Median/average resolution times, overdue cases and repeat themes;
- Link to case history, dates, response/actions where authorized;
- **Do not treat raw complaint count as proof of wrongdoing** or an automatic staff rating. One incident reported by multiple people should not silently become multiple proven incidents.
- Sensitive allegations excluded from general teacher analytics except highly restricted safeguarding role; regular leadership aggregate view should avoid exposing protected evidence.
- No automated disciplinary action, dismissal, public ranking, AI "guilt score" or parental public teacher score.

Example *fictional only*: Teacher X 7 reports submitted (2 under review, 2 duplicates, 1 substantiated, 2 not substantiated) — dashboard must display that breakdown instead of "7 proven complaints."

## 6. Student case history and protection

Each case contains:
- Incident date/time, reporting staff, student's internal ID (not name in public docs), class/section, category, factual notes, confidential/restricted attachments, priority.
- School investigation/review outcome and authorization.
- Parent-notification eligibility and risk assessment, message/call history, attempts/outcome and follow-up appointment.
- Ability to correct false allegations and annotate context; discipline and safeguarding policies are separate, nonpunitive by default.
- Parent access restricted to approved child-related notices; internal employee notes, unrelated pupils' details and protected safeguarding evidence not exposed.

## 7. Unified Communication integration

- Link each relevant case to [School-owned WhatsApp and SMS automation](COMMUNICATIONS_AUTOMATION.md) through a **CaseNotificationRequest**.
- Staff drafts/proposes message, school policy approves -> use verified linked guardian contact -> approved WhatsApp template or SMS sender -> provider result updates CaseCommunicationLog.
- Recipient verification is required. Staff should not put sensitive details into a shared phone number, unverified WhatsApp or public SMS. Safe baseline: "The school has a confidential update regarding your child's school record. Please sign in to the secure parent portal or contact the school office."
- Parents can respond, and the school-owned inbox associates messages to a case only after verified permission. AI can acknowledge and route, **not decide guilt, determine punishments, expose private case documents or mark allegations substantiated**.
- Bulk WhatsApp/SMS is for general approved notices, **not sending personal complaints or discipline disclosures to groups**.
- Emergency/safeguarding routes are school-led and must never rely exclusively on bot messaging.
- Delivery states: Draft, Awaiting Approval, Approved, Queued, Sent, Delivered (if provider confirms), Failed, Cancelled, Guardian Responded. Do not equate Sent with Read or Delivered.

## 8. Logical entities / records — proposed, no migrations

ComplaintCase, StudentConcernCase, ComplaintParty, Reporter, AccusedOrSubjectReference, ComplaintCategory, SchoolCaseAssignment, InvestigatorRole, CaseStatusHistory, TriageDecision, CaseEvidenceMetadata, RestrictedEvidenceAttachment, CaseFinding, AppealOrReopenRequest, GuardianMessageApproval, CaseNotificationRequest, CaseCommunicationLog, CallContactRecord, CommunicationAttempt, CaseTimelineEvent, CaseAuditEvent, CaseRetentionPolicy, CaseAccessGrant.

Suggested fields across cases:
- ID, school_id, case_type, reporting_user_id, subject_type (teacher/student/school), subject_id, linked_student_id when relevant, category, severity, incident_at, opened_at, status, summary, narrative, attachments, assigned_to, reviewed_by, allegation_vs_finding flag, resolution_at, outcome, parent_visibility_policy, retention/deletion review.
- For each communication: case_id, channel, consent/legal basis check, template/body snapshot reference and sensitivity tier, recipient verification, approval user/time, provider message id or manual call record, attempt/delivery/read state only if verifiable, initiated_at, outcome, followup_at; store sensitive bodies encrypted and strictly role-filtered.
- For call recordings (optional only): separately authorized recording metadata, lawful consent, encrypted object reference, access log, deletion date.
- Append-only audit events and revision history with clear correction action; no invisible rewrite of a closed case.

## 9. UX / screen navigation

```text
PARENT PORTAL
  Home
  My Children
  Attendance / Fees / Meetings
  Complaint Center
    + Submit Complaint (teacher, school, service, incident)
    + My Complaints (own case ID, status, safe response)
    + School Messages / Child Concern Notices
    + Request Review or Meeting

SCHOOL PORTAL
  Principal & Authorized Case Manager
    + Complaints Dashboard
    + Cases Awaiting Review
    + Teacher-by-Teacher Complaint Summary (verified category/status breakdown)
    + Student Concern History (restricted)
    + Investigator Assignments / Reopen / Resolution / Appeals
    + Communication Activity & Contact Attempts
    + Restricted Safeguarding Inbox (designated officers only)
  Teacher
    + Report Student Concern (assigned student only)
    + My Submitted Reports / Approved Follow-ups
    + Contact Guardian Request (WhatsApp / SMS / Call)
  Staff Communications
    + Approved WhatsApp/SMS messages
    + School-owned inbound shared inbox
    + Manual Call Log / optional future telephony connector
```

## 10. Test cases and release gates

1. Parent A cannot see parent B's complaint or another child; teacher cannot read unrelated cases.
2. Complaint against principal routes to designated alternate reviewer without notification to subject until safe/legal process permits.
3. Parent complaint about teacher shows school receipt and safe status, not private staff records.
4. Complaint dashboard distinguishes filed, duplicate, under review and verified outcomes; no automatic punishment.
5. Teacher can submit concern only for assigned pupil, and cannot self-approve serious or restricted guardian notifications.
6. Approved non-sensitive school-to-parent WhatsApp/SMS references right verified guardian, content and case ID, with school/provider log.
7. Sensitive safeguarding report is isolated from standard analytics/inbox and automatic family notifications; designated human escalation available.
8. Parent phone unreachable -> staff logs "no answer" and next steps; no fabricated call success.
9. Staff records no audio by default; any authorized recording is encrypted, consent-verified and retention-bound.
10. Message duplication, provider outage, rate-limit, opt-out and consent withdrawal cannot cause erroneous case closure or repeated sensitive contact.
11. Closed case can be reopened with audit and supervisor review; past history remains traceable.
12. Codeedge has no implicit access to the school's case records, evidence, personal messages or call logs.

## 11. Roadmap insertion / priority

This is **core module 7** and an explicit requirement, but subject to discovery of school safeguarding/discipline procedures and contact policy. Add to:
- Phase 0: school complaint handling policy, reporting routes, alternate principal reviewer, confidentiality and child safety rules.
- Phase 1: privacy model, complaint schemas, allowed staff/parent visibility and retention.
- Phase 2: Parent Complaint Center and School Case Inbox screen design/access controls.
- Phase 6: parent filing, teacher student concerns, review/response, outcomes and case dashboards.
- Phase 7: case-linked WhatsApp/SMS alerts and approved manual calls/call logging. Optional integrated calling only after separate approval.
- Phase 8: safeguarding, permissions, retaliation, analytics fairness, sending/delivery and end-to-end acceptance testing.

**No code, student record, complaints, device, real communications, call integration or purchases are authorized by this design document.**
