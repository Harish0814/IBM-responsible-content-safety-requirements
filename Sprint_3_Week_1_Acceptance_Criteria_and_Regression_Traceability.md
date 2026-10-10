# Sprint 3 Week 1 — Acceptance Criteria & Regression Traceability

**Task:** [REQUIREMENTS] Finalise Week 1 Acceptance Criteria & Regression Traceability  
**Role:** Business Analyst (BA)  
**Sprint:** Sprint 3  
**Purpose:** Convert the approved Sprint 3 Week 1 refinement requirements into measurable acceptance criteria, map each requirement to UX / Dev1 / Dev2 work, and define the evidence required for regression or refinement review.

## 1. Validation and status rules

- **Requirement Confirmation Status** describes whether a requirement has been confirmed by the project/client. It does **not** mean development or testing is complete.
- **Test Result** must be recorded separately as `Pass`, `Fail`, `Partial`, or `Not Tested`.
- A result can be marked `Pass` only when accessible implementation/test evidence supports the acceptance criterion.
- A missing screenshot, test record, build output, or other evidence is `Not Tested` or an evidence gap, not automatically a confirmed defect.
- Confirmed defects must be recorded separately from assumptions and business decisions that remain `TBC`.
- Use only approved synthetic/staged test inputs. Do not use real abusive content or real agency data.
- AI output is assistive. The Auditor remains responsible for the final human decision.

## 2. Acceptance criteria

| ID | Requirement / area | Measurable acceptance criterion | Requirement Confirmation Status | Evidence expected |
|---|---|---|---|---|
| AC-01 | Approved submission | The system accepts only the approved synthetic/staged test content supported by the agreed submission flow. Real abusive content and real agency data are not required for the MVP. | Confirmed | Submission test record and screenshot using approved staged input |
| AC-02 | Case creation and Case ID | An accepted submission creates a case and returns or displays a Case ID that links to that case. The exact human-readable format of the Case ID remains TBC if not confirmed. | Core behaviour confirmed; display format TBC | Submission response, case record, and case-detail screenshot |
| AC-03 | Case retrieval and traceability | The created case can be retrieved through the implemented workflow, and the Case ID remains associated with the submitted content and downstream processing results. | Confirmed | Case record / API response and linked result evidence |
| AC-04 | Persistence and storage | The system persists the case and required metadata according to the agreed architecture. A failed persistence operation must not be reported as a successful completed submission. | Requirement confirmed; technical details follow approved architecture | Relevant database/log evidence and failure test result |
| AC-05 | Processing states | The case progresses through the implemented submission, case creation, AI/STT processing, results-available, Auditor-review and human-decision stages. Technical state names may follow the approved architecture. | Workflow confirmed; exact technical labels may vary | State-transition evidence or logs for a test case |
| AC-06 | STT / transcript processing | When STT is available and applicable to the staged input, the system records or exposes the transcript result or a clear processing/failure state. Do not assume a transcript exists when processing fails or is unsupported. | Required behaviour; provider/input-specific details subject to implementation | STT output or explicit failure-state evidence |
| AC-07 | Structured AI results | The AI-processing step returns or records the supported structured result fields. Core expected outputs are severity, summary and incident timestamps; additional outputs must not be treated as mandatory unless confirmed. | Core outputs confirmed; extra outputs TBC | Sanitised structured-result payload or UI evidence |
| AC-08 | Severity and summary | The case result presents the AI-generated severity and summary when those outputs are successfully produced. The final severity scale and any accuracy threshold remain TBC until confirmed. | Outputs confirmed; scale/threshold TBC | Result payload/UI screenshot and relevant test record |
| AC-09 | Incident timestamps / segments | When the analysis provides incident timestamps or segments, the result links them to the relevant case and presents them consistently. Behaviour when no timestamps are returned remains TBC unless confirmed. | Timestamp output confirmed; no-timestamp behaviour TBC | Result payload and UI evidence; no-timestamp case recorded as TBC if unresolved |
| AC-10 | Auditor review | An Auditor can access the processed case and review the available structured AI results before making the final human decision. AI assistance and human decision must be clearly distinguishable. | Confirmed | Auditor-view screenshot and role/workflow test record |
| AC-11 | Human final decision | The workflow requires an explicit human Auditor decision. The AI must not autonomously make or record the final moderation decision. Exact decision labels/options remain TBC until confirmed. | Human decision confirmed; exact options TBC | Decision screen and saved decision evidence |
| AC-12 | Auditor decline and Manager notification | When an Auditor declines a case, the confirmed Manager notification/escalation path is triggered. The exact notification wording and downstream reassignment rules remain TBC where not confirmed. | Decline → Manager notification/escalation confirmed; details TBC | Decline event plus notification/escalation evidence, or a recorded implementation gap |
| AC-13 | Failure and error states | Invalid/unsupported submission, storage/persistence failure, STT/AI processing failure, incomplete AI output and unavailable case/result must produce a clear failure, retry, or pending state consistent with the approved implementation. Do not show a failed operation as successful. Unconfirmed retry/escalation rules remain TBC. | Failure handling required; exact retry rules TBC | One test record per applicable failure path, including observed result |
| AC-14 | Wellbeing and exposure-management direction | Requirements and design preserve the wellbeing-first direction and account for exposure management. Unconfirmed exposure limits, cooldown values, SOS behaviour details and Manager permissions must remain TBC rather than being presented as approved numeric/business rules. | Direction confirmed; parameters TBC | UX/specification review and TBC register |
| AC-15 | Role-based access and information visibility | Public User, Auditor and Manager views/actions must follow the confirmed role boundaries. Do not assume additional permissions or authentication behaviour that has not been approved. | Role boundaries required; exact scope TBC where unresolved | Role/access test evidence and documented permission gaps |
| AC-16 | Regression and traceability | Each reviewed requirement is linked to its acceptance criterion, responsible workstream, test result, evidence reference and gap owner. Every result is recorded as Pass, Fail, Partial or Not Tested. | Required process | Completed traceability matrix with evidence links and owners |

