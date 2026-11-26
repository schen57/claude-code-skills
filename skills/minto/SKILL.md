---
name: minto
description: Structure a memo, plan, update, proposal or long message with Barbara Minto's Pyramid Principle (answer first, then grouped support), or check an existing draft's structure. Use when the user says "minto this" or "pyramid this", or asks to structure, tighten or check the logic of a piece of writing meant for a reader. Also use it unasked, before handing over: a plan or proposal for approval, a status report or recap longer than a few lines, a decision memo, or a message the user will send that is longer than two sentences. Not for running logs, scripts, stories or casual chat.
argument-hint: "[write|check] <draft, notes or file>"
---

Work on `$ARGUMENTS`. **Check** mode if it is a finished draft, **write** mode if it is notes or a request; ask only if unclear.

## 1. The top
- Name the reader and the one question they bring. Write the answer as one sentence: the claim the whole piece supports.
- If no single answer fits, say so and ask; a piece with two answers is two pieces.
- Standing reference documents (a remit, a README) with several readers: the pyramid is the opening and the main claims; tables, lists and open questions go in a reference part after it and are not counted in the checks.

## 2. The opening (keep it to a few lines)
- **Situation:** what the reader already knows and agrees with.
- **Complication:** what changed or went wrong.
- **Question:** the one that raises.
- **Answer:** the sentence from step 1. Nothing comes before it except the situation and complication.

## 3. The support
- 2 to 5 points under the answer, each a full-sentence claim, never a topic label ("Rally cutting comes first because it decides every later number", not "Priorities").
- Same kind throughout one group: all reasons, all steps, or all parts. Never mixed.
- No overlaps, and together they cover the case. If something does not fit, it is a new group or it goes.
- Order on purpose: by time, by structure, or by importance. Say which.
- Each point answers the "why?" or "how?" the point above raises. Evidence goes at the bottom, never at the top.

## 4. Check list (both modes, and on your own draft before handing it over)
1. The answer is in the first two lines.
2. Read the headings or bold lead-ins alone: they summarise the piece.
3. No group over 5 points; each group one kind.
4. No overlaps, no gaps, and no later section (a review, an update) contradicting the body: fold changes into the body.
5. Nothing before the answer that the reader did not need first.

## 5. What to hand back
- **Write:** the draft, then one line naming its order (time, structure or importance).
- **Check:** the draft's actual pyramid as a ```mermaid graph TD (top claim, its points, their support), the problems numbered by check-list item, and a rewritten opening. Rewrite the body only if asked.

House style (edit to taste): plain words, no acronyms or internal codes, short. Drafts in another language stay in that language.
