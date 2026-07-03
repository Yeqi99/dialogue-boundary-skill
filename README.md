# LLM Communication Boundary Skill

LLM Communication Boundary Skill is a lightweight reusable skill for preventing evaluation frame misbinding and dialogue boundary failures in LLM-generated communication.

It helps AI systems decide:

- what goal and evaluation frame the answer should serve
- who is speaking
- who is receiving the text
- what context is visible
- what must remain internal
- what must not appear in final output

中文简介：

LLM Communication Boundary Skill 是一个轻量级可复用技能，用于防止大模型在生成文本时发生评价框架错配和对话边界失效。

它关注的不是“让 AI 更会说话”，而是让 AI 在回答或生成文本前先明确：

- 这个回答服务于什么目标和评价标准
- 这段话是谁说的
- 这段话是说给谁听的
- 哪些上下文可以暴露
- 哪些内容必须留在内部
- 哪些内容不能出现在最终文本里

## One-Sentence Definition

LLM Communication Boundary Skill is a pre-generation and pre-delivery checklist that locks the evaluation frame, speaker, recipient, output type, visible context, internal context, and forbidden context before an LLM answers or generates text.

## Two Core Problems

### Frame Boundary Failure / Evaluation Frame Misbinding

When a user asks whether an idea is meaningful, valuable, useful, good, bad, or worth doing, the model often silently supplies an evaluation frame. If that frame is wrong, the answer can be misleading even when the facts are correct.

Example:

```text
User: Is it meaningful to turn this idea into a paper?
```

A bad answer may only evaluate whether the idea is ready for a top conference paper. A better answer first asks what kind of value is being evaluated: open-source credibility, a technical report, a preprint, a workshop paper, or a high-level archival publication.

### Dialogue Boundary Failure

When a model writes text for a third party, tool, downstream agent, customer, HR, teacher, public audience, or another recipient, it may mix in content that should remain internal:

- user-model negotiation
- the user's correction of tone or wording
- model self-reflection or apology
- prompt traces
- hidden persuasion strategy
- explanations meant for the user
- chatty notes inside downstream agent tasks

The core issue is that the model failed to separate `speaker`, `recipient`, `output_type`, `visible_context`, `internal_context`, and `forbidden_context`.

## The Two Gates

### Gate 1: Frame Lock

Use Frame Lock before answering evaluative questions.

Determine:

- `user_goal`
- `evaluator`
- `success_standard`
- `cost_model`
- `expected_output_type`
- `low_cost_path`
- `rigorous_path`
- `likely_wrong_default_frame`

Avoid silently defaulting to the strictest expert standard unless the user clearly asks for it.

### Gate 2: Dialogue Boundary Lock

Use Dialogue Boundary Lock before generating recipient-facing text.

Determine:

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

Return only the clean output appropriate for the recipient and output type.

## Instruction Drift Guard

Instruction Drift Guard is a guardrail, not the main project. Use it when an agent rewrites this skill into a prompt, README, policy, paper outline, or downstream instruction.

It checks that the project has not drifted into:

- generic tone polishing
- ordinary politeness rules
- generic prompt engineering
- a complex multi-agent protocol
- simple prompt leak prevention
- a top-conference-only research framing

The core must remain: `Frame Lock + Dialogue Boundary Lock`.

## Minimal Bad/Good Example

Question:

```text
Is it meaningful to turn this idea into a paper?
```

Bad answer:

```text
Not really. Without benchmarks, baselines, and a systematic experiment, it is unlikely to be accepted by a top conference.
```

Problem:

The model silently used a strict top-conference evaluation frame. The user may have been asking whether the idea is meaningful as a low-cost research artifact, technical report, preprint, or project credibility layer.

Better answer:

```text
It depends on the target frame. As an open-source research artifact or technical report, it is meaningful if it clarifies the problem, gives reusable terminology, and provides representative cases. As a workshop or short paper, it needs a sharper problem definition, related-work positioning, a small dataset, and lightweight evaluation. For a high-level conference submission, it would need stronger experiments, baselines, statistical analysis, and broader theoretical framing.
```

Third-party text example:

```text
Bad: According to your request, I will make this sound more polite: Hello, the previous wording was not ideal...

Good: Hello, I would like to clarify the current situation and share the next confirmed step.
```

## Using This Skill in Agent Systems

Use this skill in Codex, Cursor, Claude Code, or multi-agent systems when an output crosses a communication boundary.

- For `evaluative_answer`, identify the evaluation frame before judging value.
- For `user_reply`, explain reasoning to the user, but keep it separate from downstream text.
- For `third_party_text`, return only the clean text the third party should see.
- For `agent_task`, return only task goal, context, constraints, inputs, outputs, and acceptance criteria.
- For `tool_instruction`, return concise structured instructions or parameters.
- For `reusable_skill`, preserve the general concept without private examples or upstream correction traces.

## Repository Structure

```text
README.md
LICENSE
skill/SKILL.md
schema/boundary-card.schema.json
examples/
  frame-misbinding.md
  codex-task.md
  third-party-message.md
  customer-reply.md
  instruction-drift.md
tests/
  cases.jsonl
paper-pack/
  README.md
  paper-brief.md
  title-options.md
  abstract-options.md
  problem-definition.md
  core-concepts.md
  taxonomy.md
  method-boundary-card.md
  dataset-design.md
  annotation-guideline.md
  experiment-plan.md
  evaluation-metrics.md
  related-work-map.md
  paper-outline.md
  intro-draft-zh.md
  intro-draft-en.md
  writing-brief-for-coauthor.md
  claims-and-limitations.md
```

## License

MIT
