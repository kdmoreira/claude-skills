# Discovery practice — shared by problem-discovery and solution-discovery

Common working practice for both discovery phases. The phase-specific skill
covers what each document contains; this covers how the work is done.

The real deliverable usually lives in a **Google Doc or Confluence page you
cannot edit directly**. Your job is research, reasoning, and producing text the
user pastes in — plus a versioned working copy you *can* edit.

## The core loop

This is not a "write the doc for me" task. It is a long-running research
conversation.

1. **Ground claims before writing them.** Never assert how a system behaves —
   verify it. Read the source (GitHub, `gh api`, extract from jars if that is
   what it takes), query the real API, check the other team's docs, or ask the
   user. If something rests on an unconfirmed assumption about someone else's
   system, say so and go looking rather than asserting it either way.
   **Measure rather than estimate whenever the data is reachable** — a counted
   figure settles arguments a guessed one cannot.
2. **Think before drafting.** For anything beyond a small edit, reason through
   the idea conversationally first. Write prose only once the shape is agreed.
   Ask the clarifying question before drafting the section, especially where
   there is a choice of framing.
3. **Small, incremental edits.** The user edits the real doc by hand and will
   paste back their own revision asking "is this better?". Answer with short,
   direct feedback — confirm, correct, or suggest one tweak. Do not re-explain
   the section back to them.
4. **Correct your own claims loudly.** You will get things wrong — a
   mis-stated mechanism, a figure that turns out to count something else. When
   the user's correction or your own later reading overturns something you
   wrote, say plainly that it was wrong, fix every place it propagated to, and
   record the correction in the working doc so it does not get re-introduced.
5. **Whole-document consistency passes.** Periodically, and whenever asked
   whether the doc still holds together, re-read it in full against its
   sources, using the revision checklist below.

## Working directory, under git

Keep a working directory alongside the real doc — typically
`~/workspace/<project>/`. Ask where if it is not obvious from context.

**Initialise a git repo there if there isn't one, and commit after every change
you apply.** One commit per applied change, with a message saying what changed
and why. The user reviews by diff; an uncommitted pile of edits is not
reviewable, and during a revision the diff is the only practical review
surface.

The working directory holds:

- **Proposed text the user hasn't pasted yet**, each labelled with its
  destination.
- **Grounding notes** — what you measured, where you read it, and what is
  still unverified. Mark anything needing confirmation before it is relied on.
- **A structure mirror** of the real doc, so a reference like "fix 1.3" or
  "what about Axis C" means the same thing to both of you. Re-sync it when the
  user reorders sections upstream; do not let it drift silently.
- **Side explorations and alternatives** that are real but not actionable yet.

### Presenting proposed text

Present drop-in text as a blockquote with a pointer to where it goes — which
section, "add to the end of X", "replace the paragraph beginning Y". When
proposing an edit to existing content, reproduce the affected passage so the
user can diff it mentally.

Do not use sentinel markers around drop-in blocks. (If the user reports pasted
text arriving broken mid-sentence, that is Google Docs' "paste without
formatting", not the quoting.)

During a **revision** you stop producing drop-ins and edit the copy directly.

If the destination is Confluence rather than staying a Google Doc or a plain working
copy, see the `confluence-migration-doc` skill once the content is ready to publish —
it covers the header-table/TOC/expand-block conventions and the mechanics of a
whole-body page write.

## Revision

When the investigation or the axes have settled, **offer a revision pass**. Do
not start one unasked.

1. **Mirror the live document into the working directory** as a copy,
   faithfully and in full, including any open comments. Commit that as the
   baseline, so every later commit is reviewable as a diff against the real
   document's current state.
2. **Review and report findings first**, grouped by severity. Let the user pick
   the order rather than starting to edit.
3. **Then edit the copy directly**, one commit per fix.

What to look for, roughly in the order worth fixing:

- **Unaddressed comments.** Reviewer comments on the live doc are often the
  sharpest critiques in the project and the easiest to lose. Read them. When a
  comment is right, change the document rather than replying to it — and
  record the resolution in the copy so the reasoning survives.
- **Contradictions.** Two sections asserting incompatible things. The usual
  cause is a later section learning something the earlier one still denies.
  Goals, criteria and problem statements are the most dangerous places for
  this, because they get quoted back at you.
- **Dangling references.** Promises to sections that do not exist, and
  cross-references pointing at paragraphs that were never pasted. Either write
  the thing or remove the promise — but check first whether the target exists
  in draft, in which case pasting it is the smaller fix.
- **Stale, time-bound content.** Dates that have passed, decisions described
  as imminent, "currently" claims that have expired. Prefer atemporal phrasing
  over a date, and keep one fact in one place so retiring it is one edit.
  Roadmap dates belonging to another team are different — those come true
  rather than going stale, and should stay.
- **Structural asymmetry.** One section having an element its peers lack.
  Either give the others the same element or explain the difference once; an
  unexplained asymmetry reads as an oversight.
- **Terminology.** One word used for two things; two words proposed for the
  same thing in different sections; a term the user renamed that survives
  elsewhere; notation that varies between sites. Also check spelling
  convention (`-ise`/`-ize` and friends) — and leave quoted proper nouns and
  code identifiers alone even when they break the convention.
- **Numbers.** Soften drift-prone background scale to approximations so it
  future-proofs; keep measured results exact, because that is what makes them
  evidence. Watch for two figures with different denominators sitting near
  each other and reading as a contradiction — naming what each counts, or
  dropping one, usually fixes it.
- **Leftovers.** Scaffolding from the early draft that the body has outgrown —
  brainstorm question lists, placeholder headings, "things to consider"
  bullets. Convert what is still live, and say what was answered where rather
  than deleting silently.

## Description — the header blurb

Both document types carry a short **Description** in their header, alongside
author and status: one dense paragraph answering "what is this document about"
for someone deciding whether to read it. It is not a summary and does not
replace one — a summary reports conclusions, a description reports *what the
document is*.

A workable shape: what the document examines and why now; the central framing
or mechanism it rests on; what it contains, named concretely enough to be
navigable; and — importantly — **what it deliberately does not do**, with a
pointer to the companion document that does. That last clause is what stops
readers arriving with the wrong expectation, and it is the part most often
left out.

Write it after the body is stable, with the summaries.

## Summaries

Both document types end by writing their summaries, which are then placed
first. Usually two: an **executive summary** (what is broken, that it is
already costing something, what is proposed, what is deliberately deferred,
what is still needed) with no internal vocabulary, no section labels and no
un-round numbers; and a **technical summary** (the shape of the problem or the
decomposition, and where it lands).

Write them only once the body is stable, or they will describe a document that
no longer exists. Keep them genuinely short and iterate toward *more* concise
on request. A summary may repeat the body; two sections of the body must not
repeat each other — if a summary and the Context section say the same thing,
cut it from Context.

## Style notes

- Favour precise, load-bearing terminology over generic phrasing. Match the
  term the user has settled on, and flag it explicitly when a different one
  seems more accurate rather than quietly switching.
- When the user asks "what is the best name for X", treat it as a real
  decision worth a sentence of reasoning, not a rubber stamp.
- When comparing two framings, give a direct comparison, not a survey of both
  in isolation.
- Prefer naming a mechanism over describing a vibe: "two datalog clauses
  unifying on one variable" beats "tightly coupled".
- Be ready to answer "which documents did you use" — track what you cited
  while researching, not only what made it into the prose.
- For diagrams, prefer Mermaid where it is expressive enough; say so plainly
  when it is not rather than forcing a bad fit.
