---
name: prd-feature-delivery
description: Plan and implement a Campus Taxi Share feature from PRD.md. Use for signup, rooms, participation, points, settlement, reporting, notifications, or any new user-facing requirement that needs scope, acceptance criteria, and verification.
---

# PRD feature delivery

Read `PRD.md` and `docs/agent-prd-contract.md`. Identify the affected FR/TR IDs before editing.

1. State the smallest MVP outcome and exclusions.
2. Map the UI, server/API, data, and authorization changes.
3. Preserve relevant invariants; delegate specialized review to the matching project agent when needed.
4. Implement the smallest coherent slice, including loading, empty, error, and invalid-state behavior.
5. Verify the affected acceptance path and report the FR/TR coverage plus remaining open decisions.

Do not silently add out-of-scope real payments, identity verification, automatic participation, or provider-specific assumptions.
