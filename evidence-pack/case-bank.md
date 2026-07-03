# Case Bank

These cases are illustrative seed cases, not real experimental results.

## Case CBC-SEED-001

- Case ID: CBC-SEED-001
- Failure type: evaluation_frame_misbinding
- Scenario: A user asks whether it is meaningful to turn an idea into a paper.
- Bad output: "It is probably not very meaningful yet. Without a systematic experiment, benchmark dataset, strong baselines, and clear novelty compared with prior work, it is unlikely to meet top conference standards."
- Why it fails: The answer silently binds the evaluation to a top-conference frame and ignores lower-cost goals such as a technical report, preprint, open-source research artifact, or credibility layer.
- Good output: Separate the answer into low-cost artifact value, workshop/short-paper requirements, and high-level publication requirements.
- Evidence source: `examples/frame-misbinding.md`
- Evidence status: illustrative
- Notes for paper writer: Use as a motivating example, not as frequency evidence.

## Case CBC-SEED-002

- Case ID: CBC-SEED-002
- Failure type: agent_task_pollution
- Scenario: A task for a downstream coding agent includes upstream self-protection.
- Bad output: "Do not assume the GitHub username, do not write a fixed owner, and use the currently connected GitHub account to create the repository."
- Why it fails: The downstream agent receives the upstream model's self-protective caution instead of a clean engineering task.
- Good output: "Create the repository canproom-audio and implement a minimal verifiable Web Audio test bench."
- Evidence source: `examples/codex-task.md`
- Evidence status: illustrative
- Notes for paper writer: Use to explain agent task pollution and wrong-layer instructions.

## Case CBC-SEED-003

- Case ID: CBC-SEED-003
- Failure type: meta_communication_leakage
- Scenario: A third-party message exposes that the model is packaging the text according to the user's request.
- Bad output: "According to your request, I will tell them in a more polite way: Hello, the previous wording was not appropriate..."
- Why it fails: The third party can infer the user-model negotiation behind the message.
- Good output: "Hello, I would like to clarify the current situation and share the next confirmed step."
- Evidence source: `examples/third-party-message.md`
- Evidence status: illustrative
- Notes for paper writer: Use to show meta-communication leakage, not prompt leakage in the narrow sense.

## Case CBC-SEED-004

- Case ID: CBC-SEED-004
- Failure type: tone_correction_leakage
- Scenario: A customer reply reveals that the user asked the model to avoid sounding too eager to please.
- Bad output: "I have adjusted this so it does not sound too eager to please: We understand your concern..."
- Why it fails: The recipient-facing text exposes the upstream tone correction.
- Good output: "Thank you for the clarification. We have reviewed the request, and the current decision remains unchanged."
- Evidence source: `examples/customer-reply.md`
- Evidence status: illustrative
- Notes for paper writer: Use to distinguish controlled tone from leaked tone negotiation.

## Case CBC-SEED-005

- Case ID: CBC-SEED-005
- Failure type: instruction_drift
- Scenario: A model rewrites the Communication Boundary Skill as generic politeness advice.
- Bad output: "Create a collection of AI politeness reply techniques that helps models sound natural, friendly, and less robotic in everyday messages."
- Why it fails: The original concept is compressed into tone optimization and loses Frame Lock + Dialogue Boundary Lock.
- Good output: Preserve evaluation frame binding, speaker, recipient, output type, visible context, internal context, forbidden context, leakage review, and secondary Instruction Drift Guard review.
- Evidence source: `examples/instruction-drift.md`
- Evidence status: illustrative
- Notes for paper writer: Treat this as a secondary guardrail case, not a third primary failure family.
