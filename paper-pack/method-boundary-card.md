# Method: Boundary Card

## Overview

Boundary Card is a lightweight structured intervention for LLM communication reliability. It is used before generation to bind the correct frame and dialogue boundary, and after generation to review leakage or drift.

Instruction Drift Guard is a secondary guardrail/check, not one of the two primary communication boundary failures.

## Fields

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`
- `expected_output_type`
- `low_cost_path`
- `rigorous_path`
- `likely_wrong_default_frame`
- `speaker`
- `recipient`
- `output_type`
- `visible_context`
- `internal_context`
- `forbidden_context`
- `tone`
- `must_include`
- `must_not_include`
- `leakage_risks`
- `instruction_drift_risks`

Frame Lock field meanings:

- `expected_output_type`: The likely form of output the user needs, such as quick advice, technical report, open-source artifact, preprint, workshop paper, formal paper, agent task, or third-party text.
- `low_cost_path`: A practical low-cost path that satisfies the user's likely goal without overfitting to an unnecessarily strict standard.
- `rigorous_path`: A more rigorous path required if the user's goal is formal publication, high-level evaluation, or stronger external validation.
- `likely_wrong_default_frame`: A default evaluation frame the model might incorrectly apply, such as assuming the user wants a top-conference paper when they only need a research-style artifact or technical report.

## Pre-generation use

For evaluative answers, fill the Frame Lock fields:

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`
- `expected_output_type`
- `low_cost_path`
- `rigorous_path`
- `likely_wrong_default_frame`

Then decide whether the answer should be layered into low-cost, medium-rigor, and high-rigor paths.

For generated text, fill the Dialogue Boundary Lock fields:

- `speaker`
- `recipient`
- `output_type`
- `visible_context`
- `internal_context`
- `forbidden_context`

Then generate only content permitted by the selected output contract.

## Post-generation use

After generation, review:

- Does the evaluative answer use the correct frame?
- Does the output address the intended recipient?
- Does the output preserve the speaker voice?
- Does it leak internal context?
- Does it contain meta-communication?
- Does it contain prompt traces?
- Does an agent task stay pure and actionable?
- Does a reusable instruction preserve Frame Lock + Dialogue Boundary Lock?

## Minimal template

```yaml
user_goal:
evaluator:
success_standard:
cost_model:
expected_output_type:
low_cost_path:
rigorous_path:
likely_wrong_default_frame:
speaker:
recipient:
output_type:
visible_context:
internal_context:
forbidden_context:
tone:
must_include:
must_not_include:
leakage_risks:
instruction_drift_risks:
```
