# Sprint 3 — Refined Build Acceptance Review & Regression Log

**Project:** IBM Responsible Content-Safety Infrastructure — Team 1  
**Role:** Business Analyst  
**Task:** [REQUIREMENTS] Validate Refined Build Against Acceptance Criteria & Log Regressions  
**Review date:** 25 October 2026  
**Review basis:** Available BA acceptance documents, Dev1 investigation/stabilisation notes, and Dev2 Sprint 3 AI-hardening evidence  
**Status:** **Ready for final regression — partial acceptance with open risks; final sign-off pending.**

> **Important scope note:** This is a document/evidence review, not an independent retest of the latest integrated build. Results below reflect the available written evidence and must be reconfirmed against the current build. The two UX `.docx` handoff documents have not yet been reviewed in full, so UX-specific conclusions remain provisional.

## Purpose and result labels

Validate the refined Sprint 3 build against agreed acceptance criteria and regression traceability. Record observed results, evidence, regressions, owners and follow-up actions. Keep unresolved business decisions (TBCs) separate from confirmed defects.

- **Pass:** Evidence demonstrates that the criterion is met in the relevant integrated build.
- **Partial:** Some behaviour is evidenced, but part remains incomplete, inconsistent or unverified.
- **Fail:** Evidence shows a reproducible conflict with a confirmed requirement.
- **Not Tested:** No sufficient implementation/test evidence has been reviewed.
- **TBC / Decision Pending:** The expected business rule is unconfirmed; it is not automatically a defect.

Do not mark a criterion Pass without supporting evidence. A component-level test or developer note is not, by itself, proof that the full integrated workflow passes.

## Evidence reviewed

### Business Analyst acceptance documents

- [Sprint 3 — Refined Build Acceptance Review & Regression Log](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Sprint_3_Refined_Build_Acceptance_Review_and_Regression_Log.md)
- [Final Acceptance Scenarios — Auth, Wellbeing & Deployment](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Final_Acceptance_Scenarios_Auth_Wellbeing_Deployment.md)

The acceptance scenarios define the tests to execute; their existence does **not** mean they have passed. The existing acceptance evidence register was marked `Not Tested`, so this review keeps final end-to-end sign-off pending.

### Developer evidence

