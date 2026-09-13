# Sprint 2 Week 1 Requirements, User Stories & Acceptance Criteria

## Purpose
Define implementation-ready Sprint 2 Week 1 requirements, user stories and acceptance criteria for the agreed Core MVP, translating Sprint 1 requirements into testable implementation boundaries.

**Planning boundary:** This document defines the implementation requirements for the Sprint 2 Raw MVP and the detailed Week 1 build baseline. Week 1 establishes the core components, contracts and implementation-ready specifications; full end-to-end integration is targeted during Week 2.

## Sprint 2 Week 1 Scope
**Core flow:** Public User submission → Case creation → Case ID → AI processing → structured AI results → Auditor review → human final decision.

### In scope
- Synthetic/staged content submission
- Case creation and unique Case ID
- Case metadata and processing-status persistence
- Media storage/reference through the agreed Cloud Object Storage direction
- Speech-to-Text processing for relevant approved audio
- Video/media analysis for approved synthetic/staged content
- AI processing and structured AI output
- Severity, summary, categories and incident timestamps/segments
- Auditor queue/case access and AI-assisted review
- Human final decision; AI must not decide autonomously
- Reduced unnecessary raw-media exposure
- Exposure tracking
- Auditor decline and Manager notification/escalation
- Wellbeing controls as agreed directions, with exact parameters marked TBC

### Not implementation-final / out of scope
- Real abusive content or real agency data
- Autonomous AI decisions
- Production deployment/load testing
- Exact severity scale
- Exact final decision labels
- Final exposure-limit values
- Final cooldown/SOS triggers
- Exact Manager permissions
- Exact reassignment rules
- Advanced enterprise hardening beyond the MVP slice

## Actors
**Public User:** submits permitted synthetic/staged content.

**Auditor:** reviews AI-generated information and makes the final human decision; wellbeing is a priority.

**Manager/Supervisor:** receives relevant wellbeing/decline escalation and provides oversight; exact permissions remain TBC.

## User Stories

### US-01 — Submit content
As a Public User, I want to submit permitted content so that a case can be created for review. **Priority: P0**

### US-02 — Create a case
As the system, I want to create a unique case and Case ID after a valid submission so that it can be tracked. **Priority: P0**

### US-03 — Process submitted content
As the system, I want to process submitted content with AI so that useful review information is generated. **Priority: P0**

### US-04 — View structured AI results
As an Auditor, I want to see AI-generated severity, summary and incident timestamps so that I can assess a case before deciding whether raw media needs to be viewed. **Priority: P0**

### US-05 — Review a case
As an Auditor, I want to review AI-assisted case information so that I can make an informed human decision. **Priority: P0**

### US-06 — Make the final human decision
As an Auditor, I want to make the final decision so that AI does not make an autonomous moderation decision. **Priority: P0**

### US-07 — Protect auditor wellbeing
As an Auditor, I want unnecessary exposure to harmful material minimised so that my wellbeing is prioritised over moderation speed. **Priority: P1**

### US-08 — Track exposure
As an Auditor, I want my content exposure tracked so that wellbeing controls can be applied appropriately. **Priority: P1**

### US-09 — Decline a case
As an Auditor, I want to decline a case when appropriate so that I do not have to continue reviewing content that may negatively affect my wellbeing. **Priority: P1**

### US-10 — Notify Manager
As a Manager/Supervisor, I want to be notified when an Auditor declines a case so that appropriate follow-up or reassignment can occur. **Priority: P1**

### US-11 — Manager wellbeing oversight
As a Manager/Supervisor, I want visibility of relevant auditor workload/exposure information so that I can support wellbeing. **Priority: P1**

## Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-S2-01 | Accept permitted synthetic/staged content submissions. | P0 |
| FR-S2-02 | Create a unique Case ID for a valid submission. | P0 |
| FR-S2-03 | Progress a created case to AI processing. | P0 |
| FR-S2-04 | Produce structured AI results for human review. | P0 |
| FR-S2-05 | Include severity, summary and incident timestamps where available. | P0 |
| FR-S2-06 | Allow the Auditor to access and review AI-generated information. | P0 |
| FR-S2-07 | Provide AI information before unnecessary raw-media exposure where applicable. | P1 |
| FR-S2-08 | Preserve Auditor responsibility for the final decision. | P0 |
| FR-S2-09 | Prevent AI from autonomously finalising moderation decisions. | P0 |
| FR-S2-10 | Support Auditor exposure tracking. | P1 |
| FR-S2-11 | Support an Auditor declining a case. | P1 |
| FR-S2-12 | Notify/escalate to the Manager/Supervisor after a decline. | P1 |
| FR-S2-13 | Support wellbeing controls such as exposure limits/cooldown/SOS, with exact thresholds TBC. | P1 |
| FR-S2-14 | Support relevant Manager wellbeing/exposure oversight. | P1 |
| FR-S2-15 | Store or reference approved submitted media using the agreed Cloud Object Storage direction rather than storing raw media directly in the case database. | P0 |
| FR-S2-16 | Persist case metadata, media reference and processing status so a case can be retrieved by Case ID throughout the Raw MVP workflow. | P0 |
| FR-S2-17 | Associate structured AI results, including transcript/output references, severity, summary, categories and incident timestamps, with the correct case. | P0 |
| FR-S2-18 | Persist the human Auditor's final decision against the relevant case. | P0 |
| FR-S2-19 | Support transcription of relevant approved audio content through the agreed Speech-to-Text integration. | P0 |
| FR-S2-20 | Support analysis of approved synthetic/staged video or media so relevant incident segments/timestamps can contribute to the structured review result. | P0 |

## Acceptance Criteria

- **AC-S2-01 Submission:** Given permitted synthetic/staged content, when the Public User submits it, the system accepts it and begins case creation.
- **AC-S2-02 Case creation:** Given a valid submission, when creation completes, a unique Case ID is generated.
- **AC-S2-03 AI processing:** Given a created case, when AI processing runs, structured AI output is produced where processing succeeds.
- **AC-S2-04 Severity:** When a severity result exists, it is displayed to the Auditor as part of the structured AI result.
- **AC-S2-05 Summary:** When an AI summary exists, it is displayed to the Auditor.
- **AC-S2-06 Timestamps:** When incident timestamps exist, they are displayed and can support targeted review.
- **AC-S2-07 Auditor review:** Given AI results, the Auditor can review them before making a final decision.
- **AC-S2-08 Human decision:** The final decision is made by the human Auditor, not automatically by AI.
- **AC-S2-09 End-to-end:** A valid submission can progress through case creation, AI processing, Auditor review and human decision by the end of the Sprint 2 Raw MVP integration.
- **AC-S2-10 Reduced exposure:** AI-generated information is available before unnecessary raw-media exposure where applicable.
- **AC-S2-11 Synthetic/staged:** Sprint 2 implementation and demonstration use permitted synthetic/staged content only.
- **AC-S2-12 No autonomous decision:** AI output cannot directly finalise a moderation decision.
- **AC-S2-13 Decline escalation:** When an Auditor declines a case, the relevant Manager/Supervisor notification or escalation is triggered.
- **AC-S2-14 Wellbeing parameters:** Wellbeing controls may be designed, but unconfirmed thresholds/triggers remain TBC and are not treated as approved business rules.
- **AC-S2-15 Storage:** Given a valid approved submission, the media is stored/referenced through the agreed storage layer and the associated media reference is linked to the correct case.
- **AC-S2-16 Persistence:** A created case and its processing status can be persisted and retrieved using its Case ID.
- **AC-S2-17 AI result persistence:** Structured AI results are associated with the correct Case ID and are available for Auditor review.
- **AC-S2-18 Decision persistence:** When the Auditor submits a final human decision, it is associated with the correct case.
- **AC-S2-19 STT:** Given valid approved audio input, the processing pipeline can return a transcript for downstream AI-assisted analysis.
- **AC-S2-20 Video/media analysis:** Given approved synthetic/staged video, the processing pipeline can identify or produce relevant media-analysis information and incident segments/timestamps for the structured result.

