# The Four-Phase Method for Using AI to Write a Paper

Before the end of every phase, you must have the AI write a memo that clearly states what was done, what lessons were learned, and how to lay the groundwork for the next phase. Each new phase must start in a fresh conversation. The reason is that, for a high-quality academic research and writing workflow, current AI systems still do not have a long enough context window. Once the context becomes overloaded, lossy compression starts to happen, and the result is that the AI suddenly becomes much dumber and much less proactive. The following four-phase method has been tested successfully under OpenAI Codex.

## Phase I

### I.1 Seed the AI with strong papers

Feed the AI a set of strong seed papers. Use tools such as `arxiv-to-prompt` or `arxiv2md` so the AI can understand your context and, most importantly, your writing style. Otherwise, the output will read like a class project. This step requires you to already have a habit of collecting good papers.

### I.2 Validate the research value and form a plan

Ask whether the thing I want to do has academic value, whether it is just a generic mainstream topic, and roughly which area has been less explored by others. You can also have the AI search for and compare possibilities from several angles:

- timeliness (can it ride a current trend?)
- storytelling value (cross-domain transfer that solves a pain point, a novel finding, a new paradigm—in short, something with strong “viral” appeal)
- whether the target research questions are worth answering (in terms of scarcity or attention-grabbing value)
- interdisciplinarity
- theoretical depth

A plan must be produced and written down as a document. To support a sufficiently solid paper plan, as a rule of thumb, an IEEE conference paper should usually have at least 20 references, while a journal paper may go up to around 35.

One important point here is to distinguish between the mindset of an engineer and that of a scientist:

- **Engineer:** This system can be made to work this way. That may already be enough for an EI-indexed paper, and possibly even an SCI paper.
- **Scientist:** Why did other systems not work? Is there some hidden pattern that nobody has had time to study, or perhaps an underlying mathematical model? Could this problem be re-examined from a completely new angle and yield a better solution? Can a mathematical model reveal patterns hidden beneath the surface phenomena? This system still does not seem good enough—under what situations does it fail? What do its underlying mathematics, numerical model, or signal flow say? Can the system be improved from another angle, or even rebuilt from the ground up into something fundamentally different? That is the level of thinking needed for patents or strong SCI papers.

At this stage, the AI must reason step by step based on facts, verification, and derivation. Whenever it does not understand something or is uncertain, it should say so directly.

## Phase II

### II.1 Implement, experiment, visualize, and draft

Start implementing the plan from Phase I. Write the code, generate figures from the results, explicitly specify IEEE style, and produce a first draft of the paper. At this stage, let the AI explore as many combinations and techniques as possible so that you obtain sufficient data. This also depends on how much literature and news you normally read, because that is how you know where the real pain points are.

Important note: any program written by AI must output progress updates. Otherwise it may time out, and then the AI will try to simplify the code for you. Ideally, have it generate a Colab notebook. No cell should exceed 300 lines of code. If `.py` files are used, require that no `.py` file exceed 400 lines. Also, everything must strictly follow Hungarian notation; otherwise the codebase will become unmaintainable.

The quality of the figures reflects whether you have accumulated enough good papers as references, especially from journals like *Nature* and *Science*. If you need to re-run experiments, make sure the AI remembers to update the figures in the paper as well. As much as possible, have the AI use `booktabs` for tables. Also make sure it separates the experiment stage from the LaTeX rendering stage; otherwise every paper-formatting update will force you to rerun the simulations, which is extremely frustrating.

You may also divide the whole process from the start into:

- the **raw data layer** (AI will often try to scrape extra data; make sure it preserves the crawler code and labels when it was developed)
- the **experiment layer**
- the **data interaction layer** (raw outputs)
- the **rendering layer** (paper, poster, slides)

### II.2 Professionalize the writing and figures

Have the AI read through the paper, and point out every unprofessional figure and expression so it can fix them. The **Introduction**, in particular, should follow a five-paragraph structure:

1. the big-picture background and why this work matters in a general sense
2. what previous work has done and what common shortcomings remain
3. what inspired this paper
4. an itemized list of the paper’s academic contributions
5. the organization paragraph

The Introduction should be around one to one and a half pages, not overly long.

A contribution should usually not exceed four items. More importantly, a contribution is **not** simply what work you did, because nobody cares about that. A contribution is what novel thing you discovered, what question you answered, and where your theoretical breakthrough or technical innovation lies.

In the **Abstract**, spend at most four lines on background and significance. The rest should focus on your method, highlights, and results. It is better to select only the two results you are most proud of, or the two most distinctive findings, for the abstract.

In the **Related Work** section, it may be necessary to compare your work against others in a list or table of distinctive features.

For the Introduction, you can also use Gemini Pro + NanoBanana to generate a high-level overview figure that captures the whole paper. The method is simply to give it the full LaTeX code of the paper together with a style reference. Again, that requires you to have collected good papers beforehand, otherwise you will not be able to find good stylistic references.

### II.3 Iterate based on errors and weak performance

Let the AI inspect where the system fails or where performance is poor. Have it iteratively improve the research design in your paper and generate a complete full draft.

### II.4 Enforce consistency and remove weak writing

Let the AI read through the paper once again. It must not invent new concepts without human review. Make sure every figure and table is explicitly mentioned in the main text, with no orphan figures or tables. Remove redundancy and self-defensive expressions. Check whether the paper contains a pattern of making a statement and then immediately trying to over-emphasize its importance; if so, remove that. Check all abbreviations and make sure each one is defined the first time it appears.

At a minimum, the first-round technical report should already be at the level of an ordinary conference paper, clearly explaining how the system was built and how it performs. This step also depends on your own reading experience, because otherwise you may not be able to judge the quality level.

### II.5 Document the code and the paper assets

Have the AI document the code and generate Markdown documentation. If necessary, use Doxygen. In particular, clearly explain how every figure and table was generated. For each figure/table—that is, each paper asset—write a short description of what it contains, what it is for, and where the code that generated it is located.

In particular, make sure the project has, and verify, the following two capabilities:

- how to rerun everything from scratch and update all data
- how to update all data, figures, and tables and then regenerate the paper PDF

## Phase III

### III.1 Fix obvious issues in code and writing

Have the AI re-examine both the code and the writing of the paper, and fix all obvious problems that can be seen at a glance.

### III.2 Reorganize the paper around value and story

Based on the existing data and results, reconsider how to reorganize the paper—from the title all the way to the conclusion—so that the research findings become valuable to society and/or form a good story. Then rewrite the whole paper.

### III.3 Remove redundancy and self-defensive language

Remove redundancy and remove self-defensive language.

## Phase IV

### IV.1 Human final pass

After this step, a human should read through the paper carefully and do a final round of polishing: eliminate fake references (with the help of tools such as Sourcely, Paperpal, and Elicit), remove repetitive wording and hallucinations, and give the paper a real human touch.
