---
name: wrap-session
description: Close a session safely. Checks that everything this session did is written into the project docs (DECISIONS, PROGRESS "Now", waiting-on-you list, learnings), commits and pushes it, and stops if a decision is still open. Use when the user says they are done, wants to clear, compact or start fresh, or says "document everything", "save everything" or "make sure it's all written down".
argument-hint: "[project for the next session, optional]"
---

Goal: nothing from this session lives only in the conversation or only on this machine. Clearing must lose nothing. Work through the steps in order and keep the replies short.

1. **List what this session did.** From the conversation (and its summary, if it was compacted): every project touched, every choice made, every finding, every task or question left for the user, every tool installed or turned down. Then run at the repo root: `git status --short`, `git log origin/HEAD..HEAD --oneline`, and `git log --since="<session start date>" --format="%h %ad %s" --date=short` to see this session's commits.

2. **Sort uncommitted files.** Files this session changed get committed in step 5. Files this session did not touch (another session's work in progress) are listed for the user and left alone: never commit, stash or revert them. They are not a reason to stop.

3. **Check each touched project's docs, one line each (pass or fixed):**
   - Each choice made is in `DECISIONS.md` (newest first, `## YYYY-MM-DD [n] Title`, with the why).
   - `PROGRESS.md` "Now" says where things stand and the next step, dated today. A "Now" dated before today's work fails.
   - Anything only the user can do is a `  - [ ] text` line under `- **Waiting on you:**`, and anything they finished is removed.
   - Every failure, fix or trap this session hit is an if-then line in the project `CLAUDE.md` "Quick reference"; a line proven wrong is fixed; the section stays short.
   - An insight that transfers across projects is in root `LEARNING-NOTES.md` (dated, with its source project) and has a line in its index.
   - A standing preference the user stated is in memory or the right `CLAUDE.md`.
   Write whatever is missing. A check passes only if the note exists in a file, not because the conversation mentions it.

4. **Stop on open decisions.** If the user was asked something this session and has not answered, and the answer changes what gets written or done, stop here. List each one as a question with its choices, and say that nothing has been cleared. Items already on a waiting list do not block: they are saved.

5. **Commit and push.** Commit per project with a `<Project>: ...` prefix, then `git push`. Verify: `git fetch` then `git status -sb` shows the branch not ahead of its remote, and none of this session's files are left in `git status --short`. If a push fails, stop and report; do not clear.

6. **Report**, at most 8 lines: what was saved where, what was fixed in step 3, files left uncommitted because they belong to other work, and the project for the next session (`$ARGUMENTS`, or the one this session mostly worked on), with the command to resume it: `/start-session <project>`.
