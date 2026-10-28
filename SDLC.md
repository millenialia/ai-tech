# SDLC — DevMentor

<!-- discovery:start -->
## Roles

- **Product owner** — decides what gets built and why; owns non-goals, business rules, and decisions in the product brief. On this project that is you.

## Discovery stage

Before a feature becomes a ticket it goes through discovery: a product brief is written or updated in `.ai/specs/product-brief.md` using `/om-discover`. The brief captures the problem, user needs, non-goals, business rules, and decisions.

A ticket may only enter implementation when it satisfies the **Definition of Ready** below.

## Definition of Ready

An issue is ready to implement when it has:
- A clear description of the problem or feature
- Acceptance criteria
- A linked spec (for features) in `.ai/specs/`
- Does not contradict a non-goal or active decision in `product-brief.md`

## Product decisions as a protected contract

Non-goals, business rules, and decisions recorded in `.ai/specs/product-brief.md` are a protected contract. A code change that builds what a non-goal excludes, or contradicts an active rule or decision, is a **blocker** in code review — the only accepted fix is an explicit, owner-approved update to the brief.
<!-- discovery:end -->

## Workflow overview

```
Discovery (brief) → Issue (backlog) → in-progress → PR (review) → qa → merge-queue → merged
```

## Issue lifecycle

| Label | Meaning |
|-------|---------|
| *(none)* | Backlog — not yet started |
| `in-progress` | Claimed and being worked on |
| `blocked` | Waiting on something external |

## PR lifecycle

| Label | Meaning |
|-------|---------|
| `review` | Ready for code review |
| `changes-requested` | Review found issues — author must fix |
| `qa` | Code review passed, awaiting QA |
| `qa-failed` | QA found issues — author must fix |
| `qa-approved` | QA passed |
| `merge-queue` | Approved and QA-passed — ready to merge |
| `do-not-merge` | Blocked from merging regardless of checks |

## Definition of Ready (issue)

An issue is ready to implement when it has:
- A clear description of the problem or feature
- Acceptance criteria
- A linked spec (for features) in `.ai/specs/`

## Pull Request rules

- Every PR targets `main`
- All CI checks must pass: `npm run lint`, `npm run test:unit`, `npm run build`
- Every PR requires at least one code review approval
- PRs with `needs-qa` cannot merge until `qa-approved` is set
- Never merge a PR with `do-not-merge` or `blocked` labels

## Claim protocol

When an agent starts working on an issue or PR it applies `in-progress`. It removes the label when done or when it stops. Never start work on an `in-progress` item without checking if it is actively claimed.

## Spec convention

Feature specs live in `.ai/specs/YYYY-MM-DD-slug.md`. Implemented specs move to `.ai/specs/implemented/`. Archived specs move to `.ai/specs/archive/`.
