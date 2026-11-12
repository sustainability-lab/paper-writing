# paper-writing

How the [Sustainability Lab](https://sustainability-lab.github.io) at IIT Gandhinagar writes research papers, packaged as an **agent skill**.

The human-readable guide, with figures and worked examples, is in the lab handbook:
**[Writing Papers](https://sustainability-lab.github.io/handbook/writing-papers.html)**. This repository holds the same rules in a form that AI agents (Claude Code, Codex, Gemini CLI, Cursor and others) can load and follow.

## What's inside

| File | What it is |
|---|---|
| [`skills/paper-writing/SKILL.md`](skills/paper-writing/SKILL.md) | Entry point: five principles, the core rules and the review workflow |
| [`skills/paper-writing/reference.md`](skills/paper-writing/reference.md) | Every rule, section by section, with examples |
| [`skills/paper-writing/checklist.md`](skills/paper-writing/checklist.md) | Pre-submission checklist |

The rules cover the skeleton (one abstract line = one intro paragraph = one section), the [RM101](https://github.com/nipunbatra/CS-Research-Methods-Bootcamp/blob/master/RM101.pdf) abstract, introductions with lead and bridge sentences, separate background and related work, intuition-first methods with toy examples, question-driven evaluation, hero figures that show the problem, the idea and the payoff in ten seconds, semantic colour in figures, takeaway-first tables, LaTeX hygiene, active voice and short sentences.

## Install

**Claude Code (as a plugin):**

```text
/plugin marketplace add sustainability-lab/paper-writing
/plugin install paper-writing@sustainability-lab
```

**Claude Code (as a plain skill):**

```bash
git clone https://github.com/sustainability-lab/paper-writing ~/.local/share/paper-writing
ln -s ~/.local/share/paper-writing/skills/paper-writing ~/.claude/skills/paper-writing
```

Update later with `git -C ~/.local/share/paper-writing pull`.

**Other agents (Codex, Gemini CLI, Cursor, ...):** copy `skills/paper-writing/` into your paper's repository, for example as `docs/writing/`, and add one line to `AGENTS.md` or `GEMINI.md`:

```text
When writing or reviewing the paper, follow docs/writing/SKILL.md.
```

## Use

Ask in plain words, for example:

- *"Review the introduction of main.tex using the paper-writing skill."*
- *"Draft a 7–8 line abstract for this paper."*
- *"Run the pre-submission checklist on this paper."*

When reviewing, the agent adds inline comments that explain *why* and puts a suggested rewrite after your text. It does not overwrite your prose, and every number it uses must come from your tables, figures or code.

## Contributing

Lab members: open a pull request. If you change a rule here, change the [handbook page](https://github.com/sustainability-lab/sustainability-lab.github.io/blob/main/handbook/writing-papers.qmd) too, so the two stay in step.

## Licence

[CC0 1.0](LICENSE): use it, adapt it, share it.
