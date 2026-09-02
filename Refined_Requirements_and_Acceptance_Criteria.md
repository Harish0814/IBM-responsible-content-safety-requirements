# [REQUIREMENTS] Refine Requirements & Acceptance Criteria

**IBM × RMIT Capstone — Responsible Content-Safety Infrastructure**

**Task:** Refine Requirements & Acceptance Criteria  
**Role:** Business Analyst (BA)  
**Project:** Responsible Content-Safety Infrastructure  
**Team:** 05-IBM-RCS Infrastructure — Team 1  
**Sprint:** Sprint 1 — Design & Bootstrap  
**Week:** Sprint 1 Week 2  
**Status:** Ready for PM / UX / Developers Review

---

## 1. Purpose

This document refines the Sprint 1 requirements baseline using confirmed project direction and Week 1 client outcomes.

It provides UX and Developers with clear, testable requirements for the core AI-assisted review workflow, Public User, Auditor and Manager behaviour, reviewer wellbeing, exposure controls, case decline/escalation, acceptance criteria, assumptions and unresolved decisions.

The university development and demonstration must use approved synthetic/staged content only.

---

## 2. Confirmed Core Workflow

**Public User submits content → Case created / Case ID generated → AI video/audio analysis → Structured AI outputs → Auditor review → Final human review decision**

AI is assistive and does not make the final review decision autonomously.

---

## 3. User and Stakeholder Requirements

### 3.1 Public User

**Goal:** Submit content for review.

The Public User shall:
- submit approved synthetic/staged content;
- receive a Case ID after successful case creation;
- not access protected Auditor or Manager functionality;
- not access sensitive reviewer, case or operational information.

### 3.2 Auditor — Primary User

**Goal:** Review cases using AI assistance while minimising unnecessary exposure to potentially distressing content.

The Auditor shall:
- access cases available for review according to access rules;
- review structured AI-assisted information;
- review severity, summary and incident timestamps;
- make the final human review decision;
- have a right to decline a case where the applicable wellbeing requirement applies;
- receive appropriate wellbeing protection when exposure thresholds are reached;
- not be required to prioritise moderation speed over reviewer wellbeing.

**Human-in-the-loop rule:** The Auditor retains responsibility for the final review decision.

### 3.3 Manager / Supervisor

**Goal:** Provide oversight of cases, reviewer wellbeing and exposure controls.

The Manager/Supervisor shall:
- receive appropriate wellbeing notifications/escalations;
- have visibility of relevant reviewer wellbeing status;
- control or adjust reviewer exposure limits where authorised;
- receive escalation when an Auditor declines a case because of wellbeing concerns;
- access only information permitted by the role.

---

## 4. Refined Functional Requirements

### FR-01 — Content Submission
The system shall allow a Public User to submit approved synthetic/staged video or audio content.

**Acceptance:** A valid approved test file can be submitted, a case is created, and a Case ID is generated.

### FR-02 — Case Creation
The system shall create a unique Case ID for submitted content.

**Acceptance:** Each successful submission receives an identifiable Case ID.

### FR-03 — AI Video/Audio Processing
The system shall process approved test content through the AI analysis workflow.

**Acceptance:** Approved test content can be processed and structured results are produced.

### FR-04 — Structured AI Outputs
The system shall provide structured AI-assisted information for Auditor review.

Core outputs:
- severity information;
- summary;
- incident timestamps.

Additional outputs such as tags or transcription may be included where confirmed and technically feasible.

**Acceptance:** Agreed outputs are available to the Auditor in an understandable structured form.

### FR-05 — Auditor Review
The system shall present AI-assisted case information to the Auditor.

**Acceptance:** The Auditor can access the relevant case and review severity, summary and timestamps before making a decision.

### FR-06 — Final Human Decision
The Auditor shall retain responsibility for the final review decision.

**Acceptance:** The Auditor can make the final decision and AI cannot autonomously make that decision.

---

## 5. Reviewer Wellbeing Requirements

### FR-07 — Wellbeing Takes Priority Over Moderation Speed
The system shall prioritise Auditor wellbeing over moderation speed when the two objectives conflict.

**Acceptance:**
- The system must not require continued review solely to maintain throughput when a wellbeing control requires intervention.
- Triggered wellbeing controls take precedence over throughput.

### FR-08 — Exposure Tracking
The system should track reviewer exposure to support exposure management.

