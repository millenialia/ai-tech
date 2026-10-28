# Synthetic panel report — DevMentor mentee booking flow
_Date: 2026-10-28. Stance: adversary. Runs: 2 × 3 personas. Flow: Mentee: find and book a session._
_Subject: .ai/specs/product-brief.md. Parity: 2026-09-02-interview-platform-dev-solves-alone.md (held out)._

**All findings are [SYNTHETIC]. Nothing here satisfies the Definition of Ready.**

---

## Verdict

Six objections survived both runs. None are individually fatal to the product, but two of them — F01 (no real-time availability) and F02 (public work is insufficient for problem-specific fit) — sit directly on the brief's most consequential design decisions: that the platform serves urgent, same-day needs and that public work can substitute for ratings as a trust signal.

---

## Findings that survived both runs

### F01 — No real-time availability signal `[SYNTHETIC]`
**What the panel said:** Across all six mentee-segment runs, the first question asked was some version of "is anyone available right now?" The booking flow shows calendar slots but not whether a mentor is present or how quickly they respond. In an urgent scenario, discovering that all slots are next week ends the session.
**Brief assumption attacked:** A01 (devs will pay when the checkout appears), A05 (5-minute booking completion)
**Replication:** P01-R1, P02-R1, P01-R2, P02-R2, P03-R2 — 5 of 6 persona runs
**Real-user check:** Observe drop-off at the slot-selection step; interview 5 target mentees about the moment they would exit. Ask: "If the nearest slot is in 48 hours, what do you do?"

### F02 — Public work is insufficient to establish problem-specific fit `[SYNTHETIC]`
**What the panel said:** Every run raised some version of: "GitHub tells me who they are, not whether they can answer this question." The gap is between general-seniority evidence (commit history, employment background) and task-specific credibility (has debugged Helm 3.12 upgrade path issues, has estimated a CRA→Vite migration on a 60k codebase). The brief's N02 decision removes ratings, which were the one proxy for past task performance.
**Brief assumption attacked:** A03 (public work sufficient for trust without ratings), N02 (the decision itself)
**Replication:** P01-R1, P02-R1, P01-R2, P02-R2, P03-R2 — 5 of 6 runs
**Real-user check:** Show 5 target mentees a mock profile (GitHub + description). Ask: "Before paying, what would you need to see on this profile to be confident this person can answer your specific question?"
**Note on N02:** The panel does not recommend reversing N02. The real interview evidence (four independent sources) strongly supports the ratings decision. What F02 suggests is that the *replacement* signal — public work — is not yet rich enough. The question is whether mentor descriptions can be structured to close the gap.

### F03 — Quality risk asymmetry: buyer pays for time, not outcome `[SYNTHETIC]`
**What the panel said:** Refund policy covers no-shows but not "present and unhelpful." For a solo payer spending out of pocket, this is the moment of hesitation before checkout: not "is the price fair?" but "what if I'm out 80 EUR and still blocked?" No-show refund addresses the 5% scenario; session-quality risk is the 30% scenario.
**Brief assumption attacked:** A01 (will pay when checkout appears)
**Replication:** P01-R1, P02-R1, P01-R2, P02-R2 — 4 of 6 runs
**Real-user check:** At checkout, show two versions — current (no-show refund only) vs. "if the mentor can't engage with your problem in the first 5 minutes, you can cancel for a full refund" — and measure which converts. This does not require implementing the policy, just testing whether the statement changes checkout behaviour.

### F04 — No pre-payment problem-context handoff `[SYNTHETIC]`
**What the panel said:** The mentor hasn't confirmed they can help before payment. In a 25-minute session, 10 minutes of context-setting is 40% of the clock. Two runs raised the related issue that a pre-session context form (what is your stack, paste the error) sent to the mentor before the session starts could recover this time.
**Brief assumption attacked:** A01, A05 (booking completes in under 5 minutes — but booking speed doesn't address session start efficiency)
**Replication:** P01-R1, P02-R1, P02-R2, P01-R2 — 4 of 6 runs
**Real-user check:** In the first 10 real sessions, measure: how many minutes before the actual problem is on the table? Compare for sessions with vs. without a pre-session form.

### F05 — No continuation mechanism for multi-session problems `[SYNTHETIC]`
**What the panel said:** Problems don't fit 25- or 50-minute containers. If a session ends mid-diagnosis, the mentee must re-onboard a new mentor from scratch. The freelancer run raised this most sharply: "the unit of sale (25 min) is misaligned with the unit of the problem (a live bug that doesn't respect time boxes)."
**Brief assumption attacked:** Implicit — 25/50 minutes is a natural unit for technical help (not listed as a riskiest assumption; candidate for addition)
**Replication:** P01-R1, P03-R1, P01-R2, P02-R2 — 4 of 6 runs
**Real-user check:** In first 20 sessions, track: session completion signal (mentee self-reports resolved/not resolved), and whether mentees immediately rebook after an incomplete session.

