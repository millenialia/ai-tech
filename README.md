# DevMentor

A mentoring marketplace for developers — connecting mentors with people looking for technical growth support.

Built as part of the AI Tech Leaders course.

## Tech Stack

- Next.js (App Router)
- TypeScript
- Tailwind CSS

## About

DevMentor is a platform inspired by Preply and Booksy that enables:
- browsing and filtering mentor profiles
- booking mentoring sessions
- managing schedules and payments

## Architecture

Monorepo with npm workspaces:

```
packages/
├── app/    # Next.js application (App Router, Tailwind, shadcn-ui, Awilix)
├── core/   # Shared business logic
├── db/     # MikroORM entities, migrations, PostgreSQL
└── ui/     # Reusable React components
```

Context and specs for AI agents live in `.ai/`.

## Getting started

```bash
npm install
npm run dev      # starts packages/app on http://localhost:3000
npm run build    # production build
npm run lint     # lint all packages
npm test         # run all tests
```
