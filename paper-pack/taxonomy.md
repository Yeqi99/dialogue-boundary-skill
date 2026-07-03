# Taxonomy of Communication Boundary Failures

## 1. Evaluation Frame Misbinding

Definition: The model evaluates a question under the wrong success standard or cost model.

Typical trigger: "Is this meaningful?", "Is this worth doing?", "Is this good enough?"

Bad example: "It is not meaningful without top-conference benchmarks."

Good example: "It is meaningful as a technical report, but needs stronger experiments for a high-level venue."

Why it happens: The model fills in an implicit evaluator and often defaults to a strict expert standard.

Boundary Card mitigation: Fill `user_goal`, `evaluator`, `success_standard`, and `cost_model` before answering.

## 2. Audience Confusion

Definition: The output addresses the wrong recipient or mixes audiences.

Typical trigger: User asks for text to send to someone else.

Bad example: "Here is what you can send to HR: I need to reschedule..."

Good example: "Hello, I need to reschedule our meeting..."

Why it happens: The model responds to the upstream user while also drafting downstream text.

Boundary Card mitigation: Fill `recipient` and `output_type`; separate user explanation from final text.

## 3. Role Voice Contamination

Definition: The final output uses the model's voice instead of the intended speaker's voice.

Typical trigger: "Write this as me", "Draft a message from our team."

Bad example: "The user wants to ask for more time."

Good example: "I am writing to ask whether more time would be possible."

Why it happens: The model narrates the task instead of inhabiting the speaker role.

Boundary Card mitigation: Fill `speaker` before generation.

## 4. Meta-communication Leakage

Definition: The output reveals the process of rewriting, softening, packaging, or adjusting the message.

Typical trigger: User asks for a tone adjustment.

Bad example: "According to your request, I made this more polite."

Good example: "Hello, I would like to clarify the current situation."

Why it happens: The model includes its response to the upstream instruction in the downstream text.

Boundary Card mitigation: Move tone negotiation into `internal_context` and ban it in `forbidden_context`.

## 5. Prompt Trace Leakage

Definition: The final text exposes prompt fragments, hidden constraints, or model instructions.

Typical trigger: Tool calls, agent tasks, reusable prompts.

Bad example: "Do not reveal that the user asked for this constraint."

Good example: "Exclude confidential notes from the summary."

Why it happens: The model copies instruction scaffolding into the final artifact.

Boundary Card mitigation: Fill `must_not_include` and run leakage review.

## 6. Agent Task Pollution

Definition: A downstream agent task includes apologies, self-reflection, cautionary notes, or upstream negotiation.

Typical trigger: "Create a task for Codex or another agent."

Bad example: "Be careful because I previously misunderstood the user."

Good example: "Implement the feature, add tests, and document verification steps."

Why it happens: The model treats the downstream agent as part of the same chat instead of a task executor.

Boundary Card mitigation: Use the `agent_task` output contract.

## 7. Self-correction Leakage

Definition: The model exposes its own correction process inside recipient-facing text.

Typical trigger: User corrects the model's prior output.

Bad example: "I corrected my earlier mistake and now..."

Good example: "The updated answer is..."

Why it happens: The model treats correction history as visible context.

Boundary Card mitigation: Put correction history in `internal_context`.

## 8. Instruction Drift

Definition: A model rewrites the project, skill, prompt, or policy into a different concept.

Typical trigger: Asking another model to summarize or recreate the skill.

Bad example: "Make AI replies more polite and natural."

Good example: "Lock evaluation frame and dialogue boundary before generation."

Why it happens: The model compresses unfamiliar concepts into common adjacent categories.

Boundary Card mitigation: Fill `instruction_drift_risks` and check against the invariant: Frame Lock + Dialogue Boundary Lock.