**Acceptance:** Relevant exposure information can be recorded and used by wellbeing-control logic.

### FR-09 — Exposure Limits
The system shall support configurable exposure limits for Auditors.

**Acceptance:**
- An exposure limit can be defined.
- The system can determine when it is reached.
- When reached, further assignment/review is prevented or paused according to the approved workflow.

### FR-10 — Cooldown
The system shall support cooldown following applicable high-severity exposure.

**Acceptance:** A configured trigger can start cooldown and prevent continued review for the required period.

### FR-11 — SOS / Supervisor Alert
The system shall support an instant supervisor/SOS escalation mechanism.

**Acceptance:** An authorised Auditor can trigger SOS and the appropriate Manager/Supervisor receives an alert.

### FR-12 — Manager Wellbeing Notification
The system shall provide an appropriate notification to the Manager/Supervisor when a reviewer wellbeing event requires managerial attention.

**Acceptance:** A qualifying event generates a notification without unnecessarily exposing sensitive content.

### FR-13 — Manager-Controlled Exposure Limits
The Manager/Supervisor shall be able to control reviewer exposure limits where authorised.

**Acceptance:** An authorised Manager can view and modify the applicable limit, and unauthorised users cannot modify it.

### FR-14 — Auditor Right to Decline
The system shall support an Auditor's right to decline a case where the applicable wellbeing requirement is triggered.

**Acceptance:** The Auditor can indicate they cannot safely continue, the system does not force continued review, and the event is recorded appropriately.

### FR-15 — Decline → Manager Escalation
Where an Auditor declines because of a wellbeing concern, the system shall support escalation to the Manager/Supervisor.

**Acceptance:** A qualifying decline generates the appropriate Manager/Supervisor escalation. Automatic reassignment is not assumed until the business rule is confirmed.

---

## 6. Access and Safety Requirements

### FR-16 — Role-Based Access
The system shall distinguish Public User, Auditor and Manager/Supervisor access.

**Acceptance:** Each role can access only authorised functions.

### FR-17 — Sensitive Information Protection
The system shall protect sensitive reviewer, case and project information.

**Acceptance:** No real agency data, real harmful content, credentials or tokens are used/exposed in the university demonstration.

### FR-18 — No Autonomous Final Decision
AI output shall remain decision support.

**Acceptance:** The final review decision remains with the Auditor.

### FR-19 — Structured AI Result
AI processing should return a structured result suitable for downstream review.

### FR-20 — AI Accuracy Validation
AI classification shall be validated against an agreed threshold when that threshold is confirmed by the client.

**Status:** Accuracy threshold remains an open decision where not yet confirmed.

---

## 7. Priority and Scope

### P0 — Core End-to-End Functionality
- Approved synthetic/staged submission
- Case creation and Case ID
- AI video/audio analysis
- Structured AI outputs
- Auditor review
- Final human decision
- Human-in-the-loop control

### P1 — Wellbeing and Exposure Design
The Sprint 1 design/prototype shall represent:
- exposure tracking;
- exposure limits;
- cooldown;
- SOS;
- Auditor right to decline;
- Manager wellbeing notification;
- Manager-controlled exposure limits;
- decline → Manager escalation.

Implementation timing must follow the agreed sprint roadmap and technical dependencies.

### P2 — Future Refinement / Enterprise Hardening
- advanced access controls;
- production deployment refinement;
- advanced wellbeing analytics;
- production-scale performance/load testing;
- other non-essential enterprise functionality.

---

## 8. Confirmed Requirements vs Assumptions vs Open Questions

### Confirmed Requirements / Direction
- AI assists rather than replaces human judgement.
- Auditor is the primary review user.
- Reviewer wellbeing is a key design objective.
- Wellbeing takes priority over moderation speed where they conflict.
- Exposure management is required in the broader solution.
- Auditor decline and Manager escalation are required design considerations.
- Manager/Supervisor oversight includes wellbeing notification and authorised exposure controls.
- The core end-to-end workflow remains the main product direction.
- Only approved synthetic/staged content is used for university development and demonstration.

### Assumptions
- Final exposure-limit values will be configured after the appropriate decision is confirmed.
- Final cooldown duration will be configured after the applicable business rule is confirmed.
- Manager/Supervisor controls apply only where the role is authorised.
- Tags/transcription depend on confirmation and technical feasibility.

