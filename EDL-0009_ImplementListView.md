# EDL-0009: Implement List View option in Explore Events
- Status: Not Accepted
- Date: 2026-10-29
- Decision Orders: Marlon Hernandez Vides and Aidan Knecht 
- Related repositories: `event-volunteer-hub`
- Related issue: #22
- Related pull request(s): N/A
- Related EDL entries: N/A
- Affected file: 'list_of_events.html'

## Context
In the Trending Events section of the Explore Events page, there is a list and grid viewing option. The default is this grid but the 'list' option does not work.

## Decision
We decided to add a functional list view that changes the layout of the events. The new layout makes the events more compacts and are stacked instead of next to each other. Events are wider and trimmed to fill a row.

## Rationale
The new list view provides a more concise way for users to explore events. Information is easier to retain and maneuver.

## Consequences
- a new list view that successfully toggles between both views

## Validation / Evidence
- the new list view has been confirmed locally on both machines 
- the buttons work accordingly and toggle appropirately
- extended text does not overflow the field

## Follow Up Work
- the views need to be adjusted to be readable across all screens
- future accessibility to event grid needs to be translated to lists as well
