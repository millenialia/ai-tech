# Product brief — DevMentor
_Last updated: 2026-10-28. Owner: founder A (Oliwia). Mode: own._

---

## Decision summary

Build a text-only marketplace where working developers book 25- or 50-minute sessions with senior engineers, pay up front, and get answers over text — no video, no ratings, trust from public work. v1 proves that developers will pay for expert help at short notice and that senior engineers will set availability on a platform. The knowledge vault and MCP layer are deferred until the booking model is validated (D01).

---

## Problem

### Mentee side
Working developers get blocked on concrete technical problems and have nobody fast to ask. Available options are too slow (courses, bootcamps), too generic (AI assistants, Stack Overflow), or transactional with no continuity (Codementor — "knowledge lost after the call"). The problem is acute: 43 of 54 survey respondents (80%) had been stuck within the last month. `[DATA: 2026-09-04-survey-discord-willingness-to-pay.md]`

A concrete example from a participant: 40 minutes on Stack Overflow, two contradictory answers in a Discord, shipped a workaround with a TODO — "half a day, and I still don't trust that code." `[INTERVIEW: 2026-08-20-interview-working-dev.md]`

### Mentor side
Senior engineers answer the same questions repeatedly in DMs, Slack, and Discord for free. One interviewee had a private paste doc with recurring answers and pasted from it weekly — "ten doc to jest całe value." Another said: "my notes are the product, the call is the delivery." Neither had ever charged. Neither had a workable way to. `[INTERVIEW: 2026-08-22-interview-mentor.md, 2026-09-03-interview-senior-python-meetups.md]`

---

## Users and segments

### Mentees
| Segment | Description | Source |
|---------|-------------|--------|
| Employed dev at a mid-size company | Concrete blocker, no senior to ask, deadline pressure; pays out of own pocket or expenses it | `[INTERVIEW: 2026-08-20, 2026-09-01]` |
| Freelancer / solo contractor | Estimating something they haven't done; billable time at risk; ceiling ~200 PLN out of pocket, won't tell the client | `[INTERVIEW: 2026-09-02-interview-freelancer-react.md]` |
| Developer at a large company | Rare scenario; only pays if expensable and found in under 5 minutes; not the beachhead | `[INTERVIEW: 2026-09-02-interview-platform-dev-solves-alone.md]` |

**Beachhead**: English-speaking TypeScript, React, Python, AI-agent developers. `[DOCUMENT: 2026-09-02-miro-board-vision-target-needs.md]`

### Mentors
| Segment | Description | Source |
|---------|-------------|--------|
| Senior engineer who already answers informally | Answers the same questions weekly, unpaid, via DMs; has a paste doc or notes; reachable via referral or community | `[INTERVIEW: 2026-08-22, 2026-09-03-interview-senior-python-meetups.md]` |
| Staff engineer / tech lead | Will not list publicly; wants question up front; high price as a filter; discoverable only via own link | `[INTERVIEW: 2026-09-03-interview-staff-engineer-declined-before.md]` |

---

## Evidence

### What's supported
- The problem is real and frequent: 80% stuck within the last month. `[DATA]`
- Text is strongly preferred over calls for technical blockers: 33/54 text, 9/54 call, 12/54 depends. `[DATA]`
- Trust signal is public work, not ratings: 41/54 chose "what they have built or written"; ratings chosen by only 12/54. `[DATA]` Confirmed by 4 of 5 mentee-side interviews independently. `[INTERVIEW]`
- No-shows and prepayment rules are expected: raised unprompted by the freelancer ("jak nie przyjdzie to zwrot tego samego dnia"), the Python mentor ("po to jest przedpłata"), and the staff engineer. `[INTERVIEW × 3]`
- Mentors want question up front before accepting a booking. `[INTERVIEW: 2026-08-22, 2026-09-03-senior-python, 2026-09-03-staff-engineer]`
- Session length of 25 minutes is right for most technical questions. `[INTERVIEW: 2026-09-03-staff-engineer ("większość pytań to 10 minut")]`, `[DOCUMENT: workshop D — 25 or 50 min]`

### Intention vs. behaviour gap (key risk)
69% of survey respondents say they would pay (37/54); only 3/54 have ever actually paid someone. This is the most important unknown: stated intent is not behaviour. `[DATA: 2026-09-04-survey-discord-willingness-to-pay.md]`

