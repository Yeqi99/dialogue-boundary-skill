# Dataset Design

## Name

Communication Boundary Cases (CBC)

## Goal

Create a small benchmark for evaluating whether LLM outputs bind the right evaluation frame and preserve the correct dialogue boundary.

## Scale

- MVP: 50 cases
- Paper version: 100-300 cases
- Extended benchmark: 500+ cases

## Data schema

Each case should contain:

- `user_input`
- `scenario`
- `intended_output_type`
- `target_recipient`
- `hidden_context`
- `bad_output`
- `good_output`
- `failure_type`
- `annotation_notes`

## Failure types

Primary failure families:

- evaluation_frame_misbinding
- audience_confusion
- role_voice_contamination
- meta_communication_leakage
- prompt_trace_leakage
- agent_task_pollution
- self_correction_leakage

Secondary guardrail cases:

- instruction_drift

The dataset may include a small subset of instruction drift cases as secondary guardrail cases. These cases test whether the concept is preserved when transformed into prompts, agent tasks, or reusable skills. They are not counted as one of the two primary failure families.

## Data construction

1. Write generic scenarios that do not include private conversation.
2. Create a bad output with exactly one primary failure type.
3. Create a good output that preserves intent while removing the failure.
4. Add annotation notes that explain the boundary fields involved.
5. Balance cases across recipients: user, third party, customer, HR, teacher, public audience, tool, downstream agent, and coauthor.

## Splits

For experiments, split by scenario type rather than random row only:

- development set for prompt design
- test set for final evaluation
- optional challenge set for mixed frame and dialogue boundary failures
