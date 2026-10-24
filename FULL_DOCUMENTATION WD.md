# Full Project Documentation — AccessHub, Orbit, and BusGo

**Document type:** Project documentation  
**Projects covered:** AccessHub (Login & Registration), Orbit (Project Workspace), BusGo (Bus Seat Selection)  
**Implementation style:** Standalone HTML pages using CSS and JavaScript  
**Audience:** Students, beginners, reviewers, and future developers

---

## 1. Introduction

This document describes three independent front-end website prototypes:

1. **AccessHub** — a login, registration, and password-recovery interface.
2. **Orbit** — a project-management workspace with a task board and dashboard-style layout.
3. **BusGo** — a bus journey and seat-selection interface with a fare summary and booking-confirmation form.

The projects are delivered as separate HTML files. They are not one integrated application, and the current versions do not include a shared server or database. The descriptions below distinguish visible interface features from backend capabilities that would need to be developed separately.

## 2. Project Overview

| Project | Main purpose | Main user interaction | Current data model |
|---|---|---|---|
| AccessHub | Demonstrate account registration and login flows | Register, log in, switch forms, request a demo password reset | Browser `localStorage` and `sessionStorage` |
| Orbit | Display and manage sample work tasks in a project workspace | Browse board, use task controls and filters, interact with task cards | Front-end sample/demo task data |
| BusGo | Demonstrate route information and seat selection | Choose seats, review passenger/fare details, open booking form | Front-end demo state; no confirmed external booking |

## 3. Technologies and Requirements

### 3.1 Technologies used

- **HTML5:** Provides the structure of the pages, forms, navigation, cards, and controls.
- **CSS3:** Controls layouts, colours, typography, responsive behaviour, focus states, and visual styling.
- **Vanilla JavaScript:** Handles client-side interactions and demonstration logic.
- **Browser storage:** AccessHub uses `localStorage` and `sessionStorage` for demo account/session data.
- **External font resource:** AccessHub imports Poppins from Google Fonts. If the font resource cannot load, the page falls back to local font choices.

No framework, package manager, or build step is required for these standalone HTML prototypes.

### 3.2 Requirements

- A modern browser such as Chrome, Edge, Firefox, or Safari.
- The project HTML files.
- Optional: Visual Studio Code and the Live Server extension for convenient local preview.

## 4. Recommended Folder Structure

Keep the three HTML files and this documentation in one folder:

```text
three-website-projects/
├── README.md
├── FULL_DOCUMENTATION.md
├── wd-28.html
├── wd-29.html
└── wd-30.html
```

The filenames map to the projects as follows:

- `wd-28.html` — AccessHub
- `wd-29.html` — Orbit
- `wd-30.html` — BusGo

If your local files have different names, update the filenames in this document accordingly.

## 5. Installation and Running

### Option A — Open directly

1. Save all three HTML files in the same folder.
2. Double-click `wd-28.html`, `wd-29.html`, or `wd-30.html`.
3. The selected project opens in your default browser.
4. Test the controls and forms described in the sections below.

### Option B — Use Visual Studio Code

1. Open Visual Studio Code.
2. Choose **File → Open Folder** and select the project folder.
3. Open the required HTML file.
4. If Live Server is installed, right-click the file and choose **Open with Live Server**.
5. The browser displays the page. Save changes in VS Code and refresh if needed.

### Troubleshooting

- **Page does not open:** Confirm the file ends in `.html` and is saved correctly.
- **Styles look missing:** Check that the complete HTML file, including its `<style>` block, was copied.
- **Font looks different in AccessHub:** The external Google Fonts request may be blocked or unavailable; a fallback font should be used.
- **AccessHub demo account is not found:** Register an account in the same browser profile first. Browser storage is local to that browser/profile and origin.
- **A control does not perform a real online action:** These are front-end demonstrations; backend services are not included.

---

# Part I — AccessHub

## 6. AccessHub: Purpose and Scope

AccessHub is an account-interface prototype titled **“AccessHub - Login & Register.”** It demonstrates common screens used in an account system: login, registration, and password-recovery request. It is designed to show the user flow and form validation in a browser.

**Important:** AccessHub is a demo, not a secure production authentication system. Its JavaScript stores demo passwords in browser storage. Do not use real passwords, personal information, or actual accounts with this prototype.

## 7. AccessHub: Main Features

### 7.1 Login form

The login form contains:
- Username or email field.
- Password field.
- “Remember me” checkbox.
- “Forgot Password?” control.
- Login button.
- Social-platform buttons presented as demo interface elements.
- Link to open the registration form.

