---
name: point-ledger-settlement
description: Implement or audit administrator point grants, deposits, returns, additional debits, and final settlement for Campus Taxi Share. Use for any point balance, transaction, receipt, disagreement, or settlement mutation.
---

# Point ledger and settlement

Read PRD sections 5.4–5.6, TR-01 through TR-03, and `docs/agent-prd-contract.md`. Use `neon_ledger_guardian` for a read-only review before risky schema or mutation changes.

Treat the ledger as authoritative. For each mutation, authenticate and authorize, validate room/participant state, receive an idempotency key, and execute balance protection, immutable ledger append, and state update in one database transaction.

- Administrator grants include issuer, recipient, amount, reason, and time.
- On confirmation, reserve the per-person estimated amount as a deposit distinct from usable balance.
- At final settlement, divide the approved actual fare by eligible participants; return surplus deposits or debit shortfalls through ledger entries.
- Do not complete settlement while a required disagreement window is open.
- Never introduce money movement, paid charging, cash refund, or client-calculated balances.

Test duplicate requests, insufficient balance, cancellation, no-show, partial return, additional debit, and concurrent settlement attempts.
