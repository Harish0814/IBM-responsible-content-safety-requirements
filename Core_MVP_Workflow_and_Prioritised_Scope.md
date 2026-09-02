# [REQUIREMENTS] Finalise Core MVP Workflow & Prioritised Scope

**IBM × RMIT Capstone — Responsible Content-Safety Infrastructure**

**Task:** Finalise Core MVP Workflow & Prioritised Scope  
**Project:** Responsible Content-Safety Infrastructure  
**Client:** IBM  
**Team:** Team 1  
**Role:** BA — Shriharish Muthumalai Arunkumar  
**Sprint:** Sprint 1 — Design & Bootstrap  
**Week:** Sprint 1 Week 2

---

## 1. Purpose

This document finalises the Core MVP workflow and prioritised scope for Sprint 2 using the existing approved requirements baseline, client clarifications and Sprint 1 discovery work.

The Core MVP is the **AI-assisted content-review workflow**.

The purpose of the MVP is to demonstrate the project's core value proposition:

> Use AI-assisted video and audio analysis to reduce unnecessary direct exposure of content auditors to harmful material while still allowing auditors to make the final review decision.

The MVP will use approved synthetic/staged content only.

---

## 2. Confirmed Core MVP Workflow

The confirmed end-to-end Core MVP workflow is:

**Public User submits content**  
↓  
**Case is created and Case ID generated**  
↓  
**AI analyses video/audio**  
↓  
**Structured AI outputs are produced**  
↓  
**Auditor reviews the AI-assisted results**  
↓  
**Auditor makes the final human review decision**

This is the single main workflow that Sprint 2 must demonstrate.

---

## 3. MVP Start and End Points

### Start Point

The Core MVP starts when:

**A Public User submits approved synthetic/staged content to the platform.**

### End Point

The Core MVP ends when:

**The Auditor reviews the AI-generated outputs and makes the final human review decision.**

Therefore:

**Content submission → Case creation → AI analysis → Structured outputs → Auditor review → Final human decision**

---

## 4. Main Actors

### Public User

**Goal:** Submit content for review.

Core interaction:
- Submit approved synthetic/staged video or audio content.
- Receive a Case ID.

### Auditor — Primary User

**Goal:** Review cases using AI-assisted analysis while reducing unnecessary direct exposure to potentially harmful content.

Core interaction:
- Access the relevant case.
- Review AI-generated severity information.
- Review the summary.
- Review incident timestamps.
- Review other available structured outputs.
- Make the final review decision.

**Important:** The Auditor remains responsible for the final decision. AI is assistive and does not make the final decision autonomously.

### Manager / Supervisor — Secondary User

**Goal:** Monitor cases, Auditor workload and Auditor wellbeing.

Manager/Supervisor functionality is part of the broader project scope but is **not part of the confirmed Sprint 2 Core MVP workflow**. It is primarily identified as a Sprint 3 refinement area.

---

## 5. Core MVP Workflow Detail

### Step 1 — Content Submission

A Public User submits approved synthetic/staged video or audio content to the platform.

### Step 2 — Case Creation

The system creates a case for the submitted content and generates a Case ID.

### Step 3 — AI Video/Audio Analysis

The submitted content is processed by the AI analysis workflow.

The AI analyses the approved test content and produces structured information to support the human review process.

### Step 4 — Structured AI Outputs

The Core MVP should provide:

- Severity information
- Summary
- Incident timestamps

Additional outputs such as tags and transcription may be provided where applicable, subject to confirmation and technical feasibility.

### Step 5 — Auditor Review

The resulting case and AI-generated information are presented to the Auditor.

The Auditor reviews the AI-assisted information rather than relying on fully autonomous AI decision-making.

### Step 6 — Final Human Review Decision

The Auditor makes the final review decision.

The AI assists the Auditor but does not make the final autonomous decision.

---

## 6. Core MVP Priority Classification

To provide a clear implementation boundary for UX and Developers, functionality is prioritised as follows.

### P0 — Core MVP / Required for Sprint 2

The following functionality is required for the Core MVP:

- Approved synthetic/staged content submission
- Case creation
- Case ID generation
- AI-assisted video/audio analysis
- Severity information
- Summary
- Incident timestamps
- Presentation of structured AI outputs to the Auditor
- Auditor review
- Final human review decision
- End-to-end workflow demonstration
- Demonstration of reduced unnecessary direct exposure to potentially harmful content

These items define the minimum end-to-end workflow that Sprint 2 must demonstrate.

