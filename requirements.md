# SPRINT 1 REQUIREMENTS BASELINE

## IBM × RMIT Capstone — Responsible Content-Safety Infrastructure

**Task:** [REQUIREMENTS] Create Sprint 1 Requirements Baseline
**Role:** Business Analyst (BA)
**Project:** IBM × RMIT Capstone Consultancy — Responsible Content-Safety Infrastructure
**Team:** 05-IBM-RCS Infrastructure — Team 1
**Sprint:** Sprint 1 — Design & Bootstrap
**Status:** Ready for PM / UX / Developers Review
**Requirements change status:** No requirement changes identified; existing requirements have been re-baselined for Sprint 1.

---

# 1. Problem Statement

The IBM × RMIT Responsible Content-Safety Infrastructure project requires a clear and consistent project-facing Team Page and Login Page as part of the Bootstrap Restyling work.

The Team Page must clearly communicate the confirmed project identity and approved team-member information. The Login Page must receive an approved visual restyling while preserving all existing authentication, session, validation and access-control behaviour.

The purpose of this requirements baseline is to provide UX, Developers and Testers with clear and testable requirements for the Team Page and Login Page without expanding the task into unrelated AI, wellbeing, moderation or authentication functionality.

The broader project is a Responsible Content-Safety Infrastructure initiative. This specific requirements task is limited to the agreed Bootstrap Restyling scope.

---

# 2. Project Users and Stakeholders

## 2.1 Public User

The Public User represents an external or general user who may encounter the project's user-facing pages.

For this Bootstrap Restyling task, the Public User is **not being given new functionality**. The role is documented to establish the user context and to ensure that protected Team Page information is not exposed to unauthenticated users.

The Public User must not gain access to protected Team Page content without satisfying the existing authentication and access-control behaviour.

---

## 2.2 Auditor — Primary Internal User

The Auditor is the **primary internal user of the broader Responsible Content-Safety Infrastructure project**, as identified in the client-approved project proposal.

The Auditor role is important to the overall project context because the broader platform includes a human-in-the-loop review layer.

However, this Bootstrap Restyling task does **not** introduce or redesign Auditor workflows.

For this task:

* Existing Auditor authentication and authorisation behaviour must remain unchanged.
* No new Auditor moderation functionality is being added.
* No real moderation cases or harmful media are displayed on the Team Page.
* The Team Page must contain only approved project/team information.

---

## 2.3 Manager / Supervisor

The Manager / Supervisor is a secondary stakeholder within the broader project.

For this Bootstrap Restyling task:

* Existing Manager access and permissions must remain unchanged.
* No new Manager functionality is being introduced.
* The Team Page must not expose sensitive moderation, reviewer or operational information.
* Existing role-based access behaviour must be preserved.

---

# 3. Purpose of This Requirements Baseline

This baseline provides:

* Clear Team Page requirements.
* Clear Login Page styling requirements.
* Testable functional requirements.
* Display and validation rules.
* Non-functional requirements.
* Edge cases.
* Scope boundaries.
* User and stakeholder context.
* Assumptions and open questions.
* Acceptance criteria.
* Traceability and handover information.

UX should use this baseline when developing the Team Page and Login Page design.

Developers should implement only the agreed styling and presentation scope.

Testers should use the acceptance criteria and edge cases for verification.

---

# 4. Scope

## 4.1 In Scope

The following items are in scope:

* Team Page content structure.
* Confirmed project identity display.
* Team member photo/avatar display.
* Team member name display.
* Team member role display.
* Team member descriptive blurb.
* Consistent Team Page member presentation.
* Login Page visual restyling.
* Login control typography, spacing, sizing and component styling.
* Responsive and readable presentation.
* Handling missing member photos.
* Handling long member blurbs.
* Preservation of existing authentication behaviour.
* Preservation of existing session behaviour.
* Preservation of existing login validation/error states.
* Preservation of existing authorisation and role-based access behaviour.
* UX validation against FR-01–FR-11 before development begins.

---

## 4.2 Out of Scope

The following items are outside the scope of this task:

* Changing, replacing or redesigning existing authentication logic.
* Changing login/session behaviour.
* Changing authentication providers.
* Changing security configuration.
* Adding registration.
* Adding password reset.
* Adding MFA.
* Adding new authentication functionality.
* Adding unrelated Team Page functionality.
* Editing team member profiles through the Team Page.
* Administration functionality.
* Building new moderation functionality.
* Implementing new AI functionality.
* Implementing new wellbeing functionality.
* Displaying real moderation cases.
* Displaying harmful media.
* Displaying reviewer case data.
* Displaying credentials, tokens or other sensitive project information.

