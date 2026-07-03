# Paper Outline

## 1. Introduction

- LLMs increasingly mediate communication across humans, tools, and agents.
- Some failures are not factual hallucinations but boundary binding errors.
- Introduce evaluation frame misbinding and dialogue boundary failure.
- Present Boundary Card as a lightweight intervention.

## 2. Background

- LLM-mediated writing and agent workflows.
- Audience, speaker, and recipient assumptions.
- Prompt traces and hidden context in generated outputs.

## 3. Problem Definition

- Define Communication Boundary.
- Define Frame Boundary Failure and Evaluation Frame Misbinding.
- Define Dialogue Boundary Failure.
- Explain visible, internal, and forbidden context.

## 4. Taxonomy of Communication Boundary Failures

- Evaluation Frame Misbinding
- Audience Confusion
- Role Voice Contamination
- Meta-communication Leakage
- Prompt Trace Leakage
- Agent Task Pollution
- Self-correction Leakage
- Secondary guardrail: Instruction Drift Guard

## 5. Boundary Card Method

- Present fields.
- Explain Gate 1: Frame Lock.
- Explain Gate 2: Dialogue Boundary Lock.
- Explain post-generation leakage review and instruction drift review.
- Keep Instruction Drift Guard as a secondary check, not a third primary communication boundary failure.

## 6. Dataset Design

- Introduce Communication Boundary Cases (CBC).
- Describe schema, failure types, balancing strategy, and splits.

## 7. Experiment Design

- Compare direct prompting and Boundary Card prompting.
- Include tasks, candidate models, annotation protocol, and table templates.

## 8. Evaluation Metrics

- Frame Accuracy
- Recipient Appropriateness
- Speaker Consistency
- Leakage rates
- Agent Task Purity
- Intent Preservation
- Secondary diagnostic metric: Instruction Drift Rate

## 9. Discussion

- Why boundary failures matter in practical LLM applications.
- How lightweight checks can improve reliability.
- Where the method may be insufficient.

## 10. Limitations

- No claim of complete prevention.
- Human annotation may be subjective.
- Dataset scale may be small in early versions.
- Related work must be completed with verified citations.

## 11. Conclusion

- Restate the problem class.
- Summarize Boundary Card and the two gates.
- Point to future benchmark and tool integration work.
