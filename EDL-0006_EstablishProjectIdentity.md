# EDL-0006: Establish Event Volunteer Hub Project Identity and Licensing

- Status: Accepted
- Date: 2026-09-22
- Decision owner(s): Course instructor
- Application repository: `Community-TOS-Projects/event-volunteer-hub`
- Related issue(s):
  - [event-volunteer-hub#1](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/1)
- Related pull request(s):
  - [event-volunteer-hub#2](https://github.com/Community-TOS-Projects/event-volunteer-hub/pull/2)
- Related EDL entries:
  - EDL-0001: Select MeetHub as the Initial Inherited Codebase
- Affected files/documentation:
  - `README.md`
  - `LICENSE`
  - `LICENSE-MIT`

## Context

MeetHub was selected as the inherited codebase for the Event Volunteer Hub project.
The initial repository import intentionally preserves the inherited source as a clear starting point before project-specific changes are introduced.
However, the new project has a different purpose, community context, development history, and long-term direction than MeetHub.
The repository therefore needs a distinct public identity while preserving the provenance and licensing requirements of the inherited source.

## Decision

Establish the repository as the Event Volunteer Hub project.

Replace the inherited MeetHub README with an Event Volunteer Hub README that describes the project purpose, current status, development workflow, and relationship to the original MeetHub project.

Use the GNU General Public License version 3 for the Event Volunteer Hub project and place the GPLv3 license text in `LICENSE`.

Preserve the original MeetHub MIT license and copyright notice unchanged in `LICENSE-MIT`.

Document in the README that Event Volunteer Hub incorporates source originally developed as MeetHub and provide a link to the original MeetHub repository.

Remove MeetHub-specific badges, screenshots, roadmap items, and project-description material that do not describe the Event Volunteer Hub project.

Do not rename internal Python or Django modules solely to remove the `meethub` name.
Internal renaming should occur only through a separate engineering decision when there is a technical or maintainability reason to justify the risk and effort.

## Rationale

The repository should clearly communicate that contributors are working on Event Volunteer Hub rather than continuing the original MeetHub project.
A distinct README and project identity reduce confusion about project goals, stakeholders, ownership, contribution expectations, and future direction.

Preserving the original MIT license and attribution maintains the provenance of the inherited source.
Using GPLv3 for the Event Volunteer Hub project establishes the licensing terms selected for the continuing project while retaining the original MeetHub notice for inherited material.

Separating public project identity from internal package renaming avoids unnecessary code churn during project initialization.
The inherited module names do not prevent the application from being developed as Event Volunteer Hub and can be reconsidered later if they create technical or maintenance problems.

## Alternatives Considered

### Continue Using the MeetHub Identity

Rejected because the project has a different purpose and development direction.
Continuing to present the repository as MeetHub would obscure the relationship between the inherited codebase and the new project.

### Retain the MIT License as the Primary Project License

Not selected because GPLv3 was chosen for the continuing Event Volunteer Hub project.
The original MeetHub MIT license is still preserved for inherited material.

### Rename All MeetHub-Labeled Code During Initial Setup

Deferred because broad internal renaming would create unnecessary risk and make the initial project transition harder to review.
User-visible or technically significant naming changes can be addressed separately when justified.

## Consequences

### Positive

- New contributors can immediately identify the repository as Event Volunteer Hub.
- The project purpose and current development status are documented independently of the inherited application.
- MeetHub provenance and the original MIT copyright and license notice remain visible.
- The project establishes a clear GPLv3 license for continuing development.
- The initial identity change remains separate from functional fixes and later feature development.

### Tradeoffs

- Some inherited code, package names, comments, and interface text may continue to contain the MeetHub name until they are deliberately reviewed.
- The repository contains more than one license file because inherited material retains its original MIT notice.
- Contributors must distinguish between project-level identity changes and later technical refactoring of inherited names.

## Validation

After implementation, verify that:

- the repository landing page identifies the project as Event Volunteer Hub;
- the README links to the original MeetHub repository and explains the inherited-code relationship;
- `LICENSE` contains the GNU GPL version 3 license;
- `LICENSE-MIT` preserves the original MeetHub MIT license and copyright notice unchanged;
- obsolete MeetHub badges, screenshots, roadmap items, and contribution language are no longer presented as current Event Volunteer Hub information; and
- the application source remains functional after the documentation and licensing changes.

## Follow-Up Work

- Update `CONTRIBUTING.md` so that contribution instructions reference the Event Volunteer Hub repository and workflow.
- Review `CODE_OF_CONDUCT.md` and replace inherited project-specific contact information with appropriate Event Volunteer Hub contact or enforcement information.
- Review user-visible MeetHub branding and create separate issues for changes that should be made in the application interface.
- Reconsider internal module or package renaming only if the inherited names create a concrete technical or maintainability problem.
