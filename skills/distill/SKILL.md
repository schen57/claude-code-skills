---
name: distill
description: Move a project's new decisions and findings up into the root LEARNING-NOTES.md and refresh its row in the root CLAUDE.md project table. Use when a project hits a milestone, pauses, or ends, or when asked to distill learnings.
argument-hint: "[project folder or keyword]"
disable-model-invocation: true
---

Distill the project named in `$ARGUMENTS`. If none is given, ask which one.

1. **Find the cutoff.** Search root `LEARNING-NOTES.md` for the most recent entry that names this project as its source. Its date is the cutoff. If there is none, use the project's start date.
2. **Read what's new since the cutoff:** `DECISIONS.md` entries, `PROGRESS.md` log entries, and any findings file the project keeps (for example `FINDINGS.md`). Skim, don't read code.
3. **Draft candidates.** A candidate is a learning only if it would change a choice in a *different* project. Project-internal facts stay where they are. For each candidate give:
   - a one-line claim,
   - the evidence (decision or finding it came from, with date),
   - how strong it is: observed once, observed repeatedly, or tested.
   Also flag any existing `LEARNING-NOTES.md` section the new evidence contradicts, refines, or makes stale.
4. **Wait for approval.** Present the candidates and flags. Write nothing until the user picks which ones to keep and how to word them.
5. **Write.** Insert approved learnings as a new `##` section at the top of `LEARNING-NOTES.md` (newest first), titled with the topic and date, and naming the source project. Apply any approved edits to older sections.
6. **Refresh status.** Update the project's stage and "revisit when" rule in the root `CLAUDE.md` project table. If it is moving to Paused, Done or Killed, first add an exit note at the top of its `PROGRESS.md` log: what was learned, and what would restart it.
7. **Commit** with message `Learning notes: <topic> (from <project>)`. Don't push unless asked.
