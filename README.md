# claude-skills

A small collection of [Claude Code Skills](https://docs.claude.com/en/docs/claude-code/skills) I use for writing technical documents.

## What's here

- **`problem-discovery/`** — investigate a fuzzy technical problem and turn it into a structured problem-discovery document (the phase before solution discovery and a design/RFC).
- **`solution-discovery/`** — turn an already-scoped problem into a document that decides something: goals, decision criteria, independent solution axes, and a first release.
- **`references/discovery-practice.md`** — the working practice shared by both skills above (how the research/writing loop runs, working-directory conventions, revision checklist, style notes). Both `SKILL.md` files point here, so it needs to live alongside them.

These two skills are meant to be used together: `problem-discovery` hands off to `solution-discovery` once the problem is well-scoped.

## Installing

Claude Code loads personal skills from `~/.claude/skills/`. Clone this repo and copy (or symlink) the folders in:

```bash
git clone https://github.com/kdmoreira/claude-skills.git
cp -r claude-skills/problem-discovery claude-skills/solution-discovery claude-skills/references ~/.claude/skills/
```

Claude Code will then surface them automatically when the conversation matches — e.g. "let's start a problem discovery" or "help me draft Axis B".

## Notes

- Both skills assume the real deliverable lives in a Google Doc or Confluence page you can't edit directly, with the skill producing drop-in text and a versioned local working copy. If your workflow is different, adapt the "working directory" section in `references/discovery-practice.md`.
- Publishing a finished document to Confluence is out of scope here — that's its own skill, specific to Confluence's HTML/ADF quirks, and isn't included in this repo.
