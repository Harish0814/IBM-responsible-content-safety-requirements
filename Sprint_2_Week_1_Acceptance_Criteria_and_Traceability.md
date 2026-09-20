# Sprint 2 Week 1 — Raw MVP Acceptance Criteria & Requirements-to-Build Traceability

**Task:** [REQUIREMENTS] Finalise Acceptance Criteria & Build Traceability  
**Role:** BA  
**Sprint:** Sprint 2  

# Sprint 2 Week 1 Acceptance Criteria & Requirements-to-Build Traceability

## Purpose

Convert the Sprint 2 Raw MVP user stories and business rules into
measurable, implementation-oriented acceptance criteria and a clear
requirements-to-build traceability view for UX and Developers.

This document defines what must be supported or represented by the Raw
MVP while keeping unconfirmed business values and implementation details
explicitly open/TBC.

> **Important:** "Confirmed" in this document refers to the confirmation
> status of the requirement itself. It does not mean that development,
> integration or testing has been completed.

---

# 1. Acceptance Criteria

## AC-01 — Approved Synthetic/Staged Content Submission

**Related stories:** US-PU-01, US-PU-03

**Given** a Public User submits content  
**When** the submission is processed by the MVP  
**Then** only approved synthetic/staged content is accepted for the
demonstration workflow.

**Testable evidence:**
- Approved synthetic/staged content can be submitted.
- The submission is associated with the intended review workflow.
- Real abusive/harmful agency content is not required or used.
- Unsupported or disallowed content is rejected or prevented from
  entering the normal workflow.

**Open detail:** Exact validation rules for identifying approved staged
content remain an implementation detail unless separately confirmed.

---

## AC-02 — Case Creation

**Related stories:** US-PU-01, US-PU-02

**Given** an approved submission is accepted  
**When** the system creates the review case  
**Then** a unique Case ID is generated and associated with the submission.

**Testable evidence:**
- A case record is created after successful submission.
- A Case ID is generated.
- The Case ID is associated with the submitted content/reference.
- The case enters the defined processing workflow.

---

## AC-03 — Case Processing States

**Related stories:** US-PU-02, US-AU-02

**Given** a case has been created  
**When** the case progresses through the workflow  
**Then** its processing state can be represented and tracked.

**Expected workflow states include:**
1. Submission received
2. Case created / Case ID generated
3. AI/STT processing
4. Structured AI results available
5. Auditor review
6. Human final decision
7. Manager notification/escalation where an Auditor decline occurs

**Testable evidence:**
- The case has a recognisable processing state.
- State transitions do not incorrectly skip required workflow stages.
- Processing failures are represented explicitly.
- Technical state names may follow the agreed architecture.

---

## AC-04 — Media Storage and Case Association

**Related stories:** Submission and case creation

**Given** approved media is submitted  
**When** the submission is accepted  
**Then** the media is stored or referenced through the agreed media-storage
layer and associated with the relevant case.

**Testable evidence:**
- Media storage/reference is associated with the Case ID.
- The case database stores appropriate metadata/state/reference information.
- Raw media is not incorrectly stored as ordinary case metadata where the
  architecture specifies a separate media-storage layer.
- Storage failures are represented as explicit failure states.

**Open implementation detail:**
Exact COS bucket, path, naming convention and database schema details
remain subject to the agreed technical architecture.

---

## AC-05 — Speech-to-Text Processing

**Related stories:** AI-assisted processing

**Given** supported media contains audio that requires transcription  
**When** STT processing is invoked  
**Then** the system attempts to produce a transcript for downstream
AI-assisted analysis.

**Testable evidence:**
- STT processing is invoked for supported input.
- A transcript is returned when processing succeeds.
- STT failure is represented by an explicit processing/failure state.
- A failed STT process is not silently treated as successful.

**Open implementation detail:**
Exact STT model, configuration and threshold values remain open unless
separately confirmed.

---

