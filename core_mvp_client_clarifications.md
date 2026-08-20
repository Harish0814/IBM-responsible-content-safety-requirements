[REQUIREMENTS] Core MVP & Client Clarifications

IBM × RMIT Capstone — Responsible Content-Safety Infrastructure

Task: [REQUIREMENTS] Define Core MVP & Client Clarifications
Project: Responsible Content-Safety Infrastructure
Client: IBM
Team: Team 1
Role: BA — Shriharish Muthumalai Arunkumar
Sprint: Sprint 1 — Design & Bootstrap
Status: Ready for PM / UX / Developers Review
Client Agreement: 13 August 2026

1. Purpose

This document defines the Core MVP for Sprint 2 based on the client-approved Project Proposal & Sprint 1 Plan.

The approved Core MVP is the AI-assisted content-review workflow.

The purpose of this MVP is to demonstrate the project's core value proposition:

Use AI-assisted video and audio analysis to reduce unnecessary direct exposure of content auditors to harmful material while still allowing auditors to make the final review decision.

The MVP will use approved synthetic/staged content only.

Sprint 2 is intended to demonstrate the core idea working end-to-end, even if the implementation is initially rough and not fully polished.

2. Core MVP Definition

Core MVP: AI-Assisted Content Review

The Core MVP workflow is:

Public User submits content
↓
Case is created and Case ID generated
↓
AI analyses video/audio
↓
Structured AI outputs are produced
↓
Auditor reviews the AI-assisted results
↓
Auditor makes the final review decision

This is the single main feature that Sprint 2 must prove.

3. Core MVP Workflow

Step 1 — Content Submission

A Public User submits approved synthetic/staged video or audio content to the platform.

Step 2 — Case Creation

The system creates a case for the submitted content and provides a Case ID.

Step 3 — AI Video/Audio Analysis

The submitted content is processed by the AI analysis workflow.

The AI analyses the approved test content and produces structured information to support the human review process.

Step 4 — Structured AI Outputs

The AI should provide the core outputs identified in the approved proposal, including:

Severity information

Summary

Incident timestamps

Other outputs such as tags and transcription may also be provided where applicable.

Step 5 — Auditor Review

The resulting case and AI-generated information are presented to the Auditor, who is the primary user.

The Auditor reviews the AI-assisted information rather than relying on fully autonomous AI decision-making.

Step 6 — Final Review Decision

The Auditor makes the final review decision.

The AI assists the Auditor but does not make the final autonomous decision.

4. Core MVP Start and End Points

Start Point

The Core MVP starts when:

A Public User submits approved synthetic/staged content to the platform.

End Point

The Core MVP ends when:

The Auditor reviews the AI-generated outputs and makes the final review decision.

Therefore, the complete Sprint 2 workflow is:

Content submission → Case creation → AI analysis → Structured outputs → Auditor review → Final decision

5. Core Value Demonstrated

The MVP must demonstrate that AI-assisted analysis can:

Process approved test content.

Produce useful structured information.

Provide severity information, summaries and incident timestamps.

Support the Auditor's review.

Reduce unnecessary direct exposure of the Auditor to potentially distressing content.

Still allow the Auditor to retain the final review decision.

6. Main Actors

6.1 Public User

The Public User submits content to the platform.

Goal: Submit content for review.

Core interaction:

Submit approved synthetic/staged content.

Receive a Case ID.

6.2 Auditor — Primary User

The Auditor is the primary user of the platform.

Goal: Review cases using AI-assisted analysis while reducing unnecessary exposure to harmful content.

Core interaction:

Access the relevant case.

Review AI-generated severity information.

Review the summary.

Review incident timestamps.

Review other available structured outputs.

Make the final review decision.

The Auditor remains responsible for the final decision.

6.3 Manager / Supervisor

Managers and supervisors are secondary users.

Goal: Monitor:

Cases

Auditor workload

Auditor wellbeing

Manager oversight is part of the broader project scope and Sprint 3 refinement, rather than the main Sprint 2 Core MVP workflow.

