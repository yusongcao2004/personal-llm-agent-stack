# Routing Strategy

Model routing is the practice of choosing the right model, tool, or workflow for a request instead of sending every task to the same endpoint.

In this project, routing is treated as an applied systems concern: capability, cost, latency, safety, and reliability all matter.

## Routing Goals

- Use lightweight models for simple classification, summarization, extraction, and formatting tasks.
- Use stronger reasoning models for ambiguous, multi-step, or high-impact work.
- Prefer local execution when privacy, latency, or inspectability is more important than maximum model capability.
- Escalate to hosted models only when the task benefits from their capabilities and the context is appropriate to share.
- Keep human approval in the path for actions with material consequences.

## Routing Inputs

A routing decision can consider:

- **Task type:** drafting, planning, retrieval, tool use, code review, extraction, or synthesis.
- **Risk level:** whether the output can change files, spend money, disclose data, or affect another person.
- **Context sensitivity:** whether the prompt contains private, confidential, or account-specific information.
- **Latency tolerance:** whether the user needs an immediate answer or can wait for a stronger model.
- **Cost sensitivity:** expected token volume, retry likelihood, and model pricing.
- **Reliability needs:** whether the task requires verification, deterministic formatting, or auditability.

## Example Routing Tiers

These tiers are conceptual. They are not claims about a specific deployed implementation in this repository.

| Tier | Intended Use | Typical Controls |
| --- | --- | --- |
| Local or small model | Low-risk classification, summarization, cleanup, first-pass drafting | Short context, no external disclosure, simple validation |
| General hosted model | Medium-complexity writing, planning, structured reasoning | Cost checks, prompt constraints, review before action |
| Strong reasoning model | Complex decisions, uncertain tasks, safety-sensitive analysis | Human confirmation, narrower scope, explicit verification |
| Tool-assisted workflow | File edits, searches, command execution, external actions | Permission checks, dry runs, logs, rollback plan |

## Cost-Aware Orchestration

Cost awareness is not only about selecting a cheaper model. It also includes:

- Reducing unnecessary context.
- Avoiding repeated retries without changing strategy.
- Summarizing intermediate state before escalation.
- Reserving expensive models for tasks that need them.
- Using deterministic tools for work that does not require language generation.

## Escalation and Fallback

A routing strategy should define what happens when the first choice is not enough:

- Escalate from a smaller model to a stronger model when the task remains ambiguous.
- Fall back to a local or manual workflow when external calls are unavailable or inappropriate.
- Ask for human confirmation before irreversible actions.
- Stop when confidence is low instead of manufacturing certainty.

## Evaluation Questions

The routing strategy should be judged by practical behavior:

- Did the system choose a model appropriate to the task?
- Did it avoid unnecessary cost?
- Did it preserve user control?
- Did it expose uncertainty clearly?
- Did it fail safely when tools or models were unavailable?

