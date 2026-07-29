---
name: nextjs-transactional-api
description: Implement or review Next.js server APIs that change taxi-share rooms, point ledgers, deposits, refunds, or settlements. Use for mutation routes and financial-safety review.
---

# Transactional Next.js API

This MVP uses administrator-granted virtual points only. It must not implement card payments, paid top-ups, or cash refunds.

For every mutation:

1. Authenticate and authorize on the server.
2. Validate the current room and participant state transition.
3. Require and persist an idempotency key for deposits, refunds, additional debits, and settlement.
4. In one database transaction, lock or safely constrain the relevant balance, append an immutable point-ledger record, and update the related room/participant/settlement state.
5. Return a retriable, explicit result without exposing sensitive user data.

The ledger is the source of truth for balances. Never derive a new balance solely from client input. Keep recommended routes, fare estimates, and their calculation inputs traceable; never claim a route calculation when there is no provider-backed result.
