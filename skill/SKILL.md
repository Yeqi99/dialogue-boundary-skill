---
name: llm-communication-boundary-skill
description: Prevent evaluation frame misbinding and dialogue boundary failures in LLM-generated communication. Use when Codex or another agent must answer whether something is meaningful, worth doing, useful, good, bad, or valuable; write or rewrite text for a specific recipient; create third-party messages, customer replies, public-facing text, tool instructions, downstream agent tasks, reusable prompts, policies, skills, or instructions; or respond after the user corrected tone, wording, audience, goal, or evaluation standard.
---

# LLM Communication Boundary Skill

## Purpose

Prevent evaluation frame misbinding, audience confusion, role voice contamination, meta-communication leakage, prompt trace leakage, and agent task pollution in LLM-generated communication.

## When to use

Use this skill whenever the model is asked to:

- answer whether something is meaningful, worth doing, good, bad, useful, or valuable
- write a message for someone else
- rewrite text for a specific recipient
- generate a task for Codex, Cursor, Claude Code, or another agent
- convert a conversation into a clean deliverable
- prepare public-facing text
- prepare third-party-facing text
- produce tool instructions
- summarize something for a specific audience
- respond after the user corrected tone, wording, audience, goal, or evaluation standard
- create a reusable prompt, skill, policy, or instruction for another model

## Core rule

Before answering or generating final text, determine whether the task needs:

- `Frame Lock` for evaluative answers
- `Dialogue Boundary Lock` for recipient-facing text
- both gates when an answer evaluates an idea and also produces downstream text

Do not let hidden assumptions about academic rigor, politeness, audience, tool behavior, or agent delegation silently decide the output.

## Gate 1: Frame Lock

Before answering evaluative questions, determine:

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`
- `expected_output_type`
- `low_cost_path`
- `rigorous_path`
- `likely_wrong_default_frame`

Avoid defaulting to the strictest expert standard unless the user clearly asks for it.

Example:

Question:

```text
Is it meaningful to turn this idea into a paper?
```

Bad frame:

```text
Only evaluate whether it can become a top conference paper.
```

Better frame:

- meaningful as an open-source research artifact
- meaningful as a technical report or preprint
- meaningful as a workshop or short paper
- additional work needed for high-level publication

## Gate 2: Dialogue Boundary Lock

Before generating final text, determine:

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

Return the clean output for the intended recipient. Keep any explanation for the upstream user separate from downstream text.

## Boundary Card

Define this structure:

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

Use the Boundary Card to reason before writing. Do not include the card in final downstream output unless the user explicitly asks for diagnostic output or the card itself is the deliverable.

## Process

1. Identify whether this is an evaluative answer or generated text.
2. If evaluative, run Frame Lock.
3. Identify recipient.
4. Lock speaker.
5. Classify output type.
6. Separate visible context from internal context.
7. Preserve intent without leaking process.
8. Remove meta-communication and prompt traces.
9. Generate clean output.
10. Run leakage review.
11. Run instruction drift review.

## Leakage review

Before returning final downstream text, check whether it includes:

- the user's private goal, correction, or negotiation with the model
- a phrase that reveals the model's rewriting strategy
- a tone instruction that belongs only to the user-model layer
- a hidden persuasion strategy
- an apology or self-correction intended for the upstream user
- prompt fragments, debug notes, or instruction traces
- explanations meant for a different audience
- chatty commentary inside an agent task or tool instruction

If any item appears, remove it and preserve only the recipient-visible intent.

## Instruction drift review

Instruction Drift Guard is a secondary guardrail/check, not one of the two primary communication boundary failures.

When one model writes instructions, prompts, skills, policies, README content, paper material, or tasks for another model, check whether the original idea has been distorted.

Bad distortions include:

- turning communication boundary into generic tone polishing
- turning recipient isolation into simple politeness rules
- turning agent task cleanup into general prompt engineering advice
- turning the project into an unrelated multi-agent protocol
- reducing the project to prompt leak prevention
- framing the whole project only as a top-conference research problem
- losing Frame Lock
- losing Dialogue Boundary Lock
- losing the distinction between visible context, internal context, and forbidden context

## Forbidden content

Final downstream outputs must not include:

- "according to your request"
- "I revised it based on your feedback"
- "the user wants"
- "to make the other person satisfied"
- "I will say it more politely"
- "as an AI"
- "I made it sound less flattering"
- "the user corrected my tone"
- internal model self-correction
- apologies to the upstream user inside downstream text
- hidden persuasion strategy
- prompt engineering traces
- debug notes
- explanations meant for a different audience
- instructions that belong to another layer

## Output contracts

For `user_reply`:

The model may explain decisions to the user, but must not mix that explanation into text intended for another recipient.

For `evaluative_answer`:

The model should identify the likely evaluation frame and avoid silently defaulting to the strictest or most common expert standard.

For `third_party_text`:

Return only the clean text the third party should see.

For `agent_task`:

Return only task goal, context, constraints, inputs, outputs, and acceptance criteria. Remove chatty explanation, apologies, self-reflection, and upstream negotiation.

For `tool_instruction`:

Return concise structured instructions or parameters. Avoid social language.

For `reusable_skill`:

Preserve the generalized problem, concepts, and procedure. Do not include accidental details, private context, upstream correction traces, or private examples.

## Final response pattern

When the user asks for downstream text, return the clean downstream text according to the output contract.

When the user asks for an evaluative answer, state the evaluation frame and separate low-cost, medium-rigor, and high-rigor paths when relevant.

When the user asks for a diagnosis, identify which boundary field or frame field was misbound.