The demo checks the entered login value and password against the accounts saved in browser storage. It displays a success or error message. It does not create a secure server session.

### 7.2 Registration form

The registration form asks for:
- Full name.
- Email address.
- Password.
- Confirm password.

The client-side JavaScript checks that:
- The name has at least two characters.
- The email has a basic valid format.
- The password has at least eight characters, includes a letter, and includes a number.
- The confirmation matches the password.
- The email is not already registered in the demo storage.

When these checks pass, the demo user is saved in `localStorage`, then the page returns to the login view with the email prefilled.

### 7.3 Password-recovery form

The recovery form asks for an email address and checks its basic format. It displays a message describing the demo outcome.

No password-reset email is sent. A real reset workflow requires a backend, a verified email-delivery service, secure time-limited reset tokens, and server-side validation.

### 7.4 Form navigation and feedback

Users can switch between login, registration, and recovery views. A shared message area displays success or error feedback. The layout includes labels and visible keyboard-focus styling.

### 7.5 Responsive layout

On wider screens, the interface uses a two-column layout with a welcome panel and a form panel. On smaller screens, the welcome panel is replaced by a compact mobile welcome area and the form is arranged in one column.

## 8. AccessHub: Data and Storage

The demo stores registered users under the browser storage key:

- `accessHubDemoUsers`

The demo session is stored under:

- `accessHubDemoSession`

The “Remember me” choice determines whether the session object is written to `localStorage` or `sessionStorage`. This is only a visual demonstration of session persistence; it is not equivalent to secure authentication.

### Storage limitations

- Data stays in the browser and is not shared across devices.
- Clearing browser site data may remove demo accounts and sessions.
- Users can inspect or modify browser storage.
- Passwords are stored in plain text in this demo, which is unsafe for real users.
- There is no server-side identity verification, authorization, or account database.

## 9. AccessHub: User Flow

1. Open `wd-28.html`.
2. Select **Register**.
3. Enter a name, email, password, and matching confirmation.
4. Submit the form and read the displayed result.
5. Return to **Login**.
6. Enter the registered email/name and password.
7. Optionally select **Remember me** and submit.
8. Use **Forgot Password?** to inspect the recovery demo.

## 10. AccessHub: Suggested Test Cases

| Test | Action | Expected demo behaviour |
|---|---|---|
| Empty login | Submit without credentials | An input-required message appears |
| Register valid account | Enter valid name/email/password and matching confirmation | Account is stored in browser storage and success feedback appears |
| Invalid email | Enter malformed email | Registration validation rejects it |
| Weak password | Use fewer than eight characters or omit a letter/number | Registration validation rejects it |
| Mismatched passwords | Enter different password and confirmation | Error message appears |
| Duplicate email | Register the same email twice | Duplicate-account message appears |
| Valid demo login | Use the registered email/name and password | Welcome message appears |
| Incorrect password | Use the wrong password | Login fails with an error message |
| Password recovery | Enter a valid email | Demo message appears; no email is sent |
| Small screen | Open on a narrow viewport | Layout changes to a single column |

## 11. AccessHub: Security and Production Improvements

Before using AccessHub for real accounts, implement all of the following:

1. Create a backend authentication API over HTTPS.
2. Store users in a database, not in browser storage.
3. Hash passwords on the server with a suitable password-hashing algorithm such as Argon2id or bcrypt.
4. Never return password hashes or sensitive account data to the browser.
5. Use secure session cookies or carefully managed tokens; set appropriate `HttpOnly`, `Secure`, and `SameSite` cookie attributes when using cookies.
6. Add server-side validation, rate limiting, abuse protection, and generic authentication error messages.
7. Implement verified email ownership and a secure, expiring, single-use password-reset token.
8. Connect social buttons only after implementing the relevant OAuth/OpenID Connect provider flow. The current buttons are demo controls, not working social sign-in.
9. Add logging and monitoring without logging passwords or reset tokens.
10. Test authorization and session expiry.

---

# Part II — Orbit

## 12. Orbit: Purpose and Scope

Orbit is a project-workspace dashboard titled **“Orbit — Project workspace.”** It presents a project-management interface with workspace navigation, a task board, task metadata, and a dashboard-style overview. The supplied HTML includes example project/task content intended to demonstrate the interface.

Orbit is a front-end prototype. Unless a backend is added, it does not provide shared team data, multi-user synchronization, persistent server storage, or production account management.

