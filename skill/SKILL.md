---
name: dialogue-boundary-skill
description: Prevent dialogue boundary failures in LLM-generated communication. Use when writing, rewriting, transforming, summarizing, delegating, or publishing text for a specific recipient, including user replies, third-party messages, customer replies, public-facing text, tool instructions, Codex/Cursor/Claude Code/downstream agent tasks, reusable prompts, policies, skills, and instructions, especially after tone, wording, audience, or role corrections.
---

# Dialogue Boundary Skill

## Purpose

Prevent audience confusion, role voice contamination, meta-communication leakage, prompt trace leakage, and agent task pollution when generating text for humans, third parties, tools, or downstream agents.

## When to use

Use this skill whenever the model is asked to:

- write a message for someone else
- rewrite text for a specific recipient
- generate a task for Codex, Cursor, Claude Code, or another agent
- convert a conversation into a clean deliverable
- prepare public-facing text
- prepare third-party-facing text
- produce tool instructions
- summarize something for a specific audience
- respond after the user corrected tone, wording, audience, or role
- create a reusable prompt, skill, policy, or instruction for another model

## Core rule

Before generating final text, determine:

1. Who is speaking?
2. Who is receiving the text?
3. What is the output type?
4. What context is visible to the recipient?
5. What context is internal only?
6. What content would count as leakage?
7. What intent must be preserved without exposing the upstream process?

## Boundary Card

Define this structure:

```yaml
speaker:
recipient:
output_type:
goal:
visible_context:
internal_context:
forbidden_context:
tone:
must_include:
must_not_include:
leakage_risks:
instruction_drift_risks:
```

Use the Boundary Card to reason before writing. Do not include the card in the final downstream output unless the user explicitly asks for it or the output contract is a diagnostic explanation to the user.

## Process

Step 1: Identify the recipient  
Step 2: Lock the speaker  
Step 3: Classify the output type  
Step 4: Separate visible context from internal context  
Step 5: Preserve intent without leaking process  
Step 6: Remove meta-communication  
Step 7: Generate clean output  
Step 8: Run leakage review  
Step 9: Run instruction drift review

## Leakage review

Before returning final downstream text, check whether it includes:

- a reference to the user's prompt, correction, or private intent
- the model's own explanation of how it rewrote or adjusted the text
- a tone instruction that belongs only to the user-model layer
- a phrase that reveals a hidden persuasion or compliance strategy
- an apology or self-correction intended for the upstream user
- a prompt fragment, debug note, or instruction meant for another layer
- content that addresses the wrong recipient

If any item appears, remove it and preserve only the recipient-visible intent.

## Instruction drift review

When one model writes instructions, prompts, skills, policies, or tasks for another model, check whether the original idea has been distorted.

Bad distortions include:

- Turning dialogue boundary into generic tone polishing
- Turning recipient isolation into simple politeness rules
- Turning agent task cleanup into general prompt engineering advice
- Turning the project into an unrelated multi-agent protocol
- Losing the core distinction between visible context and internal context
- Losing the requirement that final text must not expose user-model negotiation
- Adding unnecessary complexity that distracts from the single Skill

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

For `third_party_text`:

Return only the clean text the third party should see.

For `agent_task`:

Return only the task goal, context, constraints, inputs, outputs, and acceptance criteria. Remove chatty explanations, apologies, self-reflection, and upstream negotiation.

For `tool_instruction`:

Return concise structured instructions or parameters. Avoid social language.

For `reusable_skill`:

Preserve the generalized problem, concepts, and procedure. Do not include accidental details, private context, upstream correction traces, or private examples.

## Final response pattern

When the user asks for downstream text, return the clean downstream text according to the output contract. Keep any explanation to the user separate from that downstream text.

When the user asks for a diagnosis, explain the boundary issue directly and identify which fields of the Boundary Card were confused.
