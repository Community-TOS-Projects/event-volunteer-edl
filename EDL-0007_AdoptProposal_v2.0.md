# EDL-0007: Adopt Proposal v2.0 as the Event Volunteer Hub Project Direction

## Metadata

**Status:** Accepted  
**Date:** 2026-10-29  
**Decision Owner(s):** CS 349 Software Engineering class  
**Related Repository:** [event-volunteer-hub](https://github.com/Community-TOS-Projects/event-volunteer-hub)  
**Related Issue:** [event-volunteer-hub#30](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/30)  
**Related Pull Request:** [event-volunteer-hub#31](https://github.com/Community-TOS-Projects/event-volunteer-hub/pull/31)  
**Related Artifact:** [Event Volunteer Management Proposal v2.0](https://github.com/Community-TOS-Projects/event-volunteer-hub/blob/main/docs/EventVolunteerManagement_Proposal_v2.0.pdf)  
**Related EDL Entries:** EDL-0001, EDL-0002, EDL-0006

## Context

During the proposal-development phase, the class developed and iteratively refined a proposal for an open-source Event Volunteer Management Platform intended to support nonprofit and community organizations.

Proposal v2.0 represents the accepted project direction at the conclusion of that process. It describes the community problem, intended users, desired capabilities, technology considerations, risks, assumptions, and preliminary development direction.

After the proposal was developed, the project inherited the MeetHub Django codebase as its technical foundation. The inherited application already supports some proposal capabilities, partially supports others, and does not yet represent several capabilities described in the proposal.

The proposal therefore serves as a statement of intended product direction rather than a description of the current implementation.

## Decision

Adopt Event Volunteer Management Proposal v2.0 as the primary project-direction reference for Event Volunteer Hub.

The approved proposal will be preserved in the `event-volunteer-hub` repository under `docs/` and used to guide requirements analysis, capability evaluation, issue definition, prioritization, and future development.

## Rationale

Preserving the approved proposal provides future contributors with a stable record of the project goals and community needs that motivated development.

The proposal also provides a common reference for evaluating the inherited application and deciding which capabilities should be preserved, changed, added, clarified, or deferred.

Keeping the proposal as a fixed historical artifact avoids rewriting earlier decisions when new technical information becomes available. Later engineering decisions can instead document how and why implementation choices differ from recommendations contained in the proposal.

## Alternatives Considered

### Treat the proposal only as a course artifact

This would separate the proposal from the public project history and make it more difficult for future contributors to understand the intended product direction.

### Update the proposal whenever implementation decisions change

This would make the proposal reflect the current project more closely, but it would erase the historical context in which earlier decisions were made and reduce the usefulness of the proposal as an accepted baseline.

### Incorporate the proposal directly into the Engineering Decision Log

The proposal contains broader product direction, requirements, assumptions, and project context rather than a single engineering decision. Keeping it as a separate project artifact better preserves the distinct purposes of the proposal and the EDL.

## Consequences

- Proposal v2.0 becomes the accepted reference for the intended direction of Event Volunteer Hub.
- The proposal does not automatically describe the current implementation.
- Current system capabilities should be evaluated against the proposal using project evidence.
- GitHub issues may trace proposed work back to capabilities or gaps identified in the proposal.
- Technical recommendations in the proposal may be changed when new information or inherited-system constraints justify a different approach.
- Significant departures from the proposal should be documented through the Engineering Decision Log rather than by silently rewriting the approved proposal.
- Future contributors can distinguish among project goals, current capabilities, implementation work, and engineering decisions.

## Validation or Evidence

The approved Proposal v2.0 has been added to the `event-volunteer-hub` repository under `docs/`.

The project also maintains a capability-status document comparing Proposal v2.0 with the current inherited implementation, allowing contributors to distinguish between supported, partially supported, unsupported, and unresolved capabilities.

## Follow-Up Work

- Maintain the current-system capability analysis as the project evolves.
- Create or refine GitHub issues for proposal capabilities that become development priorities.
- Record significant technical decisions that modify or supersede proposal recommendations in future EDL entries.