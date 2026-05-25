# Safety Notes

This document records safety and reliability considerations for a personal LLM agent deployment. It is not a formal security audit or a production safety case.

## Safety Posture

The project assumes that agentic systems should be designed around user control. The more a workflow can affect files, accounts, external services, or other people, the more it should require review and confirmation.

## Human-in-the-Loop Controls

Human oversight should be used for:

- Actions that modify or delete files.
- External communications or account actions.
- Long-running or recurring tasks.
- Tool calls that access sensitive directories or credentials.
- Any workflow where the model expresses low confidence.

Useful control patterns include:

- Preview before execution.
- Dry-run mode where possible.
- Explicit approval for irreversible steps.
- Clear summaries of what will change.
- Logs that allow the user to reconstruct important actions.

## Permission Boundaries

The system should distinguish between reading, writing, executing, and network access. Treating all tools as equal makes agent behavior harder to inspect and harder to trust.

Recommended boundaries:

- Read-only access for exploration.
- Narrow write access for documentation or approved edits.
- Separate approval for command execution that changes state.
- Separate approval for network calls involving private context.
- No credentials in prompts, logs, or repository files.

## Reliability Controls

Reliability controls should make failures easier to see and recover from:

- Keep task scope explicit.
- Use checklists for multi-step changes.
- Validate generated structured data before relying on it.
- Prefer deterministic tools for parsing, formatting, and file operations.
- Record assumptions when the system cannot verify a fact.
- Use fallbacks when model, tool, or network calls fail.

## Failure Modes

Important failure modes include:

- Overconfident model output.
- Accidental disclosure of private context.
- Tool execution outside the intended scope.
- Retry loops that increase cost without improving quality.
- Silent partial completion.
- Documentation that implies more maturity than the project has.

## Conservative Defaults

For a personal deployment, conservative defaults are a strength:

- Ask before acting when risk is unclear.
- Prefer smaller scopes.
- Prefer reversible operations.
- Prefer local processing for sensitive context.
- Prefer honest uncertainty over polished speculation.

