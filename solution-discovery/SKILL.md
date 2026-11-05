---
name: solution-discovery
description: Use when helping explore and write a solution-discovery document (the kind that follows a problem-discovery doc and precedes a design/RFC) — decomposing a solution space into axes with lettered options, drafting goals/non-goals and decision criteria, defining a first release, or running a major revision of the whole document. Trigger on requests like "let's start solution discovery", "help me draft Axis B", "give me a drop-in text for the decision", "is the doc still consistent", or when the user is iterating on a Google Doc/Confluence page for this kind of write-up.
model: opus
effort: high
---

# Solution Discovery

Turning an already-scoped problem (from a problem-discovery doc — see the
`problem-discovery` skill) into a document that decides something: goals,
decision criteria, the solution space split into independent questions, and a
first release that can actually ship.

**Read `~/.claude/skills/references/discovery-practice.md` first.** It covers
the working practice shared by both discovery phases: the core loop, the
git-backed working directory, how to present proposed text, the revision pass
and its checklist, summaries, and style. This file covers only what is specific
to deciding between solutions.

## One addition to the core loop

**Check whether the axes are really independent.** Before drafting a new axis,
look at whether choices already made constrain it. Axes are meant to be
independent dimensions, and when they are not, say so explicitly rather than
writing as though they were — an axis whose answer is already determined by
another one is not an axis.

## Document shape

Adapt, don't force. This order works, and the reasons are in each entry.

**1. Context.** Point at the problem discovery; do not restate it. Carry only
what the rest of the doc needs and the problem doc does not supply — usually
the decomposition of the problem into independent directions, and a sentence
saying what this document does. Define any label the body will reuse.

**2. Goals / Non-goals.** Goals are outcomes, not implementations: the test is
whether two different solutions could satisfy the same goal. Classify them by
whether a solution is viable without them (Must / Should / Nice to have), and
state that **Musts are gates, not weights** — an option failing one is out, and
strength elsewhere does not compensate. The floor goal is almost always "do not
regress what already works".

Two failure modes to watch for, both of which turn a goal into an argument for
one option:

- **A goal only one option can satisfy** is that option's case wearing a
  goal's clothes. If exactly one option scores full marks, suspect the wording.
- **A goal stated as a dichotomy** ("explicit rather than inferred", "declared
  rather than derived") smuggles in a mechanism. State the outcome; let the
  axis choose the mechanism.

Non-goals: separate the genuinely unrelated from the adjacent-but-excluded. The
second kind need a reason. Include the ones people will ask about anyway.

**3. Decision criteria.** Stated *before* the options, deliberately — criteria
written after a favourite has emerged describe the favourite, and the
comparison stops being one. Two families are usually in play: what makes an
answer **durable** (depend in the direction of stability, prefer an interface to
an implementation, key on invariants rather than current state, own your own
concept rather than borrowing another team's, separate values that do two jobs,
fail loudly) and what makes an answer **reachable** (smaller blast radius,
earlier partial value, reversible steps, separate mechanism changes from policy
changes, coexist with what exists today). Say explicitly that the two families
conflict, and that when they do the trade should be visible rather than buried
in a score. Add a criterion when a new failure mode surfaces; do not freeze the
list.

**4. Solution options — the questions.** Split the solution space into
questions that can be answered independently, one per axis. For each, state the
question precisely, give **one concrete worked example**, and say what turns on
the answer. The example is what stops two axes being conflated, and is worth
more than another paragraph of abstraction.

Classify each question by kind:

- **Choice** — answering one way rules out the others; must be settled before
  anything ships.
- **Increment** — can be advanced later, *provided* the choices have not
  foreclosed it. Increments belong in the document precisely because earlier
  answers can quietly make them impossible.

**5. Question kinds.** A short section saying what that distinction means for
what a first release has to settle. Note any part of a choice that is separable
(what a thing is called is usually separable from what it denotes, and only one
of those is load-bearing).

**6. The first release.** A named scope, stated *before* the axes, because the
axes will refer to it. One table row per axis — splitting an axis into two rows
where it has two separable questions — plus a row for coverage or scope. Say
what it reaches and what it does not (which repositories, systems, teams).

Where the first release **does not meet a Must**, say so outright. A deferred
Must is a stated decision with a condition attached, not an omission, and
burying it is how it stops being a decision.

**7. The axes.** One section per question, in the order the questions were
posed.

- Open with **vocabulary** if this axis is where terms come apart. Defining
  two terms that were previously one is often the axis's main contribution.
- Label competing options `A1`, `A2`, `B1(i)`, `B1(ii)`. Only do this where
  options genuinely compete — some axes are one question with a position, not a
  menu, and numbering a single answer is worse than not numbering it.
- Each option: its general shape, what it touches, its key trade-off, what it
  leaves open. Not implementation detail unless asked.
- An option that is not viable gets a sentence — "not recommended, because X" —
  not a section. Over-elaborating a dead option implies it is live.
- Add **How the options relate** where they are not mutually exclusive: which
  compose, which is a prerequisite for which, whether they form a spectrum or
  a fork. Keep the count in the heading correct when options are added later.
- Close with **Where this lands**: the position the axis takes, stated
  independently of any release. This is the durable half — what a later phase
  will not revisit. The release-scoped selection lives in the first-release
  table instead, so that advancing an increment does not mean rewriting an axis.
  If an axis argues a position convincingly and never states it, that is a gap.

*A separate decision matrix is often unnecessary once the axes carry positions
and the release table carries selections. Offer one if the user wants options
scored against goals side by side, and build it only after the options have
stopped moving — a matrix against shifting options is pure rework.*

**8. Open questions.** Only what is genuinely unresolved. Open by naming which
of the original questions the document has since answered, so the section reads
as progress rather than as a deletion. Then group by **when each must be
answered**: blocking the first release / required by a specific goal / only if
an optional increment is pursued / someone else's to decide / explicitly
unscoped.

**9. References.** What you actually cited, not what looked relevant.

**Appendix — rejected options.** *Suggest* this; do not impose it. It holds
options that were explored and rejected, with the reason — so they are not
re-proposed in review. Record the property that made each one attractive: if
the calculus ever changes, that is what someone will come looking for.

**Summaries** are written last and placed first, and the header carries a
one-paragraph **Description** saying what the document is and what it stops
short of; see the shared reference for both.
