---
name: vercel-environment-audit
description: Audit Vercel environment separation and runtime configuration for the Campus Taxi Share service. Use when adding environment variables, Neon access, map APIs, analytics, or deployment configuration.
---

# Vercel environment audit

Classify each configuration value before changing it:

| Class | Handling |
| --- | --- |
| Public client configuration | Use `NEXT_PUBLIC_` only when exposure is intentional. |
| Server secret | Keep server-only; never expose through a client bundle. |
| Environment-specific endpoint or database URL | Keep separate Development, Preview, and Production values. |
| Map API credential | Use the least-privileged provider credential and document allowed origins or server-side usage. |

Required checks:

- Neon/PostgreSQL access must be server-side and use the target environment's connection details.
- Do not place user personal data, point balances, or raw location history in Vercel Analytics events.
- Map-provider access must remain behind an application adapter so Naver and Kakao can be swapped.
- A missing secret must result in a clear server-side configuration error, not a silent client fallback.

Do not invent variable names or create Vercel secrets. Propose the minimum variable contract and ask for approval before any external Vercel change.
