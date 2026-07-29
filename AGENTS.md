# Campus Taxi Share agent guidance

## Product boundaries

- `PRD.md` is the functional source of truth. This is a campus taxi-sharing MVP for 2–4 people.
- Sign-up collects student number, name, gender, and school email without an MVP verification flow. Handle personal and location data as sensitive.
- Points are administrator-granted virtual units only. Do not add card payments, paid user top-ups, cash refunds, or PG integrations.
- The point ledger is immutable and authoritative. Deposits, returns, additional debits, and final settlement must be server-authorized, transactional, and idempotent.
- Keep the trip state machine explicit: room and participant transitions must follow the PRD and reject invalid retries.
- Naver Map and Kakao Map must be accessed through a provider-neutral adapter. Never fabricate distance, duration, or fare values.

## Stack and commands

- Next.js 16, React 19, TypeScript, Tailwind CSS 4, shadcn/base UI components.
- Neon PostgreSQL is the planned database. Do not add another primary database without approval.
- Vercel is the deployment target. Keep Development, Preview, and Production configuration separate and put secrets only in environment variables.
- Validate changes with `npm run lint` and, for release-relevant work, `npm run build`.

## Working conventions

- Prefer narrow, mobile-first UI changes and reuse `components/ui` primitives.
- Keep data mutations in server-side code; clients may not decide balances, authorizations, or state transitions.
- Do not log personal data, raw location history, credentials, or point balances to analytics or client consoles.
- Before changing data, payments, maps, or deployment configuration, consult the matching custom agent when useful: `neon_ledger_guardian`, `map_provider_architect`, or `vercel_release_guardian`.

## Project skills

- Project-local skills live in `.agents/skills` and are automatically discoverable by Codex in this repository.
- Use `prd-feature-delivery` for feature work and `prd-acceptance-review` before release or merge decisions.
- Use the specialized skill matching the change boundary: `room-state-machine`, `point-ledger-settlement`, `map-provider-adapter`, `matching-recommendation`, `privacy-safety-moderation`, `mobile-flow-quality`, or `vercel-release-readiness`.
