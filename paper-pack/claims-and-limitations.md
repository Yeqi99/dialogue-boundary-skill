# Claims and Limitations

## Claims that are reasonable

- Communication boundary failure is a common and under-described LLM output error type.
- It is different from factual hallucination.
- It relates to pragmatics, audience design, role boundaries, context visibility, and instruction following.
- Evaluation Frame Misbinding explains why evaluative answers can be misleading even when factually plausible.
- Dialogue Boundary Failure explains why recipient-facing text can leak user-model negotiation or prompt traces.
- Boundary Card is a lightweight intervention method.
- The method can be evaluated through case sets and human annotation.

## Claims to avoid

- Do not claim the method completely solves the problem.
- Do not claim the project is already top-conference ready.
- Do not claim large-scale experiments have proven the method.
- Do not invent experimental results.
- Do not invent citations.
- Do not imply all prompt leakage is solved by this method.
- Do not reduce the method to tone optimization.

## Current limitations

- The current repository contains seed cases and design materials, not a complete benchmark.
- The method relies on model compliance with structured pre-generation checks.
- Human annotation may vary on borderline cases.
- Related-work positioning requires verified citations.
- Stronger empirical claims require running experiments on multiple models.

## Best framing

Frame this project as a practical problem definition, taxonomy, lightweight method, and evaluation design. That is already useful for a technical report, preprint, workshop paper, and open-source research artifact.
