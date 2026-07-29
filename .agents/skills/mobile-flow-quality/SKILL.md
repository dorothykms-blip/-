---
name: mobile-flow-quality
description: Build or verify mobile-first Campus Taxi Share user flows. Use for App Router pages, forms, cards, status screens, accessibility, responsive behavior, or end-to-end MVP acceptance checks.
---

# Mobile flow quality

Read the relevant PRD screen flow in section 6 and `docs/agent-prd-contract.md`. Reuse existing components before adding new UI primitives.

For every changed flow, cover:

1. First-time/incomplete-profile gating.
2. Loading, empty, validation, unauthorized, and server-conflict states.
3. Mobile viewport, keyboard, touch-target, and accessible-label behavior.
4. The displayed room/participant status matching server-authoritative state.
5. Clear, non-misleading presentation of estimated versus actual fares and point deposits.

Manually exercise the nearest full scenario: signup, create room, browse/recommend, apply/approve, deposit, gather/no-show, actual-fare agreement, and settlement completion. Do not present mock values as live route or payment results.
