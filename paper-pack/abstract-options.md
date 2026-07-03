# Abstract Options

## 1. Technical report version

Large language models frequently mediate communication between users, third parties, tools, and downstream agents. While many failures are discussed as hallucination or prompt leakage, another class of errors occurs when the model binds the wrong communication boundary. This report introduces LLM Communication Boundary Skill, a lightweight method for preventing two related failures: evaluation frame misbinding, where evaluative answers silently apply the wrong success standard, and dialogue boundary failure, where recipient-facing text leaks internal negotiation, prompt traces, self-correction, or wrong-audience explanations. We propose a Boundary Card with two gates, Frame Lock and Dialogue Boundary Lock, and provide a taxonomy, examples, dataset design, annotation guideline, and evaluation plan.

## 2. Workshop paper version

LLMs can produce fluent but pragmatically misbound outputs: they answer evaluative questions under an unintended standard, or generate third-party and agent-facing text that includes internal conversation traces. We call these communication boundary failures. This paper defines two core subtypes, evaluation frame misbinding and dialogue boundary failure, and proposes Boundary Cards as a lightweight pre-generation intervention. The method asks models to lock the user goal, evaluator, success standard, speaker, recipient, output type, visible context, internal context, and forbidden context before generating final text. We present a taxonomy, examples, and an evaluation design for a small benchmark of Communication Boundary Cases.

## 3. Formal paper version

Reliable LLM-mediated communication requires more than factual correctness: models must infer the appropriate evaluation frame, speaker, recipient, and visibility boundary for each output. We study communication boundary failures, a class of errors in which an LLM applies an unintended evaluation standard or exposes internal user-model negotiation in recipient-facing text. We formalize Frame Boundary Failure, Evaluation Frame Misbinding, and Dialogue Boundary Failure, and introduce Boundary Cards as a structured intervention for pre-generation frame binding and post-generation leakage review. We outline a taxonomy, annotation protocol, benchmark design, and metrics for evaluating boundary reliability across evaluative answers, third-party messages, agent tasks, tool instructions, and reusable skill generation.
