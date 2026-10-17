# Final Acceptance Scenarios — Authentication, Wellbeing & Deployment

**Project:** IBM Responsible Content-Safety Infrastructure  
**Role:** Business Analyst  
**Sprint:** Sprint 3 — Final acceptance and regression preparation  
**Status:** Draft for team review; unconfirmed business and technical rules remain TBC  
**Purpose:** Define measurable acceptance scenarios for authentication/security, role behaviour, Auditor wellbeing, failure states, and deployment/runtime validation. These scenarios are intended for Week 3 final regression and must be executed against the integrated build before any result is marked Pass.

## How to record results

For each scenario, record:
- **Result:** Pass / Fail / Partial / Not Tested
- **Evidence:** screenshot, test-run link, log excerpt, or reproducible steps
- **Owner:** responsible developer/tester
- **Defect or follow-up:** issue link and next action, if applicable

A scenario written here is a test definition, not proof that the feature has been implemented or tested. Do not mark a scenario Pass without observed evidence.

## Scope and constraints

- The MVP uses approved synthetic/staged content only. Real abusive content and real agency data are out of scope.
- AI/STT output supports the Auditor; it must not make the final case decision autonomously.
- The Auditor remains the human final decision-maker.
- An Auditor decline triggers the confirmed Manager notification/escalation path. Exact notification content and reassignment behaviour remain TBC.
- Wellbeing and exposure management are confirmed design requirements, but exact exposure limits, cooldown values, SOS behaviour, and Manager permissions remain TBC unless separately approved.
- The presence of a scenario for authentication, 2FA, reCAPTCHA, deployment, or a runtime check does not by itself confirm that a particular mechanism or configuration is approved for implementation. Validate the final scope with the PM/technical lead.
- Record confirmed defects separately from unresolved business decisions (TBCs).

## Scenario A — Authentication and security

### AUTH-01 — Unauthenticated access to protected screens
**Given** a user is not authenticated  
**When** they attempt to open a protected Auditor or Manager screen directly  
**Then** access is denied or the user is redirected to the approved sign-in flow, and protected case information is not displayed.  
**Evidence:** direct-route test and screenshot/result.  
**Scope note:** preserve the existing approved authentication and authorisation behaviour; do not introduce a new auth architecture through this test pack.

### AUTH-02 — Valid sign-in
**Given** an active account with valid credentials  
**When** the user signs in using the approved authentication flow  
**Then** authentication succeeds and the user is taken to the appropriate authorised landing page.  
**Evidence:** successful sign-in result and role/landing-page evidence.

### AUTH-03 — Invalid credentials
**Given** a user enters invalid credentials  
**When** they submit the sign-in form  
**Then** authentication is rejected, protected content remains inaccessible, and the interface displays a safe, understandable error without exposing sensitive technical details.  
**Evidence:** invalid-sign-in screenshot or test output.

### AUTH-04 — Deactivated or unauthorised account
**Given** an account is deactivated or lacks permission  
**When** the user attempts to sign in or open a protected route  
**Then** access is denied and no protected case data is exposed. The exact user-facing wording remains **TBC** if not approved.  
**Evidence:** account/permission setup, result, and screenshot.

### AUTH-05 — Role-based access boundaries
**Given** accounts representing the approved Public User, Auditor, and Manager roles  
**When** each role opens screens and actions assigned to other roles  
**Then** only approved screens, case data, and actions are available; unauthorised direct-route or action attempts are rejected.  
**Evidence:** role-by-screen/action test matrix.  
**TBC:** exact Manager permissions and any additional role restrictions.

### AUTH-06 — Session and sign-out behaviour
**Given** an authenticated user  
**When** they sign out and then try to reuse a protected route or browser history entry  
**Then** protected data is not available without re-authentication.  
**Evidence:** sign-out, refresh, and direct-route results.  
**TBC:** exact session timeout and expiry rules if not approved.

### AUTH-07 — Two-factor authentication (2FA), if in approved scope
**Given** the PM/technical lead confirms 2FA is required and enabled for the relevant role  
**When** a user completes or fails the second authentication step  
**Then** successful verification permits access, while failed or incomplete verification does not grant access.  
**Evidence:** configuration and both success/failure results.  
**Status:** **TBC — do not treat 2FA as a confirmed build requirement until scope is approved.**

### AUTH-08 — reCAPTCHA or equivalent anti-abuse check, if in approved scope
**Given** the PM/technical lead confirms an anti-abuse challenge is required and configured  
**When** a user completes or fails the challenge during the relevant flow  
**Then** the flow follows the approved success/failure behaviour and does not bypass authentication or submission validation.  
**Evidence:** configured test results.  
**Status:** **TBC — provider, trigger conditions, and expected behaviour require confirmation.**

## Scenario B — Auditor wellbeing and Manager escalation

### WELL-01 — Wellbeing direction is represented
**Given** the approved Auditor workflow and UX specification  
**When** the Auditor review experience is checked against requirements  
**Then** the design preserves the wellbeing-first direction and does not prioritise moderation speed over Auditor wellbeing.  
**Evidence:** requirement-to-screen mapping and screenshot/reference.  
**Note:** this validates requirement/design coverage; it does not prove unimplemented controls work.

