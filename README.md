# Dialogue Boundary Skill

Dialogue Boundary Skill is a lightweight reusable skill for preventing audience confusion, role voice contamination, meta-communication leakage, prompt trace leakage, and agent task pollution in LLM-generated communication.

It helps AI systems distinguish between:

- what the user says to the model
- what the model says back to the user
- what should be sent to a third party
- what should be sent to a tool or downstream agent
- what must remain internal

The first version is intentionally small: documentation, a reusable skill file, a schema, examples, and test cases. It is not a website, backend service, npm package, or multi-agent framework.

## Problem Definition: Dialogue Boundary Failure

A dialogue boundary failure happens when an LLM generates, rewrites, summarizes, or delegates text without first deciding:

1. Who is speaking?
2. Who is receiving the text?
3. What type of output is being produced?
4. Which context is visible to the recipient?
5. Which context belongs only to the user-model negotiation?
6. Whether the final text leaks meta-communication, tone adjustments, prompt traces, self-correction, or upstream reasoning that the recipient should never see.

The failure is not just "bad tone." It is a boundary error between speakers, recipients, layers, and audiences.

## Why LLMs Mix Boundaries

LLMs are optimized to continue the visible conversation. When a user asks the model to write for someone else, the model sees multiple layers at once:

- the user's instruction to the model
- the intended message to the recipient
- the model's reasoning about how to satisfy the user
- corrections about tone, wording, or audience
- constraints for tools or downstream agents

Without an explicit boundary step, these layers can collapse into one output. That is why a customer email may include "I revised this based on your feedback," or an agent task may include "do not assume the user's GitHub username" even though the downstream agent only needs a clean engineering task.

## Core Concepts

- `speaker`: the entity whose voice the final text should use.
- `recipient`: the person, tool, agent, or audience that will receive the final text.
- `output_type`: the contract for the output, such as `user_reply`, `third_party_text`, `agent_task`, `tool_instruction`, or `reusable_skill`.
- `visible_context`: facts and context the recipient is allowed to see.
- `internal_context`: upstream instructions, negotiation, corrections, or reasoning that must stay between the user and the model.
- `forbidden_context`: specific content that must not appear in the downstream output.
- `clean_output`: the final text after audience, role, and context boundaries are enforced.
- `leakage_review`: a final check for exposed meta-communication, prompt traces, self-correction, or wrong-audience explanations.

## Typical Failure Types

- `audience_confusion`: the output speaks to the wrong person or mixes multiple audiences.
- `role_voice_contamination`: the final text uses the model's voice instead of the locked speaker's voice.
- `meta_communication_leakage`: the output reveals how the user and model discussed the message.
- `prompt_trace_leakage`: the output exposes instructions, prompt fragments, or hidden constraints.
- `agent_task_pollution`: a downstream agent receives chatty explanations or upstream negotiation instead of a clean task.
- `self_correction_leakage`: the output includes apologies, revisions, or self-reflection meant only for the user.
- `instruction_drift`: a reusable prompt, policy, skill, or task is transformed into a different problem.

## Usage Workflow

1. Identify the recipient.
2. Lock the speaker.
3. Classify the output type.
4. Separate visible context from internal context.
5. Preserve the user's intent.
6. Remove meta-communication.
7. Generate clean output.
8. Run leakage review.
9. Run instruction drift review when producing instructions, prompts, skills, policies, or tasks for another model.

## Minimal Example

User instruction:

```text
Rewrite this reply for a customer. Make it firm but not too apologetic.
```

Boundary Card:

```yaml
speaker: company support representative
recipient: customer
output_type: third_party_text
goal: clarify the next step and maintain a professional tone
visible_context:
  - the customer needs a status update
internal_context:
  - the user requested a less apologetic tone
forbidden_context:
  - mention of tone adjustment
  - "based on your feedback"
  - "I made this less apologetic"
```

Bad output:

```text
I adjusted the reply so it sounds firm but not too apologetic: We are reviewing the issue...
```

Clean output:

```text
We are reviewing the issue and will share the next update once the review is complete. At this stage, the current timeline remains unchanged.
```

## Using This Skill in Agent Systems

In Codex, Cursor, Claude Code, or other agent workflows, use this skill before generating text that will leave the current conversation layer:

- For `user_reply`, explain decisions to the user separately from any downstream text.
- For `third_party_text`, return only the text the third party should see.
- For `agent_task`, return only task goal, context, constraints, inputs, outputs, and acceptance criteria.
- For `tool_instruction`, return concise structured instructions or parameters.
- For `reusable_skill`, preserve the generalized problem and avoid private examples, upstream corrections, or accidental details.

When handing work to a downstream agent, do not include self-protective notes, hidden assumptions, apologies, or prompt-engineering traces. The task should be understandable without exposing how it was negotiated upstream.

## 中文简介

Dialogue Boundary Skill 是一个轻量级可复用技能，用于解决大模型在生成文本时常见的受众错配、角色语气污染、元沟通泄漏和 Agent 任务污染问题。

它关注的不是“让 AI 更会说话”，而是让 AI 在生成文本前明确：

- 这段话是谁说给谁听的？
- 哪些上下文可以被接收方看到？
- 哪些内容必须留在内部？

这个项目的核心是不变量：在最终文本生成前锁定 `speaker`、`recipient`、`output_type`、`visible_context`、`internal_context` 和 `forbidden_context`，并在输出前检查 dialogue boundary failure 与 instruction drift。

## Repository Contents

```text
README.md
LICENSE
skill/SKILL.md
schema/boundary-card.schema.json
examples/codex-task.md
examples/third-party-message.md
examples/customer-reply.md
examples/instruction-drift.md
tests/cases.jsonl
```

## License

MIT
