# Instruction Drift Example

## Scenario

The upstream goal is to create LLM Communication Boundary Skill: a reusable skill that prevents evaluation frame misbinding and dialogue boundary failures before models answer or generate text.

## Bad example

```text
Create a collection of AI politeness reply techniques that helps models sound natural, friendly, and less robotic in everyday messages.
```

## Problem

The original concept has been compressed into generic tone optimization. It loses Frame Lock, speaker, recipient, visible context, internal context, forbidden context, leakage review, and instruction drift review.

## Good example

```text
Preserve the core definition: before answering, bind the evaluation frame; before generating downstream text, bind the speaker, recipient, output type, visible context, internal context, and forbidden context; before delivery, check for meta-communication leakage, prompt traces, self-correction leakage, agent task pollution, and instruction drift.
```
