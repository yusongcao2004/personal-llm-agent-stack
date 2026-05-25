# Personal LLM Agent Deployment Stack

A documentation-focused portfolio for a personal LLM agent deployment, configuration, routing, and safety project.

This repository does not present a production system or a finished agent framework. It is a written record of how I think about assembling and operating local-first LLM agent tooling: deployment choices, routing strategy, cost controls, human oversight, and reliability safeguards.

It also includes one completed interactive prototype, Fish Swarm Simulation, as a concrete example of Codex-assisted development: using a coding agent to move from an idea to a runnable system, then tightening scope, verification, and presentation.

中文：
这是一个以文档为核心的个人 LLM Agent 部署与安全设计作品集。它不是生产级系统或完整 Agent 框架，而是展示我如何思考本地优先部署、模型路由、成本控制、人工审核和可靠性边界。仓库中也包含 Fish Swarm Simulation，作为使用 Codex 进行交互式原型开发和整理展示的实际案例。

Deutsch:
Dies ist ein dokumentationsorientiertes Portfolio zu einem persönlichen LLM-Agent-Stack: Deployment, Konfiguration, Routing, Kostenkontrolle, menschliche Kontrolle und Zuverlässigkeit. Es ist kein produktionsreifes System und kein vollständiges Agent-Framework. Zusätzlich enthält das Repository mit Fish Swarm Simulation einen abgeschlossenen interaktiven Prototyp als praktisches Beispiel für Codex-unterstützte Entwicklung.

## Attribution and Scope

OpenClaw and Hermes Agent are third-party projects. This repository does not claim authorship of either project. Any references to them are for attribution, integration context, and documentation of a personal deployment exploration.

The work here is intentionally conservative:

- The LLM agent stack material is documentation-focused rather than a packaged production system.
- The included Fish Swarm project is a separate Codex-assisted interactive prototype, not a claim that this repository is a finished agent platform.
- No production-readiness claim is made.
- The repository focuses on configuration thinking, deployment notes, routing design, safety practices, and lessons learned.

中文：
OpenClaw 和 Hermes Agent 均为第三方项目，本仓库只用于归属说明、集成背景和个人部署探索记录。这里的定位是保守且诚实的：LLM Agent 部分以文档为主，Fish Swarm 是单独的 Codex 辅助交互原型，不代表本仓库是完整生产平台。

Deutsch:
OpenClaw und Hermes Agent sind Projekte Dritter. Dieses Repository beansprucht keine Urheberschaft daran, sondern nutzt sie nur für Attribution, Integrationskontext und persönliche Deployment-Notizen. Die Einordnung ist bewusst konservativ: Der LLM-Agent-Teil ist dokumentationsorientiert, und Fish Swarm ist ein separater Codex-unterstützter Prototyp, kein Hinweis auf eine fertige Agent-Plattform.

## What This Repository Shows

- How a personal LLM agent stack can be documented without overstating implementation maturity.
- How local deployment decisions affect privacy, latency, cost, and reliability.
- How model routing can be described as an operational design problem.
- How human-in-the-loop review can reduce risk in agentic workflows.
- How safety and reliability controls can be planned before adding more automation.
- How a coding agent can support rapid interactive prototyping when paired with stable baselines, build verification, and scope control.

中文：
这个仓库展示的是应用型 AI 系统思维：如何记录个人 Agent 栈的部署边界，如何在隐私、延迟、成本和可靠性之间做取舍，如何让人工审核成为工作流的一部分，以及如何用 coding agent 快速推进但仍保持稳定基线和范围控制。

Deutsch:
Das Repository zeigt angewandtes Denken über KI-Systeme: lokale Deployment-Grenzen, Abwägungen zwischen Datenschutz, Latenz, Kosten und Zuverlässigkeit, menschliche Kontrolle in Agent-Workflows sowie den kontrollierten Einsatz eines Coding Agents für schnelle, aber überprüfbare Prototypen.

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

中文：
Fish Swarm Simulation 是一个通过 Codex 辅助迭代完成的交互式鱼群仿真实验。它展示了 boids 风格的群体运动、2D/3D 仿真、捕食者交互、参数调节、空间网格邻域查询，以及在 AI 辅助开发中处理范围控制、性能压力和稳定版本管理的经验。

Deutsch:
Fish Swarm Simulation ist ein interaktives Schwarmintelligenz-Experiment, das iterativ mit Codex-Unterstützung entwickelt wurde. Es zeigt boids-inspirierte Gruppenbewegung, 2D- und 3D-Simulation, Predator-Interaktion, konfigurierbare Parameter, Grid-basierte Nachbarschaftssuche sowie praktische Erfahrungen mit Scope Control, Performance und stabilen Baselines in AI-assisted Development.

## Relevance to Applied AI Systems

This project is relevant to applied AI systems because it frames LLM agents as operational systems rather than demos.

- **Local deployment:** Documents why a personal stack may keep selected models, tools, and data paths close to the user for privacy, latency, and inspectability.
- **Model routing:** Separates task intent, model capability, cost, and risk so requests can be routed deliberately instead of always using the largest available model.
- **Cost-aware orchestration:** Treats model choice, retry behavior, context size, and tool use as budget-sensitive design decisions.
- **Human-in-the-loop safety:** Keeps high-impact actions reviewable by a person and treats confirmation steps as part of the system design.
- **Reliability controls:** Describes guardrails such as explicit scopes, fallbacks, logging, dry runs, and conservative defaults.

中文：
这个项目与应用型 AI 系统相关，因为它把 LLM Agent 视为需要部署边界、模型选择、成本控制、人工监督和可靠性策略的运行系统，而不是一次性演示。

Deutsch:
Das Projekt ist relevant für angewandte KI-Systeme, weil es LLM-Agenten als operative Systeme betrachtet: mit Deployment-Grenzen, Modellwahl, Kostenkontrolle, menschlicher Aufsicht und Zuverlässigkeitsmechanismen statt nur als Demo.

## Documentation Map

- [DEPLOYMENT.md](DEPLOYMENT.md): Local deployment assumptions, environment boundaries, and operational notes.
- [ROUTING_STRATEGY.md](ROUTING_STRATEGY.md): Model selection, routing criteria, cost awareness, and escalation patterns.
- [SOUL.md](SOUL.md): The project philosophy and the kind of agent experience this documentation is meant to support.
- [SAFETY_NOTES.md](SAFETY_NOTES.md): Human oversight, permission boundaries, reliability practices, and failure modes.
- [LESSONS_LEARNED.md](LESSONS_LEARNED.md): Practical takeaways from documenting and reasoning about a personal agent stack.
- [projects/fish-swarm-simulation/](projects/fish-swarm-simulation/README.md): Completed Codex-assisted fish swarm simulation prototype.

中文：
以上文档分别覆盖部署假设、模型路由、项目理念、安全边界、经验总结，以及 Fish Swarm 交互原型。建议从根 README 开始，再根据面试或评审重点进入相应文档。

Deutsch:
Diese Dokumente behandeln Deployment-Annahmen, Modellrouting, Projektphilosophie, Sicherheitsgrenzen, Lessons Learned und den Fish-Swarm-Prototyp. Für Portfolio-Gespräche ist das Root-README der beste Einstiegspunkt.

## Current Status

This is a personal documentation portfolio. It is useful as evidence of applied AI systems thinking, not as a drop-in software package.

| Project | Status | Role in portfolio |
|---|---|---|
| Personal LLM Agent Deployment Stack | Documentation portfolio | Local-first agent deployment, routing, cost, and safety thinking |
| Fish Swarm Simulation | Stable interactive prototype | Codex-assisted swarm intelligence experiment |

中文：
当前状态：LLM Agent 部分是文档型作品集，Fish Swarm 是稳定的交互式原型。两者都用于展示工程思考与 AI 辅助开发方式，而不是声明生产级成熟度。

Deutsch:
Aktueller Status: Der LLM-Agent-Teil ist ein Dokumentationsportfolio, Fish Swarm ist ein stabiler interaktiver Prototyp. Beide Teile zeigen Engineering-Denken und AI-assisted Development, ohne Produktionsreife zu behaupten.
