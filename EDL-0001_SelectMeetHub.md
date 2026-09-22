# EDL-0001: Select MeetHub as the Initial Inherited Codebase

- Status: Accepted
- Date: 2026-08-14
- Decision owner(s): Course instructor
- Related repositories:
  - Candidate: https://github.com/iyanuashiri/meethub
  - Target application repository: `Community-TOS-Projects/event-volunteer-hub`
- Related issue(s): N/A
- Related pull request(s): N/A
- Related EDL entries:
  - EDL-0002: Do Not Adopt React Volunteer Management System
- Affected file(s)/documentation: N/A

## Context

The course requires an open-source starting codebase for an event-based volunteer management system. 
The application should eventually help nonprofit organizations create and manage short-term community events, recruit and coordinate volunteers, and maintain volunteer rosters.

Two candidate codebases were evaluated locally:

- MeetHub, a Python/Django event-management application.
- React Volunteer Management System (React VMS), a React/Node volunteer-management interface.

MeetHub was installed and run locally. 
A user account could be created, persisted, and used to log in and explore the application. 
The evaluator was also able to create an event.

React VMS was also run locally. 
Accounts were not persistent because the evaluated application did not include a database-backed persistence layer. 
The organizer workflow did not expose a usable process to create shifts, assign volunteers to shifts, or identify shifts without volunteers. 
A volunteer account displayed no available shifts, preventing evaluation of the expected volunteer signup workflow.

## Decision

Use MeetHub as the initial inherited codebase for `event-volunteer-hub`.

The project will be treated as an inherited event-management foundation, not as a complete volunteer-management solution. 
Student teams will assess, document, stabilize, and extend the application to support nonprofit event-based volunteer coordination.

## Rationale

MeetHub provides a functioning Django application with persistent accounts, authentication, event creation, and an established database-backed application structure. 
These capabilities allow the course to focus on software engineering work that is relevant to stakeholder needs without requiring every student to first design and implement a database and persistence layer.

Although MeetHub has defects, usability problems, and documentation gaps, those issues create meaningful opportunities for students to practice maintenance, testing, documentation, and incremental enhancement of inherited software.

## Alternatives Considered

### React Volunteer Management System

Rejected as the initial inherited codebase.

The application appeared closer to the volunteer-management problem domain in its user interface, but local evaluation found no persistent account storage and no observable end-to-end workflow for organizer shift creation, volunteer assignment, open-shift visibility, or volunteer shift signup.

Adopting it would require students to design and build the database, persistence, and core scheduling functionality before delivering a usable stakeholder-facing prototype. 
Database design is not a prerequisite for the course, and student experience in this area is expected to vary.

## Consequences

### Positive

- Students inherit a functional, persistent web application rather than a front-end prototype.
- Django provides an existing ORM, migration workflow, authentication foundation, and administration interface.
- The project can focus early work on codebase assessment, testing, documentation, usability, and volunteer-domain features.
- The decision creates an authentic maintenance and continuity-learning experience.

### Tradeoffs

- MeetHub is event-management software, not a complete volunteer-management system.
- Students must extend its data model and workflows to add volunteer roles, shifts, capacity, signup, roster management, attendance, and related permissions.
- Existing defects and documentation gaps must be addressed before substantial feature development.

## Evidence

- MeetHub was run locally.
- A persistent account was created and used for login.
- An event was created through the application.
- React VMS was run locally.
- React VMS account state was not persistent.
- React VMS did not provide observable organizer or volunteer workflows needed to evaluate core shift-management behavior.

## Follow-Up Work

- Import MeetHub into `Community-TOS-Projects/event-volunteer-hub` without its Git history while preserving attribution/license information.
- Complete an inherited-codebase assessment.
- Create regression tests for the core account and event workflows.
- Document local setup, administrative access, architecture, known issues, and initial volunteer-management requirements.