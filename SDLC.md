# SDLC — DevMentor

## Workflow overview

```
Issue (backlog) → in-progress → PR (review) → qa → merge-queue → merged
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