### What's a founder position, not evidence
- The knowledge vault as a product layer. `[DOCUMENT]` — no interviewee asked for it by name.
- MCP delivery channel. `[DOCUMENT]` — no interviewee mentioned it.
- "Mentors earn twice." `[DOCUMENT]` — v1 removes this; deferred to v2+.

---

## Non-goals (v1)

| Id | Non-goal | Owner | Source |
|----|----------|-------|--------|
| N01 | Video calls — sessions are text only | Oliwia | workshop 2026-08-26, mentee interview 2026-08-20 |
| N02 | Ratings and reviews — public work link instead | Oliwia | mentor interview 2026-08-22, survey data |
| N03 | Knowledge vault / subscription tier | Oliwia | D01, 2026-10-28 |
| N04 | MCP integration | Oliwia | D01, 2026-10-28 |
| N05 | Async Q&A (24h SLA tier) | Oliwia | D01, 2026-10-28 |
| N06 | Community features, learning paths, courses | Oliwia | interviews (multiple rejections) |

---

## Business rules

| Id | Rule | Source |
|----|------|--------|
| R01 | Sessions are 25 or 50 minutes | workshop 2026-08-26 |
| R02 | Nothing from a session is published without the mentee's explicit approval | workshop 2026-08-26 (both founders) |
| R03 | Mentors must explicitly opt in before their notes can be used to generate AI answers | D02, 2026-10-28 |
| R04 | Booking flow must complete in under 5 minutes; booking requiring more is abandoned | `[INTERVIEW: 2026-09-01 ("jak booking trwa więcej niż pięć minut to robię rollback")]` |
| R05 | Price must be visible before any commitment or message is sent | `[INTERVIEW: 2026-09-02-freelancer ("chcę znać cenę zanim cokolwiek napiszę")]` |
| R06 | Cancellation refund must arrive the same day, not via a support ticket | `[INTERVIEW: 2026-09-02-freelancer]` |
| R07 | Mentor sets their own price | `[DOCUMENT: 2026-09-02-miro-board-product-goals.md]`, `[INTERVIEW: 2026-09-03-staff-engineer ("wysoko, żeby bookowali tylko poważni")]` |

---

## Key flows (v1)

### Mentee: find and book a session
Search → filter by stack/topic → view mentor profile (public work link, description, price, response time) → pick a slot → pay → text session → end.

### Mentor: set up and receive a booking
Create profile → write description + link to public work → set price and session length → publish availability → receive booking notification with question → accept or decline → conduct text session → receive payment.

---

## Riskiest assumptions

| Id | Assumption | What would falsify it |
|----|------------|----------------------|
| A01 | Devs who say they'd pay will actually pay when the session starts at €25–50 | First 20 bookings; conversion from browse to pay |
| A02 | Senior engineers will set up a profile and not lapse before the first booking | Mentor retention at 30 and 90 days |
| A03 | Public work is sufficient to establish trust without ratings | Conversion rate from profile view to booking; exit survey |
| A04 | Mentors will accept booking requests from unknown mentees | Acceptance rate in first month |
| A05 | A 5-minute booking flow is achievable | Usability test on the booking path |
| A06 | Text-only sessions resolve the use case (no escalation to call needed) | Session completion and satisfaction signal |

---

## Hypotheses

_Generated in this session; to be confirmed with real users._

- `[SYNTHETIC]` Mentees in a paid session context will share their actual code or config in a text thread. (Real check: observe in first 10 sessions whether mentees paste code or describe abstractly.)
- `[SYNTHETIC]` The staff-engineer profile (high price, own-link-only, question up front) will produce a booking within 30 days if seeded with 3 referrals from known contacts. (Real check: track time-to-first-booking for invite-only onboarded mentors.)
- `[SYNTHETIC]` Response time is the deciding factor when two mentors with similar profiles are available. (Real check: A/B test showing response-time indicator vs. hiding it.)

---

## Collection plan

| Item | Who | When |
|------|-----|-------|
| Willingness to actually pay: run a mock checkout with 5 target mentees | Oliwia | before v1 build starts |
| Mentor supply: invite 10 engineers from the existing list; track profile completion and first availability set | Oliwia | before v1 build starts |
| Booking flow usability: test 5 people on a clickable prototype for the 5-minute rule (R04) | Oliwia | after prototype exists |
