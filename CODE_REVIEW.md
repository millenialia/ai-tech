# Code Review Guidelines — DevMentor

## Checklist

### Correctness
- [ ] Logic is correct and handles edge cases
- [ ] No silent failures — errors are surfaced appropriately
- [ ] No race conditions or unhandled async flows

### TypeScript
- [ ] No `any` types — strict mode must be satisfied
- [ ] No type assertions (`as X`) without a comment explaining why
- [ ] Types are as narrow as possible

### Architecture
- [ ] New business logic goes in `packages/core`, not `packages/app`
- [ ] Database access goes through MikroORM in `packages/db` — no raw SQL outside migrations
- [ ] Services are injected via Awilix — no `new ServiceClass()` in application code
- [ ] DRY — no duplicated logic that should be extracted

### Tests
- [ ] Every new feature has 100% unit test coverage
- [ ] New API endpoints have integration tests using testcontainers
- [ ] Tests are meaningful — not just coverage for its own sake

### Security
- [ ] No secrets, tokens, or credentials in code or comments
- [ ] User input is validated at API boundaries
- [ ] No SQL injection, XSS, or other OWASP Top 10 issues

### General
- [ ] No commented-out code
- [ ] No debug statements (`console.log`, etc.) left in
- [ ] Commit message is clear and follows the project style
