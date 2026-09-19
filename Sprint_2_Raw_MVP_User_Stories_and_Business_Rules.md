# Sprint 2 Raw MVP User Stories & Business Rules

## Purpose

Convert the validated Sprint 1 Core MVP into implementation-ready Raw
MVP user stories and business rules for Sprint 2. Unconfirmed values
remain explicitly open.

## 1. Public User Stories

### US-PU-01 --- Submit approved staged content

As a Public User, I want to submit approved synthetic/staged content so
that a review case can be created safely.

**Acceptance Criteria** - Only approved synthetic/staged content is
accepted for the MVP. - Real abusive/harmful agency content is out of
scope. - An accepted submission creates a case.

### US-PU-02 --- Receive Case ID

As a Public User, I want my submission to receive a Case ID so that the
case can be tracked.

**Acceptance Criteria** - A Case ID is created when the submission is
accepted. - The case enters the defined processing workflow.

### US-PU-03 --- Safe submission

As a Public User, I want the submission process to use safe staged
content so that the system does not require exposure to real harmful
material.

**Acceptance Criteria** - Synthetic/staged content only. - No real
abusive content is required for demonstration or validation.

## 2. Auditor User Stories

### US-AU-01 --- View AI-assisted results

As an Auditor, I want to view structured AI-assisted results so that I
can make an informed human decision.

**Acceptance Criteria** - Structured AI results are presented. - Core
expected outputs include severity, summary and incident timestamps. - AI
output is assistance, not the final decision.

### US-AU-02 --- Review a processed case

As an Auditor, I want to review a processed case so that I can assess
the available results.

**Acceptance Criteria** - The Auditor can access the case after the
appropriate processing state. - AI analysis and the human decision are
clearly separated.

### US-AU-03 --- Make the final human decision

As an Auditor, I want to make the final decision so that moderation
remains under human control.

**Acceptance Criteria** - The Auditor remains the final
decision-maker. - AI cannot autonomously determine the final case
outcome. - The human decision is recorded against the case.

### US-AU-04 --- Decline a case

As an Auditor, I want to decline a case when appropriate so that
wellbeing and appropriate case handling are supported.

**Acceptance Criteria** - Auditor decline is supported as a confirmed
workflow requirement. - Decline can trigger the confirmed Manager
notification/escalation behaviour. - Exact reassignment rules remain
open until confirmed.

## 3. Manager User Stories

### US-MG-01 --- Receive notification after decline

As a Manager/Supervisor, I want to be notified when an Auditor declines
a case so that the case can follow the appropriate escalation path.

**Acceptance Criteria** - A Manager notification/escalation path is
represented. - The notification is associated with the relevant case. -
Exact notification content and downstream reassignment rules remain open
where not confirmed.

### US-MG-02 --- Support Auditor wellbeing

As a Manager/Supervisor, I want to support Auditor wellbeing and
exposure management so that moderation work does not unnecessarily
increase harmful-content exposure.

**Acceptance Criteria** - Wellbeing is treated as a core
consideration. - Exposure management is represented in the
requirements/design direction. - Exact exposure limits and cooldown
values remain open pending confirmation.

# 4. Raw MVP Business Rules

**BR-01 --- Synthetic/Staged Content Only:** The MVP uses approved
synthetic/staged content. Real abusive or harmful agency data/content is
out of scope.

**BR-02 --- Case Creation:** An accepted submission creates a Case ID
and enters the case-processing workflow.

**BR-03 --- Processing:** The case progresses through defined processing
states before Auditor review.

**BR-04 --- AI is Assistive:** AI/STT provides structured assistance. AI
must not make the final moderation decision autonomously.

**BR-05 --- Core AI Outputs:** The Raw MVP represents severity, summary
and incident timestamps. Additional outputs remain subject to
confirmation/feasibility.

**BR-06 --- Human Final Decision:** The final decision remains with the
human Auditor. Exact decision labels/options remain open where not
confirmed.

**BR-07 --- Auditor Decline:** An Auditor may decline a case where
appropriate.

**BR-08 --- Manager Escalation/Notification:** An Auditor decline can
trigger the confirmed Manager notification/escalation path. Exact
reassignment behaviour and notification details remain open where
unconfirmed.

**BR-09 --- Wellbeing Priority:** Auditor wellbeing takes priority over
moderation speed. Exposure and cooldown values must not be treated as
fixed until confirmed.

**BR-10 --- Open Business Values:** Exact severity scale, AI accuracy
threshold, final decision options, reassignment rules, exposure limits,
cooldown parameters, Manager permissions and notification content remain
open/TBC unless separately confirmed.

**BR-11 --- No Autonomous Decision:** No AI output may independently
determine the final case outcome.

**BR-12 --- Scope Boundary:** The Raw MVP focuses on submission → Case
ID → AI-assisted processing → structured results → Auditor review →
human final decision, with confirmed Manager notification/escalation
represented where required.

# 5. Processing State Expectations

1.  Submission received
2.  Case created / Case ID generated
3.  AI/STT processing
4.  Structured AI results available
5.  Auditor review
6.  Human final decision
7.  Manager notification/escalation where an Auditor decline occurs

Technical state names may follow the agreed architecture, but the
workflow must not imply AI authority over the final decision.

# 6. Traceability

  Sprint 1 requirement              Raw MVP coverage
  --------------------------------- ---------------------------
  Public User submission            US-PU-01, US-PU-03, BR-01
  Case creation / Case ID           US-PU-02, BR-02
  AI processing                     US-AU-01, BR-03
  Severity / summary / timestamps   US-AU-01, BR-05
  Auditor review                    US-AU-02
  Human final decision              US-AU-03, BR-06, BR-11
  Auditor decline                   US-AU-04, BR-07
  Manager notification/escalation   US-MG-01, BR-08
  Wellbeing / exposure              US-MG-02, BR-09
  Open values                       BR-10

# 7. Implementation Boundary

## In scope

-   Approved synthetic/staged submission
-   Case creation and Case ID
-   AI-assisted processing
-   Structured core AI outputs
-   Auditor review
-   Human final decision
-   Confirmed Auditor decline behaviour
-   Confirmed Manager notification/escalation direction
-   Clear separation between AI assistance and human decision-making

## Not fixed / requires confirmation

-   Exact severity scale
-   Exact accuracy threshold
-   Exact final decision labels
-   Exact reassignment rules
-   Exposure limits
-   Cooldown values
-   Exact Manager permissions
-   Exact notification content

# 8. Handoff

**Developers:** Use these user stories and business rules as the
implementation boundary. Do not hard-code unconfirmed values as final
requirements.

**UX:** Ensure Public User, Auditor and relevant Manager flows represent
the confirmed workflow and do not imply autonomous AI decisions.

**PM:** Track the open business decisions and confirm them before they
become fixed implementation requirements.

**Status:** Raw MVP user stories and business rules prepared for Sprint
2 implementation planning and cross-role handoff.
