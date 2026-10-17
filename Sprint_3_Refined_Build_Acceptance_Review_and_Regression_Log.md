# Sprint 3 — Refined Build Acceptance Review & Regression Log

**Project:** IBM Responsible Content-Safety Infrastructure — Team 1  
**Role:** Business Analyst  
**Task:** [REQUIREMENTS] Validate Refined Build Against Acceptance Criteria & Log Regressions  
**Review date:** 17 October 2026  
**Status:** Validation record prepared; actual build results must be entered from evidence.

## Purpose and result labels

Validate the refined Sprint 3 build against agreed acceptance criteria and Week 1 regression traceability. Record observed results, evidence, regressions, owners and follow-up actions. Keep unresolved business decisions (TBCs) separate from confirmed defects.

- **Pass:** Evidence demonstrates that the criterion is met.
- **Partial:** Some behaviour is demonstrated, but part remains incomplete or unverified.
- **Fail:** Evidence shows a conflict with a confirmed requirement.
- **Not Tested:** No sufficient implementation/test evidence has been reviewed.
- **TBC / Decision Pending:** The expected business rule is unconfirmed; it is not automatically a defect.

Do not mark a criterion Pass without supporting evidence.

## Acceptance-criteria review matrix

| ID | Requirement / review area | What to verify | Result | Evidence / finding | Follow-up owner |
|---|---|---|---|---|---|
| AC-01 | Approved content submission | Submission accepts approved synthetic/staged content; real harmful content is not required. | Not Tested | Add build/test evidence. | Dev owner |
| AC-02 | Case creation and Case ID | Accepted submission creates a case and associated Case ID. | Not Tested | Add build/test evidence. | Dev owner |
| AC-03 | Case traceability and persistence | Case details and processing outputs persist and can be retrieved against the correct case. | Not Tested | Add persistence/retrieval evidence. | Dev owner |
| AC-04 | AI/STT processing | Processing path/states are visible and processing failures are handled appropriately. | Not Tested | Add test evidence. | Dev owner |
| AC-05 | Structured AI outputs | Confirmed core outputs—severity, summary and incident timestamps—are represented where produced by the approved flow. | Not Tested | Add output evidence. | Dev owner |
| AC-06 | Timestamp / segment behaviour | Returned timestamps or segments are associated with the correct case and displayed consistently. | Not Tested | Add sample-case evidence. | Dev owner |
| AC-07 | Auditor review | Auditor can review the processed case and AI-assisted results. | Not Tested | Add screen/flow evidence. | UX / Dev owner |
| AC-08 | Human final decision | Auditor's human decision is explicit and recorded; AI does not autonomously make the final decision. | Not Tested | Add decision-flow evidence. | UX / Dev owner |
| AC-09 | Auditor decline → Manager notification | Auditor decline triggers the confirmed Manager notification/escalation path. Exact reassignment rules and notification details remain TBC where unconfirmed. | Not Tested | Add event/notification evidence. | Dev owner / PM |
| AC-10 | Failure states | Relevant submission, storage and processing failures are handled and recorded. | Not Tested | Add negative-test evidence. | Dev owner |
| AC-11 | AI-assistive boundary | UI and implementation show AI as assistance, not the final decision-maker. | Not Tested | Add UI/flow evidence. | UX / Dev owner |
| AC-12 | Wellbeing-first direction | Design preserves the confirmed wellbeing/exposure-management direction without treating unconfirmed limits/cooldown values as fixed. | Not Tested | Add design/build evidence. | UX / PM |
| AC-13 | Regression review | Recheck submission, case traceability, Auditor review and human-decision behaviour after refinements. | Not Tested | Add regression-test references. | BA / Dev owner |
| AC-14 | TBC separation | Open business decisions are labelled TBC, not misreported as confirmed defects or requirements. | Not Tested | Link TBC register below. | BA / PM |
| AC-15 | UX / implementation consistency | Screens and behaviour match confirmed requirements; unapproved recommendations are not mandatory build requirements. | Not Tested | Add UX/build comparison evidence. | BA / UX |
| AC-16 | Role/access scope | Review access against approved scope without inventing unconfirmed permission rules. | Not Tested | Add evidence or retain unresolved rule as TBC. | Dev owner / PM |

## Regression and gap log

Add a row for each observed regression, confirmed defect, partial result or evidence gap. Record “no regressions found” only after relevant checks have actually been run.

| Ref | Requirement / AC | Observation | Classification | Priority | Evidence | Owner | Action / status |
|---|---|---|---|---|---|---|---|
| GAP-01 | AC-01–AC-16 | Actual implementation evidence/results have not yet been entered in this record. | Evidence gap — not a confirmed defect | Pending | Add test/build links | BA + relevant developer | Review tests and update matrix |
|  |  |  |  |  |  |  |  |

Classification:
- **Confirmed defect/regression:** Reproducible implementation conflicts with a confirmed requirement.
- **Evidence gap:** Sufficient evidence has not yet been supplied or reviewed.
- **TBC/business decision:** Expected behaviour is not confirmed; track with PM.
- **Enhancement/recommendation:** Proposed improvement that is not an approved requirement.

## Open TBC decisions to preserve

Keep these open until the PM/client confirms them, and record the decision source when updated:

- Case ID format: short human-readable ID or current system-generated identifier.
- Whether a Case description belongs in the approved Public User submission flow.
- Expected behaviour when AI returns no incident timestamps.
- Supported file formats and maximum upload size.
- Raw MVP role-based access/authentication scope and exact Manager permissions.
- Whether a Severity column should appear in the Auditor queue. UX clarified this is currently a **recommendation**, pending BA confirmation under Dashboard requirements **TBC-08**; it is not a confirmed build requirement.
- Final severity scale and mandatory AI outputs beyond confirmed core outputs.
- Exact human final-decision labels/options.
- Exact decline/reassignment workflow and notification content beyond the confirmed decline → Manager notification/escalation direction.
- Exposure limits, cooldown parameters and other unconfirmed wellbeing values.
- Confirmed retry/escalation rules and whether opening/skipping raw media needs separate tracking.
- Confirmed accessibility target, if still unresolved.

## Handoff and actions

1. **Developers:** Provide evidence links for each implemented criterion and relevant failure-state tests. Report reproducible defects with steps and affected case/build.
2. **UX:** Correct evidence-supported inconsistencies. Keep recommendations separate from confirmed requirements, including the Auditor queue Severity column pending TBC-08.
3. **PM:** Confirm outstanding business decisions and assign owners/dates for TBCs.
4. **BA:** Update results, regression/gap log and traceability after reviewing evidence. Recheck fixes before marking criteria Pass.

## Completion gate

Do not mark this validation fully complete until the latest integrated build has been reviewed; each applicable criterion has an honest result; each Pass/Fail/Partial result has evidence; gaps have owners/actions; TBCs are separate from confirmed defects; and findings are shared with PM, UX and relevant developers.

**Evidence URL:** Add the GitHub URL after committing this file to the team requirements repository.
