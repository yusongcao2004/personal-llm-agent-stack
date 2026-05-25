# Deployment Notes

This document describes the intended shape of a personal LLM agent deployment. It is not a production runbook and does not claim that a complete deployable system is included in this repository.

中文：
本文说明个人 LLM Agent 部署的设计形态和边界。它不是生产运行手册，也不声称仓库中包含完整可部署系统。

Deutsch:
Dieses Dokument beschreibt die angestrebte Form eines persönlichen LLM-Agent-Deployments. Es ist kein Produktions-Runbook und behauptet nicht, dass dieses Repository ein vollständig deploybares System enthält.

## Deployment Intent

The project is centered on a local-first personal agent stack. The goal is to understand how agent tools, model providers, local models, routing decisions, and user approvals can fit together in a practical environment.

The deployment emphasis is on:

- Keeping sensitive work inspectable by the user.
- Preserving clear boundaries between local resources and external model providers.
- Choosing the smallest sufficient model for a task.
- Recording decisions that would otherwise remain hidden in ad hoc configuration.
- Treating safety checks as part of deployment, not as an afterthought.

中文：
部署目标是理解本地工具、模型提供商、本地模型、路由决策和用户批准如何组合成一个可控的个人环境。重点在于可检查性、清晰边界、合适模型选择、决策记录和前置安全检查。

Deutsch:
Ziel ist zu verstehen, wie lokale Tools, Modellanbieter, lokale Modelle, Routing-Entscheidungen und Nutzerfreigaben in einer praktischen persönlichen Umgebung zusammenpassen. Der Schwerpunkt liegt auf Prüfbarkeit, klaren Grenzen, angemessener Modellwahl, dokumentierten Entscheidungen und Sicherheit als Teil des Deployments.

## Local-First Assumptions

A personal deployment may include local models, local tool execution, local files, and optional access to hosted APIs. The important design choice is not that every step must be local, but that the system should make locality explicit.

Useful questions for each component:

- Does this step require external network access?
- Does this step expose private context to a hosted model?
- Can the user inspect or interrupt the action?
- Is there a cheaper or lower-risk model that can handle the request?
- What happens if the tool call, model call, or local process fails?

中文：
本地优先并不意味着所有步骤都必须离线完成，而是要求系统明确说明哪些步骤在本地、哪些步骤会访问外部模型或网络。每个组件都应评估隐私、成本、可中断性和失败处理。

Deutsch:
Local-first bedeutet nicht, dass jeder Schritt offline laufen muss. Entscheidend ist, dass das System transparent macht, welche Schritte lokal bleiben und welche externe Modelle oder Netzwerke nutzen. Jede Komponente sollte nach Datenschutz, Kosten, Unterbrechbarkeit und Fehlerverhalten bewertet werden.

## Environment Boundaries

The deployment boundary should separate:

- User-owned files and credentials.
- Local model runtime and cache directories.
- Hosted model API keys and provider configuration.
- Tool execution permissions.
- Logs, traces, and temporary artifacts.

For a personal stack, these boundaries help keep the project honest. They also make it easier to describe what the system can do without implying unattended production operation.

中文：
环境边界应区分用户文件、凭据、本地模型缓存、托管模型配置、工具权限和日志产物。这有助于避免夸大系统能力，也便于说明哪些操作仍需要人工监督。

Deutsch:
Die Umgebung sollte Nutzerdateien, Zugangsdaten, lokale Modell-Caches, Konfiguration für gehostete Modelle, Tool-Berechtigungen sowie Logs und temporäre Artefakte trennen. Dadurch bleibt die Projektbeschreibung präzise und impliziert keinen unbeaufsichtigten Produktionsbetrieb.

## Operational Notes

The deployment posture should favor explicit control over convenience:

- Start with manual execution before adding background automation.
- Prefer dry runs for actions that change files, accounts, or external state.
- Keep credentials outside documentation and source control.
- Use separate configuration for experiments and regular use.
- Log enough information to debug failures without storing unnecessary private content.

中文：
运行策略应优先选择显式控制：先手动执行，再考虑自动化；对会改变文件、账户或外部状态的操作使用 dry run；凭据不要写入文档或源码。

Deutsch:
Operativ sollte explizite Kontrolle wichtiger sein als Bequemlichkeit: zuerst manuelle Ausführung, dann Automatisierung; Dry Runs für zustandsändernde Aktionen; Zugangsdaten gehören nicht in Dokumentation oder Quellcode.

## Non-Goals

This repository does not include an implementation package, a hosted service, or a production deployment pipeline. It documents the reasoning and practices around a personal agent deployment.

中文：
本仓库不包含可发布的软件包、托管服务或生产部署流水线。它记录的是个人 Agent 部署的设计推理和实践原则。

Deutsch:
Dieses Repository enthält kein Implementierungspaket, keinen gehosteten Dienst und keine Produktionspipeline. Es dokumentiert die Überlegungen und Praktiken rund um ein persönliches Agent-Deployment.
