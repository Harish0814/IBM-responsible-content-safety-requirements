# Sprint 2 — Raw MVP Test Scenarios & Acceptance Evidence

**Task:** [REQUIREMENTS] Define Raw MVP Test Scenarios & Acceptance Evidence  
**Role:** BA  
**Sprint:** Sprint 2

## Purpose

Define test scenarios for validating the integrated Raw MVP against the approved user stories and acceptance criteria. Scenarios use approved synthetic/staged inputs only and identify the evidence required to demonstrate each result.

## 1. Test Scenario Matrix

| ID | Scenario | Expected Result | Evidence |
|---|---|---|---|
| TS-01 | Submit valid synthetic/staged media | Submission is accepted and a case is created | Submission screenshot/log + Case ID |
| TS-02 | Submit invalid/unsupported input | Submission is rejected or handled as an explicit failure | Error message/screenshot + status |
| TS-03 | Create and retrieve Case ID | Unique Case ID is generated and the case can be retrieved | Case record/API evidence |
| TS-04 | Persist case and processing status | Case and relevant processing state are stored correctly | Database/test evidence |
| TS-05 | Store submitted media | Media is stored and associated with the Case ID | COS/storage evidence |
| TS-06 | Run STT on supported media | Transcript is returned and status is recorded | STT result + status evidence |
| TS-07 | Handle STT failure | STT failure is shown as an explicit failure state | Failure screenshot/log |
| TS-08 | Run AI/media analysis | Structured AI result is produced | AI result screenshot/log |
| TS-09 | Handle incomplete AI output | Missing/incomplete output is not treated as successful completion | Error/status evidence |
| TS-10 | Return incident timestamps/segments | Relevant timestamps/segments are shown where available | Result screenshot |
| TS-11 | Auditor reviews processed case | Auditor can view structured AI results before deciding | Auditor UI screenshot |
| TS-12 | Auditor makes final human decision | Case outcome requires explicit Auditor action | Decision UI + saved result |
| TS-13 | Verify AI remains assistive | AI output cannot independently finalise the case | UI/backend evidence |
| TS-14 | Auditor declines a case | Decline triggers the confirmed Manager notification/escalation path | Decline + notification evidence |
| TS-15 | End-to-end happy path | Submission → Case ID → processing → AI result → Auditor review → human decision completes successfully | End-to-end demo/test evidence |
| TS-16 | End-to-end failure path | Failed processing does not appear successful and does not create an autonomous final decision | Failure-state evidence |

## 2. Acceptance-Criteria Mapping

| Scenario | Acceptance Criteria |
|---|---|
| TS-01 | AC-01 |
| TS-02 | AC-01, AC-11 |
| TS-03 | AC-02, AC-03 |
| TS-04 | AC-03 |
| TS-05 | AC-04 |
| TS-06 | AC-05 |
| TS-07 | AC-05, AC-11 |
| TS-08 | AC-06, AC-07 |
| TS-09 | AC-06, AC-11 |
| TS-10 | AC-08 |
| TS-11 | AC-09 |
| TS-12 | AC-10 |
| TS-13 | AC-12 |
| TS-14 | AC-13 |
| TS-15 | AC-01–AC-10, AC-12 |
| TS-16 | AC-11, AC-12 |

## 3. Test Data Constraint

- Use **approved synthetic/staged content only**.
- Do not use real abusive or harmful agency content.
- Test data should be safe for development, validation and demonstration.

## 4. Evidence Requirements

For each executed scenario, capture enough evidence to show:

- Test scenario ID
- Input/test condition
- System result
- Relevant Case ID/status
- Screenshot, log, API response or database evidence where applicable
- Failure state where the scenario is a negative test
- Responsible Developer/UX owner where follow-up is required

## 5. Expected Failure Scenarios

The following must be explicitly testable:

- Invalid/unsupported submission
- Case creation/persistence failure
- Media/COS storage failure
- STT failure
- AI/media-analysis failure
- Missing or incomplete structured AI output
- Processing failure before Auditor review

A failed process must not be presented as successful, and an AI failure must not result in an autonomous final human decision.

## 6. Confirmed vs TBC

### Confirmed for testing

- Synthetic/staged input only
- Case creation and Case ID
- AI-assisted processing
- Structured AI result
- Auditor review
- Human final decision
- Auditor decline → Manager notification/escalation direction
- Relevant failure-state handling

### Remain TBC

- Exact severity scale
- AI accuracy threshold
- Exact final decision labels/options
- Exact reassignment rules
- Exposure-limit values
- Cooldown values
- Exact Manager permissions
- Exact notification content
- Implementation-specific storage/STT/timestamp formats

TBC items should not be treated as failed acceptance criteria until the relevant business rule is confirmed.

## 7. Evidence / Ownership Handoff

**Developers:** Execute technical scenarios and provide API, database, storage, AI/STT and failure-state evidence.

**UX:** Provide evidence for submission, processing/error states, Auditor review, human decision separation and decline/escalation presentation.

**BA:** Maintain scenario-to-AC traceability and record gaps or unresolved decisions.

**PM:** Track TBC business decisions and confirm changes to approved requirements.

## Definition of Done

- [x] Happy-path end-to-end scenario defined
- [x] Synthetic/staged test-input requirement documented
- [x] Case creation and retrieval scenarios defined
- [x] Database/COS integration scenarios defined
- [x] STT and AI-result scenarios defined
- [x] Incident timestamp/segment scenario defined
- [x] Auditor review and human-decision scenario defined
- [x] Submission and processing failure scenarios defined
- [x] Expected result and evidence identified for each scenario
- [x] Test scenarios mapped to acceptance criteria

**BA outcome:** The Raw MVP test-scenario pack defines positive and negative validation scenarios, expected results, evidence requirements and acceptance-criteria traceability for Week 3 system testing.
