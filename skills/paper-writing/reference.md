# Paper-writing reference

The full rules behind `SKILL.md`. Human-readable version, with figures and longer examples:
https://sustainability-lab.github.io/handbook/writing-papers.html

Examples use **Kestrel**, an invented paper that counts birds from cheap phone recordings. Its numbers are made up.

---

## 1. Structure: one abstract line = one intro paragraph = one section

| Abstract line | Intro paragraph | Section |
|---|---|---|
| 1 Context | Where the field is now | Background |
| 2 Motivation | The problem, and who has it | Problem setup |
| 3 Prior art | Why existing work falls short | Related work |
| 4 Insight (optional) | What explains the gap | Analysis |
| 5 Approach | What we do | Method |
| 6 Evaluation | How we test it | Evaluation: setup |
| 7 Results | What we found, in numbers | Evaluation: results |
| 8 Conclusion | What it means, and its limits | Limitations and conclusion |

Write the abstract first. Test: the intro's lead sentences, read in order, should read like the abstract.

## 2. Title

- Name plus one line of what it does and where it applies. *Kestrel: Few-Shot Bird Counting from Cheap Phone Recordings.*
- A name people can say; if an acronym, make it spell the subtitle.
- No word the paper does not earn (novel, robust, real-world, a term never argued).
- Keep true scoping words.
- Method name in a macro: `\newcommand{\method}{Kestrel\xspace}`.

## 3. Abstract (RM101)

- Parts: context, motivation, prior art, (insight), approach, evaluation, results, conclusion. 7–8 lines; a line may hold two short sentences. Roughly 150–250 words.
- Sentences of 10–20 words; none over ~25.
- Comparative numbers: "83%, against 61% for the best baseline".
- Main limitation in the last line.
- No filler: "In this paper", "extensive experiments", "demonstrates the effectiveness".

Example (after):
> Bird counts tell ecologists how habitats change. Volunteers now record birdsong on cheap phones, at a scale no survey team can match. But phone audio is noisy, and most species have only a handful of labelled calls. Existing classifiers need hundreds of clean calls per species. On phone audio, their accuracy drops from 91% to 54%. We find that the phone's microphone, not the bird, causes most of this drop. We present Kestrel, which learns to undo each phone's microphone before it classifies a call. Kestrel needs only five labelled calls to add a new species. We test it on 12,000 clips from 40 phone models and 150 species, against six baselines. Kestrel reaches 83% accuracy on phone audio, against 61% for the best baseline. That baseline needs a hundred labelled calls per species; Kestrel needs five. Cheap phones can thus support bird surveys at scale. Kestrel still fails on overlapping calls, which we leave to future work.

## 4. Introduction

- One paragraph per abstract line, same order.
- Lead sentence states the point. Bad: "Bird monitoring has a long history." Good: "Existing bird classifiers fail on phone audio."
- Last sentence bridges. A question before the insight works well: "So why does accuracy collapse on phones?"
- No bold run-in heads ("**Challenges.**"). The lead sentence does that job.
- State goals once and reuse them (G1, G2, ...).
- Include a results paragraph with headline numbers.
- 3–5 contributions, ideally in prose.
- Caveats at the end, not before the method is known.

## 5. Background and related work (separate sections)

### Background
- Open with why it exists: "We now describe how phone microphones distort sound, because Kestrel must undo that distortion."
- Plain words, one analogy or picture: "a phone colours sound the way a tinted window colours light".
- Define every symbol the method uses, once.
- End with the two or three facts the method builds on.
- Place it before related work when the grouping of prior work depends on it.

### Related work
- First sentence: "We now categorize prior work by <axis>." Choose an axis that matters for the contribution (what methods need, where they act, what they assume).
- One family per paragraph; a short run-in head is fine here; verdict first.
- Close every family with how we relate: "Like them, Kestrel classifies calls with a neural network; unlike them, it needs five calls per species, not hundreds."
- Group by idea, never by date. The comparison table uses the same groups.
- Every claim about another method comes from its paper or our own run; say which.

## 6. Method

- Intuition first: one picture, 3–5 sentences. "Each phone colours the sound in its own way. We learn that colour and remove it."
- Subsections are plain questions: "What distorts the audio?", "How do we undo it?", "When do we trust it?"
- Inside each step: why (one sentence) → toy example (2–4 sentences, small real numbers) → how (bullets, one equation) → guarantee (one plain sentence; proof in the appendix).
- Toy example in two dimensions, followed through every step, numbers verified in code. "Sound has two bands. A bird sings (4, 2). Phone A halves the high band and records (4, 1). Kestrel learns gain (1, 0.5) and divides it out: (4, 2)." Say once what changes at full scale.
- Generic, no counts: "several phones" in the method; "40 phone models" in the evaluation.
- Few equations. Textbook results are design guarantees, not contributions.
- Clean notation: never one symbol for two things.

