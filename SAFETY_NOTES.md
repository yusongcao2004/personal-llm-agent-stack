# Safety Notes

This document records safety and reliability considerations for a personal LLM agent deployment. It is not a formal security audit or a production safety case.

中文：
本文记录个人 LLM Agent 部署中的安全与可靠性考虑。它不是正式安全审计，也不是生产级安全论证。

Deutsch:
Dieses Dokument hält Sicherheits- und Zuverlässigkeitsüberlegungen für ein persönliches LLM-Agent-Deployment fest. Es ist kein formales Security Audit und kein produktionsreifer Safety Case.

## Safety Posture

The project assumes that agentic systems should be designed around user control. The more a workflow can affect files, accounts, external services, or other people, the more it should require review and confirmation.

中文：
本项目假设 Agent 系统应围绕用户控制来设计。工作流越可能影响文件、账户、外部服务或他人，就越需要审核和确认。

Deutsch:
Das Projekt geht davon aus, dass agentische Systeme um Nutzerkontrolle herum gestaltet werden sollten. Je stärker ein Workflow Dateien, Konten, externe Dienste oder andere Personen beeinflussen kann, desto mehr Prüfung und Bestätigung sollte erforderlich sein.

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

中文：
人工监督适用于修改或删除文件、外部通信、长期任务、访问敏感目录或凭据的工具调用，以及模型信心较低的工作流。有效控制包括预览、dry run、显式批准、变更摘要和可追溯日志。

Deutsch:
Menschliche Aufsicht ist wichtig bei Dateiänderungen, externen Kommunikations- oder Kontoaktionen, lang laufenden Aufgaben, Zugriff auf sensible Verzeichnisse oder Zugangsdaten sowie bei geringer Modellzuversicht. Sinnvolle Muster sind Vorschau, Dry Run, explizite Freigabe, klare Änderungszusammenfassungen und nachvollziehbare Logs.

## Permission Boundaries

The system should distinguish between reading, writing, executing, and network access. Treating all tools as equal makes agent behavior harder to inspect and harder to trust.

Recommended boundaries:

- Read-only access for exploration.
- Narrow write access for documentation or approved edits.
- Separate approval for command execution that changes state.
- Separate approval for network calls involving private context.
- No credentials in prompts, logs, or repository files.

中文：
系统应区分读取、写入、执行和网络访问。建议默认只读探索、窄范围写入、对改变状态的命令和包含私密上下文的网络调用单独批准，并避免把凭据写入 prompt、日志或仓库文件。

Deutsch:
Das System sollte Lesen, Schreiben, Ausführen und Netzwerkzugriff klar unterscheiden. Empfohlen sind Read-only Exploration, eng begrenzte Schreibrechte, separate Freigabe für zustandsändernde Befehle und Netzwerkanfragen mit privatem Kontext sowie keine Zugangsdaten in Prompts, Logs oder Repository-Dateien.

## Reliability Controls

Reliability controls should make failures easier to see and recover from:

- Keep task scope explicit.
- Use checklists for multi-step changes.
- Validate generated structured data before relying on it.
- Prefer deterministic tools for parsing, formatting, and file operations.
- Record assumptions when the system cannot verify a fact.
- Use fallbacks when model, tool, or network calls fail.

中文：
可靠性控制应让失败更容易被发现和恢复：明确任务范围，使用检查清单，验证结构化数据，优先使用确定性工具，记录无法验证的假设，并准备模型、工具或网络失败时的后备方案。

Deutsch:
Zuverlässigkeitsmechanismen sollen Fehler sichtbar und behebbar machen: klarer Scope, Checklisten, Validierung strukturierter Daten, deterministische Tools, dokumentierte Annahmen bei nicht verifizierbaren Fakten und Fallbacks bei Modell-, Tool- oder Netzwerkfehlern.

## Failure Modes

Important failure modes include:

- Overconfident model output.
- Accidental disclosure of private context.
- Tool execution outside the intended scope.
- Retry loops that increase cost without improving quality.
- Silent partial completion.
- Documentation that implies more maturity than the project has.

中文：
重要失败模式包括模型过度自信、泄露私密上下文、工具越界执行、无效重试增加成本、静默部分完成，以及文档夸大项目成熟度。

Deutsch:
Wichtige Fehlermodi sind überzuversichtliche Modellausgaben, unbeabsichtigte Offenlegung privater Kontexte, Tool-Ausführung außerhalb des vorgesehenen Scopes, teure Wiederholungsschleifen ohne Qualitätsgewinn, stille Teilfertigstellung und Dokumentation, die mehr Reife suggeriert als vorhanden ist.

## Conservative Defaults

For a personal deployment, conservative defaults are a strength:

- Ask before acting when risk is unclear.
- Prefer smaller scopes.
- Prefer reversible operations.
- Prefer local processing for sensitive context.
- Prefer honest uncertainty over polished speculation.

中文：
对于个人部署，保守默认值是优势：风险不清楚时先询问，缩小范围，优先选择可逆操作，对敏感上下文优先本地处理，并用诚实的不确定性取代漂亮但未经验证的推测。

Deutsch:
Für ein persönliches Deployment sind konservative Defaults eine Stärke: bei unklarem Risiko nachfragen, kleinere Scopes wählen, reversible Operationen bevorzugen, sensible Kontexte möglichst lokal verarbeiten und ehrliche Unsicherheit über glatte Spekulation stellen.