7. Initial Acceptance Criteria

The Core MVP will be considered successful when the following can be demonstrated:

AC-01 — Content Submission: A Public User can submit approved synthetic/staged content.

AC-02 — Case Creation: A Case ID is created for the submitted content.

AC-03 — AI Processing: The submitted approved test content can be processed by the AI analysis workflow.

AC-04 — Severity Information: The AI returns severity information for the submitted content.

AC-05 — Summary: The AI returns a summary of the analysed content.

AC-06 — Incident Timestamps: The AI provides incident timestamps identifying relevant points in the content.

AC-07 — Auditor Review: The AI-generated outputs can be presented to the Auditor for review.

AC-08 — Final Human Decision: The Auditor can review the AI-assisted information and make the final review decision.

AC-09 — End-to-End Workflow: The complete workflow operates end-to-end: Submission → Case Creation → AI Analysis → Structured Outputs → Auditor Review → Final Decision.

AC-10 — Core Value: The workflow demonstrates how AI can assist the Auditor while reducing unnecessary direct exposure to potentially harmful content.

AC-11 — Synthetic/Staged Content Only: The MVP operates using approved synthetic/staged content only.

AC-12 — No Autonomous Final Decision: The AI does not make the final review decision autonomously.

8. Business Assumptions

The following assumptions are based on the client-approved proposal:

Only approved synthetic/staged footage will be used.

The project depends on access to IBM TechZone/Sandbox and the provided IBM services.

Sprint 2 will contain the first working product features.

The Core MVP is intended to prove the core workflow rather than represent a fully production-ready platform.

The AI assists the Auditor rather than replacing the Auditor's final decision.

The architecture should support future scalability.

Production-scale load testing is outside the student implementation.

Real agency data will not be used.

Real abusive content is outside the agreed scope.

Fully autonomous AI decision-making is outside the agreed scope.

Severity scale, accuracy threshold and some workflow details still require client confirmation.

9. Unresolved Workflow Questions

The client-approved proposal explicitly identifies severity scale, accuracy threshold and some workflow details as requiring further confirmation.

Q1 — Severity Scale

What severity scale should the AI use for content classification?

Status: Pending client confirmation.

Q2 — Accuracy Threshold

What minimum AI classification accuracy threshold should be used for the MVP?

Status: Pending client confirmation.

Q3 — Final Review Decision

What exact decision options should be available to the Auditor after reviewing the AI outputs?

Status: Pending client confirmation.

Q4 — Case Assignment / Availability

How should cases be assigned to or made available to Auditors?

Status: Pending client confirmation.

Q5 — Required AI Outputs

Beyond severity information, summaries and incident timestamps, which additional AI outputs are mandatory for the Core MVP?

Potential outputs identified in the proposal include:

Tags

Transcription

Status: Pending confirmation.

Q6 — Workflow Rules

Are there any additional business rules governing the movement of a case from AI analysis to Auditor review and final decision?

Status: Pending client confirmation.

10. Client Clarification Status

The approved proposal does not provide final answers for:

Severity scale

AI accuracy threshold

Some workflow details

Therefore, the BA will record these as open questions rather than inventing business rules.

Current status

Clarifications required: Yes

Questions documented: Yes

Questions communicated to PM: Yes

Client meeting agenda: Already finalised

PM decision: PM has confirmed that the existing client meeting does not need to be amended to add these questions.

The questions remain documented so that future client clarification can be recorded and incorporated into the requirements.

11. Sprint Allocation

Sprint 1 — Design & Bootstrap

Sprint 1 focuses on:

Requirements

System architecture

User flows

Digital prototypes

IBM cloud environment

Storage

Required services

There are no working product features in Sprint 1.

Sprint 2 — Raw/Core MVP

Sprint 2 implements the single end-to-end AI-assisted content-review workflow:

Content submission
→ Case creation
→ AI video/audio analysis
→ Structured outputs
→ Auditor review
→ Final review decision

The purpose is to demonstrate the project's core value proposition.

Sprint 3 — Refine MVP