## AC-06 — watsonx.ai Structured Output

**Related stories:** US-AU-01

**Given** the case reaches AI analysis  
**When** the AI service processes the available media/transcription inputs  
**Then** the system returns structured AI output for the Auditor workflow.

**Minimum confirmed output expectations:**
- Severity
- Summary
- Relevant incident timestamps/segments where available

**Testable evidence:**
- AI processing produces a structured result.
- Required output fields are available to the downstream review workflow.
- AI output is clearly presented as assistive information.
- The output remains associated with the relevant case.

**Open decisions:**
- Exact severity scale
- AI accuracy threshold
- Additional mandatory AI outputs

These remain unresolved unless separately confirmed.

---

## AC-07 — Video / Media Analysis

**Related stories:** AI-assisted processing

**Given** a valid supported media submission exists  
**When** media analysis is performed  
**Then** the system attempts to analyse the media and produces the
agreed structured result or an explicit processing failure state.

**Testable evidence:**
- Analysis can be initiated for supported media.
- Successful analysis produces structured output.
- Failed analysis does not produce a misleading successful result.
- Analysis results are associated with the relevant case.

**Open implementation detail:**
The exact video/media-analysis implementation and service configuration
remain subject to technical confirmation.

---

## AC-08 — Timestamp / Segment Information

**Related stories:** US-AU-01, AI analysis and Auditor review

**Given** the AI analysis identifies relevant incidents or segments  
**When** the analysis result is returned  
**Then** relevant timestamps or segment references are included where
available so the Auditor can understand when an identified event occurs.

**Testable evidence:**
- Timestamp/segment information is returned when available.
- Timestamp/segment information is linked to the relevant case/result.
- Missing timestamp information is not represented as confirmed evidence.

**Open detail:**
Exact timestamp/segment format and granularity remain implementation
details unless separately confirmed.

---

## AC-09 — Auditor Review

**Related stories:** US-AU-01, US-AU-02

**Given** AI processing has produced an available result  
**When** the Auditor opens the case  
**Then** the Auditor can review the structured AI information required for
the MVP.

**Testable evidence:**
- The Auditor can access the relevant case.
- Severity is visible where available.
- Summary is visible where available.
- Available timestamps/segments are visible.
- The Auditor can review AI output before making the final human decision.
- AI analysis and the human decision are clearly separated.

---

## AC-10 — Final Human Decision

**Related stories:** US-AU-03

**Given** the Auditor has reviewed the case and AI-assisted information  
**When** the Auditor completes the review  
**Then** the Auditor remains responsible for the final human decision.

**Testable evidence:**
- A human Auditor action is required to complete the review.
- AI output alone cannot close the case as a final decision.
- The final human decision is associated with the case.
- The UI and backend do not imply that AI independently determines the
  final outcome.

**Open decision:**
Exact final decision labels/options remain subject to confirmed business
rules.

---

## AC-11 — Failure and Error States

**Related stories:** Submission, storage, processing and review

The MVP must represent relevant failure conditions explicitly.

**At minimum, the workflow must account for:**
- Invalid or unsupported submission
- Media storage failure
- Case creation/persistence failure
- STT failure
- AI/media-analysis failure
- Missing or incomplete structured output
- Processing failure before Auditor review

**Testable evidence:**
- A failed step does not appear as a successfully completed step.
- The case/status reflects the failure sufficiently for the next role to
  understand what occurred.
- Failure states are distinguishable from successful processing.
- No final human decision is automatically generated from a failed AI
  process.

---

## AC-12 — AI Assistive / No Autonomous Final Decision

**Related stories:** US-AU-01, US-AU-03

**Given** AI processing produces a result  
**When** the result is presented to the Auditor  
**Then** the AI result remains advisory/assistive and cannot independently
make or finalise the moderation decision.

**Testable evidence:**
- AI output is presented as analysis/supporting information.
- Final case outcome requires Auditor action.
- No autonomous final decision is triggered by the AI result.
- The system does not treat the AI result as the final moderation outcome.