### P1 — Conditional / Lower Priority

The following may be included where confirmed and technically feasible:

- Tags
- Transcription
- Other structured AI outputs that directly support Auditor review

P1 functionality must not displace or delay the P0 Core MVP workflow.

### P2 — Secondary / Future Refinement

The following are secondary or future refinement areas:

- Manager/Supervisor oversight
- Auditor wellbeing controls
- Cooldown
- SOS
- Advanced exposure-management controls
- Full role-based access implementation
- Production-level deployment refinement
- Other non-essential enterprise functionality

These capabilities are primarily identified as Sprint 3 refinement areas.

---

## 7. Decline / Reassignment Priority

The exact Auditor decision options and case assignment/reassignment rules are **not yet confirmed by the client**.

Therefore:

- Decline/reassignment is **not treated as a confirmed P0 Core MVP requirement**.
- The confirmed Core MVP priority remains the **Auditor review → final human decision** path.
- The exact behaviour for decline, reassignment and case availability remains a documented open question pending client confirmation.
- UX should not present an unconfirmed decline/reassignment workflow as mandatory Core MVP functionality.
- Developers should not implement an unapproved reassignment rule without BA/PM confirmation.
- If client confirmation makes decline/reassignment necessary for the Core MVP, the requirements and acceptance criteria will be updated accordingly.

This approach avoids inventing business rules that have not yet been confirmed.

---

## 8. Core MVP Acceptance Criteria

The existing acceptance criteria remain the basis for validating the Core MVP.

### AC-01 — Content Submission

A Public User can submit approved synthetic/staged content.

### AC-02 — Case Creation

A Case ID is created for the submitted content.

### AC-03 — AI Processing

The submitted approved test content can be processed by the AI analysis workflow.

### AC-04 — Severity Information

The AI returns severity information for the submitted content.

### AC-05 — Summary

The AI returns a summary of the analysed content.

### AC-06 — Incident Timestamps

The AI provides incident timestamps identifying relevant points in the content.

### AC-07 — Auditor Review

The AI-generated outputs can be presented to the Auditor for review.

### AC-08 — Final Human Decision

The Auditor can review the AI-assisted information and make the final review decision.

### AC-09 — End-to-End Workflow

The complete workflow operates end-to-end:

**Submission → Case Creation → AI Analysis → Structured Outputs → Auditor Review → Final Decision**

### AC-10 — Core Value

The workflow demonstrates how AI can assist the Auditor while reducing unnecessary direct exposure to potentially harmful content.

### AC-11 — Synthetic/Staged Content Only

The MVP operates using approved synthetic/staged content only.

### AC-12 — No Autonomous Final Decision

The AI does not make the final review decision autonomously.

---

## 9. Business Assumptions

The following assumptions remain applicable to the Core MVP:

- Only approved synthetic/staged footage will be used.
- The project depends on access to IBM TechZone/Sandbox and the provided IBM services.
- Sprint 2 will contain the first working product features.
- The Core MVP is intended to prove the core workflow rather than represent a fully production-ready platform.
- The AI assists the Auditor rather than replacing the Auditor's final decision.
- The architecture should support future scalability.
- Production-scale load testing is outside the student implementation.
- Real agency data will not be used.
- Real abusive content is outside the agreed scope.
- Fully autonomous AI decision-making is outside the agreed scope.
- Severity scale, accuracy threshold and some workflow details still require client confirmation.

---

## 10. Unresolved Workflow Questions

The following remain open and must not be converted into unconfirmed business rules.

### Q1 — Severity Scale

What severity scale should the AI use for content classification?

**Status:** Pending client confirmation.

### Q2 — Accuracy Threshold

What minimum AI classification accuracy threshold should be used for the MVP?

**Status:** Pending client confirmation.

### Q3 — Final Review Decision

What exact decision options should be available to the Auditor after reviewing the AI outputs?

**Status:** Pending client confirmation.

### Q4 — Case Assignment / Availability

How should cases be assigned to or made available to Auditors?

**Status:** Pending client confirmation.

### Q5 — Required AI Outputs

Beyond severity information, summaries and incident timestamps, which additional AI outputs are mandatory for the Core MVP?

Potential outputs include:

- Tags
- Transcription

**Status:** Pending confirmation.

### Q6 — Workflow Rules

Are there any additional business rules governing the movement of a case from AI analysis to Auditor review and final decision?

**Status:** Pending client confirmation.

---

## 11. Confirmed Scope Boundary

### In Scope — Sprint 2 Core MVP

