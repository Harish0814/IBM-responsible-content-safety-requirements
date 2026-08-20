# Sprint 1 Core MVP & Client Clarifications

## IBM × RMIT Capstone — Responsible Content-Safety Infrastructure

**Task:** [REQUIREMENTS] Define Core MVP & Client Clarifications  
**Role:** Business Analyst (BA)  
**Project:** IBM × RMIT Capstone Consultancy — Responsible Content-Safety Infrastructure  
**Team:** 05-IBM-RCS Infrastructure — Team 1  
**Sprint:** Sprint 1 — Design & Bootstrap  
**Status:** Ready for PM / UX / Developers Review  

---

# 1. Purpose

This document defines the candidate Core MVP workflow for Sprint 2 based on the approved Sprint 1 Requirements Baseline.

The Core MVP is intentionally limited to the agreed Bootstrap Restyling scope:

- Team Page presentation
- Login Page visual restyling
- Preservation of existing authentication and access-control behaviour

No new authentication, moderation, AI, wellbeing, administration or unrelated functionality is included in this MVP.

The purpose of the MVP is to demonstrate one complete user-facing workflow from authentication through access to the protected Team Page while confirming that the approved visual changes do not alter existing system behaviour.

---

# 2. Candidate Core MVP Workflow

## MVP: Authenticate User and Access the Protected Team Page

The candidate Core MVP is:

> A user accesses the Login Page, authenticates using the existing authentication process, and is then able to access the protected Team Page where approved project and team information is displayed using the new visual design.

### End-to-End Workflow

1. User opens the Login Page.
2. User views the restyled Login Page.
3. User enters their existing login credentials.
4. Existing authentication and validation behaviour processes the login attempt.
5. If authentication fails, the existing validation/error state is displayed.
6. If authentication succeeds, the existing session behaviour is established.
7. The authenticated user accesses the protected Team Page.
8. The Team Page displays the approved project/team identity and team-member information.
9. Team members are presented consistently using:
   - Photo/avatar
   - Full name
   - Project role
   - Short descriptive blurb
10. The workflow ends when the authenticated user can view the protected Team Page without any change to existing access-control behaviour.

---

# 3. MVP Start Point

The MVP starts when a user opens the Login Page.

### Start Condition

- Login Page is available.
- Existing authentication mechanism is available.
- User is not required to have any new account or authentication functionality.
- The Login Page uses the approved visual restyling.

---

# 4. MVP End Point

The MVP ends when an authenticated user can access and view the protected Team Page.

### End Condition

The user can see:

- Responsible Content-Safety Infrastructure project identity
- IBM × RMIT Capstone context where applicable
- Team-member photo/avatar
- Team-member full name
- Team-member project role
- Team-member descriptive blurb

The Team Page must use the approved and consistent visual structure.

Existing authentication, authorisation, session behaviour and role-based access behaviour must remain unchanged.

---

# 5. Main Actors

## 5.1 Public User

The Public User represents an external or general user who may encounter the user-facing pages.

For this MVP:

- The Public User can encounter the Login Page.
- The Public User must not gain unauthorised access to protected Team Page content.
- Existing authentication and access-control behaviour remains the source of truth.

---

## 5.2 Authenticated Internal User

An authenticated internal user represents a user who has successfully passed the existing authentication process.

For this MVP:

- The user can access the protected Team Page according to existing permissions.
- The user can view approved project/team information.
- The user does not receive new moderation, AI or administration functionality.

---

## 5.3 Auditor

The Auditor remains the primary internal user of the broader Responsible Content-Safety Infrastructure project.

However, the MVP does not introduce or redesign Auditor workflows.

Existing Auditor authentication, authorisation and access behaviour must remain unchanged.

---

## 5.4 Manager

The Manager is an oversight stakeholder within the broader project.

The MVP does not introduce new Manager functionality.

Existing Manager permissions and role-based access behaviour must remain unchanged.

---

# 6. Initial Acceptance Criteria

The candidate MVP is considered successful when all of the following are satisfied.

### AC-01 — Login Page Restyling

The Login Page uses the approved visual design, including consistent typography, spacing, sizing and component styling.

### AC-02 — Existing Authentication Preserved

Valid and invalid login behaviour remains unchanged after the visual restyling.

### AC-03 — Existing Validation States Preserved

Existing login validation and authentication error states remain visible, readable and usable.

### AC-04 — Protected Team Page

An unauthenticated user cannot directly access protected Team Page content.

The user is redirected to the Login Page or handled according to the existing authentication behaviour.

### AC-05 — Project Identity

