# Pre-submission checklist

Run every item. Report each as pass, fail (with location) or not applicable.

## Structure
- [ ] The abstract has 7–8 parts (RM101), short sentences, comparative numbers, and the main limitation in its last line.
- [ ] The introduction's lead sentences, read in order, give the abstract.
- [ ] Every paragraph opens with its point and ends with a bridge; the introduction has no bold run-in heads.
- [ ] The introduction states the goals once and has a results paragraph with headline numbers.
- [ ] Background and related work are separate sections.
- [ ] Related work opens with "We now categorize", groups by idea, and each family ends with how we relate.
- [ ] The method gives the intuition first, follows a toy example, and contains no experiment counts.
- [ ] The evaluation opens with questions tied to goals, then setup (scenario, data table, grouped baselines, metrics by goal, protocol), then answer-first results, with one headline figure.
- [ ] Limitations form a numbered list with ways forward; the conclusion runs 4–6 sentences.

## Evidence
- [ ] Every number in the text matches its table, figure or results file.
- [ ] Every baseline got its best chance (same tuning rule, authors' code where possible, a reproduced published number).
- [ ] No headline table cell is empty.
- [ ] Results report intervals or effect sizes; zero-event results use the rule of three.
- [ ] Every claim about another method comes from its paper or our own run.

## Sentences
- [ ] Median sentence length ≤ 18 words; none over ~25.
- [ ] Active voice, with "we" for what we did.
- [ ] No filler ("In this paper", "It is worth noting", "extensive experiments") and no inflated words ("novel", "crucial", "groundbreaking").
- [ ] `\emph` only on argument-carrying words, at most one or two per paragraph.
- [ ] One term per concept; each acronym expanded once.
- [ ] One spelling variety (British or American) throughout.

## Figures and tables
- [ ] Each caption opens with the figure's or table's one message.
- [ ] One semantic colour code across all figures; colour-blind safe; meaning never by colour alone.
- [ ] Text ≥ 6–7 pt at final size; no overlaps, clipping or margin overflow in the rendered PDF.
- [ ] Tables: column groups labelled by goal, bold rule stated, "ours" row shaded.

## LaTeX and submission
- [ ] Every reference uses `\cref`, including references into the supplement.
- [ ] No symbol stands for two things.
- [ ] The method name and metric names are macros.
- [ ] No undefined references or citations; no overfull boxes.
- [ ] Page limit met; anonymity checked (no names, acknowledgements, self-identifying links).
- [ ] All notes are off in the submission build.
