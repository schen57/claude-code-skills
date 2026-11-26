---
name: review-plan
description: Review a plan or design before it is approved or built, with independent fresh reviewers plus a "simpler approach from the goal" pass, then merge, verify and rank the findings. Use whenever a plan, design, spec, milestone list or multi-step build proposal is about to go to someone for a go, or before starting substantial build work. Also use when asked to review, check or stress-test a plan.
argument-hint: "<plan doc or entry> [quick|full]"
---

Review the plan named in `$ARGUMENTS`. If none is given, use the plan just proposed in this conversation (write it to a scratch file first so reviewers can read it).

Why this exists: on a real build plan, three fresh reviewers with the same prompt found about 15 problems between them, but only 4 were found by all three, so one review misses roughly a third. A fourth reviewer asked only for a simpler approach found a better design none of the three raised. A rule in a prompt gets skipped; this skill is the check.

## 1. Size it
- **quick** (one reviewer plus the simpler-approach pass): a small change, one file or one script, easy to undo.
- **full** (three reviewers plus the simpler-approach pass): anything someone is asked to approve, anything touching payments, user data, accuracy numbers or launch bars, anything costing money or more than a day of work, or anything hard to undo.
- When unsure, full. Say which size was used and why in the report.

## 2. Run the reviewers (parallel, background, read only)
Use the Agent tool with a cheaper model, all in one message. Give each the plan's location and the files it rests on, never your own view of the plan, its weak spots or what you expect them to find (an agent handed a hypothesis returns it confirmed).

Reviewer prompt (identical for each of the three, or the one in quick):
> Read only, change nothing. Review this plan before any work starts: <where the plan is; the docs and code it rests on>. You may read the code to check its claims. List every substantive problem: wrong or unsupported claims, missing cases, risks, gaps in how success is measured, ordering problems, cost or time not stated. Do not take the plan's problem definition as given: say if it mistakes a symptom for the cause or a method for the goal. Trace second- and third-order effects: what else changes (other modules, user behaviour, system complexity, long-term upkeep) once this is built. For each, one line and the evidence (file and line, or the quoted plan text). End with one line: ready to implement, or not. Under 400 words.

Simpler-approach prompt (one agent):
> Read only, change nothing. Plan: <where>. Starting from first principles and the goal of this requirement, research again: is there a simpler, more suitable or cheaper approach than this plan? Under 350 words: the goal in one line, then either a concrete simpler approach (what it is, what it gives up, how to test it cheaply) or why the plan is already the simplest. Cite files or plan text for any claim.

## 3. Merge and verify (you, in this session)
1. Merge duplicates. Keep a count: how many reviewers raised each finding.
2. Check every citation yourself: the file exists, the line says what is claimed. Drop findings whose evidence is false, and say how many were dropped.
3. For each surviving finding decide: real (would happen when built), not real (say why in one line; never drop silently), or the user's call (taste, money, time, scope).
4. Where the simpler-approach pass proposes something testable cheaply with data already on hand, run that test before reporting when it takes under about 10 minutes, or name it as the first step of the revised plan.

## 4. Fix, then report
- Fix the real findings in the plan itself and mark what changed. Ask the user only about their calls.
- Report in plain words, short: size used; findings by how many reviewers raised them (all, some, one); what changed in the plan; the simpler approach and its test result if run; what is left for the user, as options with a recommendation.

## 5. Log it (every run)
Add a line to `LOG.md` in this folder, newest first: date, project, plan, size, findings (all / some / one), whether the simpler pass changed the plan, and later, once built, anything the review missed. When something the review missed shows up in the built work, add it to "Learned checks" below so reviewers are told to look for it next time (pass the list in the reviewer prompt).

## Learned checks
Problems past reviews missed; include this list in the reviewer prompt as "also check:". Add your own as they turn up.
- Does an installed skill or tool fit this work? The plan names it or says why not.
- Does a new file (an answer key, a fixture) get picked up automatically by training or by a held-out test through a folder listing? Fresh test data must stay out until it is scored.
- Can each automatic check fail in both directions (too little and too much), and does any pass bar depend on input the plan does not control (background audio, a user's upload)?
- Does a diagnostic comparison treat both sides alike (same noise, seeds, start state, number of tries)? A plan resting on one try, or on a test with noise on one side only, is not evidence.
- Does the verification use data shaped like real accounts (blank optional fields, records from before the feature existed, missing files, several spellings), not only fresh tidy seeds?
- Does every place that writes the same field stay in sync, and does a change to stored text reach things already rendered from it (videos, emails, caches)?
- Has this idea, or one close to it, been tried before? Search the project's progress and decision logs and say what is new this time.
