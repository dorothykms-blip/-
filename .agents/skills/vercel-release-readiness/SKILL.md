---
name: vercel-release-readiness
description: Prepare, review, and validate a Campus Taxi Share Next.js release on Vercel. Use for deployment configuration, preview checks, environment variables, build failures, release go/no-go, or production promotion planning.
---

# Vercel release readiness

Read TR-06 and TR-07 plus `docs/agent-prd-contract.md`; use `vercel_release_guardian` for an independent go/no-go review.

Keep Development, Preview, and Production database and integration settings separate. Secrets, Neon credentials, and privileged map credentials belong only in environment variables and server-side code.

Before release:

- Run `npm run build`; run lint when ESLint is configured.
- Check that no secret or personal data is committed or sent to analytics.
- Verify affected core scenarios, especially server-side point mutations and idempotent retries.
- Confirm provider failures and missing configuration produce safe, actionable behavior.

Use preview deployment for validation. Do not deploy to production, change Vercel configuration, or rotate secrets without explicit user approval.
