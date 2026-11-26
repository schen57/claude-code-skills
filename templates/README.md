# A workspace that remembers

The layout the session skills (`/start-session`, `/wrap-session`, `/distill`) expect. One git repo holds many projects; each session reads what earlier sessions wrote, so clearing a conversation loses nothing.

```
workspace/
  CLAUDE.md            rules for every session, plus a table of projects
  LEARNING-NOTES.md    insights that transfer between projects
  11-26-2026 Name/     one dated folder per project
    README.md          what it is
    DECISIONS.md       what was chosen and why (append only)
    PROGRESS.md        "Now" (rewritten each session) and a log
    CLAUDE.md          the project's hard rules and a short "Quick reference" of traps
  .claude/skills/      the skills in this repo
```

## Three layers, three speeds

| Layer | Answers | File | Changes |
|---|---|---|---|
| Decisions | What did we choose, and why? | `DECISIONS.md` | append only; supersede, never edit |
| Progress | Where are we, what is next? | `PROGRESS.md` | "Now" rewritten every session |
| Learnings | What carries over to other projects? | root `LEARNING-NOTES.md` | grows slowly, after outcomes land |

The loop: work piles up as progress, forks become decisions, and once a decision plays out, `/distill` turns it into a learning that guides the next project.

## The project table in root CLAUDE.md

Every project gets one row: its stage (Exploring, Campaign, Operating, Paused, Done, Killed) and a "revisit when" rule, so nothing is left in limbo. Moving to Paused, Done or Killed needs a short exit note: what was learned, and what would restart it.

```
| Folder | Stage | Revisit when |
|---|---|---|
| `11-26-2026 Example` | Exploring: one line on what it is | the event that brings it back |
```

## Where a piece of knowledge goes

| What | Where |
|---|---|
| A behavior wanted in every session | root `CLAUDE.md`, one line |
| A project's hard rule, or a trap a session hit | that project's `CLAUDE.md` |
| A choice and its reason | project `DECISIONS.md` |
| Current state, next step | project `PROGRESS.md` "Now" |
| Something only you can do | a `Waiting on you` list in "Now" |
| An insight that transfers | root `LEARNING-NOTES.md` |
| A procedure done about three times | a skill (write it with `/write-skill`) |
