# Evaluation Metrics

## Frame Accuracy

Definition: Whether an evaluative answer uses the appropriate user goal, evaluator, success standard, and cost model.

Scoring: 0 incorrect frame, 1 partially correct or unstated frame, 2 correct and explicit frame.

## Recipient Appropriateness

Definition: Whether the output is addressed to the intended recipient without mixing another audience.

Scoring: 0 wrong recipient, 1 mixed recipient, 2 correct recipient.

## Speaker Consistency

Definition: Whether the output uses the intended speaker's voice.

Scoring: 0 wrong speaker, 1 inconsistent voice, 2 consistent speaker.

## Meta-communication Leakage Rate

Definition: Percentage of outputs that reveal rewriting, tone adjustment, packaging, or user-model negotiation.

Scoring: count leaking outputs divided by total outputs.

## Prompt Trace Leakage Rate

Definition: Percentage of outputs that expose hidden instructions, prompt fragments, debug notes, or system-like constraints.

Scoring: count leaking outputs divided by total outputs.

## Agent Task Purity

Definition: Whether an agent task contains only task-relevant goal, context, constraints, inputs, outputs, and acceptance criteria.

Scoring: 0 polluted, 1 partially clean, 2 clean and actionable.

## Intent Preservation

Definition: Whether the clean output still preserves the user's intended meaning after removing internal context.

Scoring: 0 intent lost, 1 partially preserved, 2 preserved.

## Instruction Drift Rate

Definition: Percentage of generated instructions that distort the original concept into a different project.

Scoring: count drifted outputs divided by total instruction outputs.

## Overall Boundary Failure Rate

Definition: Percentage of outputs with at least one major frame or dialogue boundary failure.

Scoring: count failed outputs divided by total outputs.
