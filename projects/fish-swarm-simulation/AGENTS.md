# Fish School Foundation - Agent Notes

## Current Direction

This project keeps the simple 2D fish-school behavior foundation and a separate 3D fish-tank experiment.
The previous complex 3D game attempt was intentionally excluded from the portfolio import.
The stable 2D snapshot is preserved under `backup-2d-foundation/`.

## Hard Scope For This Version

- Use Vite + React + TypeScript.
- The 2D foundation uses HTML Canvas 2D.
- The 3D fish-tank experiment may use Three.js, React Three Fiber, and Drei.
- The 3D experiment now intentionally uses pointer lock so the mouse can rotate the outside camera without leaving the page; `Esc` releases the cursor and pauses observation.
- Do not add upgrades, scoring, eating, timing, or a formal game loop to the 3D experiment yet.
- The current core loop is fish schooling plus mouse-predator avoidance, deterministic left-click biting, optional contact penalties, and lightweight special abilities.
- Keep the UI bright, readable, and easy to observe.
- Keep parameters useful and grouped; the controls panel is hidden by default so it does not block the tank.
- Simulation logic must remain separate from canvas rendering.
- Preserve `/2d` and `/3d` entries. The 2D version must remain available.

## Commands

- Install: `npm install`
- Dev server: `npm run dev`
- Lint: `npm run lint`
- Tests: `npm run test`
- Build: `npm run build`

## Current App Structure

- `src/components/FishCanvas.tsx`: canvas, animation loop, pointer tracking.
- `src/components/ControlPanel.tsx`: minimal live controls.
- `src/simulation/boids.ts`: 2D boids update logic.
- `src/simulation/vector.ts`: small vector helpers.
- `src/simulation/createFish.ts`: deterministic fish generation.
- `src/simulation/settings.ts`: default tunings.
- `src/experiments/fish-school-2d/`: active 2D page wrapper.
- `src/experiments/fish-tank-3d/`: 3D fish-tank experiment.

## Iteration Order

1. Make the 2D school naturally swim.
2. Tune mouse avoidance until it looks good.
3. Ensure the school regroups after danger.
4. Balance deterministic biting, contact-only penalties, and special abilities.
5. Only then consider milling / bait ball, keyboard predator control, upgrades, and larger game systems.
