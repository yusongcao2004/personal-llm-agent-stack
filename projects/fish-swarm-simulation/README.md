# Fish Swarm Simulation

## Codex-Assisted Swarm Intelligence Experiment

Fish Swarm Simulation is an interactive fish-schooling project built with React, TypeScript, Canvas 2D, and Three.js. It explores boids-inspired collective motion, predator pressure, tunable simulation parameters, and the practical workflow of using Codex as a coding agent to iterate from rough prototypes toward a stable demo.

中文：
Fish Swarm Simulation 是一个使用 React、TypeScript、Canvas 2D 和 Three.js 构建的交互式鱼群仿真项目。它探索 boids 风格的群体运动、捕食者压力、可调参数，以及使用 Codex 作为 coding agent 从粗糙原型迭代到稳定演示的实际流程。

Deutsch:
Fish Swarm Simulation ist ein interaktives Fischschwarm-Projekt mit React, TypeScript, Canvas 2D und Three.js. Es untersucht boids-inspirierte kollektive Bewegung, Predator-Druck, anpassbare Simulationsparameter und den praktischen Workflow, Codex als Coding Agent vom ersten Prototyp bis zu einer stabilen Demo einzusetzen.

## Demo Preview

### 3D Aquarium Experiment

![3D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-3d.jpg)

### 2D Behavior Prototype

![2D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-2d.jpg)

No GIF or video is committed yet. A placeholder note is available at [`docs/demo-gifs/fish-swarm/`](../../docs/demo-gifs/fish-swarm/).

中文：
当前仓库包含从真实运行页面截取的 2D 和 3D 截图。GIF 或视频尚未提交，后续可在 `docs/demo-gifs/fish-swarm/` 中补充。

Deutsch:
Das Repository enthält echte Screenshots aus der laufenden 2D- und 3D-Anwendung. Ein GIF oder Video ist noch nicht enthalten und kann später unter `docs/demo-gifs/fish-swarm/` ergänzt werden.

## Implemented Features

- 2D Canvas fish-schooling simulation with mouse predator interaction.
- 3D aquarium simulation with an outside-the-tank camera and autonomous predator balls.
- Boids-inspired separation, alignment, and cohesion.
- Smooth boundary avoidance in both 2D and 3D environments.
- Predator avoidance based on distance and local threat.
- Deterministic 2D bite mechanics based on fish speed and local companion count.
- 2D contact penalties, miss cost, and optional advanced abilities that can be enabled from the controls panel.
- Species-style 2D behavior presets for sardines, jackfish, and herring.
- 3D predator strategies including orca carousel, dolphin drive, shark strike, and seal ambush.
- Configurable simulation parameters, language selection, and saved custom 2D presets.
- Uniform grid / spatial partitioning for fish neighbor lookup.
- Vitest coverage for core pure simulation logic.

中文：
已实现 2D Canvas 鱼群仿真、3D 鱼缸观察实验、基础 Boids 行为、捕食者交互、确定性 2D 捕杀逻辑、物种风格预设、3D 捕食者策略、参数面板、空间网格邻域查询，以及核心纯逻辑测试。

Deutsch:
Implementiert sind eine 2D-Canvas-Simulation, ein 3D-Aquarium-Experiment, grundlegendes Boids-Verhalten, Predator-Interaktion, deterministische 2D-Bite-Mechanik, Arten-Presets, 3D-Predator-Strategien, Parametersteuerung, Grid-basierte Nachbarschaftssuche und Tests für zentrale reine Simulationslogik.

## Interaction Guide

Run the app locally, then open:

- `/3d` for the 3D Fish Tank Experiment.
- `/2d` for the 2D Foundation.

In the 2D mode:

- Move the mouse over the water area to act as a predator.
- The larger predator radius drives avoidance.
- The smaller bite radius is used for left-click bites.
- Fish can be killed when they are slow enough and have few enough nearby companions.
- The controls panel can adjust fish count, difficulty, species, school mode, predator settings, penalties, and optional advanced abilities.

In the 3D mode:

- Click the tank to lock the pointer.
- Move the mouse to orbit the camera outside the aquarium.
- Press `Esc` to release the pointer and pause observation.
- Predator balls pursue the school automatically.
- Holding a predator ball under the center reticle and dragging can move that predator.
- The camera is constrained outside the aquarium rather than entering the tank.

中文：
本地运行后可打开 `/2d` 或 `/3d`。2D 模式中鼠标作为捕食者，左键在小半径内尝试捕杀满足速度和同伴数量条件的鱼；3D 模式中用户从鱼缸外观察自动捕食球对鱼群的影响，并可通过指针锁定控制外部视角。

Deutsch:
Nach dem lokalen Start können `/2d` und `/3d` geöffnet werden. Im 2D-Modus dient die Maus als Predator; Linksklick nutzt den kleinen Bite-Radius und kann Fische treffen, wenn Geschwindigkeit und Begleiterzahl die Bedingungen erfüllen. Im 3D-Modus beobachtet man von außerhalb des Aquariums autonome Predator-Bälle und steuert die Außenkamera über Pointer Lock.

## Tech Stack

- React
- TypeScript
- Vite
- HTML Canvas 2D API
- Three.js
- React Three Fiber
- `@react-three/drei`
- Vitest
- ESLint