## 13. Orbit: Interface Components

### 13.1 Workspace sidebar

The sidebar presents the Orbit brand, a sample workspace named **Studio North**, and workspace navigation. It provides the overall information architecture for the dashboard.

### 13.2 Overview and summary area

The main workspace uses a dashboard layout to present task/project information at a glance. Summary cards and section headings help users scan work status.

### 13.3 Task board

The task board groups tasks by workflow status. The visible markup includes status categories such as:
- To do
- In progress
- In review
- Done

Task cards display example information such as a title, description, priority, tags, due date, and assignee/avatar. The sample content includes project names such as Website redesign and Brand guidelines.

### 13.4 Task controls

The interface includes controls associated with tasks and the board, such as add-task buttons and board tools. The exact effect of each control depends on the JavaScript implemented in the supplied HTML; visual controls should not be assumed to save to a server.

### 13.5 Responsive behaviour and accessibility

The CSS adapts the dashboard for different screen widths. The source includes visible focus styling for buttons, form controls, and links, as well as reduced-motion handling for users who prefer less animation.

## 14. Orbit: Typical User Flow

1. Open `wd-29.html`.
2. Review the workspace sidebar and overview.
3. Browse the task board and status columns.
4. Read task titles, descriptions, priorities, tags, assignees, and due dates.
5. Try the available board tools and task controls.
6. Resize the browser to inspect the responsive layout.

This workflow describes the prototype. A real project-management product would additionally need durable storage, authentication, permissions, and reliable collaboration features.

## 15. Orbit: Data Model (Conceptual)

The visible task cards suggest the following conceptual task fields. This is a documentation model, not a claim that a backend database schema exists.

| Field | Meaning |
|---|---|
| Title | Short name of the task |
| Description | Additional task context |
| Status | Workflow column, such as To do or In progress |
| Priority | Priority label such as low, medium, or high |
| Project | Project associated with the task |
| Tags | Labels used to categorize the task |
| Assignee | Person or avatar associated with the task |
| Due date | Target completion date |
| Comments/metadata | Small task metadata indicators shown in the interface |

## 16. Orbit: Suggested Test Cases

| Test | Action | What to verify |
|---|---|---|
| Initial rendering | Open `wd-29.html` | Sidebar, overview, board, and sample tasks render |
| Status columns | Inspect each column | Tasks are visually grouped by status |
| Task information | Inspect several cards | Titles, descriptions, priorities, tags, assignees, and due dates are readable |
| Board controls | Click each available control | The expected visible response occurs; record controls that are placeholders |
| Responsive layout | Resize to tablet and mobile widths | Content remains usable and does not unexpectedly overlap |
| Keyboard navigation | Use Tab and Enter | Focus is visible and interactive controls can be reached |
| Reduced motion | Enable OS/browser reduced-motion preference | CSS reduces transitions as specified |

## 17. Orbit: Production Improvements

To develop Orbit into a real multi-user project-management application:

1. Define user roles, teams, workspaces, projects, and task permissions.
2. Build a backend API and a database schema.
3. Persist task creation, edits, status changes, priority, due dates, and assignments.
4. Implement authentication and server-side authorization.
5. Add input validation and safe rendering of user-entered content.
6. Add audit history for important task changes.
7. Add conflict handling and synchronization for multiple users.
8. Add accessible drag-and-drop behaviour if drag-and-drop is supported.
9. Add automated tests for task creation, editing, filtering, and status transitions.
10. Provide loading, empty, success, and error states for network operations.

---

# Part III — BusGo

## 18. BusGo: Purpose and Scope

BusGo is a bus journey and seat-selection interface titled **“BusGo — Find your seat.”** It presents route details, a stylized bus illustration, seat availability states, a fare summary, and a passenger/booking confirmation interface.

The current version is a browser-side demonstration. It is not connected to a bus operator, live inventory system, payment provider, or ticketing service. A selected seat in this demo is not a confirmed reservation.

## 19. BusGo: Main Interface Components

### 19.1 Navigation rail and tabs

The narrow navigation rail contains quick-navigation controls. Tabs switch between the views available in the prototype, including the booking-oriented screen and schedule-related content.

### 19.2 Journey overview

The main workspace includes:
- A journey heading and descriptive text.
- A stylized bus illustration built from HTML and CSS.
- Route information for the origin and destination.
- Journey metadata and suggested/trending chips.

The visual bus illustration is decorative and does not represent a live vehicle location.

