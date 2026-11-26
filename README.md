# claude-code-skills

Skills I use every day with [Claude Code](https://claude.com/claude-code), taken from the workspace where I build everything with coding agents. Each one exists because something went wrong without it.

## The skills

**Check the work**
- [`review-plan`](skills/review-plan/SKILL.md): before building, three fresh reviewers plus one asked only "is there a simpler way?". One review missed about a third of the problems three reviewers found, and the simpler-way pass found a better design none of them raised. Keeps a list of checks past reviews missed.
- [`write-skill`](skills/write-skill/SKILL.md): change a skill or `CLAUDE.md` without bloat: fix it in the script first, add a line only with evidence, edit instead of append, and record the size in the commit. Adapted from Garry Tan's gstack.

**Remember across sessions**
- [`start-session`](skills/start-session/SKILL.md): pull, read the project's "Now" and latest decisions, warn if the notes are older than the commits, and surface learnings from other projects.
- [`wrap-session`](skills/wrap-session/SKILL.md): before clearing, check every choice, finding and open question is written down, then commit and push. Stops if a decision is still open.
- [`distill`](skills/distill/SKILL.md): when a project hits a milestone or pauses, lift what would change a choice in another project into shared learning notes.
- [`templates/`](templates/README.md): the workspace layout these three expect (decisions, progress, learnings).

**Write and look**
- [`minto`](skills/minto/SKILL.md): answer first, then grouped support (Barbara Minto's Pyramid Principle), for plans, updates and long messages. Also checks a draft and draws its actual structure.
- [`analyze-painting`](skills/analyze-painting/SKILL.md): what makes a painting work, element by element, in plain words, ending with the terms to search for or prompt that look.

## Install

Copy a skill folder into `.claude/skills/` in your project (or `~/.claude/skills/` for every project):

```
git clone https://github.com/Schen57/claude-code-skills
cp -r claude-code-skills/skills/review-plan your-project/.claude/skills/
```

Then type `/review-plan` in Claude Code, or let Claude pick it up from the description. The session skills assume the layout in [`templates/`](templates/README.md); copy those files into a project folder to start.

## License

MIT. `write-skill` is adapted from [gstack](https://github.com/garrytan/gstack) (MIT, Garry Tan); see its NOTICE.
