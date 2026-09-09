# [SPRINT VALIDATION] Validate Sprint 1 Requirements Traceability & Open Decisions

**IBM × RMIT Capstone — Responsible Content-Safety Infrastructure**  
**Task:** Validate Sprint 1 Requirements Traceability & Open Decisions  
**Role:** BA — Sriharish Muthumalai Arunkumar  
**Team:** Team 1 | **Sprint:** Sprint 1 — Design & Bootstrap

## 1. Purpose

Validate that the final Sprint 1 requirements are traceable to the Core MVP, UX direction, architecture and AI/STT outputs, while clearly documenting confirmed requirements, assumptions and remaining open decisions.

No unconfirmed business rule is invented.

## 2. Traceability Review

| Area | Result | Validation |
|---|---|---|
| Core MVP | PASS | Submission → Case/Case ID → AI video/audio analysis → structured outputs → Auditor review → final human decision. |
| Auditor | PASS | Auditor is the primary user, reviews AI outputs and retains the final human decision. |
| Manager | PASS | Manager/Supervisor requirements are checked, including wellbeing notification, oversight and authorised exposure-control responsibilities. Exact permissions remain an open decision. |
| Wellbeing | PASS | Auditor wellbeing is a confirmed requirement and takes priority over moderation speed. Exact thresholds and implementation parameters remain open. |
| Exposure controls | PASS | Manager-controlled exposure limits and exposure protection are confirmed requirements. Exact limits/triggers remain open. |
| Auditor decline → Manager escalation | PASS | The decline/escalation requirement is recognised. Exact reassignment and workflow behaviour remain open. |
| UX flows | PASS | UX direction preserves confirmed requirements and does not invent unconfirmed workflow rules. |
| Prototype | PASS | Core submission, case review, AI-result presentation and final human decision direction are aligned with requirements. |
| Architecture | PASS | Technical flow supports UI/backend, storage/database, STT, watsonx.ai, structured results and human review. |
| AI/STT contract | PASS | Inputs, outputs, structured fields, authentication and known limitations are documented. |
| AI POC | PASS | Synthetic audio validated the STT → transcript → watsonx.ai → structured assistive output path. |
| Human decision boundary | PASS | AI remains assistive; the human Auditor makes the final decision. |
| Confirmed vs assumptions | PASS | Confirmed requirements are separated from assumptions and unresolved business rules. |
| Open decisions | DOCUMENTED | Remaining decisions include severity scale, accuracy threshold, final decision options, assignment/reassignment rules and exact wellbeing/exposure parameters. |

## 3. Core MVP Traceability

**Public User submits approved synthetic/staged content**  
→ **Case created / Case ID generated**  
→ **AI analyses video/audio**  
→ **Structured AI outputs**  
→ **Auditor reviews AI-assisted results**  
→ **Auditor makes final human review decision**

Confirmed acceptance criteria:

- **AC-01:** Public User can submit approved synthetic/staged content.
- **AC-02:** Case ID is created.
- **AC-03:** Approved test content is processed by AI.
- **AC-04:** Severity information is returned.
- **AC-05:** Summary is returned.
- **AC-06:** Incident timestamps are provided.
- **AC-07:** AI outputs are presented to the Auditor.
- **AC-08:** Auditor makes the final human decision.
- **AC-09:** Full workflow operates end-to-end.
- **AC-10:** AI assistance reduces unnecessary direct exposure.
- **AC-11:** Synthetic/staged content only.
- **AC-12:** No autonomous final AI decision.

**Result: PASS.**

## 4. Role Validation

### Public User

- Submit approved synthetic/staged video/audio.
- Receive a Case ID.
- No unapproved moderation or administration functionality.

**PASS.**

### Auditor — Primary User

- Access the relevant case.
- Review severity, summary and incident timestamps.
- Review other available structured outputs.
- Make the final human review decision.
- Have wellbeing protection prioritised over moderation speed.
- Be able to decline when the confirmed wellbeing/escalation requirement applies.

Exact final-decision labels and decline workflow details remain pending where not confirmed.

**PASS.**

### Manager / Supervisor

Confirmed requirements include:

- Receive wellbeing notifications/escalations.
- Support oversight of Auditor wellbeing.
- Control exposure limits through authorised Manager controls.
- Receive escalation when an Auditor declines where the requirement applies.

Exact Manager permissions, notification content and downstream reassignment behaviour remain open decisions.

**PASS.**

## 5. Wellbeing & Exposure Validation

The following are treated as **confirmed requirements**:

1. Auditor wellbeing takes priority over moderation speed.
2. The system should reduce unnecessary direct exposure to harmful material.
3. Exposure limits are required.
4. Exposure limits are Manager-controlled.
5. Manager wellbeing notification/escalation is required.
6. Auditor decline can trigger Manager escalation.

The following are **not yet confirmed parameters**:

- exact exposure-limit values;
- exposure trigger conditions;
- cooldown duration and trigger;
- SOS trigger/action;
- exact Manager notification content;
- exact Manager permissions;
- exact reassignment behaviour after decline.

These open parameters must not be invented by UX or Developers.

**PASS — requirements confirmed; implementation parameters separated as open decisions.**

## 6. UX Validation

The UX direction is consistent with the requirements by:

