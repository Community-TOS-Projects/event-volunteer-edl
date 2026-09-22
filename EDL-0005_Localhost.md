# EDL-0005: Enable Localhost Access for Local Development

- Status: Accepted
- Date: 2026-08-14
- Decision owner(s): Course instructor
- Application repository: `Community-TOS-Projects/event-volunteer-hub`
- Related issue(s):
  - [event-volunteer-hub#5](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/5)
- Related pull request(s): TBD
- Related EDL entries:
  - EDL-0001: Select MeetHub as the Initial Inherited Codebase
  - EDL-0004: Establish Reproducible Local Setup and Administration Guidance
- Affected files/documentation:
  - `config/settings.py`

## Context

During the initial local setup and evaluation of MeetHub, the application failed when accessed at:

```text
http://localhost:8000/
```

Django returned the following error:

```text
Invalid HTTP_HOST header: 'localhost:8000'.
You may need to add 'localhost' to ALLOWED_HOSTS.
```

The application configuration allowed `127.0.0.1` but did not allow `localhost`. 
Although both names commonly refer to the local computer, Django evaluates the incoming HTTP `Host` header against the configured `ALLOWED_HOSTS` list. 
This prevented a new local developer from running the application successfully when using the common `localhost:8000` development URL.

## Decision

Configure `ALLOWED_HOSTS` for the current Event Volunteer Hub development environment by allowing `127.0.0.1` and `localhost` and removing the inherited MeetHub deployment hostname.

Use:

```python
ALLOWED_HOSTS = [
    '127.0.0.1',
    'localhost',
]
```

## Rationale

The application is intended to be run locally by course instructors and changing student cohorts. 
Both `127.0.0.1:8000` and `localhost:8000` are reasonable, common local-development addresses.

Explicitly allowing `localhost` resolves the observed `DisallowedHost` error while keeping the host allowlist restricted to known current local hosts.
The project should not use a wildcard value such as `ALLOWED_HOSTS = ['*']`, because Django uses this setting as a protection against HTTP Host header attacks.

## Consequences

## Positive

- New developers can access the local application through both `http://127.0.0.1:8000/` and `http://localhost:8000/`.
- The local setup workflow is more reproducible.
- The host allowlist remains explicit rather than permitting all hosts.

### Tradeoffs

- Each new deployment domain must be deliberately added to `ALLOWED_HOSTS`.
- Future maintainers must review this setting when changing deployment platforms, domains, proxy configuration, or local-development conventions.

## Validation

After adding `localhost` to `ALLOWED_HOSTS`, the application was accessible at:

```text
http://localhost:8000/
```

## Follow-Up Work

- Add `http://localhost:8000/` and `http://127.0.0.1:8000/` to the local setup instructions in `README.md`.
- Document that a deployment hostname must be added to `ALLOWED_HOSTS` before the application is deployed under that hostname.
- Add an automated configuration check or deployment checklist item to verify that local and production hostnames are intentionally configured.