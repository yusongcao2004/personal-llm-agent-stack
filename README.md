# Personal LLM Agent Deployment Stack

A documentation-focused portfolio for a personal LLM agent deployment, configuration, routing, and safety project.

This repository does not present a production system or a finished agent framework. It is a written record of how I think about assembling and operating local-first LLM agent tooling: deployment choices, routing strategy, cost controls, human oversight, and reliability safeguards.

It also includes one completed interactive prototype, Fish Swarm Simulation, as a concrete example of Codex-assisted development: using a coding agent to move from an idea to a runnable system, then tightening scope, verification, and presentation.

## Attribution and Scope

OpenClaw and Hermes Agent are third-party projects. This repository does not claim authorship of either project. Any references to them are for attribution, integration context, and documentation of a personal deployment exploration.

The work here is intentionally conservative:

- The LLM agent stack material is documentation-focused rather than a packaged production system.
- The included Fish Swarm project is a separate Codex-assisted interactive prototype, not a claim that this repository is a finished agent platform.
- No production-readiness claim is made.
- The repository focuses on configuration thinking, deployment notes, routing design, safety practices, and lessons learned.

## What This Repository Shows

- How a personal LLM agent stack can be documented without overstating implementation maturity.
- How local deployment decisions affect privacy, latency, cost, and reliability.
- How model routing can be described as an operational design problem.
- How human-in-the-loop review can reduce risk in agentic workflows.
- How safety and reliability controls can be planned before adding more automation.
- How a coding agent can support rapid interactive prototyping when paired with stable baselines, build verification, and scope control.

## Featured Projects and Experiments

### Fish Swarm Simulation · Codex-Assisted Interactive Experiment

An interactive swarm intelligence simulation developed through iterative Codex-assisted coding.

Highlights:

- boids-inspired collective motion;
- 2D Canvas fish-school behavior lab;
- 3D aquarium observation experiment;
- predator interaction and configurable simulation parameters;
- uniform-grid neighbor lookup for simulation performance;
- engineering lessons from AI-assisted development, scope control, and verification.

Why it belongs in this portfolio:

This project demonstrates how I use a coding agent to rapidly prototype an interactive system, identify scope and performance issues, and turn iterative experiments into a stable, presentable engineering artifact.

- [Project README](projects/fish-swarm-simulation/README.md)
- [3D Screenshot](docs/screenshots/fish-swarm/fish-swarm-3d.jpg)
- [2D Screenshot](docs/screenshots/fish-swarm/fish-swarm-2d.jpg)
- [Demo GIF notes](docs/demo-gifs/fish-swarm/README.md)

> 中文摘要：鱼群工程展示了我如何使用 Codex 进行快速迭代开发：从群体行为设想到可运行的交互原型，并在过程中处理范围控制、性能优化和稳定版本管理问题。

## Relevance to Applied AI Systems

This project is relevant to applied AI systems because it frames LLM agents as operational systems rather than demos.

- **Local deployment:** Documents why a personal stack may keep selected models, tools, and data paths close to the user for privacy, latency, and inspectability.
- **Model routing:** Separates task intent, model capability, cost, and risk so requests can be routed deliberately instead of always using the largest available model.
- **Cost-aware orchestration:** Treats model choice, retry behavior, context size, and tool use as budget-sensitive design decisions.
- **Human-in-the-loop safety:** Keeps high-impact actions reviewable by a person and treats confirmation steps as part of the system design.
- **Reliability controls:** Describes guardrails such as explicit scopes, fallbacks, logging, dry runs, and conservative defaults.

## Documentation Map

- [DEPLOYMENT.md](DEPLOYMENT.md): Local deployment assumptions, environment boundaries, and operational notes.
- [ROUTING_STRATEGY.md](ROUTING_STRATEGY.md): Model selection, routing criteria, cost awareness, and escalation patterns.
- [SOUL.md](SOUL.md): The project philosophy and the kind of agent experience this documentation is meant to support.
- [SAFETY_NOTES.md](SAFETY_NOTES.md): Human oversight, permission boundaries, reliability practices, and failure modes.
- [LESSONS_LEARNED.md](LESSONS_LEARNED.md): Practical takeaways from documenting and reasoning about a personal agent stack.
- [projects/fish-swarm-simulation/](projects/fish-swarm-simulation/README.md): Completed Codex-assisted fish swarm simulation prototype.

## Current Status

This is a personal documentation portfolio. It is useful as evidence of applied AI systems thinking, not as a drop-in software package.

| Project | Status | Role in portfolio |
|---|---|---|
| Personal LLM Agent Deployment Stack | Documentation portfolio | Local-first agent deployment, routing, cost, and safety thinking |
| Fish Swarm Simulation | Stable interactive prototype | Codex-assisted swarm intelligence experiment |