Sprint 3 focuses on refining and hardening the MVP.

The approved proposal identifies:

Auditor wellbeing controls

Exposure management

Cooldown

SOS

Role-based access

Manager oversight

Improved usability

AI validation

Deployment refinement

as Sprint 3 refinement areas.

12. MVP Scope

In Scope for Sprint 2 Core MVP

Approved synthetic/staged content submission

Case creation

Case ID

AI-assisted video/audio analysis

Severity information

Summary

Incident timestamps

Presentation of AI outputs to Auditor

Auditor review

Final human review decision

End-to-end workflow

Demonstration of reduced unnecessary direct exposure

13. Out of Scope for the Core MVP

The following are not part of the Sprint 2 Core MVP:

Real abusive content

Real agency data

Fully autonomous AI decision-making

Production-scale load testing

Auditor wellbeing controls such as cooldown and SOS

Advanced exposure-management controls

Manager oversight

Full role-based access implementation

Production-level deployment refinement

Other non-essential enterprise features beyond the agreed MVP

These later/refinement capabilities are addressed primarily through Sprint 3.

14. Handoff to PM

The PM should:

Review the Core MVP workflow.

Review the unresolved clarification questions.

Coordinate future client clarification where required.

Record confirmed client decisions.

Communicate confirmed decisions to BA, UX and Developers.

Track any blockers resulting from unresolved requirements.

The client meeting has already been finalised, so the existing meeting does not need to be changed.

15. Handoff to UX

UX should use the approved Core MVP and the confirmed project actors to create the relevant user flows and prototypes.

UX should focus on:

Public User submission flow

Case creation / Case ID experience

Auditor case-review experience

Presentation of AI-generated outputs

Final Auditor review decision

The Auditor should remain the primary persona, with the Public User and Manager as supporting personas.

UX should not introduce functionality that is outside the approved MVP scope without raising it with the BA/PM.

16. Handoff to Developers

Developers should use the following workflow as the Sprint 2 implementation boundary:

Public User submission
→ Case ID creation
→ AI video/audio analysis
→ Structured AI outputs
→ Auditor review
→ Final review decision

Developers should:

Implement the workflow end-to-end.

Use approved synthetic/staged content.

Produce the agreed AI outputs.

Present the outputs to the Auditor.

Preserve human final decision-making.

Raise unresolved business rules with the BA/PM rather than making unapproved assumptions.

17. Definition of Done

This Task 4 is complete when:

One candidate Core MVP workflow is defined.

Core workflow start and end points are clear.

Main actors are identified.

Initial acceptance criteria are drafted.

Business assumptions are documented.

Unresolved workflow questions are recorded.

Client clarification questions are shared with the PM.

Core MVP definition is shared with UX and Developers.

18. MVP Success Definition

The Core MVP succeeds when the team can demonstrate:

A Public User submits approved synthetic/staged content → the system creates a Case ID → AI analyses the video/audio → the system produces severity information, a summary and incident timestamps → the Auditor reviews the AI-assisted results → the Auditor makes the final review decision.

This demonstrates the project's core value proposition of using AI to assist content auditors while reducing unnecessary direct exposure to harmful material.

19. Decision Status

Item

Status

Core MVP

Defined

Workflow start

Public User submits approved content

Workflow end

Auditor makes final review decision

Main actors

Public User, Auditor, Manager/Supervisor

Primary user

Auditor

Acceptance criteria

Drafted

Business assumptions

Documented

Open questions

Documented

Client clarification questions

Shared with PM

Client meeting

Already finalised

PM confirmation

Questions can remain documented without changing meeting

UX handoff

Ready

Developer handoff

Ready

Final clarification

Pending where required

20. BA Status

STATUS: CORE MVP DEFINED — READY FOR PM / UX / DEVELOPERS REVIEW

The Core MVP is aligned with the client-approved Project Proposal & Sprint 1 Plan. 

All currently known assumptions, acceptance criteria and unresolved client questions have been documented without inventing decisions that have not yet been confirmed. 

