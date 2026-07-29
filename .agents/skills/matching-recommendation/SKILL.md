---
name: matching-recommendation
description: Implement or review traceable AI-assisted room recommendations for Campus Taxi Share. Use for candidate selection, destination-radius matching, recommendation cards, ranking, or recommendation audit data.
---

# Matching recommendation

Read PRD section 5.3.1, FR-20 through FR-22, TR-04 and TR-05, and `docs/agent-prd-contract.md`.

Use only eligible `OPEN` room data and provider-backed distance calculations. Rank with proximity to pickup, destination similarity, departure time, remaining seats, and departure urgency according to product policy.

For every recommendation, retain or return candidate room ID, calculated distance, calculation time, relevant matching inputs, and a plain-language reason. Respect the user's adjacent-destination preference and allowed radius.

Never auto-join, auto-approve, invent destination/fare information, or make a recommendation appear certain when route evidence is unavailable. Verify exact-destination, adjacent-destination opt-out, full/closed rooms, stale results, and explainability behavior.