The Team Page clearly identifies the project as:

**Responsible Content-Safety Infrastructure**

and identifies the IBM × RMIT Capstone context where appropriate.

### AC-06 — Team Member Information

Each approved team member displays:

- Photo/avatar
- Full name
- Project role
- Short descriptive blurb

### AC-07 — Consistent Presentation

All team members use the same information hierarchy and visual structure.

### AC-08 — Missing Photo Handling

If a team member photo is unavailable, an agreed fallback treatment is displayed instead of a broken-image icon.

### AC-09 — Long Blurb Handling

Long team-member descriptions do not overlap, hide or break the page layout.

### AC-10 — Responsive and Readable

The Login Page and Team Page remain readable and usable at the supported screen sizes.

### AC-11 — No Unrelated Functionality

The MVP does not introduce:

- New authentication functionality
- Registration
- Password reset
- MFA
- New moderation functionality
- New AI functionality
- New wellbeing functionality
- Administration functionality
- Real moderation cases
- Harmful media
- Reviewer case data

### AC-12 — Access Control Preserved

Existing authentication, authorisation, session management and role-based access behaviour remain unchanged.

---

# 7. Business Assumptions

The following assumptions are used for the candidate MVP:

1. The existing authentication implementation is the source of truth for login behaviour.
2. The existing authentication and session mechanisms are already available.
3. The existing role-based access-control behaviour remains unchanged.
4. UX will determine the final visual treatment while remaining within the approved requirements.
5. The project team will provide the approved team-member names, roles, photos and blurbs.
6. The Team Page will contain only approved project/team information.
7. The Login Page is being visually restyled rather than functionally redesigned.
8. No new authentication provider or security configuration is required.
9. Supported screen sizes will be confirmed with the client/PM/UX.
10. Any unresolved requirement will be recorded as an open question rather than silently decided.
11. The candidate MVP is intended to prove the core user-facing Bootstrap Restyling workflow before broader future functionality is considered.

---

# 8. Unresolved Workflow Questions

The following questions require clarification before the workflow is treated as final.

### Q-01 — Branding

Should the Team Page use IBM branding, RMIT branding, or IBM × RMIT combined branding?

Are there approved branding assets or guidelines that UX must follow?

### Q-02 — Team Member Photo Fallback

What fallback should be used when a team member photo is unavailable?

Possible options include:

- Initials
- Generic avatar
- Approved placeholder image

### Q-03 — Long Team Member Blurbs

How should long team-member descriptions be handled?

Possible options:

- Full wrapping
- Fixed-height text area
- Truncation
- Expand/collapse

### Q-04 — Supported Screen Sizes

Which desktop and smaller screen sizes must the Team Page and Login Page support?

### Q-05 — Login Validation States

Are there any existing Login Page validation or error states that UX must explicitly represent in the design?

### Q-06 — Project Identity Wording

Should the exact wording:

**Responsible Content-Safety Infrastructure**

be used consistently throughout the Team Page?

### Q-07 — Approved Team Roles

Are there any additional approved team roles that must be displayed on the Team Page?

### Q-08 — Access Flow

After successful authentication, should the user always proceed directly to the Team Page, or should the existing application routing determine the destination?

---

# 9. Client Clarification Questions for PM

The BA will provide the following questions to the PM for consolidation with the client:

| ID | Client Clarification | Reason |
|---|---|---|
| CQ-01 | What branding treatment should be used on the Team Page? | Required for final UX direction |
| CQ-02 | What fallback should be used for missing member photos? | Required for edge-case design |
| CQ-03 | How should long member blurbs be displayed? | Required for layout decision |
| CQ-04 | What screen sizes are officially supported? | Required for responsive design |
| CQ-05 | Which existing Login validation states must be represented? | Required for UX design |
| CQ-06 | Is the project identity wording fixed? | Required for content consistency |
| CQ-07 | Are all current team roles approved for display? | Required for Team Page content |
| CQ-08 | What is the expected post-login destination? | Required to confirm the MVP workflow |

---

# 10. MVP Scope

## In Scope

- Login Page visual restyling
- Team Page visual presentation
- Project/team identity
- Team-member photos/avatars
- Team-member names
- Team-member roles
- Team-member blurbs
- Responsive presentation
- Readability and accessibility considerations
- Missing-photo handling
- Long-blurb handling
- Existing login validation/error-state presentation
- Existing authentication behaviour
- Existing session behaviour
- Existing authorisation
- Existing role-based access behaviour
- Protected Team Page access behaviour

---

# 11. MVP Out of Scope

