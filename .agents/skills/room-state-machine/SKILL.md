---
name: room-state-machine
description: Implement or review Campus Taxi Share room and participant state transitions. Use when creating, joining, approving, closing, cancelling, checking in, handling no-shows, or completing a trip.
---

# Room state machine

Read PRD sections 5.2, 5.3, 5.5, and 10 plus `docs/agent-prd-contract.md`.

Model transitions explicitly and reject invalid requests on the server. Room states are `DRAFT`, `OPEN`, `CLOSED`, `CONFIRMED`, `IN_PROGRESS`, `SETTLEMENT_PENDING`, `COMPLETED`, `CANCELLED`, and `EXPIRED`; participant states are `APPLIED`, `APPROVED`, `DEPOSITED`, `CHECKED_IN`, `NO_SHOW`, `COMPLETED`, and `CANCELLED`.

Check at every transition:

- The requester has the correct role.
- The current state permits the action and retries are safe.
- `OPEN` is required for new applications/approvals.
- Confirmed capacity never exceeds four and departure eligibility has at least two confirmed people.
- Automatic closure at departure time and manual closure yield the PRD-defined final state.
- Cancellation/no-show paths invoke the correct ledger flow rather than directly changing a displayed balance.

Return stable conflict errors for stale or concurrent requests and add scenario coverage for happy path, invalid transition, capacity, and retry.