## 7. Evaluation

- Name: *Evaluation*. Exemplar: Gemello (KDD 2016), https://www.kdd.org/kdd2016/papers/files/adp1036-batraA.pdf.
- Open: "We now evaluate X against the goals of Section 1." Then numbered questions Q1–Qn, each tied to a goal.
- Setup:
  - Scenario sentence ("Our setup mimics a volunteer survey, where ..."); derive the protocol from it.
  - Data: why this data; one table of every data set (size, purpose, what it tests); test data disjoint from training data, stated plainly.
  - Baselines grouped, each with a reason (standard, strongest, closest, practitioner's first choice). "We give every baseline its best chance": one tuning rule, authors' code where possible, one reproduced published number.
  - Metrics listed by goal, defined so they can be recomputed, direction stated.
  - Protocol: seeds, intervals, tests, multiple-comparison correction.
  - Reproducibility: what is released.
- A new metric gets a subsection inside Evaluation: open with the failure it fixes (own numbers), list failures with fixes, formula last.
- Results:
  - Each subsection is a question, answered in its first sentence. "Does Kestrel work on phones it has never seen? Yes, nearly as well: 79% on ten unseen models, against 83% on seen ones."
  - One headline figure, ideally a trade-off plot with ours alone in the good corner.
  - Why each baseline family fails, one bullet each.
  - Oracles or upper bounds to separate components.
  - Sensitivity analyses that answer deployment questions.
  - Effect sizes with intervals; rule of three for zero events (0 of n ⇒ ≤ 3/n at 95%).
  - Failure cases with causes.

## 8. Analysis

- "Why does it work?" questions in method order, each answered in the first sentence.
- Both sides of every design choice: too little fails, too much hurts, show the sweet spot.
- Admit what you cannot explain.

## 9. Limitations and conclusion

- Limitations: numbered; each has an *italic verdict*, evidence with numbers, and a way forward. "*Kestrel fails on overlapping calls.* When two species sing at once, accuracy falls to 41%. Source separation is a natural next step."
- Conclusion: 4–6 sentences mirroring the abstract's end: problem → insight → method → headline numbers → takeaway.

## 10. Sentences

- Active voice with "we". Passive only when the actor does not matter ("The clips were recorded between 2019 and 2023").
  - "It is observed that accuracy drops" → "Accuracy drops".
  - "Experiments were conducted on 12,000 clips" → "We test Kestrel on 12,000 clips".
  - "A novel framework is proposed" → "We present Kestrel".
- Median 15–18 words, maximum ~25. Split three-clause sentences. One idea per sentence.
- `\emph` for contrast and new terms on argument-carrying words (*every*, *only*, *not*, *before*); one or two per paragraph; never decoration.
- Cut filler: "In this paper, we propose" → "We present"; "It is worth noting that X" → "X"; "due to the fact that" → "because"; "significantly better" → the numbers.
- Write like a person: no inflated words (novel, crucial, groundbreaking), no stacked hedges, no rhythmic three-item lists.
- No bare numbers: comparison, unit, n.
- One term per concept; acronyms expanded once.
- One spelling variety (lab default: British, unless co-authors prefer otherwise).

## 11. Hero figure (Figure 1)

Figure 1 is the picture on page 1 or 2 that a reviewer sees before reading the introduction. Many reviewers decide how carefully to read from the title, the abstract and this figure.

A reader should answer three questions in about ten seconds:

1. **Problem.** What is hard or missing today?
2. **Idea.** What is the one thing that changes the situation?
3. **Payoff.** What becomes possible, or what improves, and by how much?

It is a visual abstract, and usually *not* the architecture diagram. That diagram answers "how is it built?", which is a question for Figure 2.

**What to lead with.** Ask which sentence of the abstract a reviewer should repeat to the other reviewers, and draw that sentence.

| If the main claim is | Lead with |
|---|---|
| "We can now do X, which nobody could." | **Payoff**: the outputs themselves, on real inputs |
| "We do X better, faster or cheaper." | **Payoff**: the evidence, with the numbers on the picture |
| "One simple idea solves X." | **Idea**: one real example going in, the idea, the result coming out |
| "One model handles many settings." | **Idea**: many real inputs, one model, many real outputs |
| "Everyone has missed problem X." | **Problem**: a failure, measured or shown |
| "Here is a dataset or a benchmark." | **Scope**: real samples, counts, and one item from start to score |
| "We make three contributions of equal weight." | **Scope**: one panel per contribution |

**Lab default for an applied paper.** A strip of three panels: problem, idea, payoff, in that order, on *one real example*, with *one number*. An applied reviewer first has to believe the problem is real, so the problem gets its own panel. Give the most space to the strongest panel: a capability paper widens the payoff; a paper with one clever idea widens the idea.

**How to make one.**

1. **Write the sentence first.** "Today, [problem]. We [idea]. Now, [payoff with a number]." If you cannot complete it, the paper is not ready for a figure.
2. **Choose what leads,** from the table above. Give that panel the most space.
3. **Pick one real example and follow it through every panel** (one home, one thermal frame, one city). Real data beats icons. Every image must come from the run it claims to show.
4. **Sketch it on paper in week one,** with three or four groups and one reading direction. Show the sketch to a labmate before opening any drawing tool.
5. **Add one number,** on the figure itself, with the baseline beside it.
6. **Colour only what is new.** Grey for existing work, one accent colour for the contribution, and the same colour code as the rest of the paper.
7. **Build it at its final width.** Draw in Figma, draw.io, Inkscape or TikZ, export a vector PDF, and check that the smallest text is at least 6–7 pt in the compiled paper. Plots inside it follow LaTeXify.
8. **Place it at the top of page 1 or 2.** Use `figure*` for a full-width figure. The ACM template also has `teaserfigure`, which sets it under the title.
9. **Open the caption with the message,** as for every figure.
10. **Run the ten-second test.** Show the figure, without its caption, to someone outside the project for ten seconds. Ask for the problem, the idea and the payoff. Redraw whatever they miss.

**Common failures.**

- **It is the system diagram.** Twenty boxes and thirty arrows show effort, not an idea.
- **It has boxes where pictures should be.** A box labelled "Encoder" or "Modeling" tells the reader nothing.
- **It uses clip-art** in place of real inputs and outputs.
- **It shows the method but not why it matters,** or the result but not what produced it.
- **It needs the caption to decode it,** or its text is too small to read at paper size.
- **Its words differ from the abstract's.** Use the same names for the same things.
- **It has a spelling mistake.** Spell-checkers do not read images, so proofread every label.

The handbook shows fifteen published first figures read this way: https://sustainability-lab.github.io/handbook/writing-papers.html#hero-figures

## 12. Figures

- One message per figure, stated in the first (bold) sentence of the caption; captions self-contained.
- Simple over complete; step-by-step panels, one idea per panel; detail to the appendix.
- One semantic colour code for the paper, stated once (e.g. orange = problem, blue = ours, green = good outcome, grey = baseline/neutral). Neutral categories get non-semantic colours.
- Movement as a colour change: orange input → blue arrow → green result.
- Okabe–Ito palette; meaning never by colour alone (✓/✗, filled/hollow, direct labels).
- Text ≥ 6–7 pt at final size; check the rendered PDF for overlaps, clipping, overflow.
- One drawing style (TikZ or matplotlib with LaTeXify); plotted numbers read from results files, source noted in a comment.
- A headline result figure (trade-off plot).

## 13. Tables

- Follow Püschel's guide: https://people.inf.ethz.ch/markusp/teaching/guides/guide-tables.pdf (booktabs, no vertical rules).
- Caption: takeaway first, then what the columns mean.
- Column groups labelled by goal ("G1: accurate?").
- No empty headline cells.
- Few columns; extras to the supplement.
- Counts for small n (7/10).
- State the bold/underline rule; shade the "ours" row.

## 14. LaTeX hygiene

- `\cref` everywhere; never hand-type numbers, including the supplement: `\usepackage{xr-hyper}`, `\externaldocument[S-]{supp}`, `\cref{S-tab:x}`. On Overleaf add a `latexmkrc` that builds the supplement.
- Macros for method name, metric names, recurring symbols.
- Author comment macros (`\nb{}` etc.) behind `\ifshownotes`; a `submission.tex` that sets `\shownotesfalse`.
- Label scheme: `sec:`, `fig:`, `tab:`, `eq:`.
- One sentence per source line.

## 15. Review protocol

1. Don't overwrite the author's text: inline comments plus a suggested rewrite after the original, behind the notes switch.
2. Comment on the why, not just the what.
3. Check every moved or rephrased number against its source.
4. Mark inferences with "please check".
5. End with a short review guide: changes by section, runs needed, facts to confirm.
6. Compile in an isolated copy; report errors, undefined references and overfull boxes; look at rendered figures.

## 16. Timeline (suggested, adjust per venue)

- Week −8: abstract and title; figure and table sketches.
- Weeks −8 to −3: experiments; full first draft from week −6.
- Week −3: results frozen; internal review by the adviser and one peer outside the paper.
- Week −2: revise, fill evidence gaps.
- Week −1: checklist, page limit, anonymity, references.
