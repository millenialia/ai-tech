# DevMentor — Agent Instructions

This file is loaded automatically by all AI coding agents working in this repository.
Follow these instructions at all times.

## Project

**DevMentor** is a mentoring marketplace for developers — connecting mentors with people seeking technical growth support.
Inspired by Preply and Booksy. Built with Next.js, TypeScript, React, PostgreSQL, MikroORM, Awilix, Tailwind, shadcn-ui.

## Repository structure

```
/
├── packages/
│   ├── app/        # Main Next.js application
│   ├── core/       # Reusable business logic
│   ├── db/         # Database tools, MikroORM entities, migrations
│   └── ui/         # Reusable UI components
├── .ai/
│   ├── specs/      # Specifications (format: YYYY-MM-DD-slug.md)
│   │   ├── implemented/
│   │   └── archive/
│   ├── runs/       # AI run logs (format: YYYY-MM-DD-slug.md)
│   ├── lessons.md  # Index of lessons learned
│   └── lessons/    # Individual lesson files
├── AGENTS.md       # This file — loaded by all agents
└── CLAUDE.md       # Claude Code entry point
```

## Tech stack

- **Language:** TypeScript (strict mode)
- **Framework:** Next.js (App Router)
- **Frontend:** React, Tailwind CSS, shadcn-ui
- **Backend:** Next.js API routes
- **Database:** PostgreSQL with MikroORM
- **DI container:** Awilix
- **Package manager:** npm workspaces (monorepo)

## Rules

### Code
- Write TypeScript with strict mode — no `any`, no type assertions without justification
- Follow the DRY principle — extract shared logic to `packages/core`
- Use Awilix for dependency injection — do not instantiate services directly
- Use MikroORM for all database access — no raw SQL unless in a migration
- Every new feature must have 100% unit test coverage
- New API endpoints must have integration tests using testcontainers

### Git & CI
- Never merge a PR with failing CI checks
- Every PR must pass: build, lint, unit tests, integration tests
- Wait for all required checks to pass before merging

### Context files
- Save specs to `.ai/specs/YYYY-MM-DD-slug.md` before implementing non-trivial features
- Log AI run summaries to `.ai/runs/YYYY-MM-DD-slug.md`
- After fixing a bug or making a key decision, record the lesson in `.ai/lessons/YYYY-MM-DD-slug.md` and update `.ai/lessons.md`

### Planning
- For complex tasks: write a plan with phases and completion criteria in `.ai/specs/` before coding
- After each phase: run available checks, fix errors, update the plan, summarize progress
- Do not mark a phase complete until checks pass

### Verification
- After making changes: run lint and tests; fix all errors before finishing
- Do not skip failing checks — investigate and fix the root cause

<!-- discovery:routing-start -->
### Product discovery routing

When the task involves product discovery, writing a brief, or reviewing the backlog:
- Read `.ai/specs/product-brief.md` and `.ai/specs/research/` first
- Non-goals, business rules, and decisions in the brief are a protected contract — do not build what a non-goal excludes without an owner-approved update to the brief
- Synthetic personas from `om-synthetic-users` are hypotheses, not validated research
<!-- discovery:routing-end -->
