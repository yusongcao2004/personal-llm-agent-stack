# Routing Strategy

Model routing is the practice of choosing the right model, tool, or workflow for a request instead of sending every task to the same endpoint.

In this project, routing is treated as an applied systems concern: capability, cost, latency, safety, and reliability all matter.

中文：
模型路由是指根据任务选择合适的模型、工具或工作流，而不是把所有请求都交给同一个端点。本项目把路由视为应用系统问题，需要同时考虑能力、成本、延迟、安全和可靠性。

Deutsch:
Model Routing bedeutet, für eine Anfrage das passende Modell, Tool oder Workflow-Muster zu wählen, statt jede Aufgabe an denselben Endpunkt zu senden. In diesem Projekt wird Routing als angewandtes Systemthema verstanden: Fähigkeit, Kosten, Latenz, Sicherheit und Zuverlässigkeit zählen gemeinsam.

## Routing Goals

- Use lightweight models for simple classification, summarization, extraction, and formatting tasks.
- Use stronger reasoning models for ambiguous, multi-step, or high-impact work.
- Prefer local execution when privacy, latency, or inspectability is more important than maximum model capability.
- Escalate to hosted models only when the task benefits from their capabilities and the context is appropriate to share.
- Keep human approval in the path for actions with material consequences.

中文：
路由目标是让简单任务使用轻量模型，让复杂或高影响任务使用更强模型；在隐私、延迟或可检查性更重要时优先本地执行；对有实际后果的操作保留人工批准。

Deutsch:
Ziel des Routings ist, einfache Aufgaben mit leichtgewichtigen Modellen zu bearbeiten und stärkere Modelle für komplexe oder folgenreiche Aufgaben zu reservieren. Wenn Datenschutz, Latenz oder Prüfbarkeit wichtiger sind, wird lokale Ausführung bevorzugt. Für folgenreiche Aktionen bleibt menschliche Freigabe im Ablauf.

## Routing Inputs

A routing decision can consider:

- **Task type:** drafting, planning, retrieval, tool use, code review, extraction, or synthesis.
- **Risk level:** whether the output can change files, spend money, disclose data, or affect another person.
- **Context sensitivity:** whether the prompt contains private, confidential, or account-specific information.
- **Latency tolerance:** whether the user needs an immediate answer or can wait for a stronger model.
- **Cost sensitivity:** expected token volume, retry likelihood, and model pricing.
- **Reliability needs:** whether the task requires verification, deterministic formatting, or auditability.

中文：
路由输入包括任务类型、风险等级、上下文敏感性、延迟容忍度、成本敏感度和可靠性需求。这样可以避免把模型选择变成固定偏好。

Deutsch:
Routing-Entscheidungen berücksichtigen Aufgabentyp, Risikoniveau, Sensitivität des Kontexts, Latenztoleranz, Kostensensitivität und Zuverlässigkeitsanforderungen. Dadurch wird Modellwahl zu einer begründeten technischen Entscheidung statt zu einer festen Vorliebe.

## Example Routing Tiers

These tiers are conceptual. They are not claims about a specific deployed implementation in this repository.

| Tier | Intended Use | Typical Controls |
| --- | --- | --- |
| Local or small model | Low-risk classification, summarization, cleanup, first-pass drafting | Short context, no external disclosure, simple validation |
| General hosted model | Medium-complexity writing, planning, structured reasoning | Cost checks, prompt constraints, review before action |
| Strong reasoning model | Complex decisions, uncertain tasks, safety-sensitive analysis | Human confirmation, narrower scope, explicit verification |
| Tool-assisted workflow | File edits, searches, command execution, external actions | Permission checks, dry runs, logs, rollback plan |

中文：
上表是概念性分层，不代表仓库中已经部署了对应系统。它用于说明不同任务应匹配不同能力、成本和控制策略。

Deutsch:
Die Tabelle beschreibt konzeptionelle Routing-Stufen und ist kein Anspruch, dass diese konkrete Implementierung im Repository vollständig deployed ist. Sie zeigt, wie Aufgaben mit unterschiedlichen Fähigkeiten, Kosten und Kontrollmechanismen verbunden werden können.

## Cost-Aware Orchestration

Cost awareness is not only about selecting a cheaper model. It also includes:

- Reducing unnecessary context.
- Avoiding repeated retries without changing strategy.
- Summarizing intermediate state before escalation.
- Reserving expensive models for tasks that need them.
- Using deterministic tools for work that does not require language generation.

中文：
成本意识不只是选择更便宜的模型，也包括减少无用上下文、避免无策略重试、升级前总结状态、把昂贵模型留给真正需要的任务，并在适合时使用确定性工具。

Deutsch:
Kostenbewusstsein bedeutet nicht nur, ein günstigeres Modell zu wählen. Es umfasst auch weniger unnötigen Kontext, weniger ziellose Wiederholungen, Zwischenzusammenfassungen vor Eskalation, den gezielten Einsatz teurer Modelle und deterministische Tools für Aufgaben ohne Sprachgenerierung.

## Escalation and Fallback

A routing strategy should define what happens when the first choice is not enough:

- Escalate from a smaller model to a stronger model when the task remains ambiguous.
- Fall back to a local or manual workflow when external calls are unavailable or inappropriate.
- Ask for human confirmation before irreversible actions.
- Stop when confidence is low instead of manufacturing certainty.

中文：
当第一选择不足时，策略应定义升级、降级和停止条件。对于不可逆操作应先请求确认；在信心不足时应停止，而不是制造确定性。

Deutsch:
Wenn die erste Wahl nicht ausreicht, sollte die Strategie Eskalation, Fallbacks und Stop-Kriterien definieren. Vor irreversiblen Aktionen ist Bestätigung nötig; bei geringer Sicherheit sollte das System stoppen, statt künstliche Gewissheit zu erzeugen.

## Evaluation Questions

The routing strategy should be judged by practical behavior:

- Did the system choose a model appropriate to the task?
- Did it avoid unnecessary cost?
- Did it preserve user control?
- Did it expose uncertainty clearly?
- Did it fail safely when tools or models were unavailable?

中文：
评估重点是实际行为：是否选对模型、避免不必要成本、保留用户控制、清楚表达不确定性，并在工具或模型不可用时安全失败。

Deutsch:
Bewertet wird das praktische Verhalten: Wurde ein passendes Modell gewählt? Wurden unnötige Kosten vermieden? Blieb der Nutzer in Kontrolle? Wurde Unsicherheit klar gemacht? Ist das System bei Tool- oder Modellproblemen sicher gescheitert?