The task remains limited to **Bootstrap Restyling of the Team Page and Login Page**.

---

# 5. Functional Requirements

## FR-01 — Project / Team Identity

**Requirement:**

The Team Page shall clearly identify the project as **"Responsible Content-Safety Infrastructure"**.

If IBM, RMIT or IBM × RMIT branding is used, the visual treatment shall follow the final branding direction approved by the relevant project/client stakeholders.

**Acceptance / Validation:**

The confirmed project name is visible on page load and is visually distinguishable from member information.

Exact branding treatment remains subject to the approved project/client direction.

---

## FR-02 — Member Photo

**Requirement:**

Each team member shall have a photo/avatar area.

**Acceptance / Validation:**

A valid image is displayed when available; a broken image is not displayed when the image is missing.

---

## FR-03 — Member Name

**Requirement:**

Each team member shall have their full name displayed.

**Acceptance / Validation:**

The name is clearly associated with the correct member.

---

## FR-04 — Member Role

**Requirement:**

Each team member shall have their assigned project role displayed clearly.

The roles displayed should be based on the team roles identified in the client-approved project proposal and the final confirmed team information.

**Acceptance / Validation:**

The role is visible and clearly associated with the correct member.

No additional or unconfirmed role information should be introduced without project/team confirmation.

---

## FR-05 — Member Blurb

**Requirement:**

Each team member shall have a short descriptive blurb.

**Acceptance / Validation:**

The blurb is readable and does not obscure or overlap other member information.

---

## FR-06 — Consistent Member Presentation

**Requirement:**

Member information shall use a consistent visual structure across all members.

**Acceptance / Validation:**

Photo, name, role and blurb follow the same hierarchy and layout pattern.

---

## FR-07 — Login Styling

**Requirement:**

The Login Page shall be visually restyled to align with the approved project visual design.

**Acceptance / Validation:**

Login controls have consistent typography, spacing, sizing and component styling.

---

## FR-08 — Existing Authentication

**Requirement:**

The restyling shall preserve existing authentication logic and session behaviour.

**Acceptance / Validation:**

Valid and invalid login behaviour remains unchanged after styling work.

---

## FR-09 — Login States

**Requirement:**

Existing validation and authentication error states shall remain usable and visually readable.

**Acceptance / Validation:**

Validation or authentication errors remain visible and understandable without changing their underlying behaviour.

---

## FR-10 — Existing Team Page Access Behaviour

**Requirement:**

The restyling shall preserve the existing access behaviour for the Team Page.

If the existing application protects the Team Page from unauthenticated users, that protection must remain unchanged.

**Acceptance / Validation:**

Styling changes must not expose protected Team Page content or bypass the existing authentication flow.

No new access-control logic is introduced as part of this restyling task.

---

## FR-11 — Preserve Existing Access Control

**Requirement:**

Login styling changes shall not alter existing authentication, authorisation, session management or role-based access behaviour.

This requirement is a **preservation constraint**, not a requirement to introduce new access-control functionality.

**Acceptance / Validation:**

Existing authentication, session and role-based access behaviour remains unchanged after the styling update.

Any existing access-control rules must continue to operate as they did before the restyling work.

---

# 6. Display & Validation Rules

| ID    | Scenario         | Required Behaviour                                                                                                                              |
| ----- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| DR-01 | Missing photo    | Use an agreed placeholder/avatar/initials treatment. Do not display a broken-image icon or collapse the member layout.                          |
| DR-02 | Long blurb       | Long text must not overlap, hide or break the layout. UX should define a consistent treatment such as controlled height, wrapping or expansion. |
| DR-03 | Multiple members | All members must follow the same information hierarchy and visual structure.                                                                    |
| DR-04 | Readability      | Text, controls and member information must remain readable at supported screen sizes.                                                           |
| DR-05 | Consistency      | Login and Team Page styling should use the same approved visual language unless UX documents a reason for a difference.                         |

---

# 7. Non-Functional Requirements

## NFR-01 — Responsiveness

The Team Page and Login Page should remain usable on supported desktop and smaller screen sizes.

## NFR-02 — Accessibility / Readability

Labels, headings, buttons and member information should be clear and readable.

