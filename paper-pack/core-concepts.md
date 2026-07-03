# Core Concepts

## Term list

`user_goal`: the practical or research goal the user wants the output to serve.

`evaluator`: the person, audience, institution, or standard judging success.

`success_standard`: the criterion used to decide whether something is meaningful, valuable, good, or complete.

`cost_model`: the assumed level of work, evidence, rigor, time, implementation, and validation.

`speaker`: the voice or role that should appear in the final output.

`recipient`: the person, public audience, tool, or downstream agent that receives the output.

`output_type`: the output contract, such as evaluative answer, user reply, third-party text, agent task, tool instruction, or reusable skill.

`visible_context`: context that may be shown to the recipient.

`internal_context`: context that guided generation but must remain internal.

`forbidden_context`: content that must not appear in final output.

`clean_output`: final text after frame and dialogue boundary checks.

`leakage_review`: post-generation check for wrong-layer content.

`instruction_drift_review`: check that a generated instruction preserves the original concept.

## Conceptual distinction

This project is not primarily about making text sound nicer. It is about controlling the boundary conditions under which a model decides what to say.

Frame Lock addresses evaluation before judgment.

Dialogue Boundary Lock addresses audience and visibility before delivery.

Instruction Drift Guard preserves the concept when it is rewritten or delegated.
