# Project Akatsuki

**An Educational Space Cybersecurity Attack Simulator**


![Version](https://img.shields.io/badge/version-2.1.0-FF2D55?style=flat-square)
![Status](https://img.shields.io/badge/status-in_development-00F5D4?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-FFB800?style=flat-square)
![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript)
![Three.js](https://img.shields.io/badge/Three.js-r158-white?style=flat-square&logo=threedotjs)

---

> **Important:** Akatsuki is a purely educational, locally-simulated cybersecurity training platform. It performs no real attacks, makes no external network calls of any kind, and has zero interaction with actual satellites, radio frequencies, ground infrastructure, or any external system. Every scenario, satellite, alert, and piece of telemetry in this application is entirely fictional. The sole purpose of this project is to make space cybersecurity concepts tangible and learnable through interactive simulation.

---

## Table of Contents

1. [What This Project Is](#what-this-project-is)
2. [Who It Is For](#who-it-is-for)
3. [Design Philosophy](#design-philosophy)
4. [Tech Stack](#tech-stack)
5. [Application Architecture](#application-architecture)
6. [Folder Structure](#folder-structure)
7. [Pages and Screens](#pages-and-screens)
8. [Component Library](#component-library)
9. [3D Visualization System](#3d-visualization-system)
10. [Simulation Engine](#simulation-engine)
11. [State Management](#state-management)
12. [Animation System](#animation-system)
13. [Simulation Scenarios](#simulation-scenarios)
14. [Educational Framework](#educational-framework)
15. [Implementation Milestones](#implementation-milestones)
16. [Getting Started](#getting-started)
17. [Environment Variables](#environment-variables)
18. [Scripts Reference](#scripts-reference)
19. [Contributing](#contributing)
20. [Acknowledgements](#acknowledgements)

---

## What This Project Is

Orbital Shield places you in the role of a Space Security Operations Center analyst. You monitor a fictional satellite network, respond to escalating cybersecurity incidents, and learn the defensive strategies that real space agencies and satellite operators use to protect critical infrastructure — all in a browser, with no installation beyond the dev server, and no external data required.

The application simulates ten distinct attack scenarios. Each one is broken into investigation stages: Detection, Investigation, Containment, Recovery, and Lessons Learned. At every stage you are given a set of decisions to make. The choices you make determine your score and shape the narrative of the incident. After each scenario, the application generates a full incident report breaking down your decisions against the optimal responses, explaining the underlying concepts, and summarizing what real organizations do to defend against the same class of attack.

The 3D globe visualizes the fictional satellite constellation in real time. Satellites follow mathematically correct Keplerian orbits computed locally. When an attack scenario is active, the globe reflects the state of the incident — targeted satellites change color, signal paths pulse or break, ground stations flash warnings, and attack propagation spreads across the scene in a way that makes the abstract concept of a satellite cyberattack feel physical and immediate.

The reason this project exists as a portfolio piece is straightforward. Space cybersecurity is one of the most underrepresented domains in security education. Most people have no mental model for how a GPS spoofing attack works, what a satellite uplink looks like from a security perspective, or why ransomware hitting a mission control network is categorically different from ransomware hitting a hospital. This project tries to fix that with an interface that takes the subject seriously.

---

## Who It Is For

This project was built with several audiences in mind, and they are all legitimate use cases:

**Cybersecurity students and CTF competitors** who want a portfolio project that demonstrates not just technical ability but systems thinking, UI craft, and the ability to take a complex domain and make it approachable. This is the kind of project a recruiter will spend more than thirty seconds on.

**Security professionals** entering the space or OT/ICS security domains who want an interactive way to build intuition about the attack surface. The scenarios are grounded in real threat classes even though all details are fictional.

**Educators** who want to demonstrate threat concepts visually. Every scenario can be walked through in a classroom setting as a discussion driver.

**Anyone evaluating this codebase** as an example of React architecture, TypeScript design patterns, Three.js integration, or animation-heavy UI work. The code is written to be read.

---

## Design Philosophy

Orbital Shield's visual identity is original. The interface draws inspiration from the design philosophy of Persona 5 — its energy, its confidence, the way it makes every state transition feel like an event rather than a page load — but no assets, typography, or artwork from the game appear anywhere in this codebase. The goal was to capture the same sense of purpose and intentionality in a UI that is legitimately functional.

The design operates on a small set of principles that are applied consistently.

**Color is semantic.** Every color in the palette carries meaning and is used only for that meaning. Red means threat. Teal means system status and data. Amber means warning. White is text. Dark navy is surface. These are not aesthetic choices that get broken when something needs to look interesting — they are load-bearing decisions that make the interface readable at a glance when a scenario is escalating.

**Light comes from the data, not from decoration.** There are no drop shadows in this interface. The only lighting is glow — and every glow is earned by the severity of whatever is generating it. A critical-severity panel glows red and pulses because it is critical, not because it looks cool. This discipline means that when something does glow, the user's eye goes to it immediately.

**Every transition is an event.** The signature transition — three stacked diagonal panels sweeping across the screen at a skew — is used exclusively for moments that matter: launching a scenario, escalating to a new threat stage, completing a mission. It is never used for incidental navigation. Using it consistently for high-stakes moments means it carries genuine weight when it plays.

**Typography is not neutral.** Bebas Neue is used for labels and headers because it is condensed, bold, and unambiguous — it reads like the kind of thing you would see on an actual mission control console. Inter handles body text because it is precise and designed for screens. JetBrains Mono handles telemetry, log entries, and code-style readouts because it is the right tool for data that needs to feel live and technical. No other typefaces appear in the application.

### Color Palette

| Name | Hex | Usage |
|---|---|---|
| Void Black | `#0A0A0F` | Base background, full bleed |
| Alert Red | `#FF2D55` | Critical severity, primary accent, diagonal transition |
| Cyber Teal | `#00F5D4` | System status, data readouts, normal-state glows |
| Warning Amber | `#FFB800` | Medium severity, caution states |
| Deep Navy | `#1A1A2E` | Card and panel backgrounds |
| Ghost White | `#F5F5F5` | All body text |

---

## Tech Stack

The stack was chosen to be appropriate for the complexity of each subsystem, not to be comprehensive. Every dependency earns its place.

| Layer | Technology | Version | Why |
|---|---|---|---|
| Framework | React | 18.x | Component model, concurrent rendering, ecosystem |
| Language | TypeScript | 5.x | Strong typing on the simulation engine and component interfaces |
| Build Tool | Vite | 5.x | Sub-second HMR during development, optimized production output |
| Styling | TailwindCSS | 3.x | Utility-first with custom design tokens in `tailwind.config.ts` |
| Animation (UI) | Framer Motion | 11.x | Layout animations, page transitions, gesture-driven interactions |
| Animation (Sequences) | GSAP | 3.x | Boot sequence, counter animations, complex multi-step timelines |
| 3D Rendering | React Three Fiber | 8.x | Declarative Three.js inside React component tree |
| 3D Helpers | @react-three/drei | 9.x | OrbitControls, Stars, useTexture, instancedMesh helpers |
| 3D Engine | Three.js | r158 | Underlying WebGL abstraction |
| Charts | Recharts | 2.x | Dashboard metric charts and attack timeline visualization |
| Icons | Lucide React | 0.400.x | Clean, consistent SVG icon set |
| Routing | React Router | 6.x | Client-side routing with loader patterns |
| State | Zustand | 4.x | Minimal, zero-boilerplate global state without Context overhead |
| Testing | Vitest | 2.x | Unit testing for the simulation engine |
| Testing | Testing Library | 16.x | Component integration tests |

### Key Package Versions

```json
{
  "dependencies": {
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "react-router-dom": "^6.24.0",
    "framer-motion": "^11.3.0",
    "gsap": "^3.12.5",
    "@react-three/fiber": "^8.17.0",
    "@react-three/drei": "^9.109.0",
    "three": "^0.167.0",
    "recharts": "^2.12.7",
    "zustand": "^4.5.4",
    "lucide-react": "^0.400.0",
    "tailwindcss": "^3.4.0",
    "clsx": "^2.1.1",
    "tailwind-merge": "^2.4.0"
  },
  "devDependencies": {
    "typescript": "^5.5.0",
    "vite": "^5.3.0",
    "@types/three": "^0.167.0",
    "vitest": "^2.0.0",
    "@testing-library/react": "^16.0.0",
    "@testing-library/user-event": "^14.0.0",
    "eslint": "^9.0.0",
    "prettier": "^3.3.0"
  }
}
```

---

## Application Architecture

Orbital Shield uses a feature-based architecture. Each major feature — dashboard, globe, scenarios, reports — owns its own pages, local components, and any feature-specific hooks. Shared design primitives live in `src/components/`. The simulation engine is a pure TypeScript module with no React dependencies, making it independently testable and fully portable.

```
                        React Router v6
                /boot  /dashboard  /scenarios  /globe  /reports
                                    |
                              App Shell
                         (Sidebar + TopBar)
                                    |
               ┌────────────────────┼───────────────────┐
               |                    |                   |
          Dashboard            Scenarios            Globe
           Feature              Feature             Feature
               |                    |                   |
               └────────────────────┼───────────────────┘
                                    |
                         Shared Component Library
                    (HUDPanel, DiagonalSlash, etc.)
                                    |
                            Zustand Stores
                     (SimStore, AlertStore, UIStore)
                                    |
                         Simulation Engine
                      (Pure TypeScript, no React)
                  SimulationEngine.ts | scoreEngine.ts
                         scenarios/*.ts
```

### Data Flow

The data flow is unidirectional and predictable. A user action in a React component dispatches a Zustand action. That action calls the simulation engine, which is a plain TypeScript class that computes a new state object and returns it. Zustand updates its store, React re-renders the relevant components, and Framer Motion and Three.js pick up the state changes to update visual output.

No action reaches outside the browser. The simulation engine has no network calls, no `setTimeout` side effects beyond what the React hooks manage, and no randomness that cannot be seeded for reproducibility.

```
User Action (click a decision card)
       |
       v
React Component (DecisionPanel.tsx)
       | calls store action
       v
Zustand Store (useSimStore.ts -> makeDecision)
       | calls engine method
       v
SimulationEngine.ts (makeDecision -> scoreImpact -> returns DecisionResult)
       | returns new state
       v
Zustand updates score, decisionLog, decisionMade
       | triggers re-render
       v
DecisionPanel re-renders (correct/wrong state revealed)
GlobeScene re-renders (attack overlay updates)
TopBar re-renders (score updates)
```

---

## Folder Structure

```
orbital-shield/
|
+-- public/
|   +-- assets/
|       +-- textures/
|       |   +-- earth_daymap.jpg          # 8K Earth surface texture (NASA public domain)
|       |   +-- earth_nightmap.jpg        # City lights, visible on the dark side of Earth
|       |   +-- earth_clouds.jpg          # Cloud layer mesh
|       |   +-- earth_specular.jpg        # Ocean specularity map
|       |   +-- starfield.jpg             # Milky Way equirectangular background
|       +-- sounds/                       # Opt-in UI audio, muted by default
|           +-- alert.mp3
|           +-- stage_advance.mp3
|           +-- boot_sequence.mp3
|
+-- src/
|   |
|   +-- main.tsx                          # Vite entry point
|   +-- App.tsx                           # Root component, provider tree assembly
|   +-- index.css                         # Tailwind directives and CSS custom properties
|   |
|   +-- router/
|   |   +-- AppRouter.tsx                 # All route definitions, loader patterns
|   |
|   +-- store/
|   |   +-- useSimStore.ts                # Active simulation lifecycle state
|   |   +-- useAlertStore.ts              # Alert feed state and generation
|   |   +-- useUIStore.ts                 # Panel visibility, modal state, globe focus
|   |
|   +-- engine/
|   |   +-- SimulationEngine.ts           # Core engine class
|   |   +-- scoreEngine.ts                # Scoring and grade computation
|   |   +-- types.ts                      # All TypeScript interfaces for the engine
|   |   +-- scenarios/
|   |       +-- index.ts                  # Scenario registry — all scenarios exported here
|   |       +-- gpsSpoofing.ts
|   |       +-- satelliteJamming.ts
|   |       +-- groundMalware.ts
|   |       +-- ransomware.ts
|   |       +-- solarFlare.ts
|   |       +-- commBlackout.ts
|   |       +-- supplyChain.ts
|   |       +-- telemetryTamper.ts
|   |       +-- authFailure.ts
|   |       +-- insiderThreat.ts
|   |
|   +-- hooks/
|   |   +-- useSimulation.ts              # Simulation lifecycle: start, advance, end
|   |   +-- useOrbit.ts                   # Satellite position computation per frame
|   |   +-- useAlerts.ts                  # Alert generation and subscription
|   |   +-- useCountdown.ts               # Stage timer with pause support
|   |   +-- useGSAP.ts                    # Ref-based GSAP animation helper
|   |
|   +-- features/
|   |   |
|   |   +-- boot/
|   |   |   +-- BootPage.tsx              # CRT boot sequence with GSAP typewriter
|   |   |
|   |   +-- dashboard/
|   |   |   +-- DashboardPage.tsx         # Main operations dashboard layout
|   |   |   +-- components/
|   |   |       +-- ThreatRadar.tsx       # SVG animated radar with threat blips
|   |   |       +-- SatelliteGrid.tsx     # Grid of satellite health indicators
|   |   |       +-- AlertFeed.tsx         # Live scrolling alert list
|   |   |       +-- MissionTimeline.tsx   # Recharts area chart for mission timeline
|   |   |       +-- SystemHealthBar.tsx   # Subsystem health progress bars
|   |   |       +-- MetricCard.tsx        # Single KPI stat with GSAP count-up
|   |   |       +-- OrbitalMinimap.tsx    # Compact embedded R3F globe, 320px height
|   |   |
|   |   +-- globe/
|   |   |   +-- GlobePage.tsx             # Full-viewport standalone globe route
|   |   |   +-- GlobeScene.tsx            # R3F Canvas wrapper with post-processing
|   |   |   +-- Earth.tsx                 # Earth mesh with multi-texture material
|   |   |   +-- Atmosphere.tsx            # Fresnel GLSL glow shader
|   |   |   +-- SatelliteSwarm.tsx        # InstancedMesh, Keplerian orbit per frame
|   |   |   +-- GroundStations.tsx        # Ground station markers and labels
|   |   |   +-- SignalPaths.tsx           # Animated CatmullRom arc signal lines
|   |   |   +-- AttackOverlay.tsx         # Attack state visualizations on the globe
|   |   |   +-- SatelliteHUD.tsx          # Slide-in telemetry panel on satellite click
|   |   |   +-- CameraController.tsx      # Smooth lerp-to-target OrbitControls wrapper
|   |   |
|   |   +-- scenarios/
|   |   |   +-- ScenarioSelectPage.tsx    # Scenario browser with filter bar
|   |   |   +-- ScenarioRunnerPage.tsx    # Active simulation layout
|   |   |   +-- components/
|   |   |       +-- ScenarioCard.tsx      # Individual scenario selection card
|   |   |       +-- StageProgress.tsx     # Five-stage horizontal progress bar
|   |   |       +-- DecisionPanel.tsx     # Response choice cards
|   |   |       +-- EducationalSidebar.tsx# Collapsible teaching content panel
|   |   |       +-- AttackTimeline.tsx    # Timestamped event log
|   |   |       +-- NarrativeBox.tsx      # Stage incident story text
|   |   |       +-- OutcomeScreen.tsx     # Post-scenario results and debrief
|   |   |
|   |   +-- reports/
|   |       +-- ReportsPage.tsx           # Completed simulation history table
|   |       +-- components/
|   |           +-- IncidentReport.tsx    # Expanded decision-by-decision debrief
|   |           +-- ScoreBreakdown.tsx    # Score visualization and grade breakdown
|   |
|   +-- components/
|   |   +-- ui/
|   |   |   +-- HUDPanel.tsx              # Core glassmorphic panel with severity glow
|   |   |   +-- DiagonalSlash.tsx         # Signature three-panel diagonal wipe transition
|   |   |   +-- GlowBadge.tsx             # Severity-colored status badge
|   |   |   +-- AlertBanner.tsx           # Top-of-screen dismissible alert banner
|   |   |   +-- RadarRing.tsx             # Reusable SVG radar ring primitive
|   |   |   +-- DataStream.tsx            # Scrolling ambient hex/binary data columns
|   |   |   +-- Scanline.tsx              # CRT scanline texture overlay
|   |   |   +-- ProgressArc.tsx           # Animated SVG circular progress arc
|   |   |   +-- TypewriterText.tsx        # Character-by-character text reveal
|   |   |
|   |   +-- layout/
|   |   |   +-- AppShell.tsx              # Persistent outer shell wrapping all routes
|   |   |   +-- Sidebar.tsx               # Left navigation sidebar
|   |   |   +-- TopBar.tsx                # Status bar with clock, score, alert count
|   |   |   +-- PageTransition.tsx        # Route-level animation wrapper
|   |   |
|   |   +-- three/
|   |       +-- StarField.tsx             # Procedural starfield using drei Points
|   |       +-- GlowMaterial.tsx          # Reusable additive glow shader material
|   |
|   +-- lib/
|   |   +-- orbitMath.ts                  # Kepler's equation solver and ECI conversion
|   |   +-- colorUtils.ts                 # Severity-to-color mapping functions
|   |   +-- formatters.ts                 # Time, score, and telemetry value formatters
|   |   +-- cn.ts                         # clsx + tailwind-merge class name utility
|   |
|   +-- types/
|       +-- simulation.ts                 # Simulation domain types re-exported for components
|       +-- satellite.ts                  # Satellite and orbital element types
|       +-- alert.ts                      # Alert system types
|
+-- tests/
|   +-- engine/
|   |   +-- SimulationEngine.test.ts      # Engine unit tests: stage advance, decision logic
|   |   +-- scoreEngine.test.ts           # Grade computation boundary tests
|   +-- hooks/
|       +-- useSimulation.test.ts         # Simulation hook integration tests
|
+-- tailwind.config.ts
+-- vite.config.ts
+-- tsconfig.json
+-- tsconfig.app.json
+-- eslint.config.js
+-- .prettierrc
+-- README.md
```

---

## Pages and Screens

### Boot Sequence — Route: `/`

This is the first thing a user sees. It is not a loading spinner. It is a deliberate, timed experience designed to set the tone before anything else renders.

The screen is pure black. A green monospace cursor blinks once. Then, line by line, a system initialization sequence types itself out at 18ms per character using GSAP's staggered `to()`:

```
ORBITAL SHIELD v2.1.0
[INITIALIZING CORE SYSTEMS]
──────────────────────────────────────────────────────
[  OK  ]  SATELLITE NETWORK ...................  ONLINE
[  OK  ]  THREAT DETECTION ENGINE .............  ARMED
[  OK  ]  GROUND STATION UPLINK ...............  ACTIVE
[  OK  ]  ENCRYPTION LAYER ....................  ENABLED
[  OK  ]  ORBITAL TRACKING ....................  LOCKED
[ WARN ]  ANOMALOUS SIGNAL DETECTED ON BAND 3.7 GHz
[  OK  ]  MISSION CONTROL INTERFACE ...........  READY
──────────────────────────────────────────────────────
PRESS ANY KEY TO ACCESS OPERATIONS CENTER
```

A CRT scanline overlay flickers over the text throughout. After the final line appears, a half-second pause, then the `DiagonalSlash` transition wipes across the screen and the user lands on the dashboard. Total duration is approximately 3.5 seconds. Pressing any key or clicking skips it.

The warning line — `ANOMALOUS SIGNAL DETECTED ON BAND 3.7 GHz` — is intentional. It sets an expectation: something is already happening, and this is not a system at peace. The color shifts to amber for that line only.

---

### Operations Dashboard — Route: `/dashboard`

The home base. This is what a mission control analyst would look at on a normal shift — a composite view of every system at once, updated continuously with simulated live data.

The layout is a 12-column grid. The left six columns are dominated by the embedded 3D globe (`OrbitalMinimap`) sitting in a `HUDPanel`. The right side is split vertically between the alert feed and the threat radar. Below that, three equal-width panels hold the satellite health grid, system health bars, and a Recharts area chart showing the mission timeline.

A full-width row of metric cards runs across the top of the content area, above the main grid:

```
  Total Satellites     Active Threats     System Health     Signal Integrity     Ground Stations
       47                    3               94.2%              98.7%               12 / 14
```

Each metric value counts up from zero when the page mounts — a one-time GSAP animation lasting 1,200ms with an ease-out curve. After mounting, each value fluctuates by a small seeded random delta every 5 seconds, giving the impression of a live system without being distracting.

The globe in the dashboard is a compact version of the full globe. It rotates slowly. Clicking it navigates to `/globe`. During an active scenario, the globe reflects the attack state in real time.

The alert feed occupies the right column. Each new alert slides in from the right edge on a spring animation. Alerts carry a colored left border: red for critical, amber for warning, teal for informational. The 15 most recent alerts are visible. Older alerts fade to 40% opacity. Clicking an alert tied to a scenario navigates directly to that scenario's runner page.

The threat radar is the bottom-right panel — an SVG radar with four concentric range rings, cross-hair lines at 45-degree intervals, and a rotating sweep arm. Threat blips appear as small circles at polar coordinates computed from scenario metadata. Each blip has a pulsing ring ripple on a 2-second interval. The color of each blip matches its severity.

---

### Scenario Select — Route: `/scenarios`

The threat library. Ten scenario cards are laid out in a staggered grid. Cards mount with a bottom-up stagger, each delayed by 50ms from the previous.

Each card contains:

- A threat category icon in a colored circle (top-left)
- The scenario name in Bebas Neue at 32px
- A one-sentence description in Inter
- A severity badge (Critical / High / Medium) with the corresponding glow color
- A difficulty rating rendered as five stars, filled according to difficulty level 1–5
- An estimated duration: approximately 12 minutes
- Tags for the affected systems: GPS, Communications, Telemetry, and so on

Cards have a diagonal clip-path applied to the bottom-right corner — a subtle nod to the design language without being heavy-handed. Hovering a card plays a shimmer that sweeps from left to right across the card surface using a Framer Motion `backgroundPositionX` animation, and the card lifts 4px with a smooth spring.

A filter bar sits at the top of the page. It filters by severity level or by threat category. The filter does not reload the page; it filters the rendered card list in memory.

Clicking a card triggers the `DiagonalSlash` transition and navigates to `/scenarios/:id` with the selected scenario's ID.

---

### Scenario Runner — Route: `/scenarios/:id`

This is the core experience. The entire screen is dedicated to the active simulation.

At the top: a stage progress bar showing the five stages connected by animated fill lines. The current stage chip is enlarged and glow-colored. Completed stages show a checkmark icon. A countdown timer sits at the far right of this bar, counting down the time allocated for the current stage.

Below the progress bar, the screen is split into two panes.

The left pane occupies roughly 65% of the width and contains two stacked sections. The upper section is the `NarrativeBox` — a text panel that tells the story of what is happening at this moment in the incident. The text changes per stage and fades in on transition. The lower section is the `DecisionPanel`, which presents 2 to 4 response choices as large clickable cards.

Each decision card shows:
- A bold action statement describing what the analyst would do
- A consequence preview that is revealed only on hover, shown in italics at reduced opacity

After a decision is made, the panel locks and the result is shown: the optimal choice gets a teal border and a checkmark that scales in from zero. Wrong choices dim to 40% opacity. The choice the analyst actually made — if wrong — gets a red border and a brief horizontal shake animation.

The right pane is the `EducationalSidebar`, approximately 320px wide and collapsible. It opens automatically at the start of each new stage with content relevant to that stage. It can be pinned open. When collapsed, a thin labeled tab remains visible at the right edge.

A scrolling event log runs along the bottom of the screen — the `AttackTimeline`. It shows timestamped events as they occur: `[T+00:02:34] Anomalous uplink signal detected on Ku-band transponder 7`. New events appear with a slide-up animation.

When the fifth stage (Lessons Learned) completes, the `OutcomeScreen` takes over with a full-panel animation sequence.

---

### Outcome Screen — overlaid on Scenario Runner

The outcome screen plays after the final stage. It is not a separate route — it appears in-place over the runner layout with the `DiagonalSlash` wipe marking the transition.

The sequence:

1. DiagonalSlash sweeps across
2. A mission report header appears: the scenario name, date, and duration
3. A circular progress arc animates from zero to the analyst's final score over 1,500ms
4. The grade letter drops in with a scale spring animation — starting at scale 3, landing at scale 1 with a slight overshoot
5. A brief performance summary appears below the grade with a stagger fade-in
6. A Lessons Learned accordion expands automatically, one item at a time
7. Two CTAs appear: `VIEW FULL REPORT` and `RUN AGAIN`

Grade thresholds:

| Score | Grade | Label |
|---|---|---|
| 90–100 | S | Elite Analyst |
| 75–89 | A | Senior Analyst |
| 60–74 | B | Analyst |
| 45–59 | C | Trainee |
| 0–44 | F | Compromised |

---

### Reports — Route: `/reports`

A table of every completed simulation run. Columns: scenario name, date completed, final score, grade badge, total duration, and a view button.

Clicking a row expands an `IncidentReport` panel directly below it. The panel shows:

- An executive summary (two to three sentences on what happened)
- A stage-by-stage breakdown of every decision made, what the analyst chose, what the optimal choice was, and the score impact of each
- The full key terminology glossary for that scenario
- A lessons section with the three most important takeaways
- A fictional reading list relevant to the scenario's threat class

The expanded report closes when the row is clicked again or when another row is opened.

---

### Globe Full View — Route: `/globe`

A standalone full-viewport 3D scene. The sidebar and top bar are hidden. Four minimal HUD overlays are placed in the corners of the screen:

- Top-left: `ORBITAL SHIELD // GLOBAL NETWORK VIEW` with total satellite count
- Top-right: active alert count, current threat level
- Bottom-left: selected satellite telemetry (hidden until a satellite is selected)
- Bottom-right: keyboard hint for camera controls

Users can click any satellite to select it. The camera lerps smoothly toward that satellite over 1,200ms. The satellite's orbital path highlights in teal. A telemetry panel slides in from the left showing: satellite ID, name, orbital altitude in kilometers, inclination in degrees, right ascension of ascending node, signal strength percentage, health status, and last contact timestamp.

Pressing Escape or clicking empty space deselects the satellite and returns the camera to its default position.

---

## Component Library

### HUDPanel

The foundational panel primitive. Every information section in the application is a HUDPanel. It is the most-used component in the codebase.

```typescript
interface HUDPanelProps {
  title: string;
  severity?: 'normal' | 'warning' | 'critical';
  className?: string;
  headerRight?: React.ReactNode;
  noPadding?: boolean;
  children: React.ReactNode;
}
```

Background is `rgba(26, 26, 46, 0.85)` with `backdrop-blur-md`. The border is 1px solid and its color is derived from the `severity` prop:

- `normal` — `rgba(0, 245, 212, 0.3)`, static
- `warning` — `rgba(255, 184, 0, 0.5)`, pulses glow every 2 seconds
- `critical` — `rgba(255, 45, 85, 0.6)`, pulses glow every 1 second

The title bar has a 4px left border in the severity accent color. Title text is Bebas Neue, uppercase, with 0.5rem letter-spacing. The right side of the header accepts an optional React node for supplemental controls or status indicators.

On mount, every HUDPanel animates from `opacity: 0, translateY: 12px` to `opacity: 1, translateY: 0` over 400ms. When panels appear in groups — such as on the dashboard — they are staggered at 60ms intervals via `AnimatePresence`.

---

### DiagonalSlash

The signature transition component. Used for every major state change.

```typescript
interface DiagonalSlashProps {
  trigger: boolean;
  onComplete?: () => void;
  colors?: [string, string, string];
}
```

Three absolutely positioned `div` elements, each `width: 120%` and `height: 100%`, transformed with `skewX(-12deg)`, staggered horizontally so they overlap without aligning. Default colors are `#FF2D55`, `rgba(255, 45, 85, 0.6)`, and `rgba(0, 245, 212, 0.3)`.

Framer Motion animates each panel's `scaleX` from 0 to 1 on enter, then from 1 to 0 on exit. `transformOrigin` is set to `left` on enter and `right` on exit. The three panels stagger by 80ms each, giving the total transition a 600ms runtime. The `onComplete` callback fires after the exit animation finishes — it is used by the router to trigger actual navigation after the visual wipe completes.

---

### ThreatRadar

```typescript
interface ThreatRadarProps {
  threats: Array<{
    id: string;
    angle: number;       // degrees, 0 at top, clockwise
    distance: number;    // 0 to 1, fraction of radar radius
    severity: 'low' | 'medium' | 'high' | 'critical';
  }>;
  size?: number;         // SVG viewport size, default 200
}
```

The radar is built in SVG. Four concentric `<circle>` elements at 25%, 50%, 75%, and 100% of the radar radius carry a stroke of `rgba(0, 245, 212, 0.15)`. Cross-hair lines run at 0, 90, 180, and 270 degrees. Diagonal lines run at 45, 135, 225, and 315 degrees at lower opacity.

The sweep arm is a `<line>` rotated by CSS `animation: spin 4s linear infinite`. Behind the arm, a conic gradient creates a fading green arc representing the "lit" area the arm has just swept, fading from `rgba(0, 245, 212, 0.25)` to transparent over 90 degrees.

Each threat blip is a `<circle>` positioned using polar-to-Cartesian conversion from the `angle` and `distance` props. A CSS `animation: ping` creates an expanding ring on each blip at 2-second intervals. Fill color is mapped to severity.

---

### DataStream

An ambient background component that runs behind content panels to reinforce the technical atmosphere.

```typescript
interface DataStreamProps {
  columns?: number;
  speed?: 'slow' | 'normal' | 'fast';
  opacity?: number;
}
```

Each column is a `div` containing a long string of mixed hex octets and binary sequences — content that reads like raw network traffic or memory dumps. The content is duplicated so that a `translateY` CSS animation can scroll it continuously without a seam. The animation runs at a speed controlled by the `speed` prop (slow: 40s, normal: 25s, fast: 15s). A `mask-image` gradient fades the top and bottom 20% of each column to transparent, so the stream dissolves into the background gracefully.

Default opacity is 0.15 — visible as texture but never competing with foreground content.

---

### TypewriterText

```typescript
interface TypewriterTextProps {
  text: string;
  speed?: number;          // milliseconds per character, default 30
  startDelay?: number;     // milliseconds before first character
  onComplete?: () => void;
  cursor?: boolean;        // show blinking cursor during and after typing
  className?: string;
}
```

Uses `useEffect` with `setInterval` to append one character at a time to a local state string. When `text` changes — such as between scenario stages — the component resets and re-types from empty. The `cursor` prop renders a blinking `|` character at the end of the current text using a CSS `animation: blink 1s step-end infinite`.

---

### ProgressArc

```typescript
interface ProgressArcProps {
  value: number;           // 0 to 100
  size?: number;           // SVG viewport size, default 160
  strokeWidth?: number;    // default 8
  color?: string;          // default: derived from value range
  label?: string;          // text rendered at center
  animate?: boolean;       // animate from 0 to value on mount
}
```

Implemented as an SVG `<circle>` with `stroke-dasharray` set to the full circumference and `stroke-dashoffset` set to `circumference * (1 - value/100)`. When `animate` is true, Framer Motion transitions `stroke-dashoffset` from `circumference` to the target value over 1,500ms with an ease-out curve.

The default color logic maps score ranges to the severity palette: 0–44 is red, 45–74 is amber, 75–89 is white, 90–100 is teal.

---

### StageProgress

```typescript
interface StageProgressProps {
  stages: string[];
  currentStage: number;    // 0-indexed
  completedStages: number[];
}
```

Renders a horizontal row of stage chips. Each chip is a small rounded rectangle containing the stage name. Between chips, a thin horizontal line represents the path between stages.

The chip for the current stage is `scale(1.05)`, accent-colored, and carries a subtle glow. Completed stage chips show a checkmark icon and are dimmed to indicate they are done rather than active. When a stage completes and the next begins, the connecting line between them fills from left to right over 500ms using a Framer Motion `scaleX` animation on a colored overlay element.

---

### DecisionPanel

```typescript
interface DecisionPanelProps {
  decisions: Decision[];
  onDecide: (id: string) => void;
  locked: boolean;
  revealed: boolean;
  selectedId?: string;
}
```

Renders 2 to 4 decision cards in a grid. Each card is a large clickable area showing the action text in bold and the consequence text — which is visible only on hover, appearing with a fade-in at reduced opacity and in italics.

When `revealed` is true and `selectedId` is set, the panel enters its result state. The optimal decision card gets `border-color: #00F5D4` and a checkmark icon that scales in from zero. Every other card dims to 40% opacity. If the selected decision was not optimal, it additionally gets `border-color: #FF2D55`, an `x` icon, and a brief horizontal shake animation (three rapid position oscillations via Framer Motion keyframes). The panel is `pointer-events: none` during the locked state and during transitions.

---

### SatelliteHUD

```typescript
interface SatelliteHUDProps {
  satellite: Satellite | null;
  onClose: () => void;
}
```

A panel that slides in from the left edge of the globe view when a satellite is selected. When `satellite` is null, it animates out to the left. When a satellite is provided, it animates in to a fixed-width panel (320px) overlaid on the bottom-left of the globe canvas.

Content: satellite ID and name as the header, then a data grid with labeled rows:

- Orbital Altitude: `562 km`
- Inclination: `53.05°`
- RAAN: `235.7°`
- Signal Strength: `94.2%`
- Health Status: `Nominal`
- Last Contact: `00:00:03 ago`

All values update in real time as the simulation runs. Signal strength and health use color coding matching the global severity system.

---

## 3D Visualization System

### Architecture

The 3D system is contained in `src/features/globe/`. The `GlobeScene.tsx` component wraps a React Three Fiber `<Canvas>` with post-processing effects. All satellite positions are computed mathematically using Keplerian orbital elements — there is no external orbit data, no API, and no file loading beyond texture maps. Everything runs inside the animation loop.

### Earth

```
Geometry:   SphereGeometry(6, 64, 64)
                 radius 6 world units, 64-segment subdivision for smooth silhouette

Material:   MeshStandardMaterial
                 map:          earth_daymap.jpg      (8K color texture)
                 emissiveMap:  earth_nightmap.jpg    (city lights, visible on the dark side)
                 emissive:     #ffffff at 0.15 intensity
                 specularMap:  earth_specular.jpg    (ocean reflectivity)

Clouds:     SphereGeometry(6.05, 64, 64)
                 alphaMap: earth_clouds.jpg
                 transparent: true, opacity: 0.4
                 rotation offset from Earth: 0.0002 rad/frame (clouds drift)

Rotation:   0.0005 rad/frame on the Y axis
```

### Atmosphere

A custom GLSL shader wrapped in a `<shaderMaterial>` creates the blue atmospheric limb glow visible on the Earth's edge. The vertex shader passes `vNormal` and `vPosition` to the fragment shader. The fragment shader computes:

```glsl
float intensity = pow(dot(vNormal, normalize(cameraPosition - vPosition)), 2.0);
gl_FragColor = vec4(0.2, 0.5, 1.0, intensity * 0.6);
```

This creates a soft blue halo that brightens near the edges where the atmosphere's thickness is greatest relative to the viewing angle — which is the same optical phenomenon that makes real atmospheres visible from orbit.

### Satellite Swarm

Fifty satellite instances are rendered using `THREE.InstancedMesh` for performance. Each satellite has six Keplerian orbital elements stored at initialization: semi-major axis `a`, eccentricity `e`, inclination `i`, right ascension of ascending node `Ω`, argument of periapsis `ω`, and mean anomaly at epoch `M₀`.

Per-frame, the simulation loop computes each satellite's position:

1. Compute mean anomaly: `M = M₀ + n * t`, where `n` is mean motion derived from `a`
2. Solve Kepler's equation `M = E - e * sin(E)` for eccentric anomaly `E` using Newton-Raphson iteration (10 steps, converges to machine precision in 4–5 iterations for typical eccentricities)
3. Compute true anomaly `ν` from `E` and `e`
4. Compute orbital radius: `r = a * (1 - e * cos(E))`
5. Convert to perifocal frame, then rotate by `ω`, `i`, and `Ω` to ECI coordinates
6. Apply Earth's rotation offset to convert to ECEF
7. Scale and set the instance matrix

When a scenario marks a satellite as under attack, the instance's color shifts to red via the `instanceColor` attribute. When the scenario enters the Recovery stage, the color shifts back to teal and a particle burst plays at the satellite's position — a billboard quad that scales up and fades out over 800ms.

Click detection uses Three.js `Raycaster` set against all satellite instances.

### Signal Paths

Signal paths between satellites and ground stations are rendered as animated lines following `THREE.CatmullRomCurve3` paths that arc above the Earth's surface rather than clipping through it. Each path uses a custom `LineMaterial` with a `dashOffset` uniform animated per frame, creating the impression of a signal traveling along the path.

In attack scenarios involving communication disruption, specific signal paths are broken — the line color shifts to red and the animation pauses, replaced by a flickering stutter effect using a noise function on the opacity uniform.

### Attack Overlay

When a scenario is active, `AttackOverlay.tsx` reads the current scenario's `globeState` from the Zustand store and applies visual states to the relevant scene elements:

- Targeted satellite instances: color set to red, intensity pulsing at 1Hz
- A `RippleRing` — a torus geometry that scales outward from the satellite and fades — animates on loop while the attack is active
- A red `PointLight` appears at the attack location with intensity proportional to scenario severity
- Targeted ground station markers flash red at 2Hz

On transition to the Containment stage, the attack visual intensity begins ramping down over 2,000ms. On Recovery, it fades completely and the teal glow returns.

---

## Simulation Engine

### SimulationEngine Class

The engine is a plain TypeScript class with no React, no Zustand, and no DOM interaction. It takes a `Scenario` object on construction and manages state for a single simulation run.

```typescript
export class SimulationEngine {
  private scenario: Scenario;
  private state: SimulationState;

  constructor(scenario: Scenario) {
    this.scenario = scenario;
    this.state = {
      currentStageIndex: 0,
      score: 100,
      decisionLog: [],
      startTime: Date.now(),
      completed: false,
    };
  }

  getCurrentStage(): Stage {
    return this.scenario.stages[this.state.currentStageIndex];
  }

  advanceStage(): Stage | null {
    if (this.state.currentStageIndex >= this.scenario.stages.length - 1) {
      this.state.completed = true;
      return null;
    }
    this.state.currentStageIndex++;
    return this.getCurrentStage();
  }

  makeDecision(decisionId: string): DecisionResult {
    const stage = this.getCurrentStage();
    const decision = stage.decisions.find(d => d.id === decisionId);

    if (!decision) throw new Error(`Decision ${decisionId} not found in stage ${stage.id}`);

    this.state.score = Math.max(0, Math.min(100, this.state.score + decision.scoreImpact));

    this.state.decisionLog.push({
      stageId: stage.id,
      decisionId,
      timestamp: Date.now(),
      isOptimal: decision.isOptimal,
      scoreImpact: decision.scoreImpact,
    });

    return {
      isOptimal: decision.isOptimal,
      consequence: decision.consequence,
      newScore: this.state.score,
      optimalDecision: stage.decisions.find(d => d.isOptimal) ?? decision,
    };
  }

  getScoreBreakdown(): ScoreBreakdown {
    return scoreEngine.compute(this.state.score, this.state.decisionLog, this.scenario);
  }

  serialize(): CompletedRun {
    return {
      scenarioId: this.scenario.id,
      scenarioName: this.scenario.name,
      completedAt: Date.now(),
      duration: Date.now() - this.state.startTime,
      finalScore: this.state.score,
      grade: this.getScoreBreakdown().grade,
      decisionLog: this.state.decisionLog,
    };
  }
}
```

### TypeScript Interfaces

```typescript
// engine/types.ts

export type Severity = 'low' | 'medium' | 'high' | 'critical';

export type ThreatCategory =
  | 'signal-attack'
  | 'malware'
  | 'authentication'
  | 'supply-chain'
  | 'insider'
  | 'natural'
  | 'data-integrity';

export interface Scenario {
  id: string;
  name: string;
  shortDescription: string;
  category: ThreatCategory;
  severity: Severity;
  difficulty: 1 | 2 | 3 | 4 | 5;
  estimatedDuration: number;           // minutes
  affectedSystems: SystemType[];
  stages: Stage[];
  educational: EducationalContent;
  globeConfig: GlobeScenarioConfig;
}

export interface Stage {
  id: string;
  name: string;
  duration: number;                    // seconds for the countdown
  narrative: string;
  events: TimelineEvent[];
  decisions: Decision[];
  educationalNote: string;
  globeState: GlobeStageState;
}

export interface Decision {
  id: string;
  text: string;
  hint: string;                        // visible on hover
  consequence: string;                 // visible after selection
  isOptimal: boolean;
  scoreImpact: number;                 // range: -20 to +15
}

export interface EducationalContent {
  title: string;
  definition: string;
  realWorldExample: string;
  howItWorks: string;
  defenseStrategies: string[];
  keyTerms: Record<string, string>;
  furtherReading: string[];
}

export interface GlobeScenarioConfig {
  targetSatellites: string[];
  targetGroundStations: string[];
  signalPaths: SignalPathConfig[];
  attackType: AttackVisualizationType;
}

export type AttackVisualizationType =
  | 'signal-intercept'
  | 'signal-jam'
  | 'uplink-inject'
  | 'ground-breach'
  | 'blackout'
  | 'solar';

export interface TimelineEvent {
  offsetSeconds: number;               // seconds after stage start
  message: string;
  severity: Severity;
}

export interface DecisionResult {
  isOptimal: boolean;
  consequence: string;
  newScore: number;
  optimalDecision: Decision;
}
```

### Score Engine

```typescript
// engine/scoreEngine.ts

export interface ScoreBreakdown {
  total: number;
  grade: 'S' | 'A' | 'B' | 'C' | 'F';
  gradeLabel: string;
  optimalDecisions: number;
  totalDecisions: number;
  accuracyPercent: number;
  stageBreakdown: Array<{
    stageName: string;
    decisionText: string;
    wasOptimal: boolean;
    scoreImpact: number;
  }>;
}

const GRADE_BOUNDARIES = { S: 90, A: 75, B: 60, C: 45 } as const;
const GRADE_LABELS = {
  S: 'Elite Analyst',
  A: 'Senior Analyst',
  B: 'Analyst',
  C: 'Trainee',
  F: 'Compromised',
};

export function compute(
  score: number,
  log: DecisionRecord[],
  scenario: Scenario
): ScoreBreakdown {
  const grade =
    score >= GRADE_BOUNDARIES.S ? 'S' :
    score >= GRADE_BOUNDARIES.A ? 'A' :
    score >= GRADE_BOUNDARIES.B ? 'B' :
    score >= GRADE_BOUNDARIES.C ? 'C' : 'F';

  const optimalDecisions = log.filter(d => d.isOptimal).length;

  return {
    total: score,
    grade,
    gradeLabel: GRADE_LABELS[grade],
    optimalDecisions,
    totalDecisions: log.length,
    accuracyPercent: log.length > 0 ? Math.round((optimalDecisions / log.length) * 100) : 0,
    stageBreakdown: log.map(record => {
      const stage = scenario.stages.find(s => s.id === record.stageId)!;
      const decision = stage.decisions.find(d => d.id === record.decisionId)!;
      return {
        stageName: stage.name,
        decisionText: decision.text,
        wasOptimal: record.isOptimal,
        scoreImpact: record.scoreImpact,
      };
    }),
  };
}
```

---

## State Management

All global state is in Zustand. Three stores cover the full application surface area.

### useSimStore

```typescript
interface SimState {
  activeScenario: Scenario | null;
  engine: SimulationEngine | null;
  currentStageIndex: number;
  score: number;
  isRunning: boolean;
  isPaused: boolean;
  decisionMade: boolean;
  completedScenarios: CompletedRun[];

  startScenario: (scenarioId: string) => void;
  advanceStage: () => void;
  makeDecision: (decisionId: string) => DecisionResult;
  pauseSimulation: () => void;
  resumeSimulation: () => void;
  endScenario: () => void;
}
```

The `startScenario` action looks up the scenario by ID from the scenario registry, instantiates a `SimulationEngine`, and sets all state to initial values. `makeDecision` calls `engine.makeDecision`, which returns a `DecisionResult` that the store propagates to the UI layer. `endScenario` calls `engine.serialize()` to produce a `CompletedRun`, pushes it to `completedScenarios`, and clears the active simulation.

Completed scenarios are persisted to `localStorage` through Zustand's `persist` middleware so the Reports page survives page refreshes.

### useAlertStore

```typescript
interface AlertState {
  alerts: Alert[];
  unreadCount: number;

  addAlert: (alert: Omit<Alert, 'id' | 'timestamp'>) => void;
  dismissAlert: (id: string) => void;
  markAllRead: () => void;
  clearAll: () => void;
}

interface Alert {
  id: string;
  timestamp: number;
  severity: Severity;
  title: string;
  message: string;
  systemAffected?: string;
  scenarioId?: string;
  read: boolean;
}
```

Alerts are generated by `useAlerts.ts` on a seeded random interval between 8 and 30 seconds. When a scenario is active, the alert store also receives scenario-driven alerts — these come from the stage's `events` array at their specified `offsetSeconds`.

The store keeps the 50 most recent alerts and drops the oldest when this limit is exceeded.

### useUIStore

```typescript
interface UIState {
  sidebarCollapsed: boolean;
  educationalSidebarOpen: boolean;
  educationalSidebarPinned: boolean;
  globeFocusTarget: string | null;
  activeModal: string | null;
  transitionPlaying: boolean;

  toggleSidebar: () => void;
  toggleEducationalSidebar: () => void;
  pinEducationalSidebar: () => void;
  setGlobeFocus: (satelliteId: string | null) => void;
  openModal: (modalId: string) => void;
  closeModal: () => void;
  setTransitionPlaying: (playing: boolean) => void;
}
```

`transitionPlaying` is set to true when the `DiagonalSlash` animation begins and false when it completes. During this window, the router is blocked from resolving the new route, ensuring navigation does not race with the transition animation.

---

## Animation System

Every animation in the application has a defined purpose. The rule is: if removing an animation makes the interface harder to understand or makes a state change harder to perceive, the animation stays. If removing it only makes the interface quieter, it is reconsidered.

| Trigger | Component | Library | Duration | Notes |
|---|---|---|---|---|
| App boot typewriter | BootPage | GSAP | 3,500ms total | `staggerTo` at 18ms per character |
| Route transition | DiagonalSlash | Framer Motion | 600ms | Three panels staggered at 80ms |
| Dashboard mount stagger | HUDPanel groups | Framer Motion | 400ms per panel | 60ms between panels |
| New alert arrival | AlertFeed item | Framer Motion | 300ms | `x: 80 to 0` on a spring |
| Metric count-up | MetricCard | GSAP | 1,200ms | `to({ innerText })` with ease-out |
| Radar sweep | ThreatRadar arm | CSS | Continuous | `spin 4s linear infinite` |
| Threat blip pulse | ThreatRadar blip | CSS | Continuous | `ping 2s ease-out infinite` |
| Scenario card hover | ScenarioCard | Framer Motion | 200ms | `y: -4`, shimmer sweep |
| Stage transition line | StageProgress | Framer Motion | 500ms | `scaleX: 0 to 1` on fill overlay |
| Decision correct reveal | DecisionPanel | Framer Motion | 400ms | Border color + checkmark scale-in |
| Decision wrong reveal | DecisionPanel | Framer Motion | 500ms | Red border + horizontal shake |
| Satellite attack | SatelliteSwarm | Three.js | 800ms | Instance color + billboard particle |
| Satellite recovery | SatelliteSwarm | Three.js | 1,500ms | Color fade back to teal |
| Score arc fill | ProgressArc | Framer Motion | 1,500ms | `strokeDashoffset` ease-out |
| Grade letter slam | OutcomeScreen | Framer Motion | 400ms | `scale: 3 to 1` with spring overshoot |
| Narrative text change | NarrativeBox | Framer Motion | 300ms | Old text slides up, new fades in |
| Data stream scroll | DataStream | CSS | Continuous | `translateY` linear, seamless loop |
| Earth rotation | Earth | Three.js | Continuous | 0.0005 rad/frame on Y axis |
| Camera lerp to satellite | CameraController | Three.js | 1,200ms | `lerpVectors` toward target position |
| Educational sidebar open | EducationalSidebar | Framer Motion | 350ms | `x: 320 to 0` |

All Framer Motion animations check `window.matchMedia('(prefers-reduced-motion: reduce)')` on mount. When reduced motion is preferred, duration values are set to 0 and transforms are removed, leaving only opacity changes where necessary for state visibility.

---

## Simulation Scenarios

### 1 — GPS Signal Spoofing

Category: Signal Attack. Severity: Critical. Difficulty: 4 of 5. Estimated duration: 14 minutes. Affected systems: GPS, Navigation, Timing Infrastructure.

A malicious actor transmits counterfeit GPS signals at higher power than the legitimate satellite broadcasts. Receivers cannot distinguish the fake from the real signal and begin reporting false positions — potentially by hundreds of kilometers. The attack requires no physical access and leaves no trace in the satellite's logs because it never interacts with the satellite at all. Only the downlink broadcast is targeted.

The scenario teaches: how GPS authentication protocols work, why civilian GPS signals are unsigned and therefore vulnerable, what Galileo OSNMA and GPS III Navigation Message Authentication provide as countermeasures, and how maritime and aviation receivers detect spoofing through cross-checking with inertial navigation systems.

---

### 2 — Satellite Signal Jamming

Category: Signal Attack. Severity: High. Difficulty: 3 of 5. Estimated duration: 10 minutes. Affected systems: Communications, Telemetry, GPS.

A broadband noise jammer in the vicinity of a ground receiver overwhelms the legitimate satellite downlink, making the receiver unable to decode any signal. Unlike spoofing, jamming is immediately detectable — the receiver reports loss of signal rather than a false position — but it is difficult to counter in the short term without physical movement or frequency agility.

The scenario teaches: the difference between jamming and spoofing, spread-spectrum and frequency-hopping techniques, anti-jam antenna design, and how militaries prioritize frequency agility in protected waveform designs.

---

### 3 — Ground Station Malware Infection

Category: Malware. Severity: Critical. Difficulty: 5 of 5. Estimated duration: 18 minutes. Affected systems: Ground Control, Uplink, Command Interface.

A spear-phishing email sent to a mission control engineer delivers a remote access trojan. The attacker establishes persistence on the ground segment network, moves laterally toward uplink systems over several days, and begins probing satellite command interfaces. The satellite itself is never directly attacked — the ground segment is the entry point.

The scenario teaches: the importance of network segmentation between corporate and operational networks, zero-trust architecture applied to ground systems, why mission control workstations should never access the public internet directly, and how to build an incident response playbook for ground segment compromises.

---

### 4 — Mission Control Ransomware

Category: Malware. Severity: Critical. Difficulty: 5 of 5. Estimated duration: 20 minutes. Affected systems: All Ground Systems.

Ransomware delivered through a compromised software update distributed by a trusted maintenance vendor encrypts mission control workstations simultaneously at 03:00 UTC. Satellite operations cease. Encrypted files include the command-and-control software, mission databases, and the key management system for satellite authentication. The attackers demand payment within 72 hours before they claim to delete decryption keys.

The scenario teaches: why offline, immutable backups are non-negotiable, the difference between recovery time objective and recovery point objective, the ethics and practical considerations of ransomware negotiation, and why supply chain software updates must be verified against hardware security module signatures.

---

### 5 — Solar Flare Interference

Category: Natural Hazard. Severity: High. Difficulty: 2 of 5. Estimated duration: 9 minutes. Affected systems: Communications, Solar Power, Radiation Shielding.

An X-class solar flare releases a coronal mass ejection that reaches Earth's magnetosphere 18 hours after observation. The resulting geomagnetic storm disrupts satellite communications across multiple frequency bands, degrades GPS accuracy for hours, and deposits cumulative radiation dose on satellites in medium and low Earth orbit that accelerates component degradation.

The scenario teaches: space weather monitoring via NOAA's Space Weather Prediction Center, how operators put satellites into safe mode before a CME arrives, the physics of why CMEs cause radio blackouts, and why radiation hardening is a design requirement rather than an afterthought.

---

### 6 — Communication Blackout

Category: Signal Attack. Severity: Medium. Difficulty: 2 of 5. Estimated duration: 8 minutes. Affected systems: Communications, Telemetry.

Coordinated jamming of all ground station uplinks covering a satellite constellation cuts the operator's ability to send commands or receive telemetry. The satellites continue operating autonomously, but they cannot be tasked, their status is unknown, and if any anomaly develops onboard, operators cannot intervene.

The scenario teaches: the design of redundant ground station networks across geographic regions, the role of TDRS-class relay satellites that can relay commands via satellite-to-satellite links when primary ground contact is lost, and how satellites implement autonomous contingency modes when they lose contact with the ground.

---

### 7 — Supply Chain Compromise

Category: Supply Chain. Severity: Critical. Difficulty: 5 of 5. Estimated duration: 20 minutes. Affected systems: Software, Firmware, Hardware.

A firmware update distributed by a trusted third-party component vendor contains a backdoor inserted during the software build process. The update is cryptographically signed — but the vendor's code signing key was compromised six months earlier in a breach the vendor has not yet disclosed. After the update installs across the fleet, an attacker can execute arbitrary commands through a covert channel on an unused telemetry downlink frequency.

The scenario teaches: software supply chain security fundamentals, why reproducible builds matter for firmware verification, how hardware security modules protect signing keys, and what organizations like CISA recommend for satellite firmware update pipelines.

---

### 8 — Telemetry Data Manipulation

Category: Data Integrity. Severity: High. Difficulty: 4 of 5. Estimated duration: 15 minutes. Affected systems: Telemetry, Monitoring, Data Processing.

An attacker with access to the telemetry processing pipeline begins injecting falsified sensor readings. Battery voltage appears nominal. Attitude control system readings appear stable. Orbital ephemeris data appears correct. Meanwhile, the satellite is actually experiencing a slow orbital decay that, if uncorrected within days, will result in reentry. Operators are managing a spacecraft based on entirely fabricated data.

The scenario teaches: why telemetry data integrity verification matters as much as confidentiality, how cryptographic signing of telemetry packets can detect injection, the role of anomaly detection in time-series sensor data — looking for statistical impossibilities or transitions that violate known physical constraints.

---

### 9 — Authentication Failure

Category: Authentication. Severity: High. Difficulty: 3 of 5. Estimated duration: 12 minutes. Affected systems: Ground Control, Command Interface.

An attacker uses a credential stuffing attack against the mission control web portal, using a database of leaked username and password combinations from an unrelated breach. One set of credentials belongs to a satellite command operator who reused a password. The attacker gains access to an operator-level account, bypasses single-factor authentication, and begins issuing unauthorized commands to a communications satellite.

The scenario teaches: why password reuse is catastrophic in high-consequence systems, how multi-factor authentication and hardware security keys close the credential stuffing vector, the principle of least privilege applied to satellite command access, and how command authentication codes provide a second layer of protection even after a user account is compromised.

---

### 10 — Insider Threat

Category: Insider. Severity: Critical. Difficulty: 5 of 5. Estimated duration: 22 minutes. Affected systems: All Systems.

A satellite systems engineer with administrator-level access to command systems has been planning to leave the organization under hostile circumstances. Over a period of three weeks before their last day, they exfiltrate mission data to personal cloud storage, document internal network architecture, and plant logic bombs — code segments set to execute on a future date and corrupt the orbital maneuver scheduling database. Their activity is logged but no automated alert fires because the access patterns fall within the baseline established by their legitimate daily work.

The scenario teaches: behavioral analytics and user entity behavior analysis (UEBA), privileged access management and why administrator accounts should require additional verification for destructive actions, the separation of duties principle that prevents any single person from having both the knowledge and the access to cause catastrophic damage, and how insider threat programs balance security against the surveillance concerns of a healthy workplace.

---

## Educational Framework

Every scenario is built around the DEFINE, EXPLAIN, APPLY, REINFORCE model.

**DEFINE** happens at the scenario selection screen. The scenario card gives a one-line description and the full educational sidebar is available before the simulation begins.

**EXPLAIN** happens during the first stage. The educational sidebar opens automatically with a plain-English explanation of the attack: what it is, how it works technically without requiring prior knowledge, and what made it possible.

**APPLY** happens throughout the simulation. Every decision in the decision panel requires the analyst to use what they just read. Wrong decisions are not penalized without explanation — the consequence text explains exactly why the wrong choice made things worse and what the correct choice would have accomplished.

**REINFORCE** happens at the outcome screen and in the full incident report. The Lessons Learned section does not restate information from earlier stages. It adds the synthesis: given everything that happened, what are the three most important things an organization should have in place to prevent or contain this class of attack?

### Key Terminology System

Each scenario's `educational.keyTerms` object maps technical terms to plain-English definitions. When those terms appear in the narrative text or educational sidebar, they are rendered as underlined spans with a tooltip that shows the definition on hover. Analysts build vocabulary contextually rather than from a glossary page they may never visit.

Example terms across scenarios:

| Term | Definition |
|---|---|
| Spoofing | Transmitting counterfeit signals designed to impersonate a legitimate source |
| Jamming | Overpowering a receiver with noise, making it unable to decode the target signal |
| OSNMA | Open Service Navigation Message Authentication — Galileo's broadcast authentication standard |
| CME | Coronal Mass Ejection — a large expulsion of plasma and magnetic field from the Sun's corona |
| NMA | Navigation Message Authentication — a mechanism for signing GPS signal content |
| PAM | Privileged Access Management — tools and policies governing administrator-level account use |
| UEBA | User and Entity Behavior Analytics — statistical anomaly detection on user activity logs |
| Logic Bomb | Malicious code that executes when a specific condition or date is reached |
| TDRS | Tracking and Data Relay Satellite — a satellite that relays communications between low-orbit assets and ground stations |
| Reproducible Build | A build process that produces byte-identical output from identical source, enabling third-party verification |

---

## Implementation Milestones

### Milestone 1 — Design System and AppShell

The visual foundation. Every subsequent milestone depends on this being correct and complete before work begins on features.

Files to produce:
- `tailwind.config.ts` with all custom color tokens, font families, animation keyframes, and extended screen sizes
- `src/index.css` with Tailwind directives, CSS custom properties for all design tokens, and global resets
- `src/lib/cn.ts` — the `clsx` + `tailwind-merge` utility used everywhere
- `src/components/ui/HUDPanel.tsx`
- `src/components/ui/DiagonalSlash.tsx`
- `src/components/ui/GlowBadge.tsx`
- `src/components/ui/DataStream.tsx`
- `src/components/ui/Scanline.tsx`
- `src/components/layout/AppShell.tsx`
- `src/components/layout/Sidebar.tsx`
- `src/components/layout/TopBar.tsx`
- `src/components/layout/PageTransition.tsx`

Definition of done: AppShell renders with Sidebar and TopBar. HUDPanel and DiagonalSlash can be demoed in isolation in a test route. All color tokens are correctly applied. No pixel is hardcoded outside the token system.

---

### Milestone 2 — Boot Sequence and Routing

First impression and navigation architecture.

Files to produce:
- `src/router/AppRouter.tsx` with all seven routes defined
- `src/features/boot/BootPage.tsx` with GSAP typewriter sequence and CRT overlay
- Route scaffolding for all feature pages (empty components)

Definition of done: Application opens to the boot sequence, completes with DiagonalSlash wipe, and lands on an empty Dashboard shell. All routes navigate without console errors. Back/forward browser navigation works correctly.

---

### Milestone 3 — Dashboard Shell

The operational home base, without the 3D globe.

Files to produce:
- `src/features/dashboard/DashboardPage.tsx`
- `src/features/dashboard/components/MetricCard.tsx`
- `src/features/dashboard/components/AlertFeed.tsx`
- `src/features/dashboard/components/ThreatRadar.tsx`
- `src/features/dashboard/components/SystemHealthBar.tsx`
- `src/features/dashboard/components/MissionTimeline.tsx`
- `src/store/useAlertStore.ts`
- Alert generation in `src/hooks/useAlerts.ts`

Definition of done: Dashboard renders all panels. Metric cards count up on mount. Alert feed receives and displays simulated alerts on a random timer. Radar renders with its sweep arm and animates continuously.

---

### Milestone 4 — 3D Globe

The cinematic orbital visualization.

Files to produce:
- `src/features/globe/GlobeScene.tsx`
- `src/features/globe/Earth.tsx`
- `src/features/globe/Atmosphere.tsx`
- `src/features/globe/SatelliteSwarm.tsx`
- `src/features/globe/GroundStations.tsx`
- `src/features/globe/SignalPaths.tsx`
- `src/features/globe/CameraController.tsx`
- `src/features/globe/GlobePage.tsx`
- `src/features/globe/SatelliteHUD.tsx`
- `src/components/three/StarField.tsx`
- `src/components/three/GlowMaterial.tsx`
- `src/lib/orbitMath.ts`

Definition of done: Full globe renders at above 60 frames per second on a mid-range laptop. Satellites orbit with mathematically correct paths. Camera lerps smoothly to a selected satellite. Atmosphere glow is visible at the limb. The `OrbitalMinimap` is embedded in the dashboard.

---

### Milestone 5 — Simulation Engine

The pure-TypeScript brain of the application.

Files to produce:
- `src/engine/types.ts`
- `src/engine/SimulationEngine.ts`
- `src/engine/scoreEngine.ts`
- `src/engine/scenarios/index.ts`
- All ten scenario files with complete data: all stages, decisions, educational content, globe config, and timeline events
- `src/store/useSimStore.ts`
- `src/hooks/useSimulation.ts`

Definition of done: All ten scenarios instantiate without errors. Engine advances through stages, records decisions, and computes accurate scores. The Vitest suite covers: decision recording, score clamping at 0 and 100, grade boundary conditions, stage advance to null on completion, and `serialize()` output structure.

---

### Milestone 6 — Scenario Select

The threat library browser.

Files to produce:
- `src/features/scenarios/ScenarioSelectPage.tsx`
- `src/features/scenarios/components/ScenarioCard.tsx`
- Category icon mapping
- Filter bar component

Definition of done: All ten scenario cards render with correct data. Filter by severity and category works without page reload. Hover animations play correctly. Clicking triggers DiagonalSlash wipe and navigates to the runner.

---

### Milestone 7 — Scenario Runner

The core interactive simulation experience.

Files to produce:
- `src/features/scenarios/ScenarioRunnerPage.tsx`
- `src/features/scenarios/components/StageProgress.tsx`
- `src/features/scenarios/components/DecisionPanel.tsx`
- `src/features/scenarios/components/EducationalSidebar.tsx`
- `src/features/scenarios/components/AttackTimeline.tsx`
- `src/features/scenarios/components/NarrativeBox.tsx`
- `src/features/scenarios/components/OutcomeScreen.tsx`
- `src/features/globe/AttackOverlay.tsx`
- `src/hooks/useCountdown.ts`

Definition of done: A full end-to-end run of all ten scenarios completes without errors. Decisions are recorded, scores update, the globe reflects the attack state, and the outcome screen appears at completion with an accurate score.

---

### Milestone 8 — Reports

Mission debrief and history.

Files to produce:
- `src/features/reports/ReportsPage.tsx`
- `src/features/reports/components/IncidentReport.tsx`
- `src/features/reports/components/ScoreBreakdown.tsx`
- Zustand `persist` middleware added to `useSimStore`

Definition of done: Completed runs persist across page refreshes. Each report expands to show the decision review. Score breakdown is accurate and matches the final score from the outcome screen. Grade thresholds are correctly applied.

---

### Milestone 9 — Globe Full View and Polish Pass

Standalone globe view plus all remaining micro-animations and visual detail.

Tasks:
- Complete the `/globe` standalone route with satellite inspection
- Add all hover micro-interactions on every card and button
- Add the `Scanline` CRT overlay to the boot sequence and radar
- Add the `ProgressArc` animation to the outcome screen
- Complete all page mount stagger sequences
- Add optional UI audio: alert sound, stage advance sound, decision feedback sound (all off by default, togglable in a settings panel accessible from the TopBar)

Definition of done: Every screen renders at its intended level of polish. No animation is left as a placeholder. The globe standalone view supports satellite selection with the HUD panel.

---

### Milestone 10 — Production Polish and Deployment

Portfolio-ready quality.

Tasks:
- Full responsive audit across 1280px, 1440px, and 1920px viewports
- Keyboard navigation audit: all interactive elements reachable via Tab, all actions triggerable via Enter or Space
- ARIA labels on all non-text interactive elements
- Focus indicator visible and styled to the design system (teal outline, not default browser blue)
- Error boundary around the R3F canvas with a fallback message for WebGL-unsupported browsers
- Skeleton loading states for the initial dashboard render
- 404 page in the mission control visual language
- Lighthouse audit targeting 90+ performance, 90+ accessibility
- Production build verification: zero console errors, zero TypeScript errors
- Vercel or Netlify deployment configuration
- Final README review

Definition of done: Production build deploys successfully. Lighthouse scores meet targets. The application works correctly in Chrome, Firefox, and Safari.

---

## Getting Started

### Prerequisites

Node.js version 20 or higher is required. The application uses native ES modules throughout and depends on Vite 5, which requires a Node.js version that supports top-level `await`. A modern browser with WebGL2 support is required for the 3D globe — Chrome 120 or higher, Firefox 121 or higher, or Safari 17 or higher.

### Installation

```bash
# Clone the repository
git clone https://github.com/seventyoseven/orbital-shield.git
cd orbital-shield

# Install dependencies
npm install

# Start the development server
npm run dev
```

The application will be available at `http://localhost:5173`.

### First Run

On first load you will see the boot sequence, which runs for approximately 3.5 seconds. Press any key or click anywhere to skip it. You will land on the Operations Dashboard.

No account, login, or configuration is required. All data is local. The application generates simulated alerts automatically and the globe starts rotating immediately.

To run your first simulation: navigate to Scenarios in the left sidebar, select any card, read the scenario overview in the educational sidebar, and click Launch Simulation. Make decisions at each stage using the decision panel. Review your outcome and score when the final stage completes.

---

## Environment Variables

Orbital Shield has no required environment variables. The entire application runs locally with no external API dependencies.

The following optional variables are available for development:

```env
# .env.local

# Enable debug overlays including orbital path wireframes,
# FPS counter, and Zustand state inspector
VITE_DEBUG_MODE=false

# Skip the boot sequence for faster iteration during development
VITE_SKIP_BOOT=false

# Seed for random alert generation.
# Default is a random seed per session.
# Set a fixed value for reproducible alert sequences during testing.
VITE_ALERT_SEED=12345
```

---

## Scripts Reference

```bash
# Development
npm run dev           # Start Vite dev server with hot module replacement
npm run dev:debug     # Start with VITE_DEBUG_MODE=true

# Build and preview
npm run build         # TypeScript compilation check followed by Vite production build
npm run preview       # Serve the production build locally for verification

# Testing
npm run test          # Run Vitest in watch mode
npm run test:run      # Run all tests once for CI environments
npm run test:ui       # Open the Vitest browser-based test UI

# Code quality
npm run lint          # Run ESLint across all source files
npm run lint:fix      # Run ESLint with automatic fix where possible
npm run format        # Run Prettier across all source files
npm run typecheck     # Run tsc --noEmit to check types without emitting output

# Combined checks
npm run check         # Runs typecheck, lint, and test:run in sequence
                      # Use before committing to verify the full suite passes
```

---

## Contributing

This is a personal portfolio project but pull requests for bug fixes, scenario additions, or improvements to educational content are welcome.

```bash
# Fork the repository and clone your fork
git clone https://github.com/YOUR_USERNAME/orbital-shield.git

# Create a feature branch with a descriptive name
git checkout -b feature/scenario-laser-dazzle

# Make your changes, then run the full check suite before committing
npm run check

# Commit using conventional commit format
git commit -m "feat(scenarios): add directed energy laser dazzle scenario"

# Push and open a pull request against main
git push origin feature/scenario-laser-dazzle
```

### Adding a New Scenario

1. Create `src/engine/scenarios/yourScenarioName.ts`
2. Implement the full `Scenario` interface from `src/engine/types.ts` — all fields are required; there are no optional shortcuts
3. Write all five stages with at least two decisions each, one of which must be `isOptimal: true`
4. Populate the full `educational` object including `keyTerms` and at least three `defenseStrategies`
5. Define a `globeConfig` specifying which satellites and ground stations the attack targets and what `attackType` visualization to use
6. Register the scenario in `src/engine/scenarios/index.ts`
7. Write at least five Vitest unit tests covering: decision recording, score impact, stage advancement, and `serialize()` output

### Code Standards

All new code must pass the full `npm run check` suite. TypeScript strict mode is enabled — no `any` types, no non-null assertions without a comment explaining why they are safe. Component props are always typed with an explicit interface. Zustand actions are never `async` — all async operations belong in hooks, not stores.

---

## Acknowledgements

**NASA Visible Earth** — Earth texture maps used in the 3D globe are from the NASA Visible Earth catalog and are in the public domain.

**Three.js and the React Three Fiber community** — The R3F ecosystem, `@react-three/drei` helpers, and the collective shader examples from the Three.js community made the 3D visualization system possible without starting from scratch.

**Atlus and Persona 5** — The interface philosophy of Persona 5 was the aesthetic direction for this project. No assets, fonts, sounds, or artwork from the game are used. The debt is one of design thinking only.

**CISA** — The Space Systems Critical Infrastructure Security and Resilience guidance documents informed the educational content across multiple scenarios.

**ESA, NASA, and SpaceX** — Public documentation on satellite operations, ground segment architecture, and space cybersecurity informed the scenario design throughout.

---

*Built by Genesis — github.com/seventyoseven — handle: Mystic707*

```
[ ALL SYSTEMS NOMINAL ] // ORBITAL SHIELD v2.1.0 // READY
```
