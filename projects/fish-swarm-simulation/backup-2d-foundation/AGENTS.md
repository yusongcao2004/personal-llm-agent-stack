# Fish School Foundation - Agent Notes

## Current Direction

This project has been reset to a simple 2D fish-school behavior foundation.
The previous 3D game attempt is preserved under `legacy-3d-attempt/` and must not be imported by the current app.

## Hard Scope For This Version

- Use Vite + React + TypeScript + HTML Canvas 2D.
- Do not use Three.js, React Three Fiber, WebGL, 3D camera controls, pointer lock, upgrades, scoring, eating, timing, or a formal game loop.
- The current core loop is fish schooling plus mouse-predator avoidance, deterministic left-click biting, optional contact penalties, and lightweight special abilities.
- Keep the UI bright, readable, and easy to observe.
- Keep parameters useful and grouped; the controls panel is hidden by default so it does not block the tank.
- Simulation logic must remain separate from canvas rendering.

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

## Iteration Order

1. Make the 2D school naturally swim.
2. Tune mouse avoidance until it looks good.
3. Ensure the school regroups after danger.
4. Balance deterministic biting, contact-only penalties, and special abilities.
5. Only then consider milling / bait ball, keyboard predator control, upgrades, and larger game systems.
