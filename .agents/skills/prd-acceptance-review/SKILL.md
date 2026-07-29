---
name: prd-acceptance-review
description: Review a Campus Taxi Share change, branch, or release against PRD.md acceptance criteria. Use for PR review, feature-completeness checks, test planning, launch readiness, or identifying requirement gaps.
---

# PRD acceptance review

Read the requested scope in `PRD.md` and `docs/agent-prd-contract.md`. Review actual code and behavior, not intended design.

Produce a compact table with requirement ID, evidence, status, and gap. Prioritize Must requirements and cross-cutting constraints: server-side authorization, transactions, idempotency, state transitions, provider-backed maps, privacy, and Vercel environment separation.

Classify each item as pass, partial, fail, or not yet testable. For gaps, cite the responsible path or missing test and give the smallest corrective next step. Do not approve features that depend on simulated client-only balances, invented map data, or unimplemented external configuration.
