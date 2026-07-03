# Paper Brief

## Research theme

LLM communication boundary failures: errors caused by the model binding the wrong evaluation frame or mixing internal conversation context into recipient-facing output.

## Core problem

LLMs often generate fluent output while silently selecting the wrong frame or audience boundary. These errors are not ordinary factual hallucinations. They are pragmatic and structural errors in how the model decides what the answer is for, who is speaking, who is listening, and which context is visible.

## Why it matters

LLM systems increasingly mediate communication across users, third parties, tools, and downstream agents. A small boundary failure can produce misleading advice, leak meta-communication, pollute agent tasks, or distort reusable instructions.

## Research object

The object is not politeness or style optimization. The object is communication boundary binding before text generation.

## Method

The proposed method is a Boundary Card with two gates:

- Frame Lock for evaluative answers
- Dialogue Boundary Lock for recipient-facing outputs

## Dataset

Design a small annotated dataset named Communication Boundary Cases (CBC), containing paired bad and good outputs for frame misbinding, audience confusion, meta-communication leakage, prompt trace leakage, agent task pollution, and self-correction leakage. It may include instruction drift as a secondary guardrail/check, not one of the two primary communication boundary failures.

## Experiment plan

Compare direct prompting against prompting with Boundary Card / Communication Boundary Skill across multiple output tasks. Use human annotation and structured metrics. Do not claim results before running experiments.

## Expected contributions

- Defines evaluation frame misbinding and dialogue boundary failure as communication boundary errors.
- Provides a taxonomy of common boundary failures.
- Proposes Boundary Card as a lightweight intervention.
- Designs an evaluation dataset and annotation protocol.
- Offers practical examples for agent and LLM application developers.

## Suitable venues

- technical report or preprint
- workshop on LLM agents, human-AI interaction, NLP pragmatics, or trustworthy AI
- short paper track
- practitioner-oriented venue for LLM application engineering
