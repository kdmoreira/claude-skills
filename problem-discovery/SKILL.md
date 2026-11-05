---
name: problem-discovery
description: Use when helping investigate and write a problem-discovery document (the kind that precedes solution discovery and a design/RFC) — clarifying a fuzzy technical problem, tracking couplings/assumptions, naming underlying causes, building guiding questions and appendices, or running a revision of the whole document. Trigger on requests like "let's start a problem discovery", "help me draft the problem statement", "give me a drop-in text for section X", or when the user is iterating on a Google Doc/Confluence page for this kind of write-up. For goals/decision-criteria/solution-axes/first-release work, use the `solution-discovery` skill instead.
model: opus
effort: high
---

# Problem Discovery

Investigating a fuzzy technical problem and turning it into a structured
document — the phase that precedes solution discovery (see the
`solution-discovery` skill).

**Read `~/.claude/skills/references/discovery-practice.md` first.** It covers
the working practice shared by both discovery phases: the core loop, the
git-backed working directory, how to present proposed text, the revision pass
and its checklist, summaries, and style. This file covers only what is specific
to investigating a problem.

## Two additions to the core loop

**Push back on the problem statement.** The stated problem is often a symptom.
Ask whether it is the real problem or a downstream consequence of something
else, and keep asking as understanding sharpens. Finding that the problem is
one level deeper than stated is the most valuable outcome this phase has.

**Verify the user's own assumptions too.** When the user says "confirm whether
these are correct", check against real sources before agreeing, and cite what
you checked. A wrong mechanism recorded here becomes a wrong goal in the
solution discovery that follows, where it is much more expensive to dislodge.

## Document shape

Adapt, don't force.

1. **Background / context primer** — the minimum a reader needs, ideally as
   confirmed assumptions, each a claim plus its source. Resist writing a
   tutorial; include only what the problem statement will lean on.
2. **Problem statement** — what breaks and why. Expect to rewrite this several
   times as the investigation moves; that is the phase working, not failing.
3. **Couplings / underlying causes** — name the *kind* of coupling
   (structural, semantic, borrowed-concept, temporal) rather than describing it
   generically. This vocabulary recurs throughout both documents and should be
   settled here, deliberately.
4. **Evidence that it is already failing** — where the problem has already
   produced observable damage, with measurements. A problem with live symptoms
   is a different conversation from a predicted one, and those symptoms become
   what a first release is judged against later.
5. **Guiding questions** — open questions for the responsible teams, phrased so
   a non-participant can act on them. Distinguish what you could not verify
   from what nobody currently owns; the second kind is usually the more
   important finding.
6. **Solution scope teaser** (optional) — minimal to maximal coverage, purely
   to bound scope. Often removed once solution discovery starts properly.
7. **Appendices** — edge cases and overlaps that deserve detail but would
   clutter the narrative.
8. **Executive summary + technical summary** — written last, placed first.
9. **Description** — the one-paragraph header blurb. See the shared reference.

## Handing off

Once the problem is well-scoped, move to the `solution-discovery` skill.

Carry the vocabulary across unchanged — terminology drift between the two
documents is the most common and most avoidable inconsistency. The couplings
named in section 3 and the live symptoms in section 4 are what the solution
document's goals and first release will be written against, so they should mean
exactly the same thing in both.