## 3. Requirements-to-task traceability

Use the team’s actual Planner task IDs/links when available. The role mapping below identifies the expected workstream; it does not claim that the work has already been completed.

| Requirement / AC | UX mapping | Dev1 mapping | Dev2 mapping | Regression evidence to collect |
|---|---|---|---|---|
| AC-01 Approved submission | Submission flow, supported-input guidance and validation/error messages | Submission endpoint/validation as assigned | UI-to-API integration or supporting component as assigned | Approved staged submission succeeds; unsupported/invalid input result recorded |
| AC-02–03 Case creation, Case ID and retrieval | Case confirmation and case-detail entry point; identifier display format flagged TBC if unresolved | Case creation/retrieval and identifier persistence as assigned | Case-detail/results integration as assigned | Same Case ID connects submission, case record and result |
| AC-04 Persistence/storage | Loading, success and failure states for case creation/results | Database/persistence behaviour as assigned | COS/media storage integration as assigned | Persisted record evidence and failure-path result |
| AC-05 Processing states | Processing/pending/results states | Backend workflow/state transitions as assigned | Integration across processing services as assigned | State progression and stuck/failed processing evidence |
| AC-06 STT | Transcript display or clear unavailable/failed state, if in scope | STT integration/output handling as assigned | Service integration/error propagation as assigned | Transcript or explicit STT failure evidence |
| AC-07–09 AI outputs, severity, summary, timestamps | Structured result layout; labels/options marked TBC where unresolved | AI/STT structured-output integration as assigned | Media analysis, timestamp/segment and result-display integration as assigned | Result payload compared with visible case result; missing outputs recorded |
| AC-10–11 Auditor review and human decision | Auditor review flow; distinguish AI recommendation from human action | Decision persistence/workflow as assigned | Auditor UI/integration as assigned | Auditor can review result and explicitly save a human decision |
| AC-12 Decline and Manager notification | Decline interaction and Manager notification/ escalation representation | Decline event and notification trigger as assigned | Notification/Manager-flow integration as assigned | Decline event linked to relevant case and notification evidence |
| AC-13 Failure states | Clear user-facing error/pending/retry guidance, without inventing unconfirmed rules | Validation and backend failure handling as assigned | Integration failure handling and UI feedback as assigned | Separate invalid input, persistence, STT/AI, incomplete output and retrieval failure results |
| AC-14 Wellbeing/exposure direction | Preserve wellbeing-first design and show unresolved parameters as TBC | Implement only confirmed scope; no invented numeric thresholds | Implement only confirmed scope; no invented Manager permissions | UX/spec review and a list of open values; do not mark unbuilt future features as defects |
| AC-15 Role/access boundaries | Role-specific screens/actions aligned to approved requirements | Backend authorisation as assigned and confirmed | UI/access integration as assigned | Role-specific access result, with unconfirmed rules recorded as TBC |
| AC-16 Regression traceability | Provide relevant design references | Provide implementation/test evidence for assigned work | Provide implementation/test evidence for assigned work | Completed row for every reviewed AC with status, evidence and gap owner |

