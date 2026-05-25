# Lessons Learned

This project is a documentation-focused portfolio, so the lessons are about designing and explaining a personal LLM agent stack responsibly.

中文：
这个项目是文档型作品集，因此经验总结重点在于如何负责任地设计和解释个人 LLM Agent 栈。

Deutsch:
Dieses Projekt ist ein dokumentationsorientiertes Portfolio. Die Lessons Learned beziehen sich daher darauf, wie ein persönlicher LLM-Agent-Stack verantwortungsvoll entworfen und erklärt werden kann.

## 1. Documentation Is Part of the System

Agent behavior depends on configuration, model choice, tool permissions, and user expectations. If those decisions are not documented, the system becomes harder to evaluate even if the tools work.

中文：
Agent 行为取决于配置、模型选择、工具权限和用户预期。如果这些决策没有记录，即使工具能运行，系统也会难以评估。

Deutsch:
Agent-Verhalten hängt von Konfiguration, Modellwahl, Tool-Berechtigungen und Nutzererwartungen ab. Wenn diese Entscheidungen nicht dokumentiert sind, wird das System schwerer zu bewerten, selbst wenn die Tools funktionieren.

## 2. Local Deployment Is a Tradeoff, Not a Slogan

Local-first design can improve privacy, latency, and inspectability, but it also introduces operational questions: hardware limits, model quality, dependency management, and fallback behavior. Good documentation should name both sides.

中文：
本地优先设计可以改善隐私、延迟和可检查性，但也带来硬件限制、模型质量、依赖管理和后备流程等问题。好的文档应同时说明收益和代价。

Deutsch:
Local-first Design kann Datenschutz, Latenz und Prüfbarkeit verbessern, bringt aber auch operative Fragen mit sich: Hardwaregrenzen, Modellqualität, Dependency Management und Fallback-Verhalten. Gute Dokumentation benennt beide Seiten.

## 3. Routing Is an Engineering Decision

Model routing connects technical and practical concerns. A routing strategy should consider task type, cost, latency, privacy, and risk instead of treating model choice as a fixed preference.

中文：
模型路由连接技术能力和实际约束。路由策略应考虑任务类型、成本、延迟、隐私和风险，而不是把模型选择当作固定偏好。

Deutsch:
Model Routing verbindet technische und praktische Aspekte. Eine Routing-Strategie sollte Aufgabentyp, Kosten, Latenz, Datenschutz und Risiko berücksichtigen, statt Modellwahl als feste Vorliebe zu behandeln.

## 4. Cost Controls Shape Product Behavior

Cost-aware orchestration affects how an agent gathers context, retries failed steps, escalates to stronger models, and decides when a deterministic tool is better than another model call.

中文：
成本意识会影响 Agent 如何收集上下文、重试失败步骤、升级到更强模型，以及何时使用确定性工具而不是再次调用模型。

Deutsch:
Kostenbewusste Orchestrierung beeinflusst, wie ein Agent Kontext sammelt, fehlgeschlagene Schritte wiederholt, zu stärkeren Modellen eskaliert und entscheidet, wann ein deterministisches Tool besser ist als ein weiterer Modellaufruf.

## 5. Human Review Is a Feature

Human-in-the-loop safety is not just a limitation. It can make a personal agent more trustworthy by keeping consequential decisions visible and reversible.

中文：
人工审核不只是限制，也是一种可信度设计。它让重要决策保持可见，并尽量保持可逆。

Deutsch:
Human-in-the-loop Safety ist nicht nur eine Einschränkung. Sie kann einen persönlichen Agenten vertrauenswürdiger machen, weil folgenreiche Entscheidungen sichtbar und möglichst reversibel bleiben.

## 6. Reliability Starts With Boundaries

Clear boundaries around file access, network calls, credentials, logs, and tool permissions make the system easier to reason about. They also reduce the temptation to overstate what the project safely supports.

中文：
围绕文件访问、网络调用、凭据、日志和工具权限建立清晰边界，可以让系统更容易推理，也能减少夸大项目安全能力的诱因。

Deutsch:
Klare Grenzen für Dateizugriff, Netzwerkaufrufe, Zugangsdaten, Logs und Tool-Berechtigungen machen das System leichter nachvollziehbar. Sie reduzieren auch die Versuchung, die sicher unterstützten Fähigkeiten des Projekts zu übertreiben.

## 7. Honest Positioning Builds Trust

The most important portfolio lesson is to be precise about the project. This repository documents personal deployment, configuration, routing, and safety thinking. It does not need to pretend to be a production platform to be useful.

中文：
最重要的作品集经验是准确定位项目。本仓库记录个人部署、配置、路由和安全思考；它不需要假装成生产平台，也能体现价值。

Deutsch:
Die wichtigste Portfolio-Lektion ist präzise Positionierung. Dieses Repository dokumentiert persönliches Deployment, Konfiguration, Routing und Sicherheitsdenken. Es muss keine Produktionsplattform vortäuschen, um nützlich zu sein.
