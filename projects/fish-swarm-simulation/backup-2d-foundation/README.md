# Fish School Foundation

A clean 2D prototype for validating fish-school movement, mouse-predator avoidance, and a minimal click-to-bite hunt loop.

This version is intentionally small. The goal is to make the school look natural, make mouse avoidance readable, and keep tuning simple before adding more game systems.

The app includes English, Chinese, and German UI text. English is the default. Use the language selector in the rules screen or top bar to switch at any time.

中文：
这是一个干净的 2D 原型，用于验证鱼群运动、鼠标捕食者躲避，以及最小化的点击捕杀循环。该版本有意保持简洁，目标是在加入更多游戏系统前，让鱼群自然、躲避行为清晰、参数调试简单。界面支持英文、中文和德语，默认语言为英文。

Deutsch:
Dies ist ein klarer 2D-Prototyp zur Validierung von Fischschwarm-Bewegung, Maus-Predator-Vermeidung und einem minimalen Click-to-Bite-Loop. Die Version ist bewusst klein gehalten: Der Schwarm soll natürlich wirken, die Mausvermeidung gut lesbar sein und das Tuning einfach bleiben, bevor weitere Spielsysteme ergänzt werden. Die UI unterstützt Englisch, Chinesisch und Deutsch; Englisch ist die Standardsprache.

## Tech Stack

- Vite
- React
- TypeScript
- HTML Canvas 2D API
- `requestAnimationFrame`

This version does not use Three.js, React Three Fiber, WebGL, a physics engine, or a heavy UI framework.

中文：
技术栈为 Vite、React、TypeScript、Canvas 2D 和 `requestAnimationFrame`。本版本不使用 Three.js、React Three Fiber、WebGL、物理引擎或重型 UI 框架。

Deutsch:
Der Tech Stack besteht aus Vite, React, TypeScript, Canvas 2D und `requestAnimationFrame`. Diese Version nutzt kein Three.js, kein React Three Fiber, kein WebGL, keine Physik-Engine und kein schwergewichtiges UI-Framework.

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

中文：
本地运行流程：先执行 `npm install`，再用 `npm run dev` 启动开发服务器。验证命令包括 `npm run lint`、`npm run test` 和 `npm run build`。

Deutsch:
Lokal wird zuerst `npm install` ausgeführt, danach startet `npm run dev` den Entwicklungsserver. Zur Prüfung dienen `npm run lint`, `npm run test` und `npm run build`.

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

中文：
使用方式：从顶部打开规则页并开始实验，鼠标在水域中代表捕食者。大圆是鱼的感知半径，小红圈是撕咬半径。左键在小半径内执行确定性捕杀，鱼是否被捕杀取决于速度阈值和附近同伴数量。控制面板默认收起，可用于难度、鱼数、参数、惩罚和可选能力调节，也可保存最多三个自定义参数版本。

Deutsch:
Nutzung: Über die obere Leiste kann die Regelansicht geöffnet und der Hunt gestartet werden. Die Maus im Wasserbereich repräsentiert den Predator. Der große Kreis ist der Wahrnehmungsradius der Fische, der kleinere rote Kreis der Bite-Radius. Linksklick führt eine deterministische Bite-Prüfung aus, abhängig von Geschwindigkeit und Anzahl naher Begleiter. Das Control Panel ist standardmäßig geschlossen und erlaubt Difficulty-, Fischzahl-, Parameter-, Penalty- und optionale Ability-Einstellungen sowie bis zu drei Custom Presets.

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

中文：
仿真使用基础 Boids 思路，包括分离、对齐、聚合、边界避让、捕食者躲避、局部群体速度优势和学校意图。邻域查询使用小型 uniform grid / spatial hash，以在 500 条以上鱼时保持可用性能。这些参考资料影响了规则设计，但没有直接复制外部实现。

Deutsch:
Die Simulation nutzt grundlegende Boids-Ideen: Separation, Alignment, Cohesion, Boundary Avoidance, Predator Avoidance, lokalen Gruppenvorteil bei Geschwindigkeit und School Intent. Die Nachbarschaftssuche nutzt ein kleines Uniform Grid / Spatial Hash, damit auch 500+ Fische nutzbar bleiben. Die Referenzen haben die Regeln beeinflusst, es wurde jedoch keine externe Implementierung kopiert.

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

中文：
控制项包括基础设置、运动参数、Boids 权重、捕食者参数、惩罚设置、可选特殊能力和高级调试项。

Deutsch:
Die Controls umfassen Basiseinstellungen, Bewegungsparameter, Boids-Gewichte, Predator-Parameter, Penalty-Einstellungen, optionale Spezialfähigkeiten und erweiterte Debug-Optionen.

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

中文：
该 2D 基础版明确不包含 3D 渲染、摄像机控制、WASD 捕食者、计分、计时、升级、复杂状态机、音效、粒子或暗色电影化效果。

Deutsch:
Diese 2D-Foundation enthält bewusst kein 3D-Rendering, keine Kamerasteuerung, keinen WASD-Predator, kein Scoring, keinen Timer, keine Upgrades, keine komplexen State Machines, keinen Sound, keine Partikel und keine dunkle cineastische Inszenierung.

## Iteration Path

```text
Step 1: Tune 2D fish schooling and mouse avoidance until it is natural, beautiful, and stable
Step 2: Add clearer group shapes, such as milling / bait ball
Step 3: Balance click-to-bite predator eating mechanics
Step 4: Consider keyboard control, upgrades, timer, and a formal game loop
Step 5: Only then consider 2.5D or richer visual packaging
```

中文：
迭代路径是先调顺 2D 鱼群和鼠标躲避，再加入更清晰的群体形态，随后平衡点击捕杀，最后才考虑键盘控制、升级、计时或更复杂的视觉包装。

Deutsch:
Die Iterationsreihenfolge lautet: zuerst 2D-Schwarmverhalten und Mausvermeidung stabil abstimmen, dann klarere Gruppenformen ergänzen, anschließend Click-to-Bite balancieren und erst danach Tastatursteuerung, Upgrades, Timer oder aufwendigere Visuals erwägen.

## Legacy 3D Attempt

The previous 3D prototype has been moved out of the active app path into:

```text
legacy-3d-attempt/
```

It is kept only for reference and is not imported by the current 2D app.

中文：
旧 3D 尝试仅作为参考保留，不会被当前 2D 应用导入。

Deutsch:
Der alte 3D-Versuch bleibt nur als Referenz erhalten und wird von der aktuellen 2D-App nicht importiert.
