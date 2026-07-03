# Missing Evidence

Before making strong empirical claims, add:

- 50-100 CBC seed cases
- direct prompting outputs from at least 2-4 models
- outputs after adding Boundary Card / Communication Boundary Skill
- completed annotation guideline use on the dataset
- at least 2 annotators and an agreement check
- if two annotators are too costly, a single-annotator pass with limitations clearly stated
- per-failure-type counts
- before/after comparison of Boundary Skill behavior
- qualitative error analysis
- real related-work citations
- documented model, prompt, and sampling settings
- a clear distinction between seed cases and empirical evaluation cases

## TODO list for a paper version

- TODO: Expand CBC beyond illustrative cases.
- TODO: Collect baseline model outputs.
- TODO: Collect Boundary Card model outputs.
- TODO: Annotate outputs using `paper-pack/annotation-guideline.md`.
- TODO: Add inter-annotator agreement if possible.
- TODO: Add verified references in `paper-pack/related-work-map.md`.
- TODO: Update `paper-pack/evaluation-metrics.md` with actual result tables only after experiments are run.
