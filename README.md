# Event Volunteer Hub Engineering Decision Log

This repository contains the public Engineering Decision Log (EDL) for the Event Volunteer Hub project.

The EDL preserves significant project decisions, their rationale, planning, implementation records, verification results, and project evolution. 
Its purpose is to help current and future contributors understand not only what changed, but why decisions were made.

## Using the EDL

Entries are assigned sequential identifiers and are intended to provide a long-term engineering record for the project.

An EDL entry may document:
- project direction and scope decisions
- architecture or data decisions
- implementation decisions
- defects and corrective actions
- documentation and setup decisions
- testing and verification decisions
- deployment and maintenance decisions

Entries may later be superseded by newer decisions, but previous entries remain part of the project history.

Accepted EDL entries are historical records. 
Substantive changes to an accepted decision should be documented in a new EDL that references and, when appropriate, supersedes the earlier entry. 
Minor corrections, link maintenance, and clearly identified implementation or validation follow-up may be added to existing entries.

## EDL Conventions

### Naming

Each Engineering Decision Log entry receives the next sequential identifier:

`EDL-0001`, `EDL-0002`, `EDL-0003`, ...

Use the identifier in both the document title and filename. `EDL-XXXX_CamelCase.md`

Example:

`EDL-0012_VolunteerShiftCapacity.md`

### Required Content

Each EDL should include the following metadata and decision-record sections, when applicable.

#### Metadata

- Status
- Date
- Decision owner(s)
- Related repository, issue, or pull request
- Related EDL entries

#### Decision Record

- Context
- Decision
- Rationale
- Alternatives considered
- Consequences
- Validation or evidence
- Follow-up work

Not every EDL requires every section. Include the sections needed to preserve the engineering reasoning behind the decision.

### Writing Expectations

An EDL should allow a future contributor to understand:

- what decision was made;
- why it was made;
- what alternatives were considered;
- what evidence or constraints influenced the decision;
- what consequences or follow-up work resulted.

Use concise engineering language. 
Tables, lists, code excerpts, and links are encouraged when they communicate the decision more clearly than prose.

### Changes to Existing EDLs

Accepted EDL entries are historical records.

Minor corrections, link updates, and clearly identified implementation or validation follow-up may be added.

If a substantive decision changes, create a new EDL and reference or supersede the earlier entry rather than rewriting the original history.

## Engineering Decision Log

### Project Initialization

| EDL | Decision | Status |
|---|---|---|
| [EDL-0001](EDL-0001_SelectMeetHub.md) | Select MeetHub as the Initial Inherited Codebase | Accepted |
| [EDL-0002](EDL-0002_RejectReactVMS.md) | Do Not Adopt React Volunteer Management System as the Initial Codebase | Accepted |
| [EDL-0003](EDL-0003_FixCustomUser.md) | Use the Authenticated Account Instance in Event Attendance Views | Accepted |
| [EDL-0004](EDL-0004_SetupGuidance.md) | Establish Reproducible Local Setup and Administration Guidance | Accepted |
| [EDL-0005](EDL-0005_Localhost.md) | Enable Localhost Access for Local Development | Accepted |
| [EDL-0006](EDL-0006_EstablishProjectIdentity.md) | Establish Event Volunteer Hub Project Identity and Licensing | Accepted |

## Related Repository

Application repository: [event-volunteer-hub](https://github.com/Community-TOS-Projects/event-volunteer-hub)