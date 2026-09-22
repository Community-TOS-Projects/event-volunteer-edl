# EDL-0002: Do Not Adopt React Volunteer Management System as the Initial Codebase

- Status: Accepted
- Date: 2026-08-14
- Decision owner(s): Course instructor
- Candidate repository: https://github.com/ajitagupta/react-volunteer-management-system
- Related issue(s): N/A
- Related pull request(s): N/A
- Related EDL entries:
  - EDL-0001: Select MeetHub as the Initial Inherited Codebase
- Affected file(s)/documentation: N/A

## Context

React Volunteer Management System (React VMS) was evaluated as a possible initial codebase because its stated purpose aligned directly with event organizers, volunteers, shifts, feedback, and communication.

The application was run locally after installing Node.js. 
An organizer account and a volunteer account could be created in the user interface.

## Observations

The following limitations were found during local testing:

- Created accounts were not persistent.
- The evaluated application did not include a database-backed persistence layer.
- After creating an organizer account, no usable functionality was found for:
  - Creating shifts.
  - Assigning a volunteer to a shift.
  - Viewing shifts that had no assigned volunteers.
- After creating a volunteer account, the application showed no available shifts.
- The expected volunteer signup and assignment workflow could not be evaluated.

## Decision

Do not adopt React VMS as the initial codebase for `event-volunteer-hub`.

Use MeetHub as the initial inherited codebase instead.

## Rationale

The class requires a project foundation that students can extend meaningfully within one semester. 
React VMS would require students to build database-backed persistence and the core volunteer-shift workflow before they could produce a functioning prototype.

Database design is not a course prerequisite, and student preparation in database modeling is expected to vary. 
Selecting React VMS would therefore create a high risk that the class would spend most of the semester building foundational infrastructure instead of responding to stakeholder requirements, testing, documentation, usability, and continuity needs.

## Consequences

### Positive

- The project begins with persistent user accounts and a database-backed application foundation.
- Students can focus on incrementally extending a working event application.
- The course avoids making database architecture the hidden prerequisite for all meaningful project work.

### Tradeoffs

- MeetHub does not already implement the volunteer-shift features that initially made React VMS attractive.
- Students will need to add volunteer-specific models, workflows, permissions, and user interfaces to MeetHub.

## Evidence

- React VMS was run locally.
- Organizer and volunteer accounts were created.
- Account data did not persist.
- No end-to-end shift creation, assignment, open-shift, or volunteer signup workflow could be demonstrated.

## Review Trigger

This decision may be reconsidered if React VMS gains a maintained, documented, database-backed implementation of event creation, shift creation, volunteer signup, assignment, capacity management, and roster visibility.