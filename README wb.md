# Three Website Projects

This repository contains three standalone front-end website demos built with HTML, CSS, and JavaScript.

## Projects

### 1. AccessHub — Login & Register
**File:** `wd-28.html`

A responsive account interface with:
- Login form using username/email and password
- Registration form with basic input validation
- Password confirmation and duplicate-email checks
- Forgot-password demo screen
- Remember-me demo session
- Responsive layout for desktop and mobile
- Demo user/session storage in browser storage

**Important:** This is a front-end demonstration only. It stores demo credentials in browser `localStorage`, which is not secure. Do not use real passwords or deploy it as production authentication. Social login buttons are placeholders, and password recovery does not send an email.

### 2. Orbit — Project Workspace
**File:** `wd-29.html`

A project and task management dashboard with:
- Project overview cards and summary statistics
- Task board organized by status
- Task priority, project filters, and search controls
- Task cards with descriptions, tags, assignees, and due dates
- Task creation interface and board interactions
- Responsive dashboard styling

Some displayed people, projects, counts, and tasks are sample/demo data.

### 3. BusGo — Find Your Seat
**File:** `wd-30.html`

A bus journey and seat-selection interface with:
- Route and journey overview
- Bus illustration and trip details
- Seat map with available, selected, and unavailable seat states
- Passenger and fare summary areas
- Booking confirmation interface

This is a front-end demo. Unless a real backend and payment/booking service are connected, it does not create a real bus reservation or charge a payment.

## Requirements

- A modern web browser (Chrome, Edge, Firefox, or Safari)
- No package installation is required for the basic demos

## Run the websites

1. Download or clone this repository.
2. Keep the three HTML files in the same folder.
3. Open the required `.html` file in your browser:
   - `wd-28.html` for AccessHub
   - `wd-29.html` for Orbit
   - `wd-30.html` for BusGo
4. Alternatively, open the folder in Visual Studio Code and use the **Live Server** extension to preview a file.

These are standalone HTML pages, so a build step is not required.

## Suggested folder structure

```text
three-website-projects/
├── README.md
├── wd-28.html
├── wd-29.html
└── wd-30.html
```

## Technologies

- HTML5 — page structure
- CSS3 — layout, styling, and responsive design
- Vanilla JavaScript — interface interactions and demo behavior
- Browser storage — used by the AccessHub demo for local-only sample account/session data

## Limitations and security

- These projects are front-end prototypes, not complete production services.
- No backend, database, real identity provider, or verified server-side authentication is included in the described AccessHub demo.
- BusGo booking should be treated as a simulation unless connected to a real booking backend.
- Do not enter sensitive personal information or real passwords into demo forms.
- Before production use, add secure server-side validation, authentication, authorization, data persistence, error handling, and appropriate privacy/security protections.

## License

No license has been specified. Add a license file if you plan to distribute or reuse this project publicly.