中文：
技术栈包括 React、TypeScript、Vite、Canvas 2D、Three.js、React Three Fiber、Drei、Vitest 和 ESLint。

Deutsch:
Der Tech Stack umfasst React, TypeScript, Vite, Canvas 2D, Three.js, React Three Fiber, Drei, Vitest und ESLint.

## Engineering Lessons from Codex-Assisted Development

This project began as an exploration of fish-school behavior and predator interaction. Codex was used as a coding agent to rapidly generate, modify, test, and reorganize the prototype.

The main engineering lesson was that AI-assisted coding can move very quickly, but speed makes scope control more important. The project went through several shifts: from a simple 2D behavior lab, toward a larger 3D game idea, then back toward preserving stable baselines and separating experiments from working versions.

Practical lessons:

- Keep a stable baseline before adding richer visuals or game systems.
- Separate experimental work from the current runnable app.
- Verify with `lint`, `test`, and `build` after structural changes.
- Keep simulation logic separate from rendering code.
- Watch performance pressure from local-neighborhood searches as fish counts increase.
- Prefer a simple uniform grid over full all-pairs neighbor checks for this project scale.

中文：
Codex 能快速推进原型，但也容易带来范围膨胀。本项目的核心经验是先保留稳定基线，再逐步验证新交互、新视觉和性能边界。结构变化后应运行 lint、test 和 build，并将仿真逻辑与渲染逻辑分开。

Deutsch:
Codex kann Prototyping stark beschleunigen, aber auch Scope Expansion begünstigen. Die wichtigste Erfahrung war, stabile Baselines zu bewahren, neue Interaktionen und Visuals schrittweise zu prüfen und Performance-Grenzen sichtbar zu machen. Nach strukturellen Änderungen sollten lint, test und build ausgeführt werden, und Simulationslogik sollte von Rendering getrennt bleiben.

## Run Locally

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Run tests:

```bash
npm run test
```

Run lint:

```bash
npm run lint
```

Build:

```bash
npm run build
```

中文：
本地运行流程是先执行 `npm install`，再使用 `npm run dev` 启动开发服务器。验证可运行 `npm run test`、`npm run lint` 和 `npm run build`。

Deutsch:
Lokal wird zuerst `npm install` ausgeführt, danach startet `npm run dev` den Entwicklungsserver. Zur Prüfung dienen `npm run test`, `npm run lint` und `npm run build`.

## Current Status

| Part | Status |
|---|---|
| Core fish swarm simulation | Stable prototype |
| 2D mode | Completed interactive prototype |
| 3D mode | Experimental but runnable aquarium prototype |
| Predator interaction | Implemented in both modes |
| Parameter tuning | Implemented |
| Localization | English, Chinese, and German |
| Tests | Core logic covered with Vitest |
| Performance optimization | Uses uniform grid / spatial partitioning; very high fish counts remain a stress case |
| Full game loop | Not implemented |

中文：
状态说明：2D 模式是较稳定的交互原型，3D 模式是可运行但仍偏实验性质的鱼缸观察原型。项目没有实现完整游戏循环；极高鱼数仍属于压力测试场景。

Deutsch:
Statushinweis: Der 2D-Modus ist ein relativ stabiler interaktiver Prototyp, der 3D-Modus ein lauffähiges, aber weiterhin experimentelles Aquarium-Experiment. Ein vollständiger Game Loop ist nicht implementiert; sehr hohe Fischzahlen bleiben ein Stressfall.

## Relation to My AI Agent Portfolio

This simulation is not itself an LLM workflow. Its relevance to this portfolio is that it served as a practical Codex-assisted development experiment: I used a coding agent to turn an idea into an interactive system, iteratively refine behavior, debug failures, manage project scope, and prepare a stable engineering artifact for presentation.

中文：
这个项目不是 LLM 工作流本身，而是我使用 Codex 作为 coding agent 完成交互式工程原型、调试、范围管理和展示整理的案例。它展示的是 AI 辅助开发流程，而不是生产级 Agent 平台。

Deutsch:
Diese Simulation ist kein LLM-Workflow an sich. Ihre Relevanz für das Portfolio liegt darin, dass sie als praktisches Codex-unterstütztes Entwicklungsprojekt diente: Idee, interaktiver Prototyp, Debugging, Scope Management und Vorbereitung als präsentierbares Engineering-Artefakt.

## Current Limits and Follow-Up Ideas

- The 3D mode is an observation experiment, not a complete game.
- GIF/video demo material still needs to be recorded if a moving preview is desired.
- Extremely high fish counts can still become expensive.
- Future work could add clearer milling / bait-ball states, a more formal game loop, and better recording/export tooling.

中文：
当前限制包括：3D 模式不是完整游戏，尚未提交 GIF/视频，极高鱼数仍有性能压力。后续可以考虑更清晰的 milling / bait-ball 状态、正式游戏循环，以及更好的录制或导出工具。

Deutsch:
Aktuelle Grenzen: Der 3D-Modus ist kein vollständiges Spiel, GIF/Video-Material ist noch nicht enthalten, und sehr hohe Fischzahlen bleiben performanceintensiv. Mögliche nächste Schritte wären klarere Milling- oder Bait-Ball-Zustände, ein formalerer Game Loop und bessere Recording- oder Export-Werkzeuge.
