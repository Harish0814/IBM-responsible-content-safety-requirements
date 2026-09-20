# Sprint 2 Week 1 — Raw MVP Acceptance Criteria & Requirements-to-Build Traceability

**Task:** [REQUIREMENTS] Finalise Acceptance Criteria & Build Traceability  
**Role:** BA  
**Sprint:** Sprint 2  

## Purpose

Convert the approved Raw MVP user stories into measurable, testable acceptance criteria and provide a requirements-to-build traceability view for UX and Developers.

---

# 1. Scope and Requirement Baseline

This artifact is based on the validated Sprint 1 Core MVP and the Sprint 2 Week 1 Raw MVP user stories and business rules.

### Core MVP workflow

**Public User → Safe Synthetic/Staged Submission → Case ID Creation → Media/AI Processing → Structured AI Results → Auditor Review → Final Human Decision**

### Core principles

- Only approved **synthetic/staged content** is used for the MVP.
- AI is **assistive**, not the final decision-maker.
- The **Auditor makes the final human decision**.
- AI results should be presented as structured information for Auditor review.
- Confirmed requirements are separated from unresolved business/implementation decisions.
- Exact values or rules that have not been confirmed must remain open rather than being treated as final requirements.

---

# 2. Acceptance Criteria

## AC-01 — Public User Submission

**Related stories:** US-PU-01, US-PU-03

**Given** a Public User has approved synthetic/staged content  
**When** the user submits the content through the MVP submission flow  
**Then** the system accepts the submission and creates/initiates a case for processing.

**Testable evidence:**
- Valid synthetic/staged submission can be submitted.
- The submission is associated with a case reference.
- Unsupported/unapproved content is not treated as valid MVP input.

---

## AC-02 — Case ID Creation

**Related stories:** US-PU-02

**Given** a valid submission is accepted  
**When** the case is created  
**Then** the system generates a unique case identifier that can be used to track the submission through processing and review.

**Testable evidence:**
- Case ID is generated.
- Case ID is associated with the submitted media.
- Case ID remains available for downstream processing/review.

---

## AC-03 — Case Persistence / Database

**Related stories:** US-PU-02, US-AU-02

**Given** a case has been created  
**When** case information is persisted  
**Then** the required case reference and relevant processing information are stored so the case can be retrieved for subsequent workflow steps.

**Testable evidence:**
- Case record can be created.
- Case record can be retrieved using the case identifier.
- Required processing/status information is associated with the case.

**Implementation note:** Exact database schema/table names remain an implementation detail unless separately confirmed.

---

## AC-04 — COS / Media Storage

**Related stories:** US-PU-01

**Given** an approved synthetic/staged media file is submitted  
**When** the submission is accepted  
**Then** the media is stored in the approved object-storage mechanism and remains associated with the case.

**Testable evidence:**
- Media upload succeeds for valid input.
- Stored media can be associated with the Case ID.
- Storage failure is surfaced as an appropriate failure state.

**Open implementation detail:** Exact COS bucket, object path and naming convention are to be confirmed by the technical implementation.

---

## AC-05 — STT Processing

**Related stories:** US-AU-01, US-AU-02

**Given** submitted media contains audio requiring transcription  
**When** STT processing is invoked  
**Then** the system attempts transcription and records the resulting transcript/status against the case.

**Testable evidence:**
- STT processing is invoked for supported input.
- Transcript is returned when processing succeeds.
- STT failure is represented by an explicit processing/failure state rather than silently treated as successful.

**Open implementation detail:** Exact STT configuration/model and threshold values are implementation decisions unless separately confirmed.

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

**Open decision:** Exact severity scale and AI accuracy threshold remain unresolved unless separately approved.

---

## AC-07 — Video / Media Analysis

**Related stories:** US-AU-01

**Given** a valid supported media submission exists  
**When** media analysis is performed  
**Then** the system attempts to analyse the media and produces the agreed structured result or an explicit processing failure state.

**Testable evidence:**
- Analysis can be initiated for supported media.
- Successful analysis produces structured output.
- Failed analysis does not produce a misleading successful result.

---

## AC-08 — Timestamp / Segment Information

**Related stories:** US-AU-01

**Given** the AI analysis identifies relevant incidents or segments  
**When** the analysis result is returned  
**Then** relevant timestamps/segment references are included where available so the Auditor can understand when an identified event occurs.

**Testable evidence:**
- Timestamp/segment information is returned when available.
- The information is linked to the relevant case/result.
- Missing timestamp information is not represented as confirmed evidence.

**Open detail:** Exact timestamp/segment format and granularity are implementation details unless confirmed.

---