## NFR-03 — Visual Consistency

Shared typography, spacing and component styling should be consistent across the two pages.

## NFR-04 — Maintainability

Styling changes should reuse the existing project structure where practical and avoid unnecessary changes to application logic.

## NFR-05 — Project Information Safety

The Team Page shall contain only approved team/project information and shall not display real moderation cases, harmful media, reviewer case data, credentials, tokens or other sensitive project information.

---

# 8. Edge Cases

| ID    | Edge Case                               | Expected Result                                                                                                                                                     |
| ----- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| EC-01 | Missing member photo                    | Display agreed fallback; no broken image.                                                                                                                           |
| EC-02 | Very long member blurb                  | Content remains readable and does not break the page layout.                                                                                                        |
| EC-03 | Invalid login                           | Existing validation/error behaviour remains functional and readable.                                                                                                |
| EC-04 | Empty login fields                      | Existing validation behaviour remains functional and readable.                                                                                                      |
| EC-05 | Several team members                    | All members remain consistently presented without unintended overlap.                                                                                               |
| EC-06 | Unauthenticated direct Team Page access | Existing authentication/access-control behaviour continues to prevent protected content from being exposed. No new access-control logic is introduced by this task. |

---

# 9. Acceptance Criteria

The requirements baseline is satisfied when:

* The Team Page clearly displays the confirmed project name **Responsible Content-Safety Infrastructure**.
* Any IBM, RMIT or IBM × RMIT branding follows the final approved branding direction.
* Each team member displays a photo/avatar, full name, role and short blurb.
* Team member information uses a consistent visual hierarchy.
* Team member roles reflect the confirmed project/team information.
* Missing photos have a defined fallback and do not produce broken-image UI.
* Long blurbs do not break, overlap or obscure the page layout.
* Login Page styling is implemented according to the approved UX design.
* Existing authentication logic and session behaviour are not changed as part of this task.
* Existing login validation/error behaviour remains functional and readable.
* Existing authentication, authorisation and role-based access behaviour is preserved.
* The pages remain usable at supported screen sizes.
* UX design has been reviewed by the BA against these requirements before development begins.
* Existing Team Page access protection, where applicable, remains functional and protected content is not exposed through the restyling changes.

---

# 10. Assumptions

1. The existing authentication implementation is the source of truth for login behaviour.
2. The existing authentication and access-control implementation is the source of truth for protected-page behaviour.
3. The UX designer will determine the exact visual treatment, component layout and fallback presentation, provided the requirements are satisfied.
4. The team member information supplied by the project team is the source of truth for names, roles and blurbs.
5. The team roles listed in the client-approved project proposal provide the current project-role baseline.
6. Exact IBM, RMIT or IBM × RMIT branding treatment will follow the final approved branding direction.
7. Existing authentication, session and role-based access behaviour is not being redesigned as part of this task.
8. The Team Page will contain only approved project/team information.
9. No new moderation, AI, wellbeing or administration functionality is introduced through this task.
10. The final visual design must remain consistent with the agreed project direction.
11. Any unresolved requirement is recorded as an open question rather than being silently decided.

---

# 11. Open Questions / Client Clarifications

The following questions remain open for PM / UX / Client confirmation:

1. Should the Team Page use IBM, RMIT, or IBM × RMIT branding, and are there approved branding assets/guidelines that UX must follow?
2. What image/avatar fallback should be used when a member photo is unavailable?
3. Should long blurbs wrap fully, be truncated, or use an expandable treatment?
4. Which screen sizes are considered supported for this project?
5. Are there any existing Login Page validation states that UX needs to explicitly design?
6. Should the project/team identity wording use exactly **"Responsible Content-Safety Infrastructure"** everywhere on the Team Page?
7. Are there any additional team roles or member information that need to be confirmed before UX finalises the design?

These questions should be confirmed before any unresolved decision is treated as final.

---

# 12. Requirement Traceability

| Requirement   | Owner / Reviewer | Design Evidence                          | Implementation | Verification |
| ------------- | ---------------- | ---------------------------------------- | -------------- | ------------ |
| FR-01–FR-06   | UX               | Team Page design                         | Developer      | Tester       |
| FR-07–FR-09   | UX               | Login styling/states                     | Developer      | Tester       |
| FR-10         | BA + UX          | Existing Team Page access behaviour      | Developer      | Tester       |
| FR-11         | BA + UX          | Existing access-control boundary         | Developer      | Tester       |
| DR-01–DR-05   | UX               | Display rules                            | Developer      | Tester       |
| EC-01–EC-05   | UX + BA          | Edge-case treatment                      | Developer      | Tester       |
| EC-06         | BA + Developer   | Existing access-control behaviour        | Developer      | Tester       |
| NFR-01–NFR-05 | UX + Developers  | Responsive/accessibility/design evidence | Developer      | Tester       |