### F06 — No sub-topic filtering; search surfaces generalists `[SYNTHETIC]`
**What the panel said:** Filtering by stack tag ("Python", "Kubernetes") returns everyone who has used the technology, not people who have solved the specific class of problem. Both freelancer runs raised needing to find "someone who has estimated a migration of this type," not "a React developer."
**Brief assumption attacked:** A05 (5-minute booking) — if filtering doesn't surface the right match quickly, 5 minutes is spent browsing, not booking
**Replication:** P02-R1, P01-R2, P02-R2 — 3 of 6 runs (weakest of the six)
**Real-user check:** In first 10 real booking attempts, track search-to-click rate and exit rate at the search step.

---

## Outlier finding (not replicated, worth watching)

**F07 — Billing creates a client relationship problem for solo contractors** `[SYNTHETIC]`
Raised only by P02-R2 (live client bug scenario): the invoice from DevMentor is visible on the contractor's expense record; explaining "I paid someone to help me fix your bug" is awkward. Only one run raised this. Not a finding. Mentee-payment-vs-client-visibility is worth one direct question in the next freelancer interview.

---

## Parity check — vs. held-out note `[INTERVIEW: 2026-09-02-interview-platform-dev-solves-alone.md]`

The held-out note is the indifferent large-company developer.

| Theme | In real note | In P03 panel |
|-------|-------------|-------------|
| Low urgency; internal channels sufficient | ✓ | ✓ |
| Employer pays, not personally | ✓ | ✓ |
| 5-minute discovery threshold | ✓ ("jak go znajdę w pięć minut") | ✓ |
| Subscription is a hard no | ✓ | ✓ |
| Text or call, whatever is faster | ✓ | partial (P03-R2 raised text-only concern) |
| **Referral as the only organic conversion trigger** | **✓ "albo ktoś, kogo znam, by powiedział"** | **✗ MISSED** |
| "Mentor" positioning reads as junior | ✗ | ✓ P03-R1 only |
| Session content confidentiality | ✗ | ✓ P03-R2 only |

**Critical miss:** The real interviewee named referral from a trusted peer as the *only* path to trust for this segment — "ktoś, kogo znam, by powiedział. tyle." The panel focused on product-level trust improvements (better profile tags, quality signals) and missed that for this segment, improving the browse experience doesn't help. The first booking from a large-company developer requires a colleague saying "this worked for me." This is a distribution/activation finding, not a product design finding.

**Panel-only themes** (questions for the next real interview): "Mentor" positioning mismatch; session content confidentiality at paste point.

**Sentiment alignment:** High on low-salience framing. Blind spot on referral-as-entry.

---

## To confirm with real users

| Id | Hypothesis | Segment to recruit | Question / check |
|----|------------|-------------------|-----------------|
| H01 | `[SYNTHETIC]` Mentees exit the booking flow when the nearest slot is >24h away | Employed dev, freelancer | Drop-off at slot-selection; "if nearest slot is 48h away, what do you do?" |
| H02 | `[SYNTHETIC]` Public work (GitHub/blog) is insufficient to confirm problem-specific fit before paying | Employed dev, freelancer | Show mock profile; "what would you need to see to be confident?" |
| H03 | `[SYNTHETIC]` Quality-risk framing at checkout ("present but unhelpful" non-refundable) reduces conversion vs. a "cancel in first 5 minutes" policy statement | Employed dev | A/B checkout copy test |
| H04 | `[SYNTHETIC]` Pre-session context form reduces context-setting time inside the session | All | First 10 sessions: minutes before problem is on the table |
| H05 | `[SYNTHETIC]` A significant share of sessions end before the problem is fully resolved | All | Session completion tracking in first 20 sessions |
| H06 | `[SYNTHETIC]` Sub-topic filtering (beyond stack tag) reduces browse-to-click time for specific problem types | All | Search exit rate in first 10 real booking attempts |

---

## New risks for the brief (candidates for `om-discover --refresh`)

These did not appear in the riskiest assumptions but survived two runs:
- **A07** `[SYNTHETIC]` — For the large-company segment, referral from a known peer is the only realistic first-booking trigger; browse-and-book does not convert this segment cold
- **A08** `[SYNTHETIC]` — Session length (25/50 min) is insufficient for a meaningful share of problems; no extension mechanism means incomplete sessions produce a worse outcome than not booking at all

---

## What the panel cannot tell you

- Whether real devs will actually pay (they said so in the survey; 3/54 have). That is A01, and only real transactions settle it.
- Whether any specific mentor profile would convert a real buyer. The panel evaluated the category, not a specific mentor.
- Whether the referral mechanism (A07) matters more than browse-and-book. Only real activation data shows this.
