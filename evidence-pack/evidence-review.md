# Evidence Review

## Current review conclusion

The current repository is strong enough to support:

- a technical blog post
- an open-source project explanation
- a technical report draft
- a preprint draft focused on problem definition, taxonomy, method proposal, and seed cases

It partially supports:

- a workshop paper
- a short paper

For those targets, the project should add a small dataset and at least lightweight human annotation.

It does not yet support:

- a strong empirical paper
- a top-conference-level claim
- claims of measured effectiveness
- claims about failure frequency across models

## Why the current evidence is useful

The repository already provides:

- clear problem definitions
- a taxonomy of failure types
- a structured method proposal
- a schema for Boundary Cards
- seed bad/good examples
- a dataset and experiment plan
- explicit claims and limitations

This is enough for early research writing, but not enough for strong empirical conclusions.

## Main evidence risks

- Claims may become stronger than the evidence.
- Seed cases may be mistaken for empirical results.
- The paper may imply that Boundary Card has been validated.
- The paper may imply model failure rates without data.
- Instruction Drift may be mistaken for a third primary failure family.

## Recommended writing strategy

Write the first version as:

- problem definition
- taxonomy
- method proposal
- dataset design
- seed cases
- experiment plan
- limitations

Avoid saying the method is empirically effective until direct prompting vs Boundary Card comparisons have been run.
