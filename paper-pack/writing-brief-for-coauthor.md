# Writing Brief for Coauthor

Before drafting the paper, review `evidence-pack/` first. The paper should not make claims stronger than the available evidence.

## What this paper should solve

The paper should define and analyze a class of LLM communication failures caused by wrong boundary binding:

- wrong evaluation frame before answering evaluative questions
- wrong dialogue boundary before generating text for a recipient, tool, or downstream agent

The central concept is LLM Communication Boundary Skill, implemented through Boundary Card with two gates:

- Frame Lock
- Dialogue Boundary Lock

## What this paper is not

Do not write it as:

- an AI politeness guide
- a customer-service response template collection
- a generic prompt-engineering paper
- a prompt leak prevention paper only
- a complex multi-agent protocol
- a top-conference paper generator
- a claim that the problem has been fully solved

## What to emphasize

- These errors are different from factual hallucination.
- The model can be fluent and still wrong because it used the wrong evaluation frame or recipient boundary.
- Frame Lock prevents the model from silently applying the strictest or most common expert standard.
- Dialogue Boundary Lock prevents internal negotiation, prompt traces, self-correction, and wrong-audience explanation from entering final text.
- Instruction Drift Guard protects the concept when another model rewrites it.

## Abstract direction

Start with the practical observation: LLMs mediate communication across users, third parties, tools, and agents. Then define the failure class. Then introduce Boundary Card and the two gates. End with taxonomy, dataset design, and evaluation plan.

## Experiment organization

Use CBC cases. Compare direct prompting with Boundary Card prompting. Evaluate across:

- evaluative answers
- third-party messages
- customer replies
- agent tasks
- tool instructions
- reusable skill generation

Use human annotation first. Automated scoring can be added later as an auxiliary analysis.

## What is currently missing

- Verified related-work citations
- A completed dataset beyond the seed cases
- Human annotation results
- Model comparison results
- Statistical analysis
- A stronger theoretical framing if targeting a high-level venue

## Suggested division of work

- Author A: introduction, problem definition, taxonomy
- Author B: related work and positioning
- Author C: dataset construction and annotation guideline
- Author D: experiment execution and metrics
- Author E: discussion, limitations, and final editing

## First writing task

Draft a technical report version first. Do not over-optimize for top-conference framing before the core problem, taxonomy, and examples are stable.
