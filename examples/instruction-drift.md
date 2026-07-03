# Instruction Drift Example

## Scenario

An upstream goal is to create Dialogue Boundary Skill: a reusable skill that prevents models from mixing recipient-visible text with internal context when generating text for different audiences.

## Bad example

```text
Create a guide of AI politeness reply techniques that helps models sound natural, friendly, and less robotic in everyday messages.
```

## Problem

The original concept has drifted into generic tone optimization. It loses the core structure: `speaker`, `recipient`, `output_type`, `visible_context`, `internal_context`, `forbidden_context`, `clean_output`, and `leakage_review`.

## Good example

```text
Create Dialogue Boundary Skill as a lightweight reusable skill for locking the speaker, recipient, output type, visible context, internal context, and forbidden context before generating final text. The skill must include a leakage review that checks for exposed meta-communication, prompt traces, self-correction, upstream negotiation, and instruction drift.
```
