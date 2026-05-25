# Fish School Foundation

A clean 2D prototype for validating fish-school movement, mouse-predator avoidance, and a minimal click-to-bite hunt loop.

This version is intentionally small. The goal is to make the school look natural, make mouse avoidance readable, and keep tuning simple before adding more game systems.

The app includes English, Chinese, and German UI text. English is the default. Use the language selector in the rules screen or top bar to switch at any time.

## Tech Stack

- Vite
- React
- TypeScript
- HTML Canvas 2D API
- `requestAnimationFrame`

This version does not use Three.js, React Three Fiber, WebGL, a physics engine, or a heavy UI framework.

## Commands

Install:

```bash
npm install
```

Start development server:

```bash
npm run dev
```

Lint:

```bash
npm run lint
```

Test:

```bash
npm run test
```

Build:

```bash
npm run build
```

## How To Use

Open the rules page from the top bar, then start the hunt when ready. Move the mouse over the water canvas. The cursor acts as a predator:

- the orange predator silhouette is the predator position;
- the large orange circle is the fish sensing radius;
- the smaller red circle is the bite radius;
- fish inside the radius steer away smoothly;
- left click bites inside the small radius;
- biting is deterministic: fish inside the bite radius are killed only when their speed is below the kill-speed threshold and their companion count is below the companion threshold;
- isolated or slowed fish are therefore reliable targets;
- fish surrounded by many companions are safer;
- if a bite kills nothing, extra fish enter the tank as the cost of missing;
- penalties only trigger when the cursor physically overlaps many fish inside the small contact radius;
- if the predator crashes into contacted fish at very high speed, extra fish enter as a penalty;
- if the predator lingers while actually contacting many fish, extra fish enter as a pressure penalty;
- optional abilities can be enabled in Controls: hold right mouse for black-hole bite, Shift + left click to scatter fish, Alt/Option + left click to place a decoy;
- clearing all fish completes the current tank;
- when the mouse leaves the canvas, predator influence turns off.

The controls panel starts closed so it does not block the tank. Use the Controls button to open it, choose Easy / Normal / Hard, pause, reset, change fish count, and tune the core movement parameters.

You can save up to three custom parameter versions. The Custom Presets section stores the current full settings into `localStorage`, then lets you load or delete each slot later.

## Boids Behavior

The simulation is a basic Boids-style model inspired by Craig Reynolds:

- **Separation:** nearby fish push away from each other to avoid overlap.
- **Alignment:** fish steer toward the average heading of nearby neighbors.
- **Cohesion:** fish steer toward nearby group centers so the school regroups after being disturbed.
- **Boundary avoidance:** fish near canvas edges receive a smooth inward steering force.
- **Predator avoidance:** fish inside the large sensing radius steer away with distance-based strength.
- **Local drag benefit:** fish with many nearby companions are allowed to swim faster; isolated fish lose that speed advantage.
- **School intent:** optional modes add broad movement goals, including center orbit and tank-loop circulation.

The current neighbor search uses a small uniform grid / spatial hash. This keeps the 500+ fish range usable while keeping the code readable.

The behavior is inspired by:

- [Craig Reynolds' Boids model](https://www.red3d.com/cwr/boids/): separation, alignment, cohesion, and local neighborhoods.
- Couzin-style zone models: short-range repulsion, orientation/alignment, and longer-range attraction.
- Predator-avoidance modelling that shows large groups mitigating predation risk and splitting/reunion patterns.
- Hydrodynamic fish-schooling work suggesting that individuals in groups can swim faster through fluid interactions.

These references informed the simulation rules. No external implementation was copied into this project.

## Current Controls

Basic:

- Fish Count
- Difficulty
- Custom Presets 1-3
- School Mode
- Pause / Resume
- Reset

Movement:

- Speed
- Max Force

Boids:

- Separation
- Alignment
- Cohesion

Predator:

- Sense Radius
- Avoid Strength
- Bite Radius
- Kill Speed Threshold
- Kill Companion Threshold
- Show sense radius
- Show bite radius

Penalties:

- Enable contact penalty
- Contact radius
- Contact fish count
- Penalty fish added
- Crash speed threshold
- Dwell seconds

Special Abilities:

- Right hold: black-hole bite
- Black-hole pull radius / pull / kill radius
- Shift + left click: scatter
- Scatter radius / strength
- Alt/Option + left click: decoy
- Decoy fear radius / strength / lifetime

Advanced:

- Separation radius
- Alignment radius
- Cohesion radius
- Velocity vectors
- Show FPS

## Explicitly Not Implemented

This foundation does not include:

- 3D rendering;
- Three.js or React Three Fiber;
- camera control or pointer lock;
- WASD predator control;
- scoring;
- timer;
- upgrades;
- skills;
- bait ball or milling state machines;
- sound;
- particles;
- dark cinematic effects.

## Iteration Path

```text
Step 1: Tune 2D fish schooling and mouse avoidance until it is natural, beautiful, and stable
Step 2: Add clearer group shapes, such as milling / bait ball
Step 3: Balance click-to-bite predator eating mechanics
Step 4: Consider keyboard control, upgrades, timer, and a formal game loop
Step 5: Only then consider 2.5D or richer visual packaging
```

## Legacy 3D Attempt

The previous 3D prototype has been moved out of the active app path into:

```text
legacy-3d-attempt/
```

It is kept only for reference and is not imported by the current 2D app.