---

## AC-13 — Confirmed Decline / Manager Notification Behaviour

**Related stories:** US-AU-04, US-MG-01

**Given** the Auditor uses the confirmed decline/escalation pathway  
**When** the Auditor declines a case  
**Then** the agreed Manager notification/escalation behaviour is triggered.

**Testable evidence:**
- Auditor decline action is available where the confirmed workflow
  requires it.
- An Auditor decline triggers the confirmed Manager
  notification/escalation pathway.
- The relevant Manager notification/escalation event is generated.
- The event remains associated with the relevant case.

**Open detail:**
Exact notification content, Manager permissions and downstream
reassignment rules remain TBC where not yet confirmed.

---

## AC-14 — Wellbeing / Exposure-Management Design Direction

**Related stories:** US-MG-02

**Given** the system is designed to support Auditor wellbeing  
**When** exposure-management and wellbeing behaviour is represented  
**Then** the design must reflect the confirmed wellbeing priority without
treating unconfirmed thresholds or parameters as final requirements.

**Testable evidence:**
- Auditor wellbeing is represented as a core design consideration.
- Exposure management is represented in the UX/requirements direction.
- The design does not imply that moderation speed overrides wellbeing.
- Unconfirmed exposure limits are not presented as approved fixed values.
- Unconfirmed cooldown values are not presented as approved fixed values.
- Wellbeing design direction can be traced to the relevant requirement.

**Important boundary:**
This acceptance criterion confirms the **wellbeing/exposure-management
design direction**. It does not require all final wellbeing controls,
thresholds or values to be fully implemented in Week 1.

**Open details:**
- Exposure-limit values
- Cooldown duration/thresholds
- SOS parameters
- Exact Manager permissions
- Other wellbeing thresholds

These remain TBC unless separately confirmed.

---

# 2. Requirement Confirmation Status

The traceability matrix uses **Requirement Confirmation Status** rather
than a generic "Status" field.

This distinction is important:

- **Confirmed** — The requirement itself has been confirmed. This does
  NOT mean development, integration or testing is complete.
- **Confirmed direction; implementation detail TBC** — The requirement
  direction is confirmed, but the technical implementation detail remains
  open.
- **Confirmed expectation; format TBC** — The expected behaviour/output is
  confirmed, but the exact representation or format remains open.
- **Required** — The behaviour is required for the MVP/build and must be
  addressed during implementation and validation.
- **Open/TBC** — The requirement or business value has not been confirmed
  and must not be treated as a fixed implementation requirement.

> **Important:** Requirement Confirmation Status is a requirements
> governance field. It is not a development progress, completion or
> testing field.

---

# 3. Requirements-to-Build Traceability Matrix