### 19.3 Seat map

The booking panel contains a seat map and a legend for seat states. Seat styling distinguishes available seats, selected seats, and unavailable/disabled seats. Some available seats have a separate window-seat style.

The passenger count and selected seats are intended to help users understand the selection before proceeding.

### 19.4 Fare summary

The fare area displays a summary of the selected seats and related amounts. The total is part of the demo interface and must not be treated as a live quote from a bus operator.

### 19.5 Booking form and feedback

The interface includes a modal-style form for entering booking/passenger details and a toast-style feedback area. These provide a demonstration of the confirmation flow. A real booking requires server-side seat locking, a booking record, payment integration where applicable, and a ticket/confirmation service.

### 19.6 Responsive layout

On narrow screens, the layout changes from a multi-column workspace to a stacked view. The seat map and booking panel are adjusted for mobile widths, and the CSS includes reduced-motion support.

## 20. BusGo: Typical User Flow

1. Open `wd-30.html`.
2. Review the route overview.
3. Inspect the seat availability legend.
4. Select one or more seats that are enabled.
5. Review the selected-seat and fare summary.
6. Open the booking/confirmation form.
7. Enter the requested demo details and submit.
8. Read the feedback message.

The steps demonstrate the intended interaction. They do not purchase a ticket or guarantee a seat.

## 21. BusGo: Conceptual Booking Data

The current interface implies the following information might be required in a real system:

| Field | Purpose |
|---|---|
| Origin | Starting location |
| Destination | Arrival location |
| Journey date/time | Date and departure time |
| Bus/service | Service selected by the passenger |
| Seat identifiers | Seats requested by the passenger |
| Passenger count | Number of passengers |
| Passenger details | Required details for each traveller, as defined by the operator |
| Fare | Price calculated by the operator/backend |
| Booking reference | Identifier returned after successful booking |
| Booking status | Pending, confirmed, cancelled, or failed |

This is a recommended conceptual model for a future system, not a description of a connected live database in the supplied prototype.

## 22. BusGo: Suggested Test Cases

| Test | Action | What to verify |
|---|---|---|
| Initial rendering | Open `wd-30.html` | Main workspace, route panel, seat map, and fare area render |
| Seat selection | Select an available seat | Its visual state changes and the summary updates as designed |
| Disabled seat | Try selecting a disabled seat | It cannot be selected |
| Multiple seats | Select more than one available seat | Passenger/seat and fare summary remain consistent |
| Booking modal | Open and close the form | Modal opens and can be dismissed |
| Form validation | Submit incomplete or malformed details | Invalid data is rejected or an appropriate message appears |
| Feedback | Submit valid demo details | The interface displays its demo confirmation/feedback |
| Mobile layout | Use a narrow viewport | Route and booking panels stack and remain readable |
| Keyboard access | Navigate controls with Tab | Focus remains visible and controls are reachable |

## 23. BusGo: Production Improvements

A real bus-booking application needs substantially more than the current interface:

1. Integrate a legitimate bus-operator or ticketing API.
2. Fetch routes, services, schedules, seat maps, and fares from the backend.
3. Revalidate seat availability on the server when a user proceeds to book.
4. Use atomic seat reservation/locking with expiry to prevent double booking.
5. Calculate fares on the server; never trust a client-provided total.
6. Store bookings and status changes in a database.
7. Integrate a payment provider only if online payment is required.
8. Handle payment success, failure, cancellation, retries, and webhook verification.
9. Issue a booking reference/ticket only after the backend confirms the reservation.
10. Provide cancellation/refund rules, privacy notices, and support contact details.
11. Protect passenger information and minimize data collection.
12. Test concurrency, seat-lock expiry, payment callbacks, and duplicate submissions.

---

# Part IV — Shared Quality, Maintenance, and Delivery

## 24. Shared Design and Implementation Principles

Across the three projects:
- HTML provides the semantic page structure.
- CSS controls the layout and visual presentation.
- JavaScript adds browser-side interaction where implemented.
- The pages are designed to run without a compile/build step.
- Responsive CSS supports narrower viewports.
- The projects are prototypes and should be clearly labelled as demonstrations until production services are added.

## 25. General Accessibility Checklist

Use this checklist when reviewing or improving the projects:

- All form fields have visible labels.
- Buttons have clear names and purposes.
- Keyboard focus is visible.
- Interactive controls can be reached by keyboard.
- Text and background colours have sufficient contrast.
- Error messages explain what needs correction.
- Layout remains usable when zoomed.
- Mobile content does not require unnecessary horizontal scrolling.
- Motion is reduced when the user requests reduced motion.
- Screen-reader status messages are announced appropriately.