---

# 13. Sprint 1 Definition of Done

The Sprint 1 Requirements Baseline is complete when all of the following are satisfied:

* [x] Problem statement is reflected in the requirements.
* [x] Public User is documented.
* [x] Auditor is documented as the primary user of the broader project.
* [x] Manager / Supervisor is documented.
* [x] Initial functional requirements are specific and testable.
* [x] In-scope items are documented.
* [x] Out-of-scope boundaries are documented.
* [x] Main assumptions and edge cases are identified.
* [x] Existing authentication and access-control preservation requirements are documented.
* [x] Branding remains subject to the appropriate approval where not yet confirmed.
* [x] Requirements document is prepared to be shared with PM, UX and Developers.

**Important:** The checklist confirms documentation coverage. It does not introduce new product functionality into the Bootstrap Restyling task.

---

# 14. BA Handover

## Handoff to PM

The PM should use this document as the current Sprint 1 requirements baseline and coordinate the outstanding clarification questions.

The PM should ensure that unresolved branding, display and workflow decisions are confirmed before they are treated as final requirements.

## Handoff to UX

UX should use this document as the baseline for the Team Page and Login Page design.

The Team Page should reflect the confirmed **Responsible Content-Safety Infrastructure** project identity and the confirmed project/team information.

UX should:

* Follow the final approved branding direction.
* Use the confirmed team roles and member information.
* Define the visual treatment for missing photos.
* Define the treatment for long member blurbs.
* Design relevant Login Page validation/error states without changing their underlying behaviour.
* Flag any requirement that cannot be represented in the proposed design before development begins.

## Handoff to Developers

Developers should implement only the agreed styling scope.

Developers must preserve:

* Existing authentication.
* Existing authorisation.
* Existing session behaviour.
* Existing login validation/error behaviour.
* Existing role-based access behaviour.
* Existing Team Page access behaviour.

Developers must not introduce new authentication, authorisation or unrelated Team Page functionality as part of this restyling task.

If an existing access-control behaviour is unclear, Developers should raise the issue with the BA/PM rather than introducing new rules independently.

## Handoff to Testers

Testers should use:

* FR-01–FR-11
* DR-01–DR-05
* NFR-01–NFR-05
* EC-01–EC-06
* Acceptance Criteria

as the basis for independent verification.

Testing should confirm that styling changes do not unintentionally change existing authentication, session or access-control behaviour.

---

# 15. BA Design Validation

**Reviewer:** BA
**Design reviewed:** To be completed after UX produces the design
**Validation status:** Pending UX design

The BA will review the UX design against:

* FR-01–FR-11
* DR-01–DR-05
* NFR-01–NFR-05
* EC-01–EC-06

before development approval is given.

The BA will specifically verify:

* Confirmed project identity is represented correctly.
* Team roles and member information match the confirmed project information.
* Branding follows the final approved direction.
* Login styling does not alter existing authentication behaviour.
* Existing Team Page access protection is preserved.
* No new functionality has been introduced outside the agreed scope.

**BA Decision:** Pending UX design review.

**BA Status:** REQUIREMENTS READY FOR PM / UX REVIEW

---

# 16. Baseline Status

**Requirements changed since previous baseline:** No functional scope changes identified.

**Purpose of this update:** Re-baseline the existing requirements for Sprint 1 and clarify the distinction between approved project information, existing-system constraints and items requiring confirmation.

**Current scope:** Team Page + Login Page Bootstrap Restyling.

**Confirmed project identity:** Responsible Content-Safety Infrastructure.

**Branding status:** Exact IBM, RMIT or IBM × RMIT branding treatment remains subject to the final approved direction.

**Team-role status:** Roles are based on the team structure identified in the client-approved Project Proposal & Sprint 1 Plan.

**Access-control status:** Existing authentication, authorisation, session and Team Page access behaviour must be preserved; no new access-control functionality is introduced by this task.

**Next BA activity:** Review UX design against FR-01–FR-11 and complete BA design validation before development.
