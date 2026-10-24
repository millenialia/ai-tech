# Backward Compatibility — DevMentor

## Protected surfaces

The following are considered public contracts. Changes to them require explicit justification and must not break existing consumers without a migration path.

### API routes (`packages/app/app/api/`)
- Request/response shapes are contracts — do not remove or rename fields without versioning
- HTTP status codes must remain stable for existing endpoints

### Database schema (`packages/db/`)
- Column removals require a migration with a deprecation period
- Column renames must use a two-step migration (add new → migrate data → remove old)
- Never drop a table in a single migration without prior deprecation

### Shared packages
- `packages/core` exports are used across the monorepo — do not remove or rename exports without updating all consumers
- `packages/ui` component props are a contract — breaking prop changes require a major bump

## At this stage (pre-1.0)

The project is pre-1.0. Breaking changes are acceptable but must be:
- Documented in the PR description
- Communicated to the team before merging
