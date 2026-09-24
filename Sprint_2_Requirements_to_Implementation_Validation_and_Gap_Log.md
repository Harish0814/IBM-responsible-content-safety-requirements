# Sprint 2 — Requirements-to-Implementation Validation & Gap Log

**Task:** [REQUIREMENTS] Validate Implemented Stories Against Acceptance Criteria & Log Gaps  
**Role:** BA | **Sprint:** Sprint 2

## Validation note
A requirement marked **Not independently verified** means implementation evidence was not available in the BA review record. It is not treated as a confirmed defect.

## Acceptance-Criteria Validation

| Area | AC | Status | Gap / Next Action |
|---|---|---|---|
| Submission | AC-01 | Not independently verified | Confirm valid synthetic/staged submission and unsupported-input handling |
| Case ID | AC-02 | Not independently verified | Demonstrate unique Case ID creation and association |
| Case persistence | AC-03 | Not independently verified | Verify create/retrieve and processing-status persistence |
| COS / media storage | AC-04 | Not independently verified | Verify storage/reference and storage-failure handling |
| STT | AC-05 | Not independently verified | Verify STT, transcript result and explicit failure state |
| watsonx.ai output | AC-06 | Not independently verified | Verify structured severity, summary and timestamps/segments |
| Media analysis | AC-07 | Not independently verified | Verify analysis path and failure handling |
| Timestamps / segments | AC-08 | Not independently verified | Verify returned timestamps/segments where available |
| Auditor review | AC-09 | Not independently verified | Verify Auditor can review structured AI results |
| Human final decision | AC-10 | Not independently verified | Verify final outcome requires Auditor action |
| Failure states | AC-11 | Not independently verified | Verify submission, storage, persistence, STT and AI/media failures |
| AI assistive role | AC-12 | Evidence required | Confirm AI cannot independently finalise a case |
| Decline → Manager notification | AC-13 | Evidence required | Verify decline generates the relevant notification/escalation event |
| Wellbeing / exposure direction | Confirmed direction | Timing/parameters separate | Do not treat unconfirmed limits/cooldown values as defects |

## Confirmed Requirements

- Approved synthetic/staged content is used for the MVP.
- Valid submission creates a Case ID and enters the workflow.
- AI provides assistive structured information.
- Severity, summary and relevant incident timestamps/segments are expected outputs.
- The Auditor remains responsible for the final human decision.
- Auditor decline triggers the confirmed Manager notification/escalation direction.
- Relevant processing and failure states must be represented.

## Open / TBC Decisions

- Exact severity scale and AI accuracy threshold.
- Exact final decision labels/options.
- Exact reassignment rules after decline.
- Exposure-limit and cooldown values.
- Exact Manager permissions and notification content.
- Exact COS bucket/path/naming convention.
- Exact STT configuration.
- Exact timestamp/segment format and granularity.

## Gap Log

| ID | Observation | Classification | Next Action |
|---|---|---|---|
| GAP-01 | End-to-end workflow requires implementation evidence | Integration evidence gap | Developer + BA validation |
| GAP-02 | Processing and failure states require evidence | Validation gap | Developer |
| GAP-03 | STT and structured AI outputs require evidence | Validation gap | T10 / T11 owners |
| GAP-04 | Media analysis and timestamps require evidence | Validation gap | T12 owner |
| GAP-05 | Decline → Manager notification requires evidence | Validation gap | Developer / PM |
| GAP-06 | Unconfirmed business values remain TBC | Business decision | PM/client confirmation |

## Validation Outcome

The BA record separates **confirmed requirements**, **implementation evidence gaps**, and **open business decisions**. Unverified implementation items are not labelled as confirmed defects without supporting evidence.

## Handoff

**Developers:** Provide evidence for case creation/persistence, COS, STT, watsonx.ai, media analysis, failure states and final-decision behaviour.

**UX:** Verify submission, processing/error states, Auditor review, human decision separation and decline/escalation flow.

**PM:** Track unresolved business decisions and confirm when TBC values become approved.

**Status:** Requirements-to-implementation validation record prepared for Sprint 2 review.
