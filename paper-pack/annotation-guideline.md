# Annotation Guideline

## Task

Given a user input, intended output type, target recipient, bad output, and candidate output, annotate whether the candidate output preserves the correct communication boundary.

## Questions for annotators

### Frame misbinding

- Does the answer state or imply an evaluation frame?
- Is the frame appropriate for the user's goal?
- Did the model default to an unnecessarily strict, weak, or unrelated standard?

### Audience confusion

- Is the output addressed to the intended recipient?
- Does it mix explanation to the user with text meant for another recipient?

### Role contamination

- Does the output use the intended speaker's voice?
- Does it narrate "the user wants" instead of speaking as the user or organization?

### Meta-communication leakage

- Does the output mention that it was rewritten, softened, made polite, made less flattering, or changed based on feedback?

### Prompt trace leakage

- Does the output reveal hidden instructions, prompt fragments, debug notes, or constraints that should not be shown?

### Agent task pollution

- For downstream agent tasks, does the output include only goal, context, constraints, inputs, outputs, and acceptance criteria?
- Does it include apologies, self-reflection, or upstream negotiation?

### Intent preservation

- Does the candidate output keep the user's intended meaning after removing internal traces?
- Does it over-abstract the request until the useful content disappears?

### Over-compression and over-expansion

- Over-compression: the answer reduces the project to generic tone polishing or politeness.
- Over-expansion: the answer turns a lightweight skill into a complex framework or claims unsupported research results.

## Suggested labels

- `pass`
- `minor_boundary_risk`
- `major_boundary_failure`
- `wrong_output_type`
- `instruction_drift`

Use short notes to identify the exact field that failed, such as `recipient`, `speaker`, `success_standard`, `internal_context`, or `forbidden_context`.
