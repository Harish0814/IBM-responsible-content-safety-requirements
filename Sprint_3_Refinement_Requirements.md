# Sprint 3 — Refinement Requirements & Carry-Over Register

**Task:** [REQUIREMENTS] Convert Sprint 2 Gaps / TBCs into Refinement Requirements  
**Role:** Business Analyst | **Sprint:** Sprint 3

## 1. Purpose and status rules

Convert Sprint 2 validation findings and unresolved decisions into prioritised Sprint 3 refinement requirements. “Not independently verified” means implementation evidence was unavailable in the BA review record; it is not automatically a confirmed defect. TBC values must not be treated as approved business rules.

## 2. Prioritised refinement requirements

| ID | Requirement | Priority | Classification | Intended owner | Acceptance / evidence |
|---|---|---|---|---|---|
| SR3-01 | Validate approved synthetic/staged submission and unsupported-input handling. | P0 | Evidence gap | Developer + BA | Demonstrate valid staged submission and unsupported-input handling; record evidence. |
| SR3-02 | Verify unique Case ID creation and association with the case/media reference. | P0 | Evidence gap; display format TBC | Developer + BA | Show the Case ID and associated case record. Do not assume a short/public-facing format. |
| SR3-03 | Verify case persistence, retrieval and processing-status updates. | P0 | Evidence gap / technical clarification | Developer | Demonstrate create/retrieve and persisted status; record any actual defect with evidence. |
| SR3-04 | Verify media/COS storage or reference, case association and storage-failure handling. | P0 | Evidence gap; technical details partly TBC | Developer | Show the media reference associated with the case and a clear failure outcome; confirm bucket/path conventions with the technical owner. |
| SR3-05 | Verify STT processing, transcript availability and explicit failure state. | P0 | Evidence gap; configuration TBC | AI/STT owner | Demonstrate success and failure handling; do not invent configuration or thresholds. |
| SR3-06 | Verify structured watsonx.ai output associated with the correct case: severity, summary and relevant timestamps/segments where available. | P0 | Evidence gap; parameters partly TBC | AI owner + Developer | Provide sample output and evidence of case association; exact severity scale and accuracy threshold remain open. |
| SR3-07 | Verify media analysis and ensure failed analysis is not shown as successful. | P0 | Evidence gap | Developer / AI owner | Demonstrate success and failure paths with visible processing status. |
| SR3-08 | Verify Auditor access to processed results and recording of a human final decision. AI must remain assistive. | P0 | Evidence gap | Developer + UX + BA | Evidence shows the available AI results, Auditor review and recorded human decision; no autonomous AI finalisation. |
| SR3-09 | Verify Auditor decline triggers the confirmed Manager notification/escalation direction. | P0 | Confirmed requirement; evidence gap | Developer + PM | Demonstrate decline and associated notification/escalation evidence. Exact content and reassignment remain TBC. |
| SR3-10 | Validate submission, storage, STT, AI/media-analysis and workflow failure states. | P0 | Evidence gap | Developer + UX + BA | Each relevant failure is distinguishable from success and recorded in the validation matrix. |
| SR3-11 | Confirm severity scale, AI accuracy threshold and any mandatory AI outputs beyond severity, summary and available timestamps/segments. | P1 | Business decision / TBC | PM/client + BA | Record the decision and source; do not invent values or claim a threshold is met. |
| SR3-12 | Confirm final human decision labels/options and reassignment workflow after Auditor decline. | P1 | Business decision / TBC | PM/client + BA | Record approved options and reassignment rules. The Manager notification/escalation direction remains confirmed. |
| SR3-13 | Confirm public-facing Case ID format and whether Case description belongs in the submission flow. | P1 | Business decision / TBC | PM/client + BA + UX | Record both decisions; UX must not treat either as mandatory until confirmed. |
| SR3-14 | Confirm supported file formats, maximum upload size and behaviour when analysis returns no incident timestamps. | P1 | Business decision / TBC | PM/client + technical owner + BA | Record approved formats, limits and missing-timestamp behaviour; update tests after confirmation. |
| SR3-15 | Confirm Raw MVP role-based access/authentication scope and Manager permissions. | P1 | Business decision / TBC | PM/client + technical owner + BA | Document approved access/permission rules; do not infer full RBAC from a prototype. |
| SR3-16 | Preserve wellbeing-first and exposure-management direction; confirm exposure limits, cooldown, SOS behaviour, notification content and Manager controls before fixing detailed behaviour. | P1 | Direction confirmed; parameters TBC | PM/client + BA + UX + Developer | Keep direction visible and record values only after confirmation. Do not label unresolved values as defects. |
| SR3-17 | Reconcile the Auditor queue Severity indicator with the approved UX requirements before treating its absence as a defect. | P1 | UX/BA clarification | BA + UX (+ PM if needed) | Record whether queue Severity is a confirmed requirement or UX recommendation. |
| SR3-18 | Maintain traceability from requirement and AC to implementation evidence, result, gap owner and next action. | P0 | BA evidence/process | BA + relevant owners | Label each reviewed criterion Pass, Fail, Partial or Not Tested, with evidence and owner; separate TBC decisions from defects. |

