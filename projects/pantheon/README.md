# Pantheon — Telegram-native Multi-LLM Roundtable

Pantheon is maintained as an independent public source repository:

https://github.com/yusongcao2004/pantheon-llm-roundtable

This directory contains a portfolio case study only. It does not duplicate Pantheon's source code.

## Project Goal

Pantheon explores how multiple LLM providers can participate in a short, Telegram-native discussion while preserving clear speaker order, bounded cost, concise output, and a neutral final synthesis.

The project is designed around a practical interaction pattern: a user addresses one bot in a Telegram group, that bot starts the discussion, and the other model-backed participants respond in cyclic full rounds before an internal synthesis step produces a concise neutral summary.

## Why I Built It

I built Pantheon to test multi-LLM coordination as an engineering system rather than a static demo. The interesting problems were not only model quality, but also provider compatibility, role control, cost control, synthesis constraints, Telegram interaction design, and safe public release practices.

The project is also a concrete example of cost-aware orchestration: not every participant needs a flagship model, and discussion length should be bounded before it becomes expensive or noisy.

## Current Model Structure

| Role | Model |
| --- | --- |
| GPT participant | `gpt-4o-mini` |
| DeepSeek participant | `deepseek-chat` |
| Doubao participant | `doubao-seed-2-0-mini-260428` |
| Gemini participant | `gemini-3.5-flash` |
| Internal synthesis | `gemini-3.1-flash-lite` |

## Implemented Features

- Telegram-native interaction in a group conversation.
- Any addressed bot can start and speak first.
- Cyclic full-round discussion among the participating models.
- Concise prompting to reduce verbosity and control cost.
- Prompt-constrained neutral synthesis after the discussion.
- Per-discussion token/cache statistics.
- Secure environment-based secret handling.

## Engineering Problems and Solutions

### Provider-specific API compatibility

Different model providers do not accept exactly the same request fields or runtime options. Pantheon handles provider-specific compatibility instead of assuming one universal OpenAI-style request shape for every model.

### Cost-driven model downgrade

The project intentionally uses smaller or cheaper models where they are sufficient for participation or synthesis. This keeps the roundtable usable without turning every message into a flagship-model call.

### Concise output control

Each participant is prompted to keep responses short. Discussion length is also bounded by round count, so the system has a predictable upper limit before synthesis.

### Neutral synthesis limitation

The synthesis step is prompt-constrained to be neutral, but this is not a formal guarantee of neutrality or factual accuracy. Multi-model agreement should not be treated as verification.

### Secret-safe GitHub release

Pantheon is designed to keep tokens, API keys, bot credentials, and environment-specific configuration outside source control. Public documentation should describe setup boundaries without exposing secrets or private Telegram group details.

## Demo

Demo media will be added later as redacted Telegram screenshots or GIFs. No fabricated image, nonexistent asset, token, group identifier, or private conversation content is included here.

## Source Repository

- [pantheon-llm-roundtable](https://github.com/yusongcao2004/pantheon-llm-roundtable)
