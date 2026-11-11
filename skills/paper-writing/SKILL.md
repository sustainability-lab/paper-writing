---
name: paper-writing
description: Write, rewrite or review a research paper (LaTeX or Markdown) in the Sustainability Lab style. Use for abstracts, titles, introductions, background and related work, method, evaluation, analysis, limitations, figures, tables, captions, sentence-level edits, and pre-submission checks. Also use when asked to review a student's draft.
---

# Paper writing (Sustainability Lab style)

Human-readable version with figures: https://sustainability-lab.github.io/handbook/writing-papers.html

Files in this skill:
- `reference.md`: every rule, section by section, with examples. Read the part for the section you are working on.
- `checklist.md`: the pre-submission checklist. Run it before calling a paper ready.

## Five principles

1. Write for a smart reader from a neighbouring field: good ML background, no knowledge of the subfield.
2. State the point first, in every abstract line, paragraph, section and caption.
3. Go from concrete to abstract: a small example with real numbers, then the general form.
4. Back every claim with evidence (a number, table, figure, proof or citation), or narrow the claim.
5. Be honest: show failures and limitations before a reviewer finds them.

## Core rules (details in reference.md)

- **Skeleton.** One abstract line = one intro paragraph = one section. The lead sentences of the intro, read in order, should read like the abstract.
- **Abstract.** RM101 parts: context, motivation, prior art, (insight), approach, evaluation, results, conclusion. 7–8 lines; a line may hold two short sentences. Comparative numbers. Main limitation in the last line.
- **Introduction.** Lead sentence states the point; last sentence bridges to the next paragraph. No bold run-in heads. Goals stated once and reused. A results paragraph with headline numbers. Caveats at the end.
- **Background vs related work.** Separate sections. Related work opens with "We now categorize prior work by ...". One family per paragraph, verdict first, closing with one line on how we relate ("Like them, ...; unlike them, ...").
- **Method.** Intuition first (3–5 sentences). Subsections are plain questions. Inside each: why, toy example (2-D, numbers checked in code), how (bullets and one equation), guarantee (one plain sentence). No experiment counts in the method.
- **Evaluation.** Open with numbered questions tied to the goals. Setup: scenario, one data-set table, baselines grouped with reasons and given their best chance, metrics by goal, protocol. A new metric is a subsection here. Results subsections are questions answered in their first sentence. One headline figure. Oracles, intervals, rule of three for zero events, failure cases.
- **Analysis, limitations, conclusion.** "Why does it work?" questions. Limitations as a numbered list, each with an italic verdict, evidence and a way forward. A 4–6-sentence conclusion.
- **Sentences.** Active voice with "we". Median 15–18 words, maximum about 25. One idea per sentence. `\emph` only on the words that carry the argument (one or two per paragraph). No filler, no inflated words, no bare numbers, one term per concept.
- **Figures.** One message, stated in the first sentence of the caption. One semantic colour code for the whole paper (for example orange = problem, blue = ours, green = good outcome, grey = baseline). Movement shown as a colour change. Colour-blind safe (Okabe–Ito), never colour alone. Text ≥ 6–7 pt.
- **Tables.** Takeaway-first caption. Column groups labelled by goal. No empty headline cells. Counts for small n. Stated bold rule; shaded "ours" row.
- **LaTeX.** `\cref` for every reference, including the supplement (`xr-hyper`, `\externaldocument[S-]{supp}`). Macros for the method name and metrics. Author comment macros behind `\ifshownotes`. One sentence per source line.

## Workflow when asked to review or rewrite

1. **Read before acting.** Read the whole paper, every included file and table, and any style guide the user names. Render the PDF and look at the figures and tables.
2. **Do not overwrite the author's prose.** For each section, add inline comments that say what is wrong and *why* (for example `\nb{Style: the lead sentence is history; lead with the claim.}`), then a full suggested rewrite after the original, inside `\ifshownotes ... \fi`, under a heading in the note colour such as "3 Method (suggested rewrite)". Inside the rewrite, avoid `\section`, `\label{sec:...}` and re-`\input` of existing floats, so nothing clashes.
3. **Keep facts exact.** Take every number from a table, figure, the supplement or code. Wrap anything you inferred in a "please check" note. After each rewrite, re-read it against the source and fix drift in counts, scope words and which variant a number belongs to.
4. **Figures.** Use the project's palette and one semantic colour code. Render each figure and fix overlaps, clipping and overflow before inserting it. Never claim you checked a figure unless you saw the rendered image.
5. **References.** Never hand-type a figure, table or section number. If the paper does, add a note that teaches the `\cref` fix.
6. **Builds.** Do not run TeX on the project's live build outputs. Compile a copy in a temporary directory, and report errors, undefined references and overfull boxes honestly.
7. **Bibliography.** Do not edit `.bib` files by hand if the project has citation tooling. Never invent a citation.
8. **Hand-off.** End with a short review guide (behind `\ifshownotes`): changes by section, new files, the colour code, runs still needed, facts to confirm.
9. **Ask the user only about decisions that are theirs:** structure changes, renames, what to cut. Recommend an option and say why.

## Writing from scratch

Write the abstract first (7–8 lines), then grow each line into an intro paragraph, then each paragraph into a section. Sketch the figures and tables early; they show which experiments are still missing.
