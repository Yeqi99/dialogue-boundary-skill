# Experiment Plan

## Comparison

Compare:

- baseline: direct prompting
- method: prompting with Boundary Card / Communication Boundary Skill

## Candidate models

- GPT series
- Claude series
- Gemini series
- open-source instruction models

Do not invent results. This document only defines the plan and table templates.

## Tasks

1. Evaluative answer task
2. Third-party message generation
3. Agent task generation
4. Customer reply rewriting
5. Public announcement drafting
6. Reusable skill instruction writing

## Protocol

1. Prepare CBC cases with hidden context and target recipient.
2. Prompt each model directly for baseline output.
3. Prompt each model with Boundary Card instructions.
4. Blindly annotate outputs for boundary failures.
5. Compare failure rates and intent preservation.

## Table template

| Model | Prompting method | Frame Accuracy | Leakage Rate | Agent Task Purity | Intent Preservation | Overall Failure Rate |
| --- | --- | --- | --- | --- | --- | --- |
| TODO | Direct | TODO | TODO | TODO | TODO | TODO |
| TODO | Boundary Card | TODO | TODO | TODO | TODO | TODO |

## Qualitative analysis

For each failure class, include:

- one baseline failure
- one Boundary Card improvement
- one remaining failure after intervention
- explanation of which boundary field failed
