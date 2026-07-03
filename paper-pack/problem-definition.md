# Problem Definition

## Communication Boundary

A Communication Boundary is the set of assumptions that determines what an LLM output is for, who is speaking, who receives it, which context is visible, and which content must remain internal.

## Frame Boundary Failure

Frame Boundary Failure occurs when an LLM answers an evaluative question using an unintended or inappropriate evaluation frame.

## Evaluation Frame Misbinding

Evaluation Frame Misbinding is a specific frame boundary failure where the model silently binds an evaluation to the wrong success standard, evaluator, cost model, or output target.

Example: judging whether an idea is meaningful only by top-conference standards when the user may be evaluating it as a technical report, preprint, open-source artifact, or portfolio credibility layer.

## Dialogue Boundary Failure

Dialogue Boundary Failure occurs when an LLM generates recipient-facing text that contains content from the wrong communication layer.

Common leaked content includes upstream negotiation, user corrections, model self-reflection, prompt traces, hidden strategy, apologies to the upstream user, or explanations meant for another audience.

## Visible Context

Visible Context is information the intended recipient is allowed to see.

## Internal Context

Internal Context is information that belongs only to the user-model interaction or upstream planning layer.

## Forbidden Context

Forbidden Context is information that must not appear in the final output, even if it helped guide generation.

## Meta-communication Leakage

Meta-communication Leakage occurs when the output reveals how the message was discussed, revised, softened, reframed, or negotiated before delivery.

## Agent Task Pollution

Agent Task Pollution occurs when a downstream agent task includes chatty explanations, apologies, self-protective notes, or upstream correction traces instead of a clean task specification.

## Instruction Drift

Instruction Drift occurs when a model rewrites a skill, prompt, policy, or task in a way that distorts the original concept. In this project, drift often turns communication boundary control into generic tone polishing, politeness rules, prompt engineering, or top-conference-only research framing.
