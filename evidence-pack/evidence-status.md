# Evidence Status

## A. Existing project evidence

The current repository already contains:

- `README.md`: project definition, two-gate framing, minimal bad/good examples
- `skill/SKILL.md`: reusable agent-facing procedure
- `schema/boundary-card.schema.json`: structured Boundary Card fields
- `examples/`: illustrative cases for frame misbinding, dialogue boundary failures, and instruction drift guard
- `tests/cases.jsonl`: 15 seed cases with bad/good outputs
- `paper-pack/`: paper brief, terminology, taxonomy, method, dataset design, annotation guideline, experiment plan, metrics, outline, and drafts

This supports a problem definition, taxonomy, method proposal, and seed-case-based technical report draft.

## B. Seed / illustrative evidence

Examples and tests provide seed evidence. They show the form of possible failures and the intended correction pattern.

They can support wording such as:

- "We identify a class of communication boundary failures."
- "We provide illustrative examples."
- "We propose a lightweight Boundary Card method."
- "We design a dataset and evaluation protocol."

They cannot support wording such as:

- "The method reduces failures by X%."
- "Most LLMs exhibit this failure at rate Y."
- "Human annotators confirmed the taxonomy."
- "Boundary Card has been validated across models."

## C. Missing empirical evidence

The repository does not yet include:

- real model-output collection
- human annotation results
- multi-model comparison
- direct prompting vs Boundary Card comparison
- statistical results
- real user scenario data
- verified related-work citations

These should be marked as TODO before making strong empirical claims.
