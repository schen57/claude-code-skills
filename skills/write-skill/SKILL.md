---
name: write-skill
description: Write a new skill or change an existing one without bloat, using the edit ladder and a size check. Use whenever creating or editing a skill in .claude/skills/, a CLAUDE.md file (root or project), or a skill's learned-checks list.
---

Adapted from gstack's `/write-skill` by Garry Tan (MIT license; see NOTICE in this folder).

## 1. Levels
Put each fact on the lowest level that still reaches the agent before it needs it.

| Level | Loaded | Holds |
|---|---|---|
| root `CLAUDE.md` | every session, every project | one line per behavior wanted everywhere |
| skill `description` | every session | when to use it, one trigger per case |
| project `CLAUDE.md` | every session in that project | that project's hard rules |
| `SKILL.md` | every use | what every run needs |
| a file beside it (registry, `LOG.md`, references) | when a line in `SKILL.md` says to read it | what some runs need |
| the script's `--help`, errors and tests | when a command is picked or a guess is wrong | flags, the right name, the fix |

## 2. Edit ladder
Stop at the first step that handles the change.
1. **Fix it below the prose.** A clearer error, a flag, a check or a test in the script. Prose is for judgment calls.
2. **Earn its place.** Add a line only with evidence it is needed (a run that went wrong without it) or a dated plan to check it. If a fresh session already does it right, add nothing.
3. **Edit, don't append.** Change the line that already covers the idea; each meaning lives in one place.
4. **Pick its level** (section 1).
5. **Rule, not story.** One rule in plain words; the incident, date and source go in the commit message or the skill's `LOG.md`, not in the skill.

Keep the safety lines inline where risk lives: writes, data leaving the machine, money spent.

## 3. Check and record
- Measure before and after with `wc -c <file>` and put `Skill-Size: <before> to <after> bytes (<file>)` in the commit message. A file that grew more than 10% since its last `Skill-Diet:` commit gets trimmed in the same change instead of only growing.
- A change to a skill needs the user's yes, and a development plan goes through `/review-plan`.
- Afterwards, rerun the case that prompted the change (a fresh agent or the next real use) and say whether it now goes right.
