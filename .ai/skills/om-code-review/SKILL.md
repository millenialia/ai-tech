# om-code-review — DevMentor overrides

Apply these rules IN ADDITION to the base om-code-review checklist.

## DevMentor-specific checks

### Dependency Injection (blocker)
- Services MUST be registered in the Awilix container and injected via constructor — never instantiated directly with `new ServiceClass()`
- API route handlers MUST receive services through the DI container, not import them directly

### Database access (blocker)
- All database access MUST go through MikroORM repositories in `packages/db`
- Raw SQL is only allowed inside migration files — never in application code

### Package boundaries (major)
- Business logic MUST live in `packages/core`, not in `packages/app`
- UI components shared across pages MUST live in `packages/ui`
- Direct imports across package boundaries are not allowed — use the published package exports

### TypeScript (blocker)
- No `any` types — the project runs in strict mode
- No type assertions (`as X`) without an inline comment explaining why it is safe

### Test coverage (major)
- Every new feature must have 100% unit test coverage
- New API endpoints must have integration tests using testcontainers
