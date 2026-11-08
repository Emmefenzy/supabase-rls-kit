# Contributing

Thanks for considering a contribution to Supabase RLS Kit.

## Before opening a pull request

1. Check existing issues and pull requests to avoid duplicate work.
2. For security-sensitive changes, open an issue first and describe the threat model.
3. Keep changes focused and include tests or a clear explanation why tests are not applicable.
4. Update documentation and examples when behavior changes.
5. Never include real credentials, access tokens, customer data or production database dumps.

## Local checks

```bash
npm install
npm run check
```

For SQL changes, use a disposable local Supabase project and run:

```bash
supabase start
supabase db reset
supabase test db
```

Do not run destructive reset commands against a production project.

## Pull request checklist

- [ ] The change solves a clearly described problem.
- [ ] Tests cover the intended behavior.
- [ ] Documentation is updated.
- [ ] No secrets or private data are included.
- [ ] SQL examples state their assumptions and limitations.
