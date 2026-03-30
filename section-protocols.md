# Section Protocols

Use this reference when the request targets a specific paper section, a technical report section, a result-documentation artifact, when the source text is immature or diffuse, or when a rewrite needs a stricter checklist than the main skill provides. Apply the same PI-style standard across all such outputs unless the user explicitly requests a different tone.

## Pipeline Discipline

- Keep raw data acquisition and cleaning separate from experimental code.
- Document and save every URL, command, and script used to download or acquire data from any source.
- Use Hungarian naming conventions for variables, result identifiers, and asset names unless the user explicitly requests a different naming scheme.
- Keep experimental code separate from reporting code.
- Route all metrics, ablations, and benchmark outputs through structured artifacts such as CSV, JSON, or databases before rendering.
- Regenerate figures, tables, and manuscript numerics from those structured artifacts rather than by manual transcription.
- When proposing project structure, make the dependency chain explicit: raw data to experiments to result store to rendering.
- Place different pipeline layers in separate folders or clearly separated directory trees for clarity and maintainability.

## Automation Standards

- Create a complete project backup or snapshot before modifying core method mechanisms or experimental logic.
- Add progress indicators to long-running scripts instead of replacing rigorous computation with a smaller shortcut.
- Preserve computational fidelity when the user requests publication-grade results.
- Design rerun paths so that updated metrics automatically propagate into figures, tables, and paper text.
- Prefer deterministic filenames, clear output directories, and stable schemas for result artifacts.
- Maintain summary memos for all generated research-output assets, including figures, tables, papers, presentations, posters, and slides.
- Maintain a dedicated `memo/` folder, or an equivalently clear memo directory, for rebuild notes, modification records, and lessons learned.
- Maintain Markdown provenance notes for figures and tables so the generation workflow, inputs, and outputs remain reproducible.
- Immediately after creating a figure or table, record a concise summary of what it shows for later manuscript integration.
- Immediately after creating any research-output asset, record a concise memo describing its content, purpose, target use, and dependencies.
- After a figure or table is approved by the user, update its provenance note to reflect the accepted version.
- After any asset is approved by the user, update its summary memo to reflect the accepted version.
- After each user-instructed rebuild or modification, create or update a memo entry recording what was done, why it was done, the resulting change, and lessons learned.
- Record the backup point in the relevant documentation when a mechanism-level revision is accepted.

## Abstract

- Keep the abstract to one paragraph.
- Do not exceed approximately one-fifth of a page unless the venue or user gives a different length constraint.
- Spend at most one or two sentences on background.
- Keep the abstract style concise, direct, and evidence-led.
- Open with the problem in one sentence and do not overteach background.
- Frame the task clearly by stating what is being analyzed, classified, predicted, compared, or evaluated.
- Introduce the method directly rather than narrating project history.
- Introduce the method or evaluation setup plainly before rhetoric.
- State the real novelty, not implementation housekeeping.
- Report only the two or three most significant findings or novelties, following the user's requested count when provided.
- Report those findings with concrete outcomes when they are available.
- Prioritize evidence-backed abstract results. Use quantitative values when they best support the core claims, but allow concise qualitative synthesis when it conveys the key takeaway more effectively. Avoid unsupported qualitative praise and unnecessary numeric overload.
- Keep the language technical but readable, maintain a PI-style tone with no hype or padding, and let evidence rather than exaggerated superiority claims support the abstract.
- Keep the abstract self-contained; do not rely on internal tool names or unexplained abbreviations.

## Introduction

- Build the introduction in five paragraphs:
  1. Background and field context.
  2. Specific gap or pain point.
  3. Core idea and why it should work.
  4. Itemized contributions and discoveries.
  5. Paper organization.
- Make the contribution paragraph evidentiary; include proved properties, discovered behaviors, or measured gains when supported.

## Methodology

- Define notation once and use it consistently throughout the section.
- Move from the system-level framing to the algorithmic components in a deductive order.
- Give each module a reason to exist.
- Tie losses, constraints, architectural blocks, and hyperparameters to a design principle or observed failure mode.

## Evaluation

