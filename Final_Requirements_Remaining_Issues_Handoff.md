# Final Requirements & Remaining-Issues Handoff

**Project:** IBM Responsible Content-Safety Infrastructure — Team 1  
**Prepared by:** Business Analyst (BA)  
**Review date:** 26 October 2026  
**Related Planner task:** `[REQUIREMENTS] Prepare Final Requirements / Remaining-Issues Handoff : 120`  
**Status:** Handoff draft prepared; PM handoff and final scope confirmation remain pending.

> This is an evidence-based document review, not an independent retest of the latest integrated build. The findings below must be reconfirmed against current-build evidence.

## 1. Executive summary

The available evidence supports moving into final regression and closure review, but it does not support declaring the MVP fully accepted or release-ready. Dev1 notes document submission, case creation, persistence and retrieval work, while also recording that Manager assignment and Auditor final-decision persistence were incomplete at the time of that report. Dev2 Sprint 3 reports provide evidence of repeatability and structured failure handling, but also record an open category issue for V2/CASE-102 and unsupported details in some generated summaries.

**Current scope position: Ready for final regression — partial acceptance with open risks; final sign-off pending.**

## 2. Evidence reviewed

### BA acceptance documents
- [Sprint 3 — Refined Build Acceptance Review & Regression Log](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Sprint_3_Refined_Build_Acceptance_Review_and_Regression_Log.md)
- [Final Acceptance Scenarios — Auth, Wellbeing & Deployment](https://github.com/Harish0814/IBM-responsible-content-safety-requirements/blob/main/Final_Acceptance_Scenarios_Auth_Wellbeing_Deployment.md)

The acceptance scenarios define tests to execute; their existence does not mean they passed. The available acceptance evidence register was marked `Not Tested`.

### Developer evidence
- [Dev1 investigation repository](https://github.com/GitIsFried/IBM-SPRINT-1-Developer-Investigation)
- [Dev2 Sprint 3 AI-hardening branch](https://github.com/KumKaiLek/capstone-dev2-sprint2/tree/sprint3-ai-hardening)
- [Dev2 refinement log](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REFINEMENT_LOG.md)
- [Dev2 error-handling report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/ERROR_HANDLING.md)
- [Dev2 repeatability report](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/REPEATABILITY_REPORT.md)
- [Dev2 Sprint 3 handoff](https://github.com/KumKaiLek/capstone-dev2-sprint2/blob/sprint3-ai-hardening/docs/HANDOFF_SPRINT3.md)

### UX evidence requiring review
- [Authentication, 2FA and reCAPTCHA UX review](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Authentication_2FA_reCAPTCHA_UX_Review_and_Dev1_Refinement_Handoff_HarneetKaur.docx)
- [Auditor/Manager UX review and Week 3 handoff](https://github.com/s4059119/IBM_Sprint1_UX_investigation/blob/main/Refined_Auditor_Manager_UX_Review_Usability_Gap_Register_and_Week3_Handoff_HarneetKaur.docx)

**Evidence limitation:** The UX `.docx` files have not been reviewed in full for this handoff. UX-specific conclusions remain provisional until the documents and current UI are compared.

## 3. Requirements position

| Area | Current position | Evidence / next action |
|---|---|---|
| Submission and case creation | Partially evidenced | Dev1 notes describe submission and case creation. Retest latest build; attach Case ID and UI/API evidence. |
| Persistence and traceability | Partially evidenced | Dev1 documents persistence/retrieval; Dev2 reports matching Case IDs across `case.json`, `transcript.json` and `analysis.json` in 35 repeatability runs. Verify integrated UI-to-storage flow. |
| AI/STT processing and errors | Partially evidenced | Dev2 reports live timeout evidence and simulated failure tests. Verify current-build UI errors and recovery paths. |
| AI category correctness | Open issue | V2/CASE-102 reportedly returns `violence` but can omit expected `harassment`. Keep open until fixed or formally dispositioned with evidence. |
| AI summary grounding | Open issue | Dev2 evidence records unsupported details in some summaries. Retest summary accuracy against source transcripts. |
| Timestamp behaviour | Partial / decision may be needed | Malformed timing handling was reportedly improved. V3 may return a whole-clip timestamp when STT supplies one segment; confirm expected behaviour. |
| Manager-to-Auditor assignment | High-priority verification | Dev1 notes recorded the Manager workflow MVP as not implemented at that time. Confirm current status and test assignment/access isolation. |
| Auditor final decision | High-priority verification | Dev1 notes recorded final-decision persistence as incomplete at that time. Verify save, persistence after reload, and Manager visibility. |
| Wellbeing controls | Not evidenced for final sign-off | Confirm approved exposure/cooldown/SOS scope and test agreed behaviour. Do not invent thresholds. |
| Authentication and roles | Requires current-build verification | Test login, protected access, role restrictions and sign-out. Test 2FA/reCAPTCHA once required scope is confirmed. |
| UX completeness | Evidence review pending | Review authentication, Case Preview, Analysis & Decision, role visibility, loading/empty/error states and accessibility. |
| Deployment | Requires current deployment evidence | Dev1 notes indicated Code Engine testing was still planned at that time. Confirm current deployment and attach smoke-test results. |

## 4. Remaining issues and actions

| ID | Issue / gap | Priority | Owner | Required action / closure evidence |
|---|---|---|---|---|
| RI-01 | Manager assignment and Auditor case isolation | High | Dev1 / integration owner | Demonstrate assignment, correct Auditor access, and prevention of unauthorised cross-Auditor access under approved rules. |
| RI-02 | Auditor final-decision persistence | High | Dev1 + UX | Demonstrate decision entry, save, persistence after reload and visibility to authorised Manager. |
| RI-03 | V2/CASE-102 missing `harassment` category | High | Dev2 | Reproduce, correct or formally disposition; attach before/after outputs and regression results. |
| RI-04 | AI summaries include unsupported details | High | Dev2 | Run transcript-grounding checks and attach representative input/output evidence. |
| RI-05 | Integrated failure-state verification | High | Dev1 + Dev2 | Test STT/AI/storage/auth failures in current integrated build; verify no fabricated results and clear errors. |
| RI-06 | Code Engine deployment smoke test | High | Dev1 / deployment owner | Test current deployed environment, startup/configuration, dependency failures and core workflow. |
| RI-07 | Timestamp granularity / missing timestamps | Medium | Dev2 + BA/PM | Confirm expected behaviour and record decision and test result. |
| RI-08 | UX evidence and screen-state coverage | Medium | UX + BA | Review UX handoff documents against current UI and approved requirements. |
| RI-09 | Authentication, 2FA and reCAPTCHA scope | Decision pending | PM/client + BA + Dev1 | Confirm required MVP controls and update acceptance criteria. |
| RI-10 | Wellbeing limits, cooldown and SOS | Decision pending | PM/client + UX + BA | Confirm intended behaviour/values before treating them as acceptance requirements. |
| RI-11 | Human decision labels and decline/reassignment | Decision pending | PM/client + BA + UX | Confirm decision options, notification details and reassignment rules. |
| RI-12 | Auditor queue Severity column | Decision pending | BA + PM | Resolve Dashboard TBC-08. Treat Severity column as a recommendation until approved. |

**Status note:** RI-01 and RI-02 were documented as gaps in earlier Dev1 notes; recheck the latest build before saying they remain unresolved. RI-03 and RI-04 are recorded in Dev2 Sprint 3 evidence. Other items are verification gaps or decisions unless current evidence confirms a defect.

## 5. TBC / client-dependent decisions

Keep these items labelled **TBC** until the PM/client confirms them. Record decision-maker, date and source.

- Whether 2FA and reCAPTCHA are mandatory for MVP.
- Exact role-based permissions and Manager access rules.
- Case ID format and whether a user-entered Case description is required.
- Supported file formats and maximum upload size.
- Expected behaviour when AI returns no timestamps and acceptable timestamp granularity.
- Final severity scale and mandatory AI outputs.
- Exact human final-decision labels/options.
- Decline, reassignment, escalation and notification details beyond the confirmed high-level direction.
- Wellbeing exposure limits, cooldown parameters and SOS behaviour.
- Retry/escalation rules and whether raw-media opening/skipping requires tracking.
- Accessibility target, if not already agreed.
- Whether the Auditor queue should include a Severity column (Dashboard TBC-08).

A TBC is not automatically a defect. Do not mark an item failed solely because its business rule is unconfirmed.

## 6. Deferred / out-of-scope items

Do not call an item formally out of scope unless the PM/client agrees. Classify items as:
- **Confirmed MVP requirement:** must be tested against agreed acceptance criteria.
- **Confirmed defect:** current implementation conflicts with an approved requirement.
- **Evidence gap:** insufficient current-build evidence.
- **TBC / decision pending:** expected behaviour is not confirmed.
- **Deferred / out of scope:** only after PM/client approval, with impact documented.

| Item | Decision | Approver / source | Date | Impact / workaround |
|---|---|---|---|---|
| No confirmed deferrals recorded in the evidence reviewed for this draft. | Pending confirmation | PM/client to confirm | — | Do not assume open issues are out of scope. |

## 7. Final regression checklist

- [ ] Authentication: valid/invalid login, protected access, role restrictions and sign-out/session behaviour.
- [ ] 2FA/reCAPTCHA tested if confirmed in scope.
- [ ] Submission validation, supported formats/size and duplicate submission tested.
- [ ] Case creation, Case ID traceability, persistence and retrieval tested in integrated build.
- [ ] AI/STT success, timeout, malformed output and missing timestamp cases tested.
- [ ] V2/CASE-102 category regression retested and disposition recorded.
- [ ] AI summaries checked against source transcripts for unsupported details.
- [ ] Manager assignment and Auditor access isolation demonstrated.
- [ ] Auditor human decision saved and shown to authorised Manager.
- [ ] Decline/escalation notification tested against confirmed requirements.
- [ ] Wellbeing controls tested against confirmed scope and values.
- [ ] UX screens and loading/empty/error states reviewed against approved requirements.
- [ ] Current deployed Code Engine smoke tests completed and evidence linked.
- [ ] Each applicable scenario has Pass, Partial, Fail or Not Tested status.
- [ ] Each result has test steps, build/commit reference and evidence link where applicable.
- [ ] High-priority issues fixed or formally dispositioned by authorised decision-maker.
- [ ] TBC decisions and approved deferrals recorded separately from defects.
- [ ] Final handoff shared with PM and relevant developers/UX.

## 8. PM handoff summary

Suggested message:

> Hi Dat, I’ve consolidated the current requirements position and remaining issues for the final handoff. The available evidence supports proceeding with final regression, but I’m not recommending final sign-off yet. Key items to verify are Manager-to-Auditor assignment and access isolation, Auditor final-decision persistence, the Dev2 D9 category issue, unsupported AI summary details, integrated failure handling, and current Code Engine deployment evidence. I’ve separated evidence gaps and unresolved TBC decisions from confirmed issues. Could you please confirm the outstanding business decisions and advise which items, if any, are formally deferred or out of scope? I’ll update the acceptance matrix and close the handoff once the latest evidence and decisions are recorded.

**PM handoff status:** Pending — send the summary above (or equivalent) in Teams/task chat and record the date/link after it has been sent. Do not mark the Planner item complete until the handoff is actually made.

## 9. Final scope recommendation

**Ready for final regression — partial acceptance with open risks; final sign-off pending.**

Final closure requires:
1. Current integrated-build results and evidence for applicable acceptance scenarios.
2. Retest or authorised disposition of high-priority AI and workflow issues.
3. Confirmation of TBCs and any formal deferrals by the PM/client.
4. Deployment smoke-test evidence.
5. PM handoff completed and recorded.

**Document maintenance:** Update this handoff when new test evidence or PM/client decisions arrive. Replace pending statuses only when supported by evidence.