### WELL-02 — Exposure information and limits
**Given** the approved exposure-management specification and test data  
**When** exposure information is displayed or an approved exposure limit is reached  
**Then** the system follows the approved behaviour and presents the relevant status/action consistently.  
**Evidence:** test case and result.  
**TBC:** exposure-limit values, measurement window, threshold behaviour, and Manager override permissions. Do not invent numeric limits.

### WELL-03 — Cooldown behaviour
**Given** an approved cooldown rule and test configuration  
**When** the rule’s trigger condition is met  
**Then** the system applies the approved cooldown behaviour and communicates the resulting state clearly.  
**Evidence:** trigger, timestamps, and observed result.  
**TBC:** trigger threshold, duration, reset rules, and whether cooldown is implemented in this release.

### WELL-04 — SOS or urgent wellbeing action
**Given** an approved SOS/urgent-support requirement and configured test environment  
**When** the Auditor invokes the action  
**Then** the system follows the approved escalation/support path and provides a clear confirmation or safe failure message.  
**Evidence:** action result and notification/escalation evidence.  
**TBC:** exact SOS behaviour, recipients, response expectations, and implementation scope.

### WELL-05 — Auditor declines a case
**Given** an Auditor is reviewing an assigned/available case  
**When** the Auditor declines the case  
**Then** the decline is recorded and the confirmed Manager notification/escalation path is triggered.  
**Evidence:** case state/audit evidence and notification/escalation result.  
**TBC:** exact notification content, subsequent reassignment, and detailed routing rules.

### WELL-06 — Manager notification failure
**Given** an Auditor decline occurs and the Manager notification path is unavailable or fails  
**When** the system attempts to notify/escalate  
**Then** the failure is observable to the responsible system/operator, is not silently represented as a successful notification, and can be followed up.  
**Evidence:** simulated failure/log and recorded follow-up.  
**TBC:** retry policy, fallback recipient, alerting mechanism, and service-level expectations.

### WELL-07 — AI does not make the final decision
**Given** a processed case with AI-assisted severity, summary, and timestamp results  
**When** the case is presented for review  
**Then** the AI output is distinguishable from the human decision, and a final case outcome requires an authorised human action.  
**Evidence:** UI and persisted case-state evidence.

## Scenario C — Submission, processing and failure states

### FAIL-01 — Unsupported or invalid submission
**Given** a submission that violates the approved file/type/validation rules  
**When** the Public User submits it  
**Then** the submission is rejected safely, a useful validation message is shown, and no invalid case is represented as successfully accepted.  
**Evidence:** test file/type and result.  
**TBC:** supported formats, maximum upload size, and exact validation wording.

### FAIL-02 — Case creation or persistence failure
**Given** a valid staged submission  
**When** case creation or persistence fails  
**Then** the system does not falsely confirm successful case creation; the failure is surfaced safely and is diagnosable from available logs.  
**Evidence:** simulated failure, UI result, and log/reference.

### FAIL-03 — STT or AI service unavailable
**Given** an accepted case and an unavailable/failing STT or AI dependency  
**When** processing is attempted  
**Then** the case enters a clear non-success/error state, no fabricated AI result is shown, and the human decision workflow does not treat missing output as a completed analysis.  
**Evidence:** service-failure test and resulting case state.  
**TBC:** retry count, timeout values, and recovery policy.

### FAIL-04 — Missing incident timestamps
**Given** the AI result contains no incident timestamps  
**When** the result is displayed to the Auditor  
**Then** the UI handles the absence clearly without inventing timestamps or implying that timestamps were found.  
**Evidence:** fixture/result and UI screenshot.  
**TBC:** exact display wording and whether a case can proceed to final decision without timestamps.

### FAIL-05 — Partial or malformed AI output
**Given** the AI service returns incomplete or malformed structured output  
**When** the system validates or displays the result  
**Then** invalid fields are not silently presented as valid; the case/result state is clear and safe, with diagnostics available to authorised maintainers.  
**Evidence:** malformed-output test and logs.  
**TBC:** field-level fallback and retry policy.

### FAIL-06 — Duplicate submission or repeated action
**Given** a user retries a submission or action because of delay or uncertain feedback  
**When** the same request is submitted again  
**Then** the system follows the approved duplicate-handling behaviour and does not silently create confusing duplicate cases or duplicate final decisions.  
**Evidence:** repeated-request test.  
**TBC:** idempotency and duplicate-detection rules.

### FAIL-07 — Case state and traceability
**Given** a case moves through submission, creation, processing, AI result availability, Auditor review, and human decision  
**When** each transition occurs  
**Then** the current state and case identifier remain consistent across relevant views and persisted records.  
**Evidence:** end-to-end case trace and database/log reference.

## Scenario D — Deployment and runtime

### DEPLOY-01 — Application starts in the approved environment
**Given** the approved deployment configuration and dependencies  
**When** the application is started or redeployed  
**Then** it starts successfully, reports a healthy state through the approved health check, and does not expose secrets in logs or responses.  
**Evidence:** deployment result and health-check output.