A checklist is a review guide, not a claim that every criterion has been formally audited.

## 26. General Security and Privacy

- Do not use AccessHub to store real credentials.
- Do not enter real passenger details into the BusGo demo.
- Treat all demo data in Orbit as sample information.
- Do not publish secrets, API keys, passwords, or private data inside HTML or JavaScript.
- Any real account, task, or booking operation must be validated and authorized by a backend.
- If a backend is added, use HTTPS, server-side validation, least-privilege access, safe error handling, logging that avoids secrets, and regular dependency/security reviews.
- Publish a privacy notice before collecting real personal information.

## 27. Manual Verification Checklist

Before submitting or demonstrating the projects:

- [ ] All three HTML files open in a modern browser.
- [ ] AccessHub can switch between login, registration, and recovery views.
- [ ] AccessHub validation messages are tested.
- [ ] AccessHub is clearly identified as a demo and no real passwords are used.
- [ ] Orbit's workspace and task board render without broken layout.
- [ ] Orbit controls have been tested and any placeholders are identified.
- [ ] BusGo's route view and seat map render correctly.
- [ ] BusGo seat selection and fare summary have been tested.
- [ ] BusGo's confirmation flow is described as a demo, not a real booking.
- [ ] Each project has been checked at desktop and mobile widths.
- [ ] No browser console errors remain for the intended demo workflow.
- [ ] Documentation matches the files actually delivered.

## 28. Known Limitations

| Project | Current limitation |
|---|---|
| AccessHub | Demo users and session data are stored in browser storage; passwords are not safely hashed; no real backend, email reset, or social authentication |
| Orbit | Sample front-end workspace; no production backend, shared persistence, authentication, or real-time collaboration is established by the supplied standalone file |
| BusGo | Demo seat selection and booking UI; no live inventory, operator integration, server-side seat lock, payment processing, or issued ticket |
| All three | No automated test suite, deployment pipeline, or production monitoring is included in the standalone HTML deliverables |

## 29. Future Development Roadmap

### Phase 1 — Stabilize the prototypes
- Confirm all interactions in each HTML file.
- Fix broken controls and console errors.
- Verify responsive behaviour.
- Keep demo/sample content clearly labelled.

### Phase 2 — Define real requirements
- Specify users, permissions, workflows, validation, and expected outcomes.
- Define data retention and privacy requirements.
- Create wireframes and acceptance tests.

### Phase 3 — Backend and persistence
- Design API endpoints and database tables.
- Implement server-side validation and authorization.
- Store persistent data securely.
- Add logging, error handling, and backups.

### Phase 4 — Integrations
- AccessHub: email verification, password reset, and optional OAuth/OIDC.
- Orbit: user/team management and persistent task collaboration.
- BusGo: live route/seat inventory, booking, payment, and ticket issuance.

### Phase 5 — Testing and deployment
- Add unit, integration, accessibility, and end-to-end tests.
- Run security reviews.
- Configure production environment variables and secrets.
- Deploy with HTTPS and monitoring.
- Document backup, recovery, and support procedures.

## 30. Glossary

- **Frontend:** The part of an application that users see and interact with in the browser.
- **Backend:** Server-side logic that validates requests, enforces permissions, and handles business operations.
- **Database:** Persistent storage for application records.
- **Responsive design:** Layout that adapts to different screen sizes.
- **`localStorage`:** Browser storage that persists until cleared.
- **`sessionStorage`:** Browser storage generally limited to the current tab session.
- **Validation:** Checking that user input follows expected rules.
- **Authentication:** Verifying a user's identity.
- **Authorization:** Deciding what an authenticated user is allowed to do.
- **API:** A defined interface that allows software components to communicate.
- **Seat locking:** Temporarily reserving a seat while a booking is being completed.

## 31. Conclusion

AccessHub, Orbit, and BusGo demonstrate three common web application patterns: account forms, project task management, and seat selection/booking. Their current strength is the browser-based interface and demonstration flow. They should be treated as learning/prototype projects, not production services. To make them production-ready, each needs a clearly defined backend, secure data handling, validation, testing, and appropriate service integrations.

---

**Documentation note:** This document is based on the supplied standalone HTML files and their visible code. Recommendations for production development are guidance for future work; they do not imply that those services already exist in the current projects.
