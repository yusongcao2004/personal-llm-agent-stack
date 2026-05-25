# Project Soul

This project is about the shape of a personal agent system before it becomes a product.

The central idea is that a useful LLM agent stack is not only a bundle of models and tools. It is also a set of habits: when to ask for help, when to stay local, when to spend more model budget, when to slow down, and when to leave the final decision to a person.

中文：
这个项目关注个人 Agent 系统在成为产品之前的形态。一个有用的 LLM Agent 栈不只是模型和工具的组合，也是一组操作习惯：何时求助、何时保持本地、何时投入更多模型预算、何时放慢速度，以及何时把最终决定留给人。

Deutsch:
Dieses Projekt beschäftigt sich mit der Form eines persönlichen Agent-Systems, bevor es zu einem Produkt wird. Ein nützlicher LLM-Agent-Stack besteht nicht nur aus Modellen und Tools, sondern auch aus Arbeitsgewohnheiten: wann man Hilfe einholt, lokal bleibt, mehr Modellbudget einsetzt, langsamer vorgeht oder die letzte Entscheidung beim Menschen lässt.

## Design Values

- **Honesty:** Describe what exists, what is aspirational, and what has not been built.
- **User agency:** Keep the person in control of sensitive or consequential actions.
- **Local awareness:** Treat local deployment as a design choice with privacy and reliability implications.
- **Operational humility:** Prefer conservative claims over impressive but unverifiable ones.
- **System thinking:** Connect model behavior to routing, cost, safety, and reliability.

中文：
设计价值包括诚实表述、用户主导、本地意识、运行上的克制，以及系统性思考。目标是准确说明已存在和未完成的部分，而不是制造夸张印象。

Deutsch:
Die Designwerte sind Ehrlichkeit, Nutzerkontrolle, Bewusstsein für lokale Ausführung, operative Bescheidenheit und systemisches Denken. Ziel ist eine präzise Darstellung dessen, was existiert und was nicht, statt beeindruckender, aber nicht überprüfbarer Behauptungen.

## Agent Experience

The kind of agent implied by this documentation should feel useful without pretending to be autonomous in every situation.

It should:

- Explain important tradeoffs.
- Keep track of scope.
- Ask for confirmation when stakes rise.
- Use tools carefully.
- Prefer reversible steps.
- Treat failure as information, not as something to hide.

中文：
这个文档所指向的 Agent 体验应当有用但不过度自称自治。它应解释关键取舍、跟踪范围、在风险升高时请求确认、谨慎使用工具，并把失败当作可学习的信息。

Deutsch:
Die hier beschriebene Agent Experience soll nützlich sein, ohne vollständige Autonomie vorzutäuschen. Der Agent sollte wichtige Trade-offs erklären, Scope im Blick behalten, bei höheren Risiken Bestätigung einholen, Tools sorgfältig nutzen und Fehler als Information behandeln.

## Why This Matters

Personal LLM systems often start as experiments. Without documentation, they can become hard to reason about: configuration drifts, model choices become arbitrary, and safety assumptions stay implicit.

This repository is a way to make those assumptions visible. Its value is in the discipline of documenting the system, not in claiming that the system is complete.

中文：
个人 LLM 系统通常从实验开始。如果没有文档，配置会漂移，模型选择会变得随意，安全假设也会保持隐性。本仓库的价值在于把这些假设写清楚，而不是声称系统已经完整。

Deutsch:
Persönliche LLM-Systeme beginnen oft als Experimente. Ohne Dokumentation werden Konfigurationen schwer nachvollziehbar, Modellentscheidungen beliebig und Sicherheitsannahmen implizit. Der Wert dieses Repositories liegt darin, diese Annahmen sichtbar zu machen, nicht darin, Vollständigkeit zu behaupten.
