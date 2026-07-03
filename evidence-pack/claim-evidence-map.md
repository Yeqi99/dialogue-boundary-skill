# Claim Evidence Map

## Claim 1

LLM-generated communication can fail even when the factual content is correct, because the model binds the wrong evaluation frame or dialogue boundary.

Evidence:

- `examples/frame-misbinding.md`
- `examples/third-party-message.md`
- `examples/codex-task.md`
- `tests/cases.jsonl`

Evidence strength: Seed / illustrative. Needs empirical validation.

Recommended wording: "We define and illustrate this failure class."

Do not write yet: "This failure is frequent across deployed LLM systems."

## Claim 2

Evaluation Frame Misbinding occurs when the model silently applies an inappropriate evaluation standard, such as judging a low-cost research artifact by top-conference standards.

Evidence:

- `examples/frame-misbinding.md`
- `paper-pack/problem-definition.md`
- `paper-pack/taxonomy.md`

Evidence strength: Conceptual + illustrative. Needs more real cases.

Recommended wording: "We describe Evaluation Frame Misbinding and provide a seed example."

Do not write yet: "This is the dominant failure mode in evaluative LLM answers."

## Claim 3

Dialogue Boundary Failure occurs when the model mixes user-facing explanation, third-party-facing text, agent tasks, self-correction, or prompt traces.

Evidence:

- `examples/codex-task.md`
- `examples/third-party-message.md`
- `examples/customer-reply.md`
- `tests/cases.jsonl`

Evidence strength: Seed / illustrative. Needs model-output dataset.

Recommended wording: "Seed cases show several forms of Dialogue Boundary Failure."

Do not write yet: "The taxonomy is empirically exhaustive."

## Claim 4

Boundary Card / Communication Boundary Skill is a plausible lightweight intervention.

Evidence:

- `skill/SKILL.md`
- `schema/boundary-card.schema.json`
- `paper-pack/method-boundary-card.md`

Evidence strength: Method proposal. Needs ablation or before/after evaluation.

Recommended wording: "We propose Boundary Card as a lightweight intervention."

Do not write yet: "Boundary Card has been proven effective."

## Claim 5

Instruction Drift is a secondary guardrail issue when one model turns the skill into prompts, docs, or tasks for another model.

Evidence:

- `examples/instruction-drift.md`
- `paper-pack/taxonomy.md`
- `paper-pack/evaluation-metrics.md`

Evidence strength: Secondary diagnostic. Not a primary failure family.

Recommended wording: "Instruction Drift Guard is included to prevent distortion during reuse."

Do not write yet: "Instruction Drift is a third primary communication boundary failure."
