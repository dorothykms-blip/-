# Campus Taxi Share engineering contract

Read this file with `PRD.md` before changing a user flow, mutation, schema, integration, or release configuration.

## MVP boundaries

- Support 2–4 passengers. A room needs at least 2 confirmed participants to depart.
- Sign-up stores student number, name, gender, and school email; MVP has no phone, student-ID, or school-email verification.
- Points are administrator-granted virtual units. Exclude card payments, paid top-ups, cash refunds, and PG integration.
- Treat personal data, raw location data, receipt images, and point balances as sensitive.

## Invariants

- Enforce authorization, balance checks, and state changes on the Next.js server.
- Persist point grants, deposits, returns, additional debits, and settlement as immutable ledger entries inside a database transaction.
- Require an idempotency key for every deposit, return, additional debit, and settlement execution.
- Prevent applications or approvals for non-`OPEN` rooms, more than four confirmed people, and departure with fewer than two confirmed people.
- Map results must come from a provider-backed calculation. Keep map providers behind a normalized adapter and never invent distance, duration, or fare values.
- AI recommendations must be explainable, traceable, and require an explicit user join action; they never auto-join or auto-approve a user.
- Keep Vercel Development, Preview, and Production settings separate. Secrets exist only in environment variables.

## Required verification

- Run `npm run build` for release-relevant changes.
- Run the relevant focused tests when they exist; otherwise document the manual scenario exercised.
- Validate the affected PRD acceptance criteria, especially cancellation, no-show, retry, and concurrent-request behavior for mutations.
