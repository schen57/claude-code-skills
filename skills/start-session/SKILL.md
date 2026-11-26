---
name: start-session
description: Ground a new session in one project of this workspace. Pulls, reads the project's current state and recent decisions, and surfaces relevant cross-project learnings. Use at the start of a session when resuming a project.
argument-hint: "[project folder or keyword]"
disable-model-invocation: true
---

Resume the project named in `$ARGUMENTS` (a folder name or keyword). If none is given, list the project folders with the first line of each `PROGRESS.md` "Now" section and ask which one.

Assumes the workspace layout in `templates/README.md`: one folder per project with `DECISIONS.md` and `PROGRESS.md`, and a root `LEARNING-NOTES.md`.

1. **Sync.** Run `git pull` at the repo root. If the pull fails or the tree is dirty, stop and report rather than resolving it silently.
2. **Read state, in this order:** the project's `CLAUDE.md` (if any), the `PROGRESS.md` "Now" section, and the top 3 entries of `DECISIONS.md`. Follow any start-of-session steps the project's own `CLAUDE.md` lists.
3. **Check for staleness.** Compare the "Now" section's date with the latest commit touching the folder (`git log -1 --format=%cd --date=short -- "<folder>"`). If commits are newer than "Now", say so: the state file may be behind, so don't quote it as current.
4. **Surface learnings.** Read the index at the top of root `LEARNING-NOTES.md` and pick the lines that bear on this project's next step. Read only those sections. If none apply, say so; don't force a link.
5. **Brief.** Reply in at most ~12 lines: where the project stands, the next step, anything blocked or stale, and any learning worth keeping in mind (one line each, with its heading). Then wait for direction.