## Edge Cases
- Invalid or unsupported submission
- Submission or processing failure
- Database connection or persistence failure
- Cloud Object Storage/media-reference failure
- Incomplete/unavailable AI output
- Missing Speech-to-Text result
- Missing or failed video/media analysis
- Missing incident timestamps
- Missing/uncertain severity
- Auditor declines a case
- Exposure threshold reached once confirmed
- Cooldown/SOS triggers remain unconfirmed
- Manager notification failure
- Raw media remains hidden until intentionally revealed where required
- Final decision labels remain draft/TBC until client confirmation

## Dependencies
- Client confirmation of severity scale
- Exact final decision options
- Accuracy threshold/validation target
- Exposure-limit values
- Cooldown and SOS parameters
- Manager permissions
- Final technical architecture/database-status consistency
- Sprint 2 database service/technology confirmation
- Sprint 2 environment/API availability
- Cloud Object Storage/backend integration availability
- AI/STT integration contract and proof of concept
- Video/media-analysis implementation approach
- UX alignment with requirements

## Assumptions
- AI is assistive, not autonomous.
- Auditor remains responsible for the final decision.
- Sprint 2 uses synthetic/staged content only.
- Wellbeing is prioritised over moderation speed.
- Exposure tracking and wellbeing controls are confirmed directions, while exact parameters remain open.
- Decline → Manager notification/escalation is a confirmed direction; exact reassignment rules remain open.
- AI output is structured for downstream presentation and review.
- Raw media is stored/referenced through the agreed media-storage layer; the case database stores metadata, state and references rather than raw media bytes.

## Priority Summary
**P0:** submission, case creation/ID, case/database persistence, media storage/reference, STT, video/media analysis, AI processing, structured output, severity, summary, categories, timestamps, Auditor review, final-decision persistence, human final decision, end-to-end flow, no autonomous AI decision.

**P1:** reduced exposure, exposure tracking/limits, cooldown, SOS, Auditor decline, Manager notification/escalation, Manager wellbeing/exposure oversight.

**P2:** future enterprise hardening and non-core capabilities.

## Traceability to Sprint 1
| Sprint 1 baseline | Sprint 2 Week 1 |
|---|---|
| AC-01 Submission | AC-S2-01 |
| AC-02 Case creation | AC-S2-02 |
| AC-03 AI processing | AC-S2-03 |
| AC-04 Severity | AC-S2-04 |
| AC-05 Summary | AC-S2-05 |
| AC-06 Timestamps | AC-S2-06 |
| AC-07 Auditor review | AC-S2-07 |
| AC-08 Human final decision | AC-S2-08 |
| AC-09 End-to-end | AC-S2-09 |
| AC-10 Reduced exposure | AC-S2-10 |
| AC-11 Synthetic/staged only | AC-S2-11 |
| AC-12 No autonomous decision | AC-S2-12 |
| Wellbeing/exposure/decline direction | AC-S2-13 to AC-S2-14 |
| Sprint 1 storage/database foundation | AC-S2-15 to AC-S2-18 |
| Sprint 1 AI/STT validation direction | AC-S2-19 |
| Sprint 1 video/media Raw MVP direction | AC-S2-20 |

## Week 1 Task Mapping
| Requirement area | Sprint 2 Week 1 task |
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

## Handoff
**PM:** This document was provided to the PM as the requirements baseline for Sprint 2 Week 1 task planning, dependency mapping and sequencing.

**UX:** The user stories, acceptance criteria and open/TBC rules were provided to UX as the requirements reference for implementation-ready flow and interface handoff.

**Developers:** The functional requirements and acceptance criteria were provided to Dev1 and Dev2 as the implementation boundary for the Raw MVP, including the requirement to preserve final human decision-making.

## Definition of Done
- Sprint 2 Week 1 scope defined
- Week 1 versus Sprint 2 end-to-end boundary clarified
- Relevant user stories defined
- Functional requirements implementation-oriented
- Acceptance criteria specific and testable
- Database/COS requirements explicitly represented
- STT and video/media requirements explicitly represented
- Edge cases documented
- Dependencies documented
- Assumptions separated from confirmed requirements
- Priorities identified
- Requirements mapped to proposed Week 1 tasks
- Artifact ready for PM Sprint 2 planning and cross-role handoff