- Approved synthetic/staged content submission
- Case creation
- Case ID
- AI-assisted video/audio analysis
- Severity information
- Summary
- Incident timestamps
- Presentation of AI outputs to Auditor
- Auditor review
- Final human review decision
- End-to-end workflow
- Demonstration of reduced unnecessary direct exposure

### Out of Scope — Core MVP

- Real abusive content
- Real agency data
- Fully autonomous AI decision-making
- Production-scale load testing
- Auditor wellbeing controls such as cooldown and SOS
- Advanced exposure-management controls
- Manager oversight
- Full role-based access implementation
- Production-level deployment refinement
- Other non-essential enterprise features beyond the agreed MVP

---

## 12. Handoff to PM

The PM should:

- Review the final Core MVP workflow and prioritised scope.
- Review the unresolved clarification questions.
- Coordinate future client clarification where required.
- Record confirmed client decisions.
- Communicate confirmed decisions to BA, UX and Developers.
- Track blockers resulting from unresolved requirements.

No unconfirmed business rule should be treated as final without the appropriate PM/client confirmation.

---

## 13. Handoff to UX

UX should use this Core MVP workflow and prioritised scope to constrain the Sprint 1 digital prototype.

UX should focus on:

- Public User submission flow
- Case creation / Case ID experience
- Auditor case-review experience
- Presentation of AI-generated outputs
- Final Auditor review decision

The Auditor remains the primary persona, with Public User and Manager/Supervisor as supporting personas.

UX should not introduce functionality outside the approved Core MVP scope without raising it with the BA/PM.

---

## 14. Handoff to Developers

Developers should use the following as the Sprint 2 implementation boundary:

**Public User submission**  
→ **Case ID creation**  
→ **AI video/audio analysis**  
→ **Structured AI outputs**  
→ **Auditor review**  
→ **Final human review decision**

Developers should:

- Implement the confirmed workflow end-to-end.
- Use approved synthetic/staged content.
- Produce the agreed Core MVP AI outputs.
- Present the outputs to the Auditor.
- Preserve human final decision-making.
- Raise unresolved business rules with the BA/PM rather than making unapproved assumptions.

---

## 15. Definition of Done

This task is complete when:

- One Core MVP workflow is defined.
- Core workflow start and end points are clear.
- Main actors are identified.
- Submission, AI processing, Auditor review and final human decision are defined.
- Core and secondary functionality are clearly separated.
- Decline/reassignment priority is documented without inventing unconfirmed business rules.
- Acceptance criteria are linked to the Core MVP workflow where applicable.
- Business assumptions are documented.
- Unresolved workflow questions are recorded.
- The Core MVP scope is shared with PM, UX and Developers.
- Handoff information is provided for the next roles.
- Accessible evidence is provided.

---

## 16. MVP Success Definition

The Core MVP succeeds when the team can demonstrate:

**A Public User submits approved synthetic/staged content → the system creates a Case ID → AI analyses the video/audio → the system produces severity information, a summary and incident timestamps → the Auditor reviews the AI-assisted results → the Auditor makes the final human review decision.**

This demonstrates the project's core value proposition of using AI to assist content auditors while reducing unnecessary direct exposure to harmful material.

---

## 17. Final Decision Status

| Item | Status |
|---|---|
| Core MVP | Defined |
| Workflow start | Public User submits approved content |
| Workflow end | Auditor makes final human review decision |
| Main actors | Public User, Auditor, Manager/Supervisor |
| Primary user | Auditor |
| Submission step | Defined |
| AI processing step | Defined |
| Auditor review | Defined |
| Human final decision | Defined |
| Core vs secondary scope | Separated |
| Decline/reassignment | Pending confirmation; not treated as confirmed P0 |
| Acceptance criteria | Defined |
| Business assumptions | Documented |
| Open questions | Documented |
| UX handoff | Ready |
| Developer handoff | Ready |
| PM handoff | Ready |
| Final client clarification | Pending where required |

---

## 18. BA Status

**STATUS: CORE MVP WORKFLOW AND PRIORITISED SCOPE FINALISED — READY FOR PM / UX / DEVELOPERS REVIEW**

The Core MVP remains aligned with the existing approved requirements baseline.

The confirmed workflow, scope priorities, acceptance criteria, assumptions and unresolved questions have been consolidated for Sprint 1 Week 2.

No unconfirmed client decision has been converted into a mandatory requirement.

The document provides UX and Developers with a clear implementation boundary for future Sprint 2 planning.
