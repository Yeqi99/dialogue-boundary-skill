# Method: Boundary Card

## Overview

Boundary Card is a lightweight structured intervention for LLM communication reliability. It is used before generation to bind the correct frame and dialogue boundary, and after generation to review leakage or drift.

## Fields

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`
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

## Pre-generation use

For evaluative answers, fill the Frame Lock fields:

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`

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