- [Dev1 investigation repository](https://github.com/GitIsFried/IBM-SPRINT-1-Developer-Investigation)
- [Dev2 Sprint 3 AI-hardening branch](https://github.com/KumKaiLek/capstone-dev2-sprint2/tree/sprint3-ai-hardening)
- [Dev2 refinement log](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REFINEMENT_LOG.md)
- [Dev2 error-handling report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/ERROR_HANDLING.md)
- [Dev2 repeatability report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REPEATABILITY_REPORT.md)
- [Dev2 Sprint 3 handoff](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/HANDOFF_SPRINT3.md)

### UX evidence pending full review

- [Authentication, 2FA and reCAPTCHA UX review](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Authentication_2FA_reCAPTCHA_UX_Review_and_Dev1_Refinement_Handoff_HarneetKaur.docx)
- [Auditor/Manager UX review and Week 3 handoff](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Refined_Auditor_Manager_UX_Review_Usability_Gap_Register_and_Week3_Handoff_HarneetKaur.docx)

The UX documents are listed for traceability but have not been reviewed in full for this version. Upload them or provide readable text before treating UX-specific findings as final.

## Acceptance-criteria review matrix

| ID | Requirement / review area | What to verify | Current result | Evidence-based finding / limitation | Follow-up owner |
|---|---|---|---|---|---|
| AC-01 | Approved content submission | Submission accepts approved synthetic/staged content; real harmful content is not required. | Partial | Dev1 stabilisation notes describe submission testing and a video validation issue/fix. Reconfirm against the latest integrated build and approved file rules. | Dev1 / integration owner |
| AC-02 | Case creation and Case ID | Accepted submission creates a case and associated Case ID. | Partial | Dev1 documents case creation and persistence. Run a fresh integrated-build test and attach a case ID plus UI/API evidence. | Dev1 |
| AC-03 | Case traceability and persistence | Case details and processing outputs persist and can be retrieved against the correct case. | Partial | Dev1 documents case persistence/retrieval. Dev2 reports matching Case IDs across `case.json`, `transcript.json` and `analysis.json` in 35 repeatability runs. This does not prove the full UI-to-database workflow. | Dev1 + Dev2 |
| AC-04 | AI/STT processing and failure handling | Processing states are visible and processing failures are handled appropriately. | Partial | Dev2 reports live timeout evidence and simulated error-path tests. Latest integrated workflow and UI error presentation still require regression. | Dev2 + integration owner |
| AC-05 | Structured AI outputs | Confirmed core outputs—severity, summary and incident timestamps—are represented where produced by the approved flow. | Partial | Repeatability evidence reports stable outputs, but V2/CASE-102 can omit expected `harassment`, and unsupported details remain in some summaries. Stable output is not necessarily correct output. | Dev2 |
| AC-06 | Timestamp / segment behaviour | Returned timestamps or segments are associated with the correct case and displayed consistently. | Partial | Dev2 reports malformed STT timing handling was improved to return null times with a reason instead of crashing. V3 may return a whole-clip timestamp because STT returns one segment; confirm expected behaviour and UI handling. | Dev2 + BA/PM for expected rule |
| AC-07 | Auditor review and case assignment | Auditor can access the appropriate case(s), including only cases assigned to that Auditor under the approved workflow. | Partial | Dev1 notes say an Auditor could receive cases in IBM COS but could not retrieve specific Manager-assigned cases because the Manager workflow MVP was not implemented in that stabilisation record. Verify current implementation before closing. | Dev1 + Manager workflow owner |
| AC-08 | Human final decision | Auditor makes an explicit human decision and that decision is persisted; AI does not autonomously make the final decision. | Partial | Dev1 stabilisation notes identify Auditor editing and final human-decision persistence as incomplete at that time. Current integrated-build evidence is required to confirm whether this is now implemented. | Dev1 + UX |
| AC-09 | Auditor decline → Manager notification | Auditor decline triggers the confirmed Manager notification/escalation path. | Partial | The acceptance plan identifies this scenario, but Dev1 notes indicate the Manager workflow MVP was not implemented at the time of stabilisation. Verify the live path and record evidence. Exact reassignment and notification details remain TBC where unconfirmed. | Dev1 + PM |
| AC-10 | Failure states | Submission, storage and processing failures are handled and recorded without fabricated AI results. | Partial | Dev2 documents structured error handling and live timeout evidence plus simulated failure tests. Verify the latest build’s user-visible errors, logs and recovery behaviour. | Dev2 + Dev1 |
| AC-11 | AI-assistive boundary | UI and implementation show AI as assistance, not the final decision-maker. | Partial | Dev2 documents AI output handling; Dev1 notes final human-decision persistence was incomplete at the time of its report. Verify that the current Auditor flow requires and records a human decision. | Dev1 + Dev2 + UX |
| AC-12 | Wellbeing-first direction | Design preserves the confirmed wellbeing/exposure-management direction without treating unconfirmed limits/cooldown values as fixed. | Not Tested | Final integrated UX/build evidence has not been reviewed in this version. Exact exposure limits, cooldown and SOS behaviour remain subject to confirmed scope. | UX + PM + BA |
| AC-13 | Regression review | Recheck submission, case traceability, Auditor review and human-decision behaviour after refinements. | Partial | Dev2 reports 7 cases × 5 runs (35 runs) with exact-equality checks and Case ID linkage. These component/pipeline checks do not replace full end-to-end regression. | BA + Dev1 + Dev2 |
| AC-14 | TBC separation | Open business decisions are labelled TBC, not misreported as confirmed defects or requirements. | Partial | TBCs are listed below. PM/client decisions and decision sources still need to be recorded. | BA + PM |
| AC-15 | UX / implementation consistency | Screens and behaviour match confirmed requirements; unapproved recommendations are not mandatory build requirements. | Not Tested | UX `.docx` evidence has not been reviewed in full for this version. Case Preview, Analysis & Decision and role/state coverage need evidence review. | UX + BA |
| AC-16 | Role/access scope and console integration | Access matches approved roles and Manager/Auditor consoles use the intended case assignment and role permissions. | Partial | Dev1 notes document role/access and case workflow work, but also identify missing Manager assignment workflow at the time of stabilisation. Firebase integration with Auditor/Manager consoles and assignment isolation need current-build proof. | Dev1 + PM |

## Regression and gap log

| Ref | Requirement / AC | Observation | Classification | Priority | Evidence | Owner | Action / status |
|---|---|---|---|---|---|---|---|
| D-GAP-01 | AC-07, AC-09, AC-16 | Dev1 stabilisation notes state that an Auditor could receive cases but could not retrieve specific cases assigned by the Manager because the Manager workflow MVP was not implemented at that time. | Previously documented implementation gap; current status must be rechecked | High | [Dev1 repository](https://github.com/GitIsFried/IBM-SPRINT-1-Developer-Investigation) — `Stabilisation.md` | Dev1 / Manager workflow owner | Validate latest build; demonstrate Manager assignment, Auditor isolation and correct case retrieval end to end. |
| D-GAP-02 | AC-08, AC-11 | Dev1 stabilisation notes identify Auditor editing and final human-decision persistence as incomplete at that time. | Previously documented implementation gap; current status must be rechecked | High | [Dev1 repository](https://github.com/GitIsFried/IBM-SPRINT-1-Developer-Investigation) — `Stabilisation.md` | Dev1 + UX | Confirm decision options, save/persistence, audit trail and AI-assistive boundary in the current build. |
| D-AI-01 | AC-05, AC-13 | V2/CASE-102 consistently returns `violence` but can omit expected `harassment`; the same content under another case ID reportedly returns both categories. | Confirmed issue in Dev2 regression evidence | High | [Dev2 refinement log](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REFINEMENT_LOG.md); [repeatability report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REPEATABILITY_REPORT.md) | Dev2 | Keep open until category correctness is resolved or accepted with documented rationale and test evidence. |
| D-AI-02 | AC-05, AC-11 | Some generated summaries add details not supported by the transcript; the repeatability report records an unsupported summary detail in 4/5 runs for the cited V2 example. | Confirmed quality issue in Dev2 evidence | High | [Dev2 repeatability report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REPEATABILITY_REPORT.md) | Dev2 | Add/execute transcript-grounding checks and representative regression tests; do not treat repeatability alone as correctness. |
| D-AI-03 | AC-06 | V3 timestamp may cover the whole clip because STT returns a single segment. | Known limitation / expected-behaviour decision may be needed | Medium | [Dev2 repeatability report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REPEATABILITY_REPORT.md) | Dev2 + BA/PM | Confirm expected timestamp granularity and ensure the UI explains/handles the returned segment correctly. |
| D-AI-04 | AC-04, AC-06, AC-10 | Dev2 reports malformed STT timing handling was changed to use null times with a reason rather than crashing. | Fix reported; retest required | Medium | [Dev2 refinement log](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REFINEMENT_LOG.md) | Dev2 | Retest malformed/missing timing inputs and verify UI/log behaviour in the integrated build. |
| D-AI-05 | AC-05, AC-13 | Dev2 reports V4 category behaviour improved so mild frustration no longer receives an `other` category in the cited tests. | Fix reported; retest required | Medium | [Dev2 refinement log](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REFINEMENT_LOG.md) | Dev2 | Rerun V4 regression cases and record actual outputs and build/commit reference. |
| D-GAP-03 | AC-04, AC-10 | Dev2 error-handling report includes live timeout evidence and simulated failure tests; full current-build integration and user-facing error behaviour are not established by those tests alone. | Evidence/integration gap | High | [Dev2 error-handling report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/ERROR_HANDLING.md) | Dev1 + Dev2 | Run integrated negative tests for STT/AI/storage/auth failures; attach logs/screenshots and verify no fabricated outputs are shown. |
| D-GAP-04 | AC-12, AC-15 | UX evidence for authentication and Auditor/Manager handoff documents has not been reviewed in full for this version. | Evidence gap — not a confirmed defect | Medium | [Authentication UX review](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Authentication_2FA_reCAPTCHA_UX_Review_and_Dev1_Refinement_Handoff_HarneetKaur.docx); [Auditor/Manager UX review](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Refined_Auditor_Manager_UX_Review_Usability_Gap_Register_and_Week3_Handoff_HarneetKaur.docx) | BA + UX | Review the documents and compare the current build against confirmed UX requirements and evidence. |
| D-GAP-05 | AC-01–AC-16 | The BA acceptance matrix and final acceptance scenario register still need execution results, build references and evidence links for the latest integrated build. | Evidence gap — not a confirmed defect | High | [Acceptance log](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Sprint_3_Refined_Build_Acceptance_Review_and_Regression_Log.md); [final acceptance scenarios](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Final_Acceptance_Scenarios_Auth_Wellbeing_Deployment.md) | BA + all relevant owners | Execute scenarios, record Pass/Partial/Fail/Not Tested honestly, attach evidence, and retest fixes. |
| D-GAP-06 | Deployment | Dev1 stabilisation notes describe local/runtime checks and indicate that testing on the actual Code Engine deployment was still planned at that time. | Deployment evidence gap; current status must be rechecked | High | [Dev1 repository](https://github.com/GitIsFried/IBM-SPRINT-1-Developer-Investigation) — `Stabilisation.md` | Dev1 / deployment owner | Run and document deployed smoke tests on the current Code Engine environment; confirm configuration, startup, dependencies and core end-to-end path. |

**Classification guide**
- **Confirmed issue in evidence:** Reproducible issue explicitly documented in a developer test/report.
- **Previously documented implementation gap:** A developer report identified the gap at that time; verify whether it remains in the current build.
- **Fix reported; retest required:** A change is documented, but the current integrated build has not yet been independently verified.
- **Evidence/integration gap:** Available component evidence does not establish integrated behaviour.
- **TBC/business decision:** Expected behaviour is not confirmed; track with PM/client.
- **Enhancement/recommendation:** Proposed improvement that is not an approved requirement.

## Open TBC decisions to preserve

Keep these open until the PM/client confirms them, and record the decision source when updated:

- Case ID format: short human-readable ID or current system-generated identifier.
- Whether a Case description belongs in the approved Public User submission flow.
- Expected behaviour when AI returns no incident timestamps.
- Supported file formats and maximum upload size.
- Authentication scope, whether 2FA and reCAPTCHA are mandatory, and exact role/Manager permissions.
- Whether a Severity column should appear in the Auditor queue. UX described this as a **recommendation**, pending BA confirmation under Dashboard requirements **TBC-08**; do not treat it as a confirmed build requirement until approved.
- Final severity scale and mandatory AI outputs beyond confirmed core outputs.
- Exact human final-decision labels/options.
- Exact decline/reassignment workflow and notification content beyond the confirmed decline → Manager notification/escalation direction.
- Exposure limits, cooldown parameters, SOS behaviour and other unconfirmed wellbeing values.
- Confirmed retry/escalation rules and whether opening/skipping raw media needs separate tracking.
- Confirmed accessibility target, if still unresolved.
- Exact acceptance expectation for timestamp granularity when STT returns only one segment.

## Final regression checklist

Before requesting final sign-off, run the latest integrated build and attach evidence for each applicable item:

- [ ] Authentication: valid/invalid login, unauthenticated protected access, role restrictions, sign-out/session behaviour.
- [ ] 2FA and reCAPTCHA: test only after scope/expected behaviour is confirmed; attach screen and test evidence.
- [ ] Submission: valid/invalid input, supported formats/size, validation messages and duplicate submission handling.
- [ ] Case creation: case persists and can be retrieved with the same Case ID.
- [ ] AI/STT: success, timeout, malformed output, missing timestamps, retry/error states and no fabricated results.
- [ ] AI correctness: rerun D9 V2/CASE-102 category test, summary grounding tests and V4 category regression.
- [ ] Manager workflow: assign case to Auditor; verify correct Auditor sees the case and other Auditors cannot access it unless permitted.
- [ ] Auditor workflow: view case and AI outputs; make a human decision; verify it persists and is visible to the appropriate Manager.
- [ ] Decline/escalation: verify Manager notification and record the actual result; confirm any unresolved reassignment rule separately.
- [ ] Wellbeing and UX: review approved exposure/cooldown/SOS requirements, loading/empty/error states, role visibility and accessibility evidence.
- [ ] Deployment: run smoke tests on the current deployed Code Engine environment, not only local development.
- [ ] Evidence register: update each result with build/commit, test steps, outcome, evidence link, owner and follow-up.
- [ ] Retest every fixed high-priority issue before sign-off.

## Handoff and actions

1. **Developers:** Provide current-build evidence for implemented criteria and failure-state tests. Report reproducible defects with steps, case ID, build/commit and expected versus actual result.
2. **Dev2:** Keep D-AI-01 (D9 category omission) and D-AI-02 (unsupported summary detail) open until resolved or formally dispositioned with evidence. Retest the reported D8/V4 fixes.
3. **Dev1 / integration owner:** Verify Firebase integration with Auditor/Manager consoles, Manager-to-Auditor assignment, role isolation, human-decision persistence and deployed Code Engine behaviour.
4. **UX:** Provide/review evidence for authentication, Case Preview, Analysis & Decision, Auditor/Manager role states, and loading/failure/empty states. Keep recommendations separate from approved requirements.
5. **PM/client:** Confirm outstanding business decisions and assign owners/dates for TBCs.
6. **BA:** Review the two UX handoff documents, update the acceptance matrix from actual test evidence, maintain the regression/gap log, and share the final findings with PM, UX and developers.

## Completion gate

**Do not sign off the release yet.** Final acceptance requires the latest integrated build to be reviewed; each applicable criterion to have an honest result; each Pass/Fail/Partial result to have evidence; high-priority defects to be resolved or explicitly dispositioned by the authorised decision-maker; gaps to have owners/actions; TBCs to be separated from confirmed defects; and the end-to-end workflow to pass from authentication and submission through AI results, Auditor review, human decision and Manager oversight. Deployment smoke-test evidence must also be recorded.

**Current recommendation:** **Ready for final regression — partial acceptance with open risks; final sign-off pending.**

**Evidence URL:** After you review this draft, replace the existing repository file or commit this updated Markdown to the team requirements repository and paste the resulting GitHub URL here.