- keeping the Auditor as the primary persona;
- representing AI pre-analysis and structured AI-result presentation;
- preserving the final human decision;
- supporting wellbeing-first behaviour;
- representing exposure protection and Manager controls;
- allowing the confirmed Auditor decline → Manager escalation direction;
- avoiding invented severity scales, exposure thresholds, reassignment rules or Manager permissions.

**PASS.**

## 7. Architecture & AI/STT Validation

The technical direction supports:

**Frontend/UI → Backend/API on IBM Code Engine → media storage/database → Speech-to-Text → watsonx.ai → structured AI result → Auditor UI → human final decision**

The AI/STT contract supports transcript/confidence output from STT and a structured watsonx.ai result containing fields such as `caseId`, `severity`, `summary`, `categories` and `timestamps`.

The technical POC validated the conceptual path:

**Synthetic audio → Speech-to-Text → transcript → watsonx.ai → structured AI-assisted result**

Known authentication/API limitations are documented by the developer outputs.

**PASS.**

## 8. Confirmed Decisions

The Sprint 1 validation confirms the following:

- AI-assisted content-review workflow is the Core MVP.
- Auditor is the primary user.
- Human Auditor retains the final decision.
- Core outputs include severity, summary and incident timestamps.
- Approved synthetic/staged content is used.
- Sprint 2 targets the Core MVP end-to-end implementation.
- AI does not make the final decision autonomously.
- Auditor wellbeing takes priority over moderation speed.
- Exposure controls are required.
- Exposure limits are Manager-controlled.
- Manager wellbeing notification/escalation is required.
- Auditor decline → Manager escalation is required.
- Exact rules and parameters for these controls remain to be confirmed.

## 9. Assumptions / Pending Rules

The following must not be treated as confirmed until BA/PM/client confirmation:

- exact severity scale;
- minimum AI accuracy threshold;
- exact final-decision options;
- case assignment/availability;
- mandatory AI outputs beyond the confirmed core outputs;
- exact decline/reassignment workflow;
- exposure-limit values and trigger rules;
- cooldown duration/trigger;
- SOS behaviour;
- Manager notification trigger/content;
- Manager permissions/actions;
- optional tags/transcription.

## 10. Open Decisions for Playback / PM

| ID | Open decision | Status |
|---|---|---|
| OD-01 | Severity scale | Pending |
| OD-02 | Minimum AI accuracy threshold | Pending |
| OD-03 | Exact Auditor final-decision options | Pending |
| OD-04 | Case assignment / availability | Pending |
| OD-05 | Mandatory AI outputs beyond severity, summary and timestamps | Pending |
| OD-06 | Exact decline / reassignment workflow after Auditor decline | Pending |
| OD-07 | Exposure-limit values and trigger rules | Pending |
| OD-08 | Cooldown threshold/duration | Pending |
| OD-09 | SOS trigger/action | Pending |
| OD-10 | Manager notification trigger/content | Pending |
| OD-11 | Manager permissions/exposure-control actions | Pending |

These are recorded for traceability and do not create new requirements.

## 11. Playback-Relevant Findings

1. The Core MVP is one clear end-to-end AI-assisted review workflow.
2. The Auditor is the primary user and final human decision-maker.
3. AI/STT technical outputs support the required review information.
4. Only synthetic/staged content is used.
5. Architecture and AI/STT outputs describe a consistent technical flow.
6. Auditor wellbeing is a confirmed priority over moderation speed.
7. Exposure controls and Manager-controlled exposure limits are confirmed requirements.
8. Manager wellbeing notification/escalation is confirmed.
9. Auditor decline → Manager escalation is confirmed, while exact reassignment behaviour remains pending.
10. Severity scale, accuracy threshold and exact final-decision options remain open.
11. Exact wellbeing/exposure thresholds, cooldown, SOS and Manager permissions remain open.
12. Playback evidence must not expose credentials, tokens, real agency data or real harmful content.

## 12. Final Validation Decision

**OVERALL STATUS: PASS — READY FOR SPRINT 1 PLAYBACK / REVIEW**

The Sprint 1 requirements are traceable to the Core MVP, user roles, acceptance criteria, UX direction, architecture and AI/STT work.

Confirmed wellbeing, exposure-control, Manager notification and Auditor decline/escalation requirements are explicitly included. Their unconfirmed parameters are separately documented as open decisions.

## 13. Handoff

**PM:** Track the open decisions and communicate confirmed changes to BA, UX and Developers.

**UX:** Keep the confirmed P0 workflow primary and represent confirmed wellbeing/exposure/decline-escalation requirements without inventing unresolved parameters.

**Developers:** Use the confirmed Core MVP and AI/STT direction; preserve human final decision-making; implement only confirmed business rules and raise unresolved parameters before making assumptions.

## 14. Definition of Done

- [x] Core MVP checked against requirements
- [x] Auditor requirements checked
- [x] Manager requirements checked
- [x] Wellbeing requirements checked
- [x] UX flows checked against requirements
- [x] Prototype checked against requirements/direction
- [x] Key architecture behaviours reviewed
- [x] AI remains assistive, not final decision-maker
- [x] Confirmed decisions separated from assumptions
- [x] Remaining open questions documented
- [x] Playback-relevant findings identified

**BA Status: SPRINT 1 REQUIREMENTS TRACEABILITY VALIDATED — READY FOR PLAYBACK**
