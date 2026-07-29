---
name: map-provider-adapter
description: Build or review the provider-neutral Naver Map or Kakao Map integration for place search, route distance, duration, and taxi-fare estimates. Use when adding maps, route APIs, location search, or fare estimation.
---

# Map provider adapter

Read FR-10 through FR-15, TR-08, and `docs/agent-prd-contract.md`. Ask `map_provider_architect` to review provider boundaries when the integration is new or changing.

Define normalized domain inputs and outputs before calling a provider: place, coordinates, route distance, duration, fare estimate, calculation time, provider, and source data needed for traceability.

- Keep SDK calls and credentials behind a server-safe adapter.
- Keep UI code provider-agnostic and make the adapter replaceable.
- Surface unavailable/failed estimates honestly; never generate a synthetic route, duration, or fare.
- Use explicit user consent and minimal retention for current-location use.
- Keep public browser keys separate from server secrets and document their exposure boundary.

Verify the provider response mapping, failure handling, and a provider-swap seam rather than hard-coding a vendor across the application.
