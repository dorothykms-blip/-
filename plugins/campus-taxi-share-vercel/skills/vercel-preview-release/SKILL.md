---
name: vercel-preview-release
description: Prepare and verify a safe Vercel preview or production release for the Campus Taxi Share Next.js application. Use for deployment readiness, preview validation, build failures, or release checklists.
---

# Campus Taxi Share Vercel release

The application is Next.js 16 with a Vercel deployment target. Treat development, preview, and production as separate environments.

Before a deployment:

1. Inspect the changed user flow and run `npm run lint` plus `npm run build`.
2. Check that no secrets, map-provider keys, or Neon connection strings are committed.
3. Confirm environment-specific values are injected through Vercel environment variables rather than source code.
4. For any point, deposit, refund, or settlement change, require a server-side transaction and an idempotency key before release.

For preview deployments, report the intended test paths: signup, room creation, join/approval, deposit, cancellation, and settlement. Never promote a preview to production or change Vercel project settings without explicit user approval.

When a deploy fails, identify the failing build or runtime boundary, make the smallest scoped correction, rerun the relevant checks, and state what still needs Vercel-side configuration.