### DEPLOY-02 — Required configuration is present
**Given** the application is configured for the target environment  
**When** it starts with required configuration missing or invalid  
**Then** it fails safely or reports a clear configuration error rather than silently running with unsafe defaults.  
**Evidence:** configuration test and startup logs.  
**TBC:** exact environment variables, secret-management approach, and required configuration list must match the approved technical design.

### DEPLOY-03 — Dependency or database unavailable
**Given** a required database, storage service, or AI/STT dependency is unavailable  
**When** the application starts or processes a case  
**Then** the failure is handled predictably, no false success is shown, and recovery can be verified when the dependency returns.  
**Evidence:** dependency-down and recovery results.

### DEPLOY-04 — Runtime error visibility
**Given** a controlled runtime error occurs  
**When** the system handles the error  
**Then** the user sees a safe message, sensitive details are not exposed, and authorised logs contain enough diagnostic information for investigation.  
**Evidence:** UI response and redacted log reference.

### DEPLOY-05 — End-to-end smoke test after deployment
**Given** the integrated build is deployed to the approved test environment  
**When** a synthetic/staged case is submitted and processed through Auditor review  
**Then** case creation, Case ID, available structured AI outputs, human final decision, and applicable decline-to-Manager notification behaviour can be traced end to end.  
**Evidence:** case ID, test run, screenshots/log references, and result.  
**TBC:** any service integration or deployment dependency that is not available must be marked Not Tested, not Pass.

## Acceptance evidence register

Complete this table during execution. Leave results as **Not Tested** until evidence is observed.

| Scenario ID | Result (Pass/Fail/Partial/Not Tested) | Evidence reference | Defect / TBC / follow-up | Owner |
|---|---|---|---|---|
| AUTH-01 | Not Tested | TBC |  |  |
| AUTH-02 | Not Tested | TBC |  |  |
| AUTH-03 | Not Tested | TBC |  |  |
| AUTH-04 | Not Tested | TBC |  |  |
| AUTH-05 | Not Tested | TBC |  |  |
| AUTH-06 | Not Tested | TBC |  |  |
| AUTH-07 | Not Tested | TBC | Confirm whether 2FA is in approved scope |  |
| AUTH-08 | Not Tested | TBC | Confirm anti-abuse challenge scope/provider |  |
| WELL-01 | Not Tested | TBC |  |  |
| WELL-02 | Not Tested | TBC | Confirm limits and threshold behaviour |  |
| WELL-03 | Not Tested | TBC | Confirm cooldown rules and implementation scope |  |
| WELL-04 | Not Tested | TBC | Confirm SOS behaviour and implementation scope |  |
| WELL-05 | Not Tested | TBC | Confirm notification content/reassignment details |  |
| WELL-06 | Not Tested | TBC | Confirm retry/fallback rules |  |
| WELL-07 | Not Tested | TBC |  |  |
| FAIL-01 | Not Tested | TBC | Confirm formats and upload limit |  |
| FAIL-02 | Not Tested | TBC |  |  |
| FAIL-03 | Not Tested | TBC | Confirm retry/timeout rules |  |
| FAIL-04 | Not Tested | TBC | Confirm missing-timestamp handling |  |
| FAIL-05 | Not Tested | TBC | Confirm malformed-output handling |  |
| FAIL-06 | Not Tested | TBC | Confirm duplicate-handling rules |  |
| FAIL-07 | Not Tested | TBC |  |  |
| DEPLOY-01 | Not Tested | TBC | Confirm target environment/health check |  |
| DEPLOY-02 | Not Tested | TBC | Confirm required configuration |  |
| DEPLOY-03 | Not Tested | TBC |  |
| DEPLOY-04 | Not Tested | TBC |  |
| DEPLOY-05 | Not Tested | TBC |  |

## Handoff and completion criteria

**For Developers / DevOps**
- Execute applicable scenarios against the integrated build.
- Attach evidence and record Pass, Fail, Partial, or Not Tested accurately.
- Log confirmed implementation defects separately from TBC business decisions.
- Do not hard-code unconfirmed values or treat optional scenarios as approved scope without confirmation.

**For UX**
- Check that authentication errors, processing failures, missing AI outputs, and wellbeing states are communicated clearly and accessibly.
- Keep unconfirmed labels, queue fields, and wellbeing thresholds marked as recommendations/TBC until approved.

**For PM**
- Confirm scope for 2FA, reCAPTCHA/anti-abuse, exact role permissions, wellbeing thresholds/cooldown/SOS, notification details, retry rules, and deployment configuration.
- Prioritise carry-over defects and assign owners.

**Ready for sign-off when**
1. Applicable scenarios have execution results and evidence.
2. Failures/partials have owners and follow-up actions.
3. Not-tested scenarios are explicitly identified with reasons.
4. TBC decisions remain separate from confirmed defects.
5. Week 3 regression handoff is shared with PM, UX, Developers, and the responsible tester.

**Important:** This document defines the test scenarios and evidence expectations. It does not claim that the scenarios have been executed or that the build has passed.