### Open Questions
1. What exact severity scale should be used?
2. What minimum AI accuracy threshold should be used?
3. What exact final decision options should be available to the Auditor?
4. What exact case assignment/reassignment behaviour should follow an Auditor decline?
5. What exposure-limit values should apply?
6. What cooldown duration and trigger thresholds should apply?
7. What exact Manager/Supervisor notification content should be shown?
8. What role permissions should apply to Manager-controlled exposure settings?

Unresolved questions must remain documented until confirmed rather than being silently assumed.

---

## 9. Acceptance Criteria Traceability

| Requirement | Acceptance Criteria |
|---|---|
| FR-01 Content Submission | AC-01 |
| FR-02 Case Creation | AC-02 |
| FR-03 AI Processing | AC-03 |
| FR-04 Structured Outputs | AC-04 |
| FR-05 Auditor Review | AC-05 |
| FR-06 Final Human Decision | AC-06 |
| FR-07 Wellbeing Priority | AC-07 |
| FR-08 Exposure Tracking | AC-08 |
| FR-09 Exposure Limits | AC-09 |
| FR-10 Cooldown | AC-10 |
| FR-11 SOS | AC-11 |
| FR-12 Manager Wellbeing Notification | AC-12 |
| FR-13 Manager-Controlled Exposure Limits | AC-13 |
| FR-14 Auditor Right to Decline | AC-14 |
| FR-15 Decline → Manager Escalation | AC-15 |
| FR-16 Role-Based Access | AC-16 |
| FR-17 Sensitive Information Protection | AC-17 |
| FR-18 No Autonomous Final Decision | AC-18 |
| FR-19 Structured AI Result | AC-19 |
| FR-20 AI Accuracy Validation | AC-20 |

---

## 10. Handoff to UX

UX should use this document to create detailed Auditor and Manager workflows and the Sprint 1 digital prototype.

The prototype should represent:
- core submission → analysis → review → final decision;
- AI-result presentation;
- wellbeing and exposure controls;
- cooldown;
- SOS;
- Auditor decline;
- Manager notification;
- Manager-controlled exposure limits;
- decline → escalation.

The Auditor remains the primary persona. Any design conflict or ambiguity should be raised with the BA/PM.

---

## 11. Handoff to Developers

Developers should use these requirements and acceptance criteria as the implementation boundary.

Developers should:
- implement confirmed requirements only;
- preserve human final decision-making;
- use approved synthetic/staged content;
- treat wellbeing controls as explicit product requirements;
- align exposure controls with authorised Manager behaviour;
- avoid inventing unconfirmed decline/reassignment rules;
- raise technical dependencies and requirement conflicts to the BA/PM.

---

## 12. Handoff to PM

The PM should:
- review the refined requirements;
- track unresolved client decisions;
- confirm severity scale and accuracy threshold when available;
- coordinate confirmation of decision and assignment/reassignment rules;
- confirm exposure-limit and cooldown parameters;
- confirm Manager/Supervisor permissions;
- communicate confirmed decisions to BA, UX and Developers.

---

## 13. Definition of Done

This task is complete when:
- [x] Requirements baseline reviewed.
- [x] Week 1 client decisions/outcomes incorporated.
- [x] Public User requirements refined.
- [x] Auditor requirements refined.
- [x] Manager/Supervisor requirements refined.
- [x] Wellbeing requirements defined.
- [x] Exposure controls defined.
- [x] Initial acceptance criteria written.
- [x] Assumptions clearly separated from confirmed requirements.
- [x] Refined artifact shared with UX, Developers and PM.

---

## 14. Sprint 1 BA Outcome

The refined requirements establish a shared baseline for the team.

**Core workflow:**  
Public User submission → Case creation → AI video/audio analysis → Structured outputs → Auditor review → Final human decision

**Wellbeing layer:**  
Exposure management → Cooldown → SOS → Right to decline → Manager notification/escalation

The solution remains human-in-the-loop, uses approved synthetic/staged content for university demonstration, and does not convert unresolved business decisions into unsupported implementation rules.

---

## 15. BA Status

**STATUS: REQUIREMENTS AND ACCEPTANCE CRITERIA REFINED — READY FOR PM / UX / DEVELOPERS REVIEW**

The document provides the refined requirements baseline, acceptance criteria, scope priorities, wellbeing requirements, exposure controls, assumptions, open questions and role-based handoffs for Sprint 1 Week 2.