**Priority meaning:** P0 = needed to establish/validate the Raw MVP workflow or meet a confirmed core requirement. P1 = confirmation/refinement for safe, accurate scope and Sprint 3 handoff. Priority does not mean work is already implemented or tested.

## 3. Carry-over classification

### Confirmed requirements that still need implementation evidence
- Approved synthetic/staged content only.
- Accepted submission creates a case and Case ID.
- AI/STT provides structured assistance.
- Expected core outputs include severity, summary and relevant timestamps/segments where available.
- Auditor reviews results and makes the final human decision.
- Auditor decline triggers the confirmed Manager notification/escalation direction.
- Relevant processing and failure states are represented.
- Wellbeing is a core consideration; exposure management remains part of the requirements/design direction.

### Not independently verified — not automatically defects
- Submission and unsupported-input behaviour.
- Case ID creation/association; database persistence/retrieval; media/COS storage.
- STT, structured AI output, media analysis and timestamps/segments.
- Auditor review, recorded human decision and AI assistive-only behaviour.
- Decline-to-Manager notification/escalation, failure states and end-to-end integration.

The implementation owner must provide evidence. If evidence shows incorrect behaviour against a confirmed criterion, record a defect with steps, expected result, actual result and evidence.

### Open/TBC decisions
- Exact severity scale and AI accuracy threshold.
- Final human decision labels/options.
- Reassignment rules after decline and exact notification content.
- Exposure limits, cooldown values, SOS details and exact Manager permissions.
- Public-facing Case ID format and whether Case description is in scope.
- Supported file formats, maximum upload size and behaviour when timestamps are absent.
- Role-based access/authentication scope.
- COS bucket/path/naming convention, STT configuration and timestamp/segment format/granularity.

These remain open until confirmed by the appropriate PM/client or technical owner. Do not call them defects simply because a value has not been selected.

## 4. Handoff

- **Developers / technical owners:** Supply reproducible evidence for P0 requirements; distinguish actual defects from missing evidence; do not hard-code TBC values.
- **UX:** Reflect confirmed submission, processing/error, Auditor review, human decision and decline/escalation behaviour. Annotate unresolved decisions as TBC.
- **PM/client:** Confirm the open decisions above and prioritise accepted carry-over items.
- **BA:** Maintain requirements baseline, traceability, decision log and evidence links; update status when evidence or an approved decision changes.

## 5. Definition of done

- [ ] Sprint 2 gaps mapped to a requirement or open decision.
- [ ] Confirmed defects distinguished from “Not independently verified” evidence gaps.
- [ ] Priorities and intended owners visible.
- [ ] Case traceability retained.
- [ ] AI remains assistive and the Auditor makes the final decision.
- [ ] Auditor decline → Manager notification/escalation direction preserved.
- [ ] Wellbeing/exposure direction retained without inventing limits or cooldown values.
- [ ] No TBC value represented as confirmed.
- [ ] Handoff shared with PM, UX and Developers.
- [ ] Evidence URL added to Planner and Master Document.

## 6. Status

**Prepared:** Sprint 3 refinement requirements and carry-over register. This document prioritises follow-up work and decisions; it does not claim the listed implementation items have been completed or tested.