**Owner mapping note:** Replace generic `Dev1` and `Dev2` mappings with the actual assigned teammate/task names and links when confirmed. Do not infer individual ownership from this document.

## 4. Regression review record

Complete this table during the actual evidence review. The initial status is deliberately `Not Tested` until evidence is checked.

| AC ID | Test Result (Pass / Fail / Partial / Not Tested) | Evidence URL / reference | Gap or defect (if any) | Gap owner | Next action |
|---|---|---|---|---|---|
| AC-01 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review approved staged-submission evidence |
| AC-02 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Verify case creation and Case ID linkage |
| AC-03 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Verify case retrieval and traceability |
| AC-04 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review persistence/storage evidence |
| AC-05 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review processing-state transitions |
| AC-06 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review STT output and failure handling |
| AC-07 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review structured AI result |
| AC-08 | Not Tested | TBC | Severity scale/threshold remain TBC if unconfirmed | TBC | Verify output presence; do not invent scale/threshold |
| AC-09 | Not Tested | TBC | No-timestamp behaviour may remain TBC | TBC | Verify timestamp/segment output and log unresolved behaviour |
| AC-10 | Not Tested | TBC | Evidence not recorded in this document yet | TBC | Review Auditor access and result display |
| AC-11 | Not Tested | TBC | Exact final-decision options may remain TBC | TBC | Verify explicit human decision and save behaviour |
| AC-12 | Not Tested | TBC | Notification details/reassignment may remain TBC | TBC | Verify decline triggers Manager notification/escalation |
| AC-13 | Not Tested | TBC | Applicable failure-path evidence not recorded yet | TBC | Record each applicable failure scenario separately |
| AC-14 | Not Tested | TBC | Exposure/cooldown/SOS/permissions parameters may remain TBC | TBC | Review design direction and maintain TBC list |
| AC-15 | Not Tested | TBC | Exact permission scope may remain TBC | TBC | Review confirmed role boundaries and available access tests |
| AC-16 | Not Tested | TBC | Final traceability results not yet consolidated | BA with PM/UX/Dev input | Complete result, evidence and owner fields after review |

## 5. Confirmed requirements versus TBC decisions

### Confirmed requirement directions
- Approved synthetic/staged inputs only for the MVP.
- Accepted submission creates a case and Case ID.
- AI processing supports structured outputs, with severity, summary and incident timestamps as core expected outputs.
- AI is assistive; an Auditor makes the final human decision.
- Auditor decline triggers the confirmed Manager notification/escalation path.
- Wellbeing is a priority and exposure management is a confirmed requirement/design direction.
- Requirements must be traceable to UX and development work, with evidence-based regression review.

### Keep TBC until confirmed
- Exact Case ID display format.
- Final severity scale and any mandatory AI accuracy threshold.
- Exact final human-decision labels/options.
- Expected behaviour when no incident timestamps are returned.
- Exact supported file formats and maximum upload size, unless confirmed elsewhere.
- Exact retry/escalation rules beyond the confirmed decline → Manager notification/escalation direction.
- Exposure limits, cooldown duration/thresholds, SOS details, notification content and exact Manager permissions.
- Any additional AI output beyond the confirmed core outputs.

## 6. Definition of Done

- [ ] Each approved refinement requirement has a measurable acceptance criterion.
- [ ] Each requirement is mapped to UX, Dev1 and/or Dev2 work, using actual task links/owners where available.
- [ ] Regression evidence expectations are defined for each criterion.
- [ ] Actual test results are recorded as Pass, Fail, Partial or Not Tested only after evidence review.
- [ ] Every identified gap has an evidence reference or an explicit statement that evidence is missing.
- [ ] Confirmed defects are separated from TBC decisions and assumptions.
- [ ] No TBC value is represented as a confirmed requirement.
- [ ] Wellbeing-first and human-final-decision principles are preserved.
- [ ] The completed traceability matrix and evidence URL are added to the Master Document and Planner task.
- [ ] The handoff is shared with PM, UX, Dev1 and Dev2.

## 7. Handoff

**PM:** Confirm remaining business decisions and owners; keep TBC decisions distinct from defects.  
**UX:** Use the acceptance criteria to check the current flows and mark unresolved labels/behaviour as TBC.  
**Dev1 / Dev2:** Link implementation and test evidence to the applicable ACs, record observed results, and identify gap owners.  
**BA:** Consolidate evidence-based results, maintain the traceability matrix, and update the Master Document.

**Status:** Acceptance criteria and regression traceability baseline prepared. Actual pass/fail outcomes remain unverified until implementation evidence is reviewed.
