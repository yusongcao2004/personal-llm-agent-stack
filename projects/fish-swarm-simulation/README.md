# Fish Swarm Simulation

## Codex-Assisted Swarm Intelligence Experiment

Fish Swarm Simulation is an interactive fish-schooling project built with React, TypeScript, Canvas 2D, and Three.js. It explores boids-inspired collective motion, predator pressure, tunable simulation parameters, and the practical workflow of using Codex as a coding agent to iterate from rough prototypes toward a stable demo.

## Demo Preview

### 3D Aquarium Experiment

![3D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-3d.jpg)

### 2D Behavior Prototype

![2D Fish Swarm](../../docs/screenshots/fish-swarm/fish-swarm-2d.jpg)

No GIF or video is committed yet. A placeholder note is available at [`docs/demo-gifs/fish-swarm/`](../../docs/demo-gifs/fish-swarm/).

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
| Localization | Multiple UI language options |
| Tests | Core logic covered with Vitest |
| Performance optimization | Uses uniform grid / spatial partitioning; very high fish counts remain a stress case |
| Full game loop | Not implemented |

## Relation to My AI Agent Portfolio

This simulation is not itself an LLM workflow. Its relevance to this portfolio is that it served as a practical Codex-assisted development experiment: I used a coding agent to turn an idea into an interactive system, iteratively refine behavior, debug failures, manage project scope, and prepare a stable engineering artifact for presentation.

## Current Limits and Follow-Up Ideas

- The 3D mode is an observation experiment, not a complete game.
- GIF/video demo material still needs to be recorded if a moving preview is desired.
- Extremely high fish counts can still become expensive.
- Future work could add clearer milling / bait-ball states, a more formal game loop, and better recording/export tooling.