## AC-09 — Auditor Review

**Related stories:** US-AU-01, US-AU-02

**Given** AI processing has produced an available result  
**When** the Auditor opens the case  
**Then** the Auditor can review the structured AI information required for the MVP.

**Testable evidence:**
- Auditor can access the case.
- Severity, summary and available timestamps/segments are visible.
- The Auditor can review AI output before making the final human decision.

---

## AC-10 — Final Human Decision

**Related stories:** US-AU-03

**Given** the Auditor has reviewed the case and AI-assisted information  
**When** the Auditor completes the review  
**Then** the Auditor remains responsible for the final human decision.

**Testable evidence:**
- A human Auditor action is required to complete the review.
- AI output alone cannot close the case as a final decision.
- The final decision is associated with the case.

**Open decision:** Exact final decision labels/options remain subject to confirmed business rules.

---

## AC-11 — Failure and Error States

**Related stories:** US-PU-01, US-PU-02, US-AU-01, US-AU-02

The MVP must represent relevant failure conditions explicitly.

**At minimum, the workflow must account for:**
- Invalid/unsupported submission
- Media storage failure
- Case creation/persistence failure
- STT failure
- AI/media-analysis failure
- Missing/incomplete structured output
- Processing failure before Auditor review

**Testable evidence:**
- A failed step does not appear as a successful completed step.
- The case/status reflects the failure sufficiently for the next role to understand what occurred.
- No final human decision is automatically generated from a failed AI process.

---

## AC-12 — AI Assistive / No Autonomous Final Decision

**Related stories:** US-AU-01, US-AU-03

**Given** AI processing produces a result  
**When** the result is presented to the Auditor  
**Then** the AI result remains advisory/assistive and cannot independently make or finalise the moderation decision.

**Testable evidence:**
- AI output is presented as analysis/supporting information.
- Final case outcome requires Auditor action.
- No autonomous final decision is triggered by the AI result.

---

## AC-13 — Confirmed Decline / Manager Notification Behaviour

**Related stories:** US-AU-04, US-MG-01

**Given** the Auditor uses the confirmed decline/escalation pathway  
**When** the Auditor declines a case  
**Then** the confirmed Manager notification/escalation behaviour is triggered.

**Testable evidence:**
- Auditor decline action is available where the confirmed workflow requires it.
- The confirmed Manager notification/escalation event is generated when the Auditor declines the case.
- The event remains associated with the relevant case.

**Open detail:** Exact notification content, Manager permissions and reassignment rules remain open where not yet confirmed.

---

## AC-14 — Wellbeing / Exposure-Management Design Direction

**Related stories:** US-MG-02

**Given** the confirmed requirement that Auditor wellbeing and exposure management are part of the solution direction  
**When** Sprint 2 UX and implementation planning is performed  
**Then** the design direction is represented without treating unconfirmed thresholds or the full wellbeing feature set as fixed Week 1 implementation requirements.

**Testable evidence:**
- UX/design documentation represents wellbeing and exposure-management considerations.
- Unconfirmed exposure limits, cooldown values and related thresholds remain explicitly TBC.
- The requirement is not interpreted as requiring the full wellbeing feature set to be completed in Week 1.

---

# 3. Requirements-to-Build Traceability Matrix

| Requirement / User Story | Acceptance Criteria | UX Build / Validation | Developer Build / Validation | Requirement Confirmation Status |
|---|---|---|---|---|
| Public User submits approved synthetic/staged content | AC-01 | Submission flow clearly identifies allowed MVP input | Submission endpoint/flow accepts valid staged input | Confirmed |
| Case is created after valid submission | AC-02, AC-03 | Case ID/status shown appropriately | Case creation and persistence implemented | Confirmed |
| Media is stored against the case | AC-04 | No unnecessary raw-media exposure in Auditor UI | COS/media-storage integration and case association | Confirmed direction; implementation detail TBC |
| Processing state is visible/trackable | AC-03, AC-11 | Processing/loading/error states represented | Case/processing status persisted and updated | Confirmed |
| STT assists processing where required | AC-05 | Transcript/result presentation where applicable | STT integration and failure handling | Confirmed direction; technical details TBC |
| watsonx.ai produces structured AI output | AC-06 | Structured result presentation | AI integration/output contract | Confirmed direction |
| Media analysis is performed | AC-07 | Analysis state/result represented | Media-analysis integration and failure handling | Confirmed direction |
| Relevant incident timestamps/segments are returned | AC-08 | Timestamp/segment information shown where available | Timestamp/segment data included in structured result | Confirmed expectation; format TBC |
| Auditor reviews AI result | AC-09 | Auditor review flow | Retrieve/display structured case result | Confirmed |
| Auditor makes final decision | AC-10, AC-12 | Human decision step clearly separated from AI output | Final decision requires Auditor action | Confirmed |
| AI remains assistive | AC-06, AC-12 | UI must not imply autonomous moderation | Backend must not finalise outcome from AI alone | Confirmed |
| Auditor decline triggers relevant Manager behaviour | AC-13 | Decline/escalation flow represented | Notification/escalation event supported | Confirmed requirement; exact rules TBC |
| Manager receives the relevant notification/escalation | AC-13 | Manager notification/interaction represented | Notification/escalation event supported | Confirmed requirement; exact rules TBC |
| Wellbeing/exposure management is represented as a design direction | AC-14 | Wellbeing/exposure considerations represented without fixed TBC values | Do not hard-code unconfirmed thresholds | Confirmed design direction; values TBC |
| Failure states are handled | AC-11 | Error/loading/failure states represented | Error states and status handling implemented | Required |
| Unresolved values remain open | All applicable ACs | Do not display TBC values as approved rules | Do not hard-code unconfirmed business values | Confirmed requirement |

