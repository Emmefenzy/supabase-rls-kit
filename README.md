# Supabase RLS Kit

Practical, test-first starter patterns for PostgreSQL Row Level Security (RLS) in Supabase projects.

> **Security note:** This repository is a learning and starter toolkit, not a security certification or an automatic audit. The database's grants and RLS policies are the security boundary. TypeScript permission helpers in this package are for application UX and must never replace database authorization.

## What is included

- Small TypeScript permission utilities with unit tests.
- A sample `profiles` table migration with explicit grants and per-operation RLS policies.
- A pgTAP test example to demonstrate database-level policy testing.
- Contribution, security-reporting and issue templates.

## Requirements

- Node.js 20+
- npm
- For database examples: Supabase CLI and Docker (for a local Supabase stack)

## Quick start

```bash
npm install
npm run check
```

Build output is written to `dist/`.

## TypeScript example

```ts
import { hasPermission, type Role } from "supabase-rls-kit";

const role: Role = "editor";
const canPublish = hasPermission(role, "posts:publish");
```

These helpers are suitable for hiding or showing interface actions. Always enforce the same rule in PostgreSQL RLS policies or trusted server-side code.

## Try the database example

The sample migration and pgTAP test are in `supabase/`.

1. Install and start the Supabase CLI.
2. Run `supabase start`.
3. Review the example migration before applying it to any database.
4. Run `supabase db reset`.
5. Run `supabase test db`.

The test uses Supabase's local Postgres test environment. It is separate from the TypeScript unit tests.

## Security principles

- Enable RLS on every table exposed through the Data API.
- Review SQL grants as well as policies; policies do not remove existing grants.
- Write separate policies for `SELECT`, `INSERT`, `UPDATE` and `DELETE` where appropriate.
- Test both allowed and denied access, especially cross-user access.
- Index columns used by policy predicates where appropriate.
- Never expose a secret/service-role key in browser code.
- Review every example for your own schema, threat model and business rules.

## Project status

Early-stage starter project. APIs, examples and documentation may change before a stable release. Contributions and security reviews are welcome.

## License

MIT. See [LICENSE](LICENSE).
