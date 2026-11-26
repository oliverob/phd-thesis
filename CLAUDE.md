# PhD thesis: Harnessing Transformations in Quantum Computation

LaTeX thesis (Cambridge PhD template). Main file `thesis.tex`, macros in `Preamble/preamble.tex`, bibliography in `References/references.bib`. Paper sources the chapters were built from live in `source_material/` (reference only, not compiled).

Structure: Chapter 1 Introduction (outside any part), then three parts. Each part opens with `\part{...}` followed by unnumbered opener text (no figures, equations or tables there, since they would be numbered under the previous chapter).
- Part I Fermion-to-qubit mappings (`Chapter2/`): Background · Hybrid mappings · Local JW on the torus
- Part II Coherently boosting QPE (`Chapter3/` and `Chapter4/`): Background · Piecewise QSVT · BSI-QPE · Quantum Metropolis sampling revived
- Part III Trapped-ion experiments (`Chapter5/`): non-abelian HSP on IonQ · duality defects on Quantinuum

**Each part is a mini thesis.** Follow this pattern for every part, including new ones and any restructuring:
1. Part opener (after `\part`): the motivation for the part and its contributions, kept short. No figures, equations or tables.
2. A chapter titled "Background" reviewing the standard material used throughout the part (not just its first chapter). It contains no new results.
3. The research chapters, each with its own introduction and discussion/conclusion.

Background for a part belongs in that part's Background chapter, not in Chapter 1 and not inside a single research chapter.

The folder names `ChapterN/` are historical and now correspond to parts. Part labels are `part:*`. Chapters promoted from former sections kept their `section:*` labels (e.g. `section:hybrid_mappings` is a chapter), so check what a label points to before writing "Section"/"Chapter"/"Part" in front of `\ref`.

## Always mark AI-written text

- Wrap **every** sentence you write or modify in `\aitext{...}` (defined in `Preamble/preamble.tex`; renders magenta so the author can review it).
- Wrap sentence by sentence, one `\aitext{}` per sentence, never a whole paragraph (`\textcolor` cannot span paragraphs).
- This includes section/paragraph headings (`\section{\aitext{...}}`), captions, table cells, list items and footnote text.
- Do not wrap display maths or environments. Wrap the prose sentences around and inside them.
- If you edit an existing unmarked sentence, wrap the edited sentence in `\aitext{}`. Never remove `\aitext{}` from text, and never unwrap text the author has not reviewed.
- Moving the author's text unchanged does not need marking.

## Always write in the author's voice

When learning the style, prefer unmarked text (written by the author) over `\aitext{}` text. The clearest examples of the author's own voice are the discussions/conclusions of the hybrid-mapping, piecewise-QSVT and PEPO sections, and the opening of the Quantum Metropolis chapter.

- British spelling: utilise, initialise, organised, behaviour, favourable, optimised, realise.
- First person plural throughout ("we present", "we show", "our construction").
- Plain, direct declarative sentences. Explain the idea first, then give the technical detail. The occasional short, punchy sentence is fine ("The classical computer is attempting to replicate the interference that physics gives for free on a quantum computer.").
- Favoured connectives: "Hence,", "Therefore,", "Further,", "Furthermore,", "In particular,", "As such,", and mid-sentence ", however, ". Phrases the author uses: "navigate around", "Luckily", "falls down", "It is important to note that", "remarkable", "drastically", "significantly".
- Abbreviations in parentheses: "(e.g. ...)", "(i.e. ...)".
- Contributions are given as enumerated lists with bold labels and section references: `\item \textbf{Label} (Section~\ref{...}): ...`.
- State headline numbers concretely (98% shorter Pauli strings, 1.016 qubits per fermion, 50 times fewer Toffolis) and be honest about limitations and comparisons with prior work.
- Avoid em dashes, rhetorical flourishes, hype words ("groundbreaking", "delve", "crucially" in every paragraph) and padding. Use colons, commas and parentheses instead.
- Cite only keys that exist in `References/references.bib`. Never invent results, numbers, citations or statements of contribution. Leave a `% TODO` comment instead.