**Traceability status note:** The **Requirement Confirmation Status** column indicates whether the requirement/business rule itself is confirmed, directionally confirmed, or still subject to TBC/open decisions. **Confirmed does not mean the requirement has already been fully developed, integrated, or tested.**

---

# 4. Raw MVP Story-to-AC Traceability

| Story ID | User Story | Primary ACs |
|---|---|---|
| US-PU-01 | Public User submits approved synthetic/staged content | AC-01, AC-04, AC-11 |
| US-PU-02 | Public User receives/uses a Case ID for tracking | AC-02, AC-03, AC-11 |
| US-PU-03 | Public User receives safe/clear submission behaviour | AC-01, AC-11 |
| US-AU-01 | Auditor reviews structured AI-assisted results | AC-05, AC-06, AC-07, AC-08, AC-09, AC-12 |
| US-AU-02 | Auditor reviews the case and processing state | AC-03, AC-09, AC-11 |
| US-AU-03 | Auditor makes the final human decision | AC-10, AC-12 |
| US-AU-04 | Auditor can use the confirmed decline/escalation pathway | AC-13 |
| US-MG-01 | Manager receives the relevant notification/escalation | AC-13 |
| US-MG-02 | Manager interaction remains within confirmed wellbeing/exposure requirements | AC-14 |

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
10. Wellbeing/exposure-management design direction.
11. No UI treatment that implies AI independently makes the final decision.
12. Do not present unresolved values as confirmed requirements.

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
13. Confirmed decline/Manager notification behaviour.
14. Protection against autonomous AI final decisions.
15. Do not hard-code unconfirmed business values.

---

# 6. Unresolved Assumptions / TBC Items

The following must remain visible and must not be silently converted into confirmed requirements:

- Exact severity scale.
- AI accuracy threshold.
- Exact final decision labels/options.
- Exact case reassignment rules after decline.
- Exposure-limit values.
- Cooldown duration/threshold values.
- Exact Manager permissions.
- Exact Manager notification content.
- Exact COS bucket/path/naming convention.
- Exact STT model/configuration.
- Exact timestamp/segment format and granularity.
- Any implementation-specific database/table naming not yet confirmed.

---

# 7. Definition of Done

- [x] Each Raw MVP story has testable acceptance criteria.
- [x] Submission acceptance criteria defined.
- [x] Case ID acceptance criteria defined.
- [x] Database/persistence acceptance criteria defined.
- [x] COS/media-storage acceptance criteria defined.
- [x] STT acceptance criteria defined.
- [x] watsonx.ai structured-output acceptance criteria defined.
- [x] Video/media-analysis acceptance criteria defined.
- [x] Timestamp/segment acceptance criteria defined.
- [x] Auditor final-decision acceptance criteria defined.
- [x] Confirmed Auditor decline → Manager notification/escalation acceptance criterion defined.
- [x] Wellbeing/exposure-management design direction represented without fixing TBC values.
- [x] Relevant failure/error states included.
- [x] Requirements mapped to UX and Developer work.
- [x] Unresolved assumptions remain visible.
- [x] AI remains assistive and does not make the final decision autonomously.

**BA outcome:** The Raw MVP user stories have been converted into measurable acceptance criteria and mapped to the UX and Developer build/validation responsibilities. Confirmed requirements are separated from unresolved business and implementation decisions.

**Week 1 build-baseline note:** Week 1 establishes the Raw MVP build baseline and implementation-ready requirements. End-to-end integration is targeted for Week 2.