| Requirement / User Story | Acceptance Criteria | UX Build / Validation Target | Developer Build / Validation Target | Requirement Confirmation Status |
|---|---|---|---|---|
| Public User submits approved synthetic/staged content | AC-01 | Submission flow clearly identifies allowed MVP input | Submission handling accepts valid staged input | Confirmed |
| Case is created after valid submission | AC-02, AC-03 | Case ID and processing state shown appropriately | Case creation, persistence and Case ID generation | Confirmed |
| Media is stored/referenced against the case | AC-04 | No unnecessary raw-media exposure in Auditor UI | COS/media-storage integration and case association | Confirmed direction; implementation detail TBC |
| Processing state is visible/trackable | AC-03, AC-11 | Processing, loading and failure states represented | Case/processing status persisted and updated | Confirmed |
| STT assists processing where required | AC-05 | Transcript/result presentation where applicable | STT integration and failure handling | Confirmed direction; technical details TBC |
| watsonx.ai produces structured AI output | AC-06 | Structured result presentation | AI integration/output contract | Confirmed direction |
| Media analysis is performed | AC-07 | Analysis state/result represented | Media-analysis integration and failure handling | Confirmed direction |
| Relevant incident timestamps/segments are returned | AC-08 | Timestamp/segment information shown where available | Timestamp/segment data included in structured result | Confirmed expectation; format TBC |
| Auditor reviews AI result | AC-09 | Auditor review flow | Retrieve/display structured case result | Confirmed |
| Auditor makes final human decision | AC-10, AC-12 | Human decision step clearly separated from AI output | Final decision requires Auditor action | Confirmed |
| AI remains assistive | AC-12 | UI must not imply autonomous moderation | Backend must not finalise outcome from AI alone | Confirmed |
| Auditor decline triggers Manager notification/escalation | AC-13 | Decline/escalation flow represented | Notification/escalation event supported | Confirmed direction; exact rules TBC |
| Manager receives relevant notification/escalation | AC-13 | Relevant Manager interaction represented | Manager notification/escalation behaviour supported | Confirmed direction; exact details TBC |
| Auditor wellbeing and exposure management are represented | AC-14 | Wellbeing/exposure-management design direction represented | Support required data/state without hard-coding unconfirmed thresholds | Confirmed direction; parameters TBC |
| Failure states are handled | AC-11 | Error/loading/failure states represented | Error states and status handling | Required |
| Unresolved values remain open | AC-06, AC-08, AC-10, AC-13, AC-14 | TBC values are not presented as approved requirements | Unconfirmed values are not hard-coded as final rules | Confirmed requirement |

---

# 4. Raw MVP Story-to-AC Traceability

| Story ID | User Story | Primary ACs |
|---|---|---|
| US-PU-01 | Public User submits approved synthetic/staged content | AC-01 |
| US-PU-02 | Public User receives/uses a Case ID for tracking | AC-02, AC-03 |
| US-PU-03 | Public User receives safe/clear submission behaviour | AC-01, AC-11 |
| US-AU-01 | Auditor reviews structured AI-assisted results | AC-06, AC-07, AC-08, AC-09, AC-12 |
| US-AU-02 | Auditor reviews the case and processing state | AC-03, AC-09, AC-11 |
| US-AU-03 | Auditor makes the final human decision | AC-10, AC-12 |
| US-AU-04 | Auditor uses the confirmed decline/escalation pathway | AC-13 |
| US-MG-01 | Manager receives the relevant notification/escalation | AC-13 |
| US-MG-02 | Manager interaction supports confirmed wellbeing/exposure-management direction | AC-14 |

---

# 5. Requirements → UX / Developer Task Mapping

## UX

UX should validate/design:

1. Public User submission flow.
2. Synthetic/staged content constraint messaging.
3. Case ID presentation.
4. Processing/loading/error states.
5. Auditor case review screen.
6. Structured AI result presentation:
   - severity
   - summary
   - timestamps/segments where available
7. Clear separation between AI analysis and final human decision.
8. Confirmed Auditor decline/escalation pathway.
9. Relevant Manager notification/interaction.
10. Wellbeing and exposure-management design direction.
11. No UI treatment that implies AI independently makes the final
    decision.
12. Do not present unresolved values as confirmed requirements.
13. Do not represent unconfirmed exposure/cooldown thresholds as final
    values.

## Developers

Developers should build/validate:

1. Submission handling.
2. Case creation and persistence.
3. Case ID generation.
4. COS/media storage integration.
5. Processing status handling.
6. STT integration/contract.
7. watsonx.ai structured-output integration.
8. Media-analysis processing.
9. Timestamp/segment handling.
10. Auditor result retrieval/review support.
11. Human final-decision persistence.
12. Failure/error states.
13. Confirmed Auditor-decline → Manager notification/escalation behaviour.
14. Protection against autonomous AI final decisions.
15. Data/state support required for wellbeing and exposure-management
    direction without hard-coding unconfirmed thresholds.

---

# 6. Unresolved Assumptions / TBC Items

