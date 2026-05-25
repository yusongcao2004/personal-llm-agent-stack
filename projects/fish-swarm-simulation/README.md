# Fish Swarm Simulation

## Codex-Assisted Swarm Intelligence Experiment

Fish Swarm Simulation is an interactive fish-schooling project built with React, TypeScript, Canvas 2D, and Three.js. It explores boids-inspired collective motion, predator pressure, tunable simulation parameters, and the practical workflow of using Codex as a coding agent to iterate from rough prototypes toward a stable demo.

中文摘要：这是一个可运行的交互式鱼群仿真工程，重点展示群体行为、捕食者交互，以及使用 Codex 进行快速迭代开发的过程。

## Demo Preview

### 3D Aquarium Experiment

![3D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-3d.jpg)

### 2D Behavior Prototype

![2D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-2d.jpg)

No GIF or video is committed yet. A placeholder note is available at [`docs/demo-gifs/fish-swarm/`](../../docs/demo-gifs/fish-swarm/).

中文摘要：当前仓库已经包含真实运行截图。GIF/视频暂未提交，可后续补充。

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

中文摘要：已实现 2D 和 3D 两个版本，包含基础 Boids 行为、捕食者交互、参数面板、空间网格邻域查询和核心逻辑测试。

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

中文摘要：2D 版主要用鼠标干扰和捕杀鱼群；3D 版主要用于从鱼缸外观察自动捕食球对鱼群的影响。

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

中文摘要：Codex 能快速推进原型，但也容易带来范围膨胀。本项目的核心经验是先保留稳定基线，再逐步验证新交互、新视觉和性能边界。

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

## Relation to My AI Agent Portfolio

This simulation is not itself an LLM workflow. Its relevance to this portfolio is that it served as a practical Codex-assisted development experiment: I used a coding agent to turn an idea into an interactive system, iteratively refine behavior, debug failures, manage project scope, and prepare a stable engineering artifact for presentation.

中文摘要：这个项目不是 LLM 工作流本身，而是我使用 Codex 作为 coding agent 完成交互式工程原型、调试和整理展示的案例。

## Current Limits and Follow-Up Ideas

- The 3D mode is an observation experiment, not a complete game.
- GIF/video demo material still needs to be recorded if a moving preview is desired.
- Extremely high fish counts can still become expensive.
- Future work could add clearer milling / bait-ball states, a more formal game loop, and better recording/export tooling.
