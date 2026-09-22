# EDL-0004: Establish Reproducible Local Setup and Administration Guidance

- Status: Accepted
- Date: 2026-08-14
- Decision owner(s): Course instructor
- Application repository: `Community-TOS-Projects/event-volunteer-hub`
- Related issue(s):
  - [event-volunteer-hub#4](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/4)
- Related pull request(s): 
  - [event-volunteer-hub#7](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/7)
- Related EDL entries: N/A
- Affected files/documentation:
  - `README.md`

## Context

MeetHub was installed and run locally using its virtual-environment setup instructions. 
The application could be started, a user account could be created, and an event could be created.

During setup and exploration, several documentation gaps were identified:

- The README did not include instructions to create a Django superuser in the virtual-environment/non-Docker workflow.
- The `createsuperuser` command prompts for `Client status`, but the README does not explain what value is expected or what the field means.
- The README does not document how to access the Django administration interface.
- The repository contains the administrative capability in code, but a new maintainer cannot readily discover the workflow from project documentation.

## Decision

Document a complete local administrative setup workflow in the README.

The documented workflow must include:

```bash
python manage.py createsuperuser
```

`Client status` corresponds to the custom `Account.is_client` field.
It must explain that the `Client status` prompt accepts `True` or `False`.

For a superuser intended for project administration, enter `False`. 

```text
False
```

This field is separate from Django's `is_staff` and `is_superuser` permissions.

The documentation must also state that the Django administration interface is available at:

```text
http://127.0.0.1:8000/admin/
```

A maintainer should sign in using the superuser credentials created with `python manage.py createsuperuser`.

## Rationale

A project that runs locally but cannot be administered by a new maintainer is not operationally reproducible. 
The course emphasizes continuity across changing student cohorts, so setup and administration instructions must allow a future team to initialize, operate, inspect, and manage the application without relying on undocumented oral knowledge.

## Consequences

### Positive

- New students can create administrative accounts without guessing how to answer the custom model's `Client status` prompt.
- New maintainers can discover and use the administrative interface.
- The setup process becomes more reproducible for each semester's incoming cohort.
- The README better reflects the actual implementation.

## Follow-Up Work

- Add the superuser and admin-access instructions to the README.
- Test the instructions from a clean local clone.
- Add a short explanation of the custom `Account` model and its client-status field to developer documentation.
- Add troubleshooting guidance for common migration, database, account, and admin-login failures.
- Review all setup instructions at least once each semester as part of the project handoff process.