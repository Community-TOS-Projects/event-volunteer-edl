# Engineering Decision Log (EDL): Require POST Requests and CSRF Protection for Event Attendance Actions

- **Date:** November 22, 2026
- **Authors:** Benny-Hardy Deha & Gabriel Nuzzo
- **Status:** Accepted / Implemented
- **Related Issue:** [Issue #55: Require POST requests for event attendance actions (Join / Cancel Attendance)](https://github.com/Community-TOS-Projects/event-volunteer-hub/issues/55)
- **Branch:** `fix/issue-55-attendance-post`

---

## Context
In `meethub/events/templates/events/detail.html`, the "Join Event" and "Cancel Attendance" controls were previously implemented as standard `<a>` hyperlink tags issuing HTTP `GET` requests to `attend_event` and `not_attend_event` in `meethub/events/views.py`. Because neither view enforced HTTP method validation, visiting those URLs via `GET` (through browser link prefetching, bookmarks, or direct address-bar navigation) mutated database attendance records (`event.attendees.add` / `remove`) and bypassed Django's CSRF protection.

---

## Decisions Made

### 1. Enforce `@require_POST` Beneath `@login_required()` (`meethub/events/views.py`)
- **Decision:** Decorate `attend_event` and `not_attend_event` with `@require_POST` from `django.views.decorators.http`, placed directly beneath `@login_required()`.
- **Rationale:** `@require_POST` is idiomatic Django and automatically rejects `GET` requests with an `HTTP 405 Method Not Allowed` response and `Allow: POST` header before any database queries execute. Placing `@login_required()` first ensures unauthenticated users are redirected (`302`) to the login page rather than encountering a raw `405` error before authentication is checked.
- **Tradeoffs:** Users who previously bookmarked the old `/attend/` or `/not_attend/` URLs will receive a raw `405 Method Not Allowed` page rather than a redirect, which is an intentional and standard Django tradeoff to clearly signal HTTP protocol misuse to browsers and crawlers.

### 2. Replace `<a>` Tags with Block-Level CSRF-Protected `<form method="post">` Controls (`meethub/events/templates/events/detail.html`)
- **Decision:** Wrap the "Join Event" and "Cancel Attendance" buttons in `<form method="post" action="{% url ... %}">` blocks containing `{% csrf_token %}` and `<button type="submit">` elements preserving the original Bootstrap classes (`btn-lg w-100 mb-3`), without adding `d-inline`.
- **Rationale:** Both controls already span full width (`w-100 mb-3`) inside a `col-md-4` container, so keeping `<form>` as a standard block element preserves the exact UI layout while satisfying Django's `CsrfViewMiddleware`.

### 3. Scope Automated Test Updates Exclusively to `AttendEventTestView` Using `get_user_model()` (`meethub/events/tests/test_views.py`)
- **Decision:** Update `AttendEventTestView` to authenticate with the project's custom `accounts.Account` model (`email`-based login via `get_user_model()`) and add tests covering `405` rejection on `GET`, `403` rejection without a CSRF token (`Client(enforce_csrf_checks=True)`), `POST` attendance removal, and `csrfmiddlewaretoken` rendering. Leave unrelated legacy test classes in `test_views.py` that still reference `auth.User` untouched.
- **Rationale:** Isolating test modifications to `AttendEventTestView` keeps the pull request bounded and focused on Issue #55, while documenting the legacy `auth.User` vs. `accounts.Account` mismatch across unrelated test classes as separate follow-up work.

---

## Consequences
- **Positive:** Prevents accidental or unauthorized attendance mutations via `GET` requests, enforces CSRF token validation on all attendance state transitions, and provides full automated test coverage in `AttendEventTestView`.
- **Follow-Up Work:** Legacy test classes in `meethub/events/tests/test_views.py` (such as `EventListViewTest` and `EventDetailViewTest`) still reference `auth.User` instead of `accounts.Account` and should be updated in a dedicated test-suite cleanup issue.