- Describe setups as evaluation, study, or simulation scenarios unless the user provides an established internal term worth preserving.
- Report not only what changed numerically, but what the pattern implies about the model or system behavior.
- Surface failure modes, tradeoffs, and edge cases where the method underperforms.
- Verify that reported numbers trace back to structured result artifacts rather than ad hoc notebook output.
- Report no orphaned result in the paper; every reported result must be supported by figures, tables, or documented result artifacts.

## Results Documentation

- Document figures, tables, metrics, and ablations in a form that can stand alone outside the paper when needed.
- State what each result shows, why it matters, and what limitation or caveat should accompany it.
- Keep narrative claims synchronized with the underlying result artifacts and provenance notes.
- Keep each research-output asset synchronized with its summary memo so documentation, presentation material, and manuscript assets do not drift apart.

## Related Work

- Organize prior work by approach, assumptions, or research philosophy.
- Contrast the present work against those groups instead of enumerating papers serially.
- Use citations to support synthesis, not as a substitute for synthesis.

## Language Cleanup

Remove or replace the following patterns during revision:

- Non-PI-style writing that is padded, hype-driven, weakly evidenced, or rhetorically inflated.
- Prose that is logically disjointed, hard to follow, or thin in technical or scientific insight.
- Abbreviations that appear before they are defined.
- Newly coined concept names or awkward noun phrases that have not been approved by the user.
- Pedagogical exposition of standard concepts.
- Empty intensifiers such as `very`.
- Generic praise words such as `good`.
- Weak quantity words such as `a lot`.
- Sales language, hype, or promotional framing.
- Unsupported speed claims such as `fast`.
- Hand-wavy qualifiers such as `plausible` or `contextual`.
- Sentences that first state a fact and then separately announce that it matters.

## LaTeX Guardrails

- Keep figure and asset references local to the current folder, for example `\includegraphics{figures/example}`.
- Require each paper-asset label to match its filename stem exactly unless the user explicitly requests a different convention.
- Use only the `[h]` float option for figures and tables unless the user explicitly requests a different placement rule.
- Return clean LaTeX without mixing prose commentary into the code unless explicitly requested.
- Preserve user-provided labels, citation keys, and macros unless they are clearly broken.
- Use `booktabs` conventions for tables.
- For IEEE papers, use `\resizebox` for every table unless the user explicitly requests a different approach.
- Avoid second-line wrapping in the first column of tables whenever possible by adjusting wording, abbreviations, or layout.
- Avoid abbreviated terms in figures and tables whenever possible; if one must appear, provide a footnote in the paper asset that defines it.
- Favor professional scientific graphics appropriate for IEEE venues and high-end journal presentation quality.
- Create a PNG proof for each figure and inspect it directly before manuscript insertion.
- Inspect generated figures before insertion and verify legibility, label quality, alignment, and consistency with the manuscript narrative.
- Render each table after creation or update and visually inspect the rendered table before manuscript insertion or acceptance.
- Use a white or transparent background for all flow diagrams.
- Use high-quality vector graphics for flowgraphs and flow diagrams unless the user explicitly requests another format.
- Allow no orphaned paper asset of any kind. Ensure each figure, table, algorithm, equation block, appendix asset, or other manuscript asset is explicitly referenced in the text and placed in the subsection where it is actually used.
- When revising a manuscript, add or tighten the surrounding prose so each cited asset is interpreted rather than merely mentioned when interpretation is appropriate.
- Do not cluster paper assets at the beginning of the manuscript or section merely for convenience; insert them near the subsection that uses them.
- After modifying any section, and during full-paper rereads and proofreading reviews, visually inspect all related figures and tables again rather than assuming earlier checks were sufficient.
- After updating any paper asset, re-read the paper body from Methods through Conclusion and verify consistency of claims, references, result interpretation, and discussion.
- After any update to code, paper assets, or manuscript text, run a strict consistency review across code, paper, and documentation for terminology consistency, configuration-description consistency, claims-versus-results consistency, and section-level logical coherence, then present a findings list with exact file references.
- Check figure captions and table captions explicitly for language quality, logical consistency, and alignment with the referenced content.
- If an orphaned paper asset cannot be integrated cleanly, ask the user for permission before removing it or any related asset.
- Preserve established manuscript terminology by default, and ask the user before introducing new labels for concepts, modules, or system components.
- Keep each figure and table aligned with its Markdown generation note so manuscript assets and documentation do not drift apart.
