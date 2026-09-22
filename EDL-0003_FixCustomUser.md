# EDL-0003: Use the Authenticated Account Instance in Event Attendance Views

- Status: Accepted
- Date: 2026-08-14
- Decision owner(s): Course instructor
- Application repository: `Community-TOS-Projects/event-volunteer-hub`
- Related issue(s):
  - [event-volunteer-hub#3](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/3)
- Related pull request(s): TBD
- Related EDL entries:
- Affected files/documentation:
  - `meethub/events/views.py`

## Context

During local evaluation of MeetHub, a user created an event and then attempted to join that event. 
The event-join action failed with a Django traceback.

The traceback identified the failure in `meethub.events.views.attend_event`:

```text
Manager isn't available; 'auth.User' has been swapped for 'accounts.Account'
```

The original implementation imported Django's default user model:

```python
from django.contrib.auth.models import User
```

It then attempted to retrieve the attendee with:

```python
attendee = User.objects.get(username=request.user)
```

## Investigation

The project configuration sets:

```python
AUTH_USER_MODEL = 'accounts.Account'
```

This means the project uses a custom `Account` model instead of Django's default `auth.User` model.

The custom `Account` model uses email as its `USERNAME_FIELD` and does not use the default `username` field. 
Therefore, the original query had two problems:

- It referenced Django's inactive/swapped-out default `User` model.
- It queried by `username`, which is not the custom account model's login field.

In an authenticated view, `request.user` is already the active authenticated `Account` instance. 
A second database query was unnecessary.

## Decision

Use `request.user` directly as the attendee in the `attend_event` and `not_attend_event` views.

Remove the incorrect import of Django's default `User` model.

## Rationale

`request.user` is already the authenticated `Account` instance configured by the application.
Using it directly avoids referencing Django's inactive default `User` model and avoids an unnecessary database query.

## Implementation

Remove:

```python
from django.contrib.auth.models import User
```

Replace this line in both `attend_event` and `not_attend_event`:

```python
attendee = User.objects.get(username=request.user)
```

With:

```python
attendee = request.user
```

## Consequences

### Positive

- Event attendance uses the project's configured custom account model.
- The implementation avoids an unnecessary database query.
- The event-join workflow now functions during local testing.
- The code aligns with Django's custom-user-model configuration.

## Validation

After the change:

- The diagnostics check reported no errors.
- The event-join workflow completed successfully in the browser.
- The evaluator confirmed that the previously failing event-join operation worked.

## Follow-Up Work

- Add automated regression tests for joining an event.
- Add automated regression tests for leaving an event.
- Review the repository for other imports of `django.contrib.auth.models.User`.
- Document the custom `Account` model and email-based authentication design.