The following must remain visible and must not be silently converted into
confirmed requirements:

- Exact severity scale.
- AI accuracy threshold.
- Exact final decision labels/options.
- Exact case reassignment rules after decline.
- Exposure-limit values.
- Cooldown duration/threshold values.
- SOS parameters.
- Exact Manager permissions.
- Exact Manager notification content.
- Exact COS bucket/path/naming convention.
- Exact STT model/configuration.
- Exact timestamp/segment format and granularity.
- Any implementation-specific database/table naming not yet confirmed.
- Any technical integration detail not yet agreed by the development
  team.

---

# 7. Sprint 2 Week 1 vs Sprint 2 End-to-End Boundary

Week 1 establishes the Raw MVP build baseline and implementation-ready
requirements.

The Week 1 requirements work defines:

- User stories
- Business rules
- Acceptance criteria
- Requirements-to-build traceability
- UX requirements
- Developer requirements
- Failure-state expectations
- Confirmed requirements versus TBC decisions

Week 1 does not imply that all end-to-end integration or final MVP
functionality has already been completed.

**End-to-end integration is targeted for Sprint 2 implementation.**

The Sprint 2 Raw MVP target remains:

**Submission → Case Creation → AI/STT Processing → Structured AI Results
→ Auditor Review → Human Final Decision**

with the confirmed:

**Auditor Decline → Manager Notification/Escalation**

path represented where required.

---

# 8. Priority and Scope Boundary

## P0 — Core Raw MVP

- Approved synthetic/staged submission
- Case creation
- Case ID
- Case/database persistence
- Media storage/reference
- STT processing
- Video/media analysis
- AI processing
- Structured AI output
- Severity
- Summary
- Incident timestamps/segments where available
- Auditor review
- Final-decision persistence
- Human final decision
- End-to-end workflow
- No autonomous AI final decision

## P1 — Confirmed Direction / Wellbeing and Escalation

- Reduced unnecessary exposure
- Exposure tracking
- Exposure-management direction
- Cooldown direction
- Auditor decline
- Manager notification/escalation
- Manager wellbeing/exposure oversight

Exact values and permissions remain TBC unless confirmed.

## P2 — Future / Enterprise Hardening

- Additional enterprise capabilities
- Production-scale hardening
- Further scalability features
- Other non-core capabilities outside the agreed Raw MVP

---

# 9. Dependencies

The following dependencies must remain visible:

- Client confirmation of severity scale.
- Exact final decision options.
- Accuracy threshold/validation target.
- Exposure-limit values.
- Cooldown and SOS parameters.
- Manager permissions.
- Exact Manager notification content.
- Final technical architecture/database-status consistency.
- Sprint 2 database service/technology confirmation.
- Sprint 2 environment/API availability.
- Cloud Object Storage/backend integration availability.
- AI/STT integration contract and proof of concept.
- Video/media-analysis implementation approach.
- UX alignment with requirements.

---

# 10. Assumptions

The following assumptions are used unless separately confirmed:

1. AI is assistive, not autonomous.
2. The Auditor remains responsible for the final decision.
3. Sprint 2 uses approved synthetic/staged content only.
4. Wellbeing is prioritised over moderation speed.
5. Exposure tracking and wellbeing controls are confirmed directions,
   while exact parameters remain open.
6. Auditor decline → Manager notification/escalation is a confirmed
   direction.
7. Exact reassignment rules remain open.
8. AI output is structured for downstream presentation and review.
9. Raw media is stored/referenced through the agreed media-storage layer.
10. The case database stores metadata, state and references rather than
    raw media bytes where the architecture separates those concerns.
11. Technical state names may follow the agreed architecture.
12. Unresolved business values will not be hard-coded as final
    requirements.

---

# 11. Week 1 Task Mapping

| Requirement Area | Sprint 2 Week 1 Task |
|---|---|
| Raw MVP user stories and business rules | T3 — Finalise Raw MVP User Stories & Business Rules |
| Acceptance criteria and build traceability | T4 — Finalise Acceptance Criteria & Build Traceability |
| Public User submission and case-state UX | T5 — Finalise Public User Submission & Case-State Specification |
| Auditor review and Manager oversight UX | T6 — Finalise Auditor Review & Manager Oversight Specification |
| Case creation and retrieval API | T7 — Implement Case Creation & Retrieval API |
| Database schema and processing-status persistence | T8 — Implement Core MVP Case Schema & Processing-Status Persistence |
| Cloud Object Storage and IBM runtime | T9 — Connect Cloud Object Storage & IBM Runtime Baseline |
| Speech-to-Text processing | T10 — Implement Speech-to-Text Processing & Transcript Contract |
| watsonx structured analysis | T11 — Implement watsonx Structured Analysis & Result Contract |
| Video/media analysis and incident timestamps | T12 — Implement Video/Media Analysis & Incident Timestamp Adapter |

---

# 12. Handoff

## PM

Use this document to:

- Track confirmed versus open requirements.
- Track unresolved business decisions.
- Coordinate Sprint 2 dependencies.
- Ensure TBC values are not treated as final requirements.
- Confirm changes before requirements become fixed implementation rules.

## UX

Use this document to:

- Design the Public User submission flow.
- Represent processing and error states.
- Design the Auditor review experience.
- Represent the human final decision clearly.
- Represent the confirmed decline → Manager notification/escalation path.
- Represent wellbeing/exposure-management direction.
- Avoid presenting unresolved business values as confirmed.

## Developers

Use this document as the implementation boundary for Sprint 2.

Developers should:

- Implement confirmed requirements.
- Preserve human final decision-making.
- Support the confirmed decline → Manager notification/escalation
  behaviour.
- Represent relevant failure states.
- Avoid hard-coding unconfirmed business values.
- Treat technical implementation details marked TBC as requiring
  confirmation before being treated as final.

---

# 13. Definition of Done

- [x] Each Raw MVP story has testable acceptance criteria.
- [x] Submission acceptance criteria defined.
- [x] Case ID acceptance criteria defined.
- [x] Processing-state expectations defined.
- [x] Database/persistence acceptance criteria defined.
- [x] COS/media-storage acceptance criteria defined.
- [x] STT acceptance criteria defined.
- [x] watsonx.ai structured-output acceptance criteria defined.
- [x] Video/media-analysis acceptance criteria defined.
- [x] Timestamp/segment acceptance criteria defined.
- [x] Auditor review acceptance criteria defined.
- [x] Auditor final-decision acceptance criteria defined.
- [x] AI assistive/no-autonomous-decision requirement defined.
- [x] Confirmed Auditor decline → Manager notification/escalation
      behaviour defined.
- [x] Separate wellbeing/exposure-management acceptance criterion
      defined.
- [x] Relevant failure/error states included.
- [x] Requirements mapped to UX and Developer work.
- [x] Raw MVP stories mapped to acceptance criteria.
- [x] Requirement Confirmation Status is distinguished from development
      completion/testing status.
- [x] Unresolved assumptions remain visible.
- [x] Exact notification content and reassignment rules remain TBC.
- [x] Exposure/cooldown values remain TBC.
- [x] AI remains assistive and does not make the final decision
      autonomously.
- [x] Week 1 build baseline is distinguished from Sprint 2
      end-to-end integration.
- [x] Artifact is ready for PM review and cross-role handoff.

---

## Status

**Sprint 2 Week 1 Acceptance Criteria & Requirements-to-Build
Traceability — Updated for PM Review**

The document defines the implementation-oriented acceptance criteria,
requirements confirmation status, traceability, wellbeing/exposure
direction, confirmed decline → Manager notification/escalation behaviour,
failure states, dependencies and remaining TBC decisions.

**Week 1 establishes the build baseline. End-to-end integration is
targeted for Sprint 2.**
