---
name: privacy-safety-moderation
description: Review or implement personal-data, location, reporting, blocking, receipt, and analytics behavior for Campus Taxi Share. Use for signup fields, maps, chat, reports, images, logs, notifications, or data exposure decisions.
---

# Privacy and safety

Read FR-01 through FR-05, PRD section 7, and `docs/agent-prd-contract.md`.

Minimize data returned to the client and shown to other users. Do not log student numbers, school email addresses, raw locations, receipt images, balances, access tokens, or database URLs to analytics or consoles.

For reports and blocks, enforce authorization, retain an auditable moderation record, prevent blocked-user contact where applicable, and avoid exposing reporter identity. For receipts, use access-controlled storage and validate file type/size before persistence.

Treat the MVP's no-verification policy as a product boundary, not permission to weaken authorization or privacy. Include abuse, unauthorized access, and deletion/retention implications in every relevant review.