The following are explicitly excluded from the Core MVP:

- Changing authentication logic
- Replacing authentication providers
- Changing session behaviour
- Changing security configuration
- Registration
- Password reset
- MFA
- New authentication features
- Team-member profile editing
- Administration functionality
- New moderation functionality
- New AI functionality
- New wellbeing functionality
- Real moderation cases
- Harmful media
- Reviewer case data
- Credentials
- Tokens
- Other sensitive project information

---

# 12. Traceability to Sprint 1 Requirements

The Core MVP directly uses the existing Sprint 1 requirements.

| MVP Area | Related Requirement |
|---|---|
| Project/team identity | FR-01 |
| Member photo/avatar | FR-02 |
| Member name | FR-03 |
| Member role | FR-04 |
| Member blurb | FR-05 |
| Consistent presentation | FR-06 |
| Login styling | FR-07 |
| Existing authentication | FR-08 |
| Login states | FR-09 |
| Protected Team Page | FR-10 |
| Existing access control | FR-11 |
| Missing photo | DR-01 / EC-01 |
| Long blurb | DR-02 / EC-02 |
| Multiple members | DR-03 / EC-05 |
| Readability | DR-04 |
| Visual consistency | DR-05 |
| Responsiveness | NFR-01 |
| Accessibility/readability | NFR-02 |
| Visual consistency | NFR-03 |
| Maintainability | NFR-04 |
| Project information safety | NFR-05 |

---

# 13. Handoff to PM

The PM should:

1. Review the candidate Core MVP workflow.
2. Consolidate the unresolved client clarification questions.
3. Add the questions to the appropriate client meeting agenda.
4. Record client responses.
5. Communicate confirmed decisions back to BA, UX and Developers.
6. Track any blocker or dependency created by unresolved questions.

---

# 14. Handoff to UX

UX should use this Core MVP together with the Sprint 1 Requirements Baseline to:

- Design the Login Page restyling.
- Design the Team Page.
- Represent the approved team-member information consistently.
- Define the missing-photo treatment.
- Define long-blurb behaviour.
- Confirm responsive behaviour.
- Represent existing Login validation/error states.
- Ensure the proposed design satisfies FR-01–FR-11.
- Raise any requirement conflict before development begins.

UX must not introduce functionality outside the agreed MVP scope.

---

# 15. Handoff to Developers

Developers should use the Core MVP and Sprint 1 Requirements Baseline as the implementation boundary.

Developers should:

- Implement the approved Login Page visual restyling.
- Implement the approved Team Page presentation.
- Preserve existing authentication.
- Preserve existing authorisation.
- Preserve existing session behaviour.
- Preserve existing login validation/error behaviour.
- Preserve existing role-based access behaviour.
- Preserve protected Team Page behaviour.
- Avoid introducing unrelated functionality.

Any technical constraint that prevents an MVP acceptance criterion from being satisfied should be raised with the BA and PM before implementation decisions are finalised.

---

# 16. MVP Success Definition

The Core MVP succeeds when a user can complete the following end-to-end journey:

**Open Login Page**
→ **Enter existing credentials**
→ **Existing authentication processes the request**
→ **Existing validation/error state is preserved when applicable**
→ **Successful authentication establishes the existing session**
→ **User accesses the protected Team Page**
→ **Approved project/team information is displayed**
→ **Team members are presented consistently**
→ **Existing access-control behaviour remains unchanged**

This demonstrates the core value of the Sprint 1 Bootstrap Restyling work without expanding the project into unrelated functionality.

---

## 17. Decision Status

**Candidate Core MVP:** Defined

**Workflow Start:** Login Page opened by user

**Workflow End:** Authenticated user successfully views the protected Team Page

**Acceptance Criteria:** Drafted

**Business Assumptions:** Documented

**Open Questions:** Documented

**Client Clarifications:** Prepared and shared with PM

**UX Handoff:** Ready

**Developer Handoff:** Ready

**Client Meeting Status:** Client meeting agenda was already finalised; additional BA clarification questions could not be added to the meeting agenda. PM has reviewed the situation and confirmed that this is acceptable.

**Final Client Approval:** Pending future clarification where required

---

## 18. BA Status

**Status: CORE MVP DEFINED — READY FOR PM / UX / DEVELOPER REVIEW**

The candidate Core MVP is aligned with the Sprint 1 Bootstrap Restyling requirements. All known requirements, assumptions, acceptance criteria and unresolved questions have been documented. The outstanding clarification questions have been communicated to the PM, with the PM confirming that the already-finalised client meeting does not need to be amended. 
