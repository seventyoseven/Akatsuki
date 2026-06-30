<div align="center">
```
 ██████╗ ██████╗ ██████╗ ██╗████████╗ █████╗ ██╗         
██╔═══██╗██╔══██╗██╔══██╗██║╚══██╔══╝██╔══██╗██║         
██║   ██║██████╔╝██████╔╝██║   ██║   ███████║██║         
██║   ██║██╔══██╗██╔══██╗██║   ██║   ██╔══██║██║         
╚██████╔╝██║  ██║██████╔╝██║   ██║   ██║  ██║███████╗    
 ╚═════╝ ╚═╝  ╚═╝╚═════╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝╚══════╝   
                                                           
███████╗██╗  ██╗██╗███████╗██╗     ██████╗               
██╔════╝██║  ██║██║██╔════╝██║     ██╔══██╗              
███████╗███████║██║█████╗  ██║     ██║  ██║              
╚════██║██╔══██║██║██╔══╝  ██║     ██║  ██║              
███████║██║  ██║██║███████╗███████╗██████╔╝              
╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═════╝               
```
 
**An Educational Space Cybersecurity Attack Simulator**
 
*Mission Control Interface for the Next Generation of Space Security Analysts*
 
---
 
![Version](https://img.shields.io/badge/version-2.1.0-FF2D55?style=for-the-badge)
![Status](https://img.shields.io/badge/status-in_development-00F5D4?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-FFB800?style=for-the-badge)
![React](https://img.shields.io/badge/React-18.x-61DAFB?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript)
![Three.js](https://img.shields.io/badge/Three.js-r158-white?style=for-the-badge&logo=threedotjs)
 
</div>
---
 
> **⚠️ EDUCATIONAL USE ONLY**  
> Orbital Shield is a **purely educational, locally-simulated** cybersecurity training platform. It performs **no real attacks**, makes **no real network calls**, and has **zero interaction** with actual satellites, infrastructure, radio frequencies, or external systems. All scenarios, data, satellites, and events are fictional and designed exclusively for learning purposes.
 
---
 
## Table of Contents
 
1. [Project Overview](#-project-overview)
2. [Live Demo](#-live-demo)
3. [Design Philosophy](#-design-philosophy)
4. [Tech Stack](#-tech-stack)
5. [Application Architecture](#-application-architecture)
6. [Folder Structure](#-folder-structure)
7. [Pages & Screens](#-pages--screens)
8. [Component Library](#-component-library)
9. [3D Visualization System](#-3d-visualization-system)
10. [Simulation Engine](#-simulation-engine)
11. [State Management](#-state-management)
12. [Animation System](#-animation-system)
13. [Simulation Scenarios](#-simulation-scenarios)
14. [Educational Framework](#-educational-framework)
15. [Implementation Milestones](#-implementation-milestones)
16. [Getting Started](#-getting-started)
17. [Environment Variables](#-environment-variables)
18. [Scripts Reference](#-scripts-reference)
19. [Contributing](#-contributing)
20. [Acknowledgements](#-acknowledgements)
---
 
## 🛰 Project Overview
 
**Orbital Shield** is a portfolio-grade, interactive web application that puts you in the role of a **Space Security Operations Center (SOC) analyst**. You monitor a fictional satellite network in real time, respond to escalating cybersecurity incidents, and learn the defensive strategies that real space agencies and satellite operators use to protect critical infrastructure.
 
The application simulates **10 distinct attack scenarios** — from GPS spoofing and ransomware infections to insider threats and solar flare interference — each broken into investigation stages where your decisions determine the outcome. A fully animated 3D Earth displays live orbital paths, ground stations, and attack visualizations, all rendered in-browser with no server required.
 
### Why Space Cybersecurity?
 
Space infrastructure — GPS, weather satellites, communications networks, scientific platforms — underpins almost every sector of modern civilization. Disrupting a single satellite constellation can cripple navigation for millions of devices, blind weather forecasting systems, or sever critical military communications. As the number of commercial and government satellites grows into the tens of thousands, so does the attack surface. Orbital Shield exists to make these risks **tangible, visual, and learnable** without any real-world risk.
 
### Who Is This For?
 
- Cybersecurity students and CTF competitors building their portfolio
- Security professionals exploring space/OT security domains  
- Educators delivering engaging, visual threat modeling content
- Recruiters and interviewers assessing a candidate's systems thinking
- Anyone curious about how modern space infrastructure is defended
---
 
## 🌐 Live Demo
 
> **Coming soon** — deployment to Vercel/Netlify pending M10 polish milestone.
 
To run locally: see [Getting Started](#-getting-started).
 
---
 
## 🎨 Design Philosophy
 
Orbital Shield's visual identity is an original creation heavily **inspired by the interface philosophy of Persona 5** — not copied from it. No assets, fonts, or artwork from the game are used. What we borrow is the *energy*: bold diagonal geometry, high-contrast color blocking, cinematic transitions, and a UI that feels like it's always a fraction of a second away from something dramatic happening.
 
### Design Language
 
| Element | Decision | Rationale |
|---|---|---|
| **Base color** | `#0A0A0F` Void Black | Infinite depth — the void of space |
| **Primary accent** | `#FF2D55` Alert Red | Urgency, danger, P5 signature energy |
| **Secondary accent** | `#00F5D4` Cyber Teal | Technology, data, system readouts |
| **Warning** | `#FFB800` Amber | Mid-severity without full alarm |
| **Surface** | `#1A1A2E` Deep Navy | Depth without flatness |
| **Text** | `#F5F5F5` Ghost White | Contrast without harshness |
| **Display font** | Bebas Neue | Cinematic, condensed, unforgettable |
| **Body font** | Inter | Precision utility reading |
| **Mono font** | JetBrains Mono | Telemetry, code, log data |
 
### Signature Element: The Diagonal Slash Wipe
 
Every major state transition — route changes, scenario launches, threat escalations, mission completions — triggers a full-screen **diagonal wipe** composed of three stacked panels sweeping left-to-right at `skewX(-12deg)`. Colors are `#FF2D55`, `rgba(255,45,85,0.6)`, and `rgba(0,245,212,0.3)` staggered by 80ms. This is implemented entirely in Framer Motion and is the most recognizable motion signature in the application.
 
### HUD Aesthetic Principles
 
- All panels use **glassmorphism**: `rgba(26,26,46,0.8)` background + `backdrop-blur-md`
- Borders glow with color matched to severity level (teal = normal, amber = warning, red = critical)
- Critical panels **pulse** their border glow on a 2s sine wave
- Typography hierarchy: Bebas Neue for labels, Inter for values, JetBrains Mono for live data
- CRT scanline overlay on the boot screen and radar components adds tactile analog texture
- No drop shadows — only glows. The light source is always the data itself.
---
 
## 🧰 Tech Stack
 
| Layer | Technology | Purpose |
|---|---|---|
| **Framework** | React 18 + TypeScript 5 | Component architecture + type safety |
| **Build Tool** | Vite 5 | Near-instant HMR, optimized production build |
| **Styling** | TailwindCSS v3 | Utility-first; custom tokens defined in `tailwind.config.ts` |
| **Animation** | Framer Motion 11 | Page transitions, layout animations, gesture interactions |
| **Animation** | GSAP 3 | Boot sequence, number count-ups, complex timelines |
| **3D** | React Three Fiber + Three.js r158 | Earth globe, satellite orbits, signal paths |
| **3D Helpers** | @react-three/drei | OrbitControls, Stars, useTexture, Instances |
| **Charts** | Recharts | Dashboard metric charts, timeline visualization |
| **Icons** | Lucide React | Consistent, clean SVG icon set |
| **Routing** | React Router v6 | Client-side routing with loader patterns |
| **State** | Zustand | Lightweight, zero-boilerplate global state |
| **Linting** | ESLint + Prettier | Code consistency |
| **Testing** | Vitest + Testing Library | Unit tests for simulation engine logic |
 
### Dependency Tree (Key Packages)
 
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
    "eslint": "^9.0.0",
    "prettier": "^3.3.0"
  }
}
```
 
---
 
## 🏗 Application Architecture
 
Orbital Shield follows a **feature-based architecture** where each major feature owns its pages, components, and local state. Shared primitives live in `src/components/`. The simulation engine is a pure TypeScript module completely decoupled from React, making it independently testable.
 
```
┌─────────────────────────────────────────────────────────┐
│                    REACT ROUTER v6                       │
│         /boot → /dashboard → /scenarios → /globe        │
└──────────────────────┬──────────────────────────────────┘
                       │
          ┌────────────▼────────────┐
          │       APP SHELL         │
          │  (Sidebar + TopBar)     │
          └────────────┬────────────┘
                       │
        ┌──────────────┼──────────────┐
        │              │              │
   ┌────▼────┐   ┌─────▼─────┐  ┌───▼────┐
   │DASHBOARD│   │ SCENARIOS │  │ GLOBE  │
   │ Feature │   │  Feature  │  │Feature │
   └────┬────┘   └─────┬─────┘  └───┬────┘
        │              │             │
        └──────────────▼─────────────┘
                       │
          ┌────────────▼────────────┐
          │    SHARED COMPONENTS    │
          │  HUDPanel, DiagonalSlash│
          │  AlertBanner, Scanline  │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │      ZUSTAND STORES     │
          │  SimStore | AlertStore  │
          │  UIStore               │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │    SIMULATION ENGINE    │
          │  (Pure TypeScript)      │
          │  SimulationEngine.ts    │
          │  scenarios/*.ts         │
          │  scoreEngine.ts         │
          └─────────────────────────┘
```
 
### Data Flow
 
```
User Action
    │
    ▼
React Component
    │ dispatches action
    ▼
Zustand Store (useSimStore)
    │ calls
    ▼
SimulationEngine (pure logic)
    │ returns
    ▼
New State Object
    │ triggers re-render
    ▼
React Components + R3F Scene
    │ reads from store
    ▼
Visual Update (Framer Motion / Three.js)
```
 
All simulation logic is **synchronous and deterministic** unless the scenario uses seeded random generation. There is no async I/O except texture loading for the Earth mesh.
 
---
 
## 📁 Folder Structure
 
```
orbital-shield/
│
├── public/
│   └── assets/
│       ├── textures/
│       │   ├── earth_daymap.jpg        # 8K Earth surface texture
│       │   ├── earth_nightmap.jpg      # City lights texture
│       │   ├── earth_clouds.jpg        # Cloud layer
│       │   ├── earth_specular.jpg      # Ocean specularity map
│       │   └── starfield.jpg           # Milky Way background
│       └── sounds/                     # Optional UI audio (muted by default)
│           ├── alert.mp3
│           ├── stage_advance.mp3
│           └── boot_sequence.mp3
│
├── src/
│   │
│   ├── main.tsx                        # Vite entry point
│   ├── App.tsx                         # Root component, provider tree
│   ├── index.css                       # Tailwind directives + global CSS vars
│   │
│   ├── router/
│   │   └── AppRouter.tsx               # All route definitions
│   │
│   ├── store/                          # Zustand global state slices
│   │   ├── useSimStore.ts              # Active simulation state
│   │   ├── useAlertStore.ts            # Alert feed state
│   │   └── useUIStore.ts               # UI state (panels, modals, focus)
│   │
│   ├── engine/                         # Pure TypeScript simulation engine
│   │   ├── SimulationEngine.ts         # Core engine class
│   │   ├── scoreEngine.ts              # Scoring and grading logic
│   │   ├── types.ts                    # All engine TypeScript interfaces
│   │   └── scenarios/
│   │       ├── index.ts                # Scenario registry
│   │       ├── gpsSpoofing.ts
│   │       ├── satelliteJamming.ts
│   │       ├── groundMalware.ts
│   │       ├── ransomware.ts
│   │       ├── solarFlare.ts
│   │       ├── commBlackout.ts
│   │       ├── supplyChain.ts
│   │       ├── telemetryTamper.ts
│   │       ├── authFailure.ts
│   │       └── insiderThreat.ts
│   │
│   ├── hooks/                          # Custom React hooks
│   │   ├── useSimulation.ts            # Simulation lifecycle management
│   │   ├── useOrbit.ts                 # Satellite orbit math hook
│   │   ├── useAlerts.ts                # Alert generation and polling
│   │   ├── useCountdown.ts             # Stage timer hook
│   │   └── useGSAP.ts                  # GSAP animation ref hook
│   │
│   ├── features/
│   │   │
│   │   ├── boot/
│   │   │   └── BootPage.tsx            # CRT boot sequence
│   │   │
│   │   ├── dashboard/
│   │   │   ├── DashboardPage.tsx       # Main dashboard layout
│   │   │   └── components/
│   │   │       ├── ThreatRadar.tsx     # SVG animated radar
│   │   │       ├── SatelliteGrid.tsx   # Satellite health grid
│   │   │       ├── AlertFeed.tsx       # Live alert list
│   │   │       ├── MissionTimeline.tsx # Recharts timeline
│   │   │       ├── SystemHealthBar.tsx # Subsystem health bars
│   │   │       ├── MetricCard.tsx      # KPI stat card
│   │   │       └── OrbitalMinimap.tsx  # Compact R3F globe
│   │   │
│   │   ├── globe/
│   │   │   ├── GlobePage.tsx           # Full-viewport globe route
│   │   │   ├── GlobeScene.tsx          # R3F Canvas wrapper
│   │   │   ├── Earth.tsx               # Earth mesh with textures
│   │   │   ├── Atmosphere.tsx          # Glow atmosphere shader
│   │   │   ├── SatelliteSwarm.tsx      # Instanced satellite meshes
│   │   │   ├── GroundStations.tsx      # Ground station markers
│   │   │   ├── SignalPaths.tsx         # Animated signal lines
│   │   │   ├── AttackOverlay.tsx       # Red pulse on attack
│   │   │   ├── SatelliteHUD.tsx        # Click-to-inspect HUD
│   │   │   └── CameraController.tsx    # Smooth OrbitControls wrapper
│   │   │
│   │   ├── scenarios/
│   │   │   ├── ScenarioSelectPage.tsx  # Scenario browser
│   │   │   ├── ScenarioRunnerPage.tsx  # Active simulation
│   │   │   └── components/
│   │   │       ├── ScenarioCard.tsx    # Selection card
│   │   │       ├── StageProgress.tsx   # Stage timeline bar
│   │   │       ├── DecisionPanel.tsx   # Response choices
│   │   │       ├── EducationalSidebar.tsx  # Teaching content
│   │   │       ├── AttackTimeline.tsx  # Event log
│   │   │       ├── NarrativeBox.tsx    # Incident story text
│   │   │       └── OutcomeScreen.tsx   # End-of-scenario results
│   │   │
│   │   └── reports/
│   │       ├── ReportsPage.tsx         # Completed runs history
│   │       └── components/
│   │           ├── IncidentReport.tsx  # Detailed report view
│   │           └── ScoreBreakdown.tsx  # Decision analysis
│   │
│   ├── components/
│   │   ├── ui/                         # Design system primitives
│   │   │   ├── HUDPanel.tsx
│   │   │   ├── DiagonalSlash.tsx
│   │   │   ├── GlowBadge.tsx
│   │   │   ├── AlertBanner.tsx
│   │   │   ├── RadarRing.tsx
│   │   │   ├── DataStream.tsx
│   │   │   ├── Scanline.tsx
│   │   │   ├── ProgressArc.tsx
│   │   │   └── TypewriterText.tsx
│   │   │
│   │   ├── layout/
│   │   │   ├── AppShell.tsx
│   │   │   ├── Sidebar.tsx
│   │   │   ├── TopBar.tsx
│   │   │   └── PageTransition.tsx
│   │   │
│   │   └── three/
│   │       ├── StarField.tsx
│   │       └── GlowMaterial.tsx
│   │
│   ├── lib/
│   │   ├── orbitMath.ts                # Kepler orbital mechanics
│   │   ├── colorUtils.ts               # Severity → color mapping
│   │   ├── formatters.ts               # Time, score, telemetry formatters
│   │   └── cn.ts                       # clsx + tailwind-merge utility
│   │
│   └── types/
│       ├── simulation.ts               # Simulation domain types
│       ├── satellite.ts                # Satellite + orbit types
│       └── alert.ts                    # Alert system types
│
├── tests/
│   ├── engine/
│   │   ├── SimulationEngine.test.ts
│   │   └── scoreEngine.test.ts
│   └── hooks/
│       └── useSimulation.test.ts
│
├── tailwind.config.ts
├── vite.config.ts
├── tsconfig.json
├── tsconfig.app.json
├── eslint.config.js
├── .prettierrc
└── README.md
```
 
---
 
## 📺 Pages & Screens
 
### Page 1 — Boot Sequence (`/`)
 
The first thing the user ever sees. Sets the entire tone.
 
**Visual:** Full black screen. A green monospace cursor blinks once, then begins typing system initialization lines:
 
```
ORBITAL SHIELD v2.1.0
[INITIALIZING CORE SYSTEMS]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[OK]  SATELLITE NETWORK ................. ONLINE
[OK]  THREAT DETECTION ENGINE ........... ARMED
[OK]  GROUND STATION UPLINK ............. ACTIVE
[OK]  ENCRYPTION LAYER .................. ENABLED
[OK]  ORBITAL TRACKING .................. LOCKED
[WARN] ANOMALOUS SIGNAL DETECTED ON BAND 3.7 GHz
[OK]  MISSION CONTROL INTERFACE ......... READY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PRESS ANY KEY TO ACCESS OPERATIONS CENTER
```
 
Lines type in using GSAP staggered `to()` animations at 18ms per character. CRT scanline overlay flickers over the text. After the final line, a `DiagonalSlash` wipe sweeps across and the user lands on the Dashboard. Duration ~3.5s. Spacebar or click skips.
 
---
 
### Page 2 — Operations Dashboard (`/dashboard`)
 
The mission control home base. Always visible when not in a scenario.
 
**Layout (12-column grid):**
 
```
┌─────────────────────────────────────────────────────────────────┐
│ ORBITAL SHIELD // OPERATIONS CENTER            [CLOCK] [STATUS] │
├───────────────────────────┬──────────────┬───────────────────────┤
│                           │              │                       │
│   3D GLOBE (GlobeScene)   │  ALERT FEED  │    THREAT RADAR       │
│      6 columns            │  3 columns   │    3 columns          │
│                           │              │   (SVG animated)      │
│                           │              │                       │
├─────────────┬─────────────┴──────┬───────┴───────────────────────┤
│             │                    │                               │
│  SATELLITE  │   SYSTEM HEALTH    │     MISSION TIMELINE          │
│  GRID       │   BARS             │     (Recharts area chart)     │
│  4 cols     │   4 cols           │     4 cols                    │
│             │                    │                               │
└─────────────┴────────────────────┴───────────────────────────────┘
```
 
**Metric Cards Row** (above the grid, full width):
- Total Active Satellites: `47`
- Active Threats: `3`
- System Health: `94.2%`
- Signal Integrity: `98.7%`
- Ground Stations Online: `12/14`
All metric values are live-simulated and count up on mount using GSAP. They fluctuate ±2% every 5 seconds using seeded random values to feel alive without being distracting.
 
**Globe (OrbitalMinimap):** A compact R3F canvas (`height: 320px`) showing Earth with orbiting satellites. Rotating slowly at 0.0005 rad/frame. Clicking opens the full `/globe` route.
 
**Alert Feed:** Right panel. Each alert slides in from the right with a spring animation. Color-coded left border: red=critical, amber=warning, teal=info. Clicking an alert that's tied to a scenario navigates there directly.
 
**Threat Radar:** Bottom-right. SVG radar with four concentric rings and a rotating sweep arm. Threat blips appear at polar coordinates and pulse with ring ripples. No real data — positions are derived from scenario metadata.
 
---
 
### Page 3 — Scenario Select (`/scenarios`)
 
The threat library. Where analysts choose what to train against.
 
**Layout:** Staggered masonry-ish card grid. Cards stagger in from bottom on mount with 50ms delay between each.
 
Each **ScenarioCard** contains:
- Top: Threat category icon (Lucide) in a colored circle
- Diagonal clip on bottom-right corner (CSS `clip-path`)
- Scenario name in Bebas Neue, large
- One-line description
- Severity badge: `CRITICAL` / `HIGH` / `MEDIUM`
- Difficulty stars (1–5)
- Estimated duration: `~12 min`
- Systems affected tags: e.g., `GPS`, `COMMS`, `TELEMETRY`
Hovering a card: background shimmer sweeps left-to-right (Framer Motion `backgroundPositionX` animation), card lifts 4px with drop shadow.
 
Clicking a card: triggers the `DiagonalSlash` wipe, then navigates to `/scenarios/:id`.
 
A filter bar at the top allows filtering by: **All | Critical | High | Medium | By Category**.
 
---
 
### Page 4 — Scenario Runner (`/scenarios/:id`)
 
The core experience. Occupies the full screen while a scenario is active.
 
**Layout:**
 
```
┌───────────────────────────────────────────────────────────────┐
│  [STAGE PROGRESS BAR]  Detection > Investigation > ...  [04:32]│
├────────────────────────────────────┬──────────────────────────┤
│                                    │                          │
│   NARRATIVE BOX                    │  EDUCATIONAL SIDEBAR     │
│   (what's happening right now)     │  (collapsible, ~320px)   │
│                                    │                          │
├────────────────────────────────────│  "What Is GPS Spoofing?" │
│                                    │  ─────────────────────── │
│   DECISION PANEL                   │  Definition              │
│   (2–4 choice cards)               │  Real-world examples     │
│                                    │  Defense strategies      │
│                                    │  Key terminology         │
├────────────────────────────────────┴──────────────────────────┤
│  ATTACK TIMELINE (scrolling event log, bottom)                │
└───────────────────────────────────────────────────────────────┘
```
 
**Stage Progress Bar:** Five chips labeled `Detection`, `Investigation`, `Containment`, `Recovery`, `Lessons Learned`. Current stage is enlarged and accent-colored. Completed stages show a checkmark. A timer counts down in the top-right corner.
 
**Narrative Box:** Incident story text in Inter. Updates per stage. New text fades in and the old text slides up and away.
 
**Decision Panel:** 2–4 large clickable cards. Each shows:
- An action statement (bold, large)
- A consequence preview revealed on hover (italics, dimmed)
After selection: correct answer glows `#00F5D4` with a checkmark animation. Wrong answers glow `#FF2D55` with a shake animation. Score updates in the top bar.
 
**Educational Sidebar:** A panel that auto-opens when a new stage begins. Contains rich explanations per stage of the scenario. Can be pinned open or collapsed.
 
**Attack Timeline:** A scrolling event log at the bottom showing timestamped events: `[T+00:02:34] Anomalous uplink signal detected on Ku-band transponder`. New events appear with a slide-up animation.
 
---
 
### Page 5 — Outcome Screen (overlaid on Scenario Runner)
 
Triggered when the final stage (`Lessons Learned`) completes. Takes over the full screen.
 
**Sequence:**
1. `DiagonalSlash` wipe
2. Screen reveals with mission report header
3. Score arc animates from 0 to final score
4. Grade letter (`S` / `A` / `B` / `C` / `F`) slams in with a scale + rotation spring
5. Performance summary appears below
6. Lessons Learned accordion expands automatically
7. Two CTAs: `VIEW FULL REPORT` | `RUN AGAIN`
**Grade Thresholds:**
- `S` — 90–100: Elite Analyst
- `A` — 75–89: Senior Analyst
- `B` — 60–74: Analyst
- `C` — 45–59: Trainee
- `F` — 0–44: Compromised
---
 
### Page 6 — Reports (`/reports`)
 
Post-mission debrief history.
 
**Layout:** Table of completed scenario runs with columns:
- Scenario name
- Date completed
- Final score
- Grade badge
- Duration
- `▶ VIEW REPORT` button
Clicking a row expands an `IncidentReport` panel below it (accordion style):
- Executive Summary
- Stage-by-stage decision review
- What the optimal choices were
- Key lessons
- Recommended reading (fictional references)
---
 
### Page 7 — Globe Full View (`/globe`)
 
Standalone cinematic experience. Full viewport, no sidebar.
 
A minimal HUD overlays in corners:
- Top-left: `ORBITAL SHIELD // GLOBAL NETWORK VIEW`
- Top-right: satellite count, active threats
- Bottom-left: selected satellite telemetry (when clicked)
- Bottom-right: camera controls hint
Users can click any satellite to inspect it. The camera smoothly lerps to focus on that satellite. The selected satellite's orbit path highlights in teal. A HUD card slides in from the left showing: Satellite ID, Orbital Altitude, Inclination, Signal Status, Last Contact, Health Status.
 
ESC or clicking empty space deselects and returns the camera to default orbit.
 
---
 
## 🧩 Component Library
 
### `HUDPanel`
 
The foundational panel component. Every information section in the app is a `HUDPanel`.
 
```typescript
interface HUDPanelProps {
  title: string;
  severity?: 'normal' | 'warning' | 'critical';
  className?: string;
  headerRight?: React.ReactNode;  // optional right-side header content
  noPadding?: boolean;
  children: React.ReactNode;
}
```
 
**Behavior:**
- Background: `rgba(26, 26, 46, 0.85)` + `backdrop-blur-md`
- Border: `1px solid` with color derived from severity:
  - `normal`: `rgba(0, 245, 212, 0.3)`
  - `warning`: `rgba(255, 184, 0, 0.5)` — pulses glow at 2s interval
  - `critical`: `rgba(255, 45, 85, 0.6)` — pulses glow at 1s interval
- Title bar: left-border accent `4px`, Bebas Neue, uppercase, 0.5rem letter-spacing
- Mounts with `opacity: 0 → 1` + `translateY(12px → 0)` Framer Motion animation
---
 
### `DiagonalSlash` (Signature Transition)
 
```typescript
interface DiagonalSlashProps {
  trigger: boolean;           // when true, plays enter animation
  onComplete?: () => void;    // called after exit animation ends
  colors?: [string, string, string]; // override the three panel colors
}
```
 
**Implementation:** Three absolutely-positioned `div`s, each `width: 120%`, `height: 100%`, `skewX(-12deg)`, staggered `left` offset. Framer Motion `scaleX: 0 → 1 → 0` on `transformOrigin: left`. Total duration: 600ms. Used as a higher-order wrapper around `<Outlet>` in the router.
 
---
 
### `ThreatRadar`
 
SVG-based animated radar ring component.
 
```typescript
interface ThreatRadarProps {
  threats: RadarThreat[];  // { angle: number; distance: number; severity: Severity }[]
  size?: number;           // SVG viewport size, default 200
}
```
 
**Implementation:**
- Four `<circle>` rings at 25%, 50%, 75%, 100% radius, stroke `rgba(0,245,212,0.15)`
- Cross-hair lines at 0°, 45°, 90°, 135°
- Sweep arm: `<line>` rotated via CSS `animation: spin 4s linear infinite`
- Sweep gradient: `conic-gradient` from transparent to `rgba(0,245,212,0.3)` (the "lit" arc behind the arm)
- Threat blips: `<circle r="4">` at polar coordinates, `fill` color-mapped to severity, animated `r` pulse rings
---
 
### `DataStream`
 
Ambient background component adding technical atmosphere.
 
```typescript
interface DataStreamProps {
  columns?: number;      // default 2
  speed?: 'slow' | 'normal' | 'fast';
  opacity?: number;      // 0–1, default 0.15
}
```
 
**Implementation:** Each column is a `<div>` with a long string of hex octets and binary sequences, animated with `animation: scrollData linear infinite` where `@keyframes scrollData { from { transform: translateY(0) } to { transform: translateY(-50%) } }`. Content is duplicated so the scroll loops seamlessly. Top and bottom fade via `mask-image: linear-gradient(transparent, black, transparent)`.
 
---
 
### `TypewriterText`
 
```typescript
interface TypewriterTextProps {
  text: string;
  speed?: number;        // ms per character, default 30
  startDelay?: number;   // ms before typing begins
  onComplete?: () => void;
  cursor?: boolean;      // show blinking cursor while typing
  className?: string;
}
```
 
Used in boot sequence, narrative boxes, and educational sidebar reveals. Uses `useEffect` with `setInterval` to append characters one by one to local state.
 
---
 
### `ProgressArc`
 
Circular SVG progress indicator used in OutcomeScreen.
 
```typescript
interface ProgressArcProps {
  value: number;      // 0–100
  size?: number;      // SVG size, default 160
  strokeWidth?: number;
  color?: string;
  label?: string;     // center label
  animate?: boolean;  // animate from 0 to value on mount
}
```
 
Uses `stroke-dasharray` and `stroke-dashoffset` with a Framer Motion `animate` prop for the fill animation.
 
---
 
### `StageProgress`
 
```typescript
interface StageProgressProps {
  stages: string[];        // stage names
  currentStage: number;    // 0-indexed
  completedStages: number[];
}
```
 
Renders a horizontal row of stage chips connected by animated fill lines. Current stage chip is `scale(1.1)` with accent glow. Completing a stage triggers a fill animation on the connecting line.
 
---
 
### `DecisionPanel`
 
```typescript
interface DecisionPanelProps {
  decisions: Decision[];
  onDecide: (id: string) => void;
  locked: boolean;        // true during transitions
  revealed: boolean;      // true after a choice is made (shows correct/wrong)
  selectedId?: string;
}
```
 
After `revealed = true`, all cards show their outcome state. Correct card: teal border + checkmark. Wrong cards: dim to 40% opacity. Selected wrong card: red border + X icon + shake animation.
 
---
 
### `SatelliteHUD`
 
```typescript
interface SatelliteHUDProps {
  satellite: Satellite | null;  // null = closed
  onClose: () => void;
}
```
 
Slides in from the left when a satellite is selected in the globe. Shows: ID, name, orbital altitude (km), inclination (°), RAAN (°), signal strength (%), health status, last contact timestamp. Closes on ESC or the X button.
 
---
 
## 🌍 3D Visualization System
 
### Architecture
 
The 3D system lives inside `features/globe/`. The `GlobeScene.tsx` component wraps a React Three Fiber `<Canvas>` with post-processing. All satellite positions are computed mathematically using Keplerian orbital elements — no external orbit data APIs, everything runs locally.
 
### Earth
 
```typescript
// Earth.tsx
// Mesh: SphereGeometry(6, 64, 64) — radius 6 units
// Material: MeshStandardMaterial with:
//   map: earth_daymap.jpg (8K)
//   emissiveMap: earth_nightmap.jpg (city lights, visible on dark side)
//   specularMap: earth_specular.jpg
// Cloud layer: separate SphereGeometry(6.05) with alphaMap
// Rotation: 0.0005 rad/frame on Y axis
```
 
### Atmosphere
 
A custom GLSL shader creates the blue atmospheric glow visible on the Earth's limb. The shader uses `dot(vNormal, normalize(cameraPosition))` to compute fresnel-style glow intensity, outputting `rgba(0.2, 0.5, 1.0, intensity)`.
 
### Satellite Swarm
 
```typescript
// SatelliteSwarm.tsx
// Uses Three.js InstancedMesh for performance (up to 50 instances)
// Each satellite has Keplerian elements: a, e, i, Ω, ω, M₀
// Per-frame: compute mean anomaly M = M₀ + n*t, solve Kepler's equation
//   for eccentric anomaly E, compute true anomaly ν, compute r, 
//   convert to ECI coordinates, then to Three.js world space
// Attack state: instance color → red (via instanceColor attribute)
// Recovery state: instance color → teal, emits a BillboardParticle burst
```
 
**Orbital Math (`lib/orbitMath.ts`):**
```typescript
// Solves Kepler's equation iteratively (Newton-Raphson, 10 iterations)
export function solveKeplerEquation(M: number, e: number): number { ... }
 
// Converts Keplerian elements to Cartesian ECI position
export function keplerToCartesian(elements: OrbitalElements, t: number): Vector3 { ... }
 
// Converts ECI to ECEF (accounting for Earth rotation)
export function eciToECEF(eci: Vector3, t: number): Vector3 { ... }
```
 
### Signal Paths
 
Animated lines connecting satellites to ground stations and to each other during communication events. Uses `THREE.CatmullRomCurve3` for smooth arc paths that follow the Earth's curvature. Animated via `dashOffset` uniform in a custom `LineMaterial`.
 
### Attack Overlay
 
When a scenario targets a satellite or region:
1. The targeted satellite's instance turns red
2. A `RippleRing` mesh animates outward from the satellite's position (ring geometry that scales up and fades out)
3. A red pulsing `PointLight` appears at the attack location
4. If it's a ground station attack, a `GroundStation` marker flashes red
---
 
## ⚙️ Simulation Engine
 
### Core Engine Class
 
```typescript
// engine/SimulationEngine.ts
 
export class SimulationEngine {
  private scenario: Scenario;
  private state: SimulationState;
  
  constructor(scenario: Scenario) {
    this.scenario = scenario;
    this.state = this.initializeState();
  }
  
  // Returns the current stage
  getCurrentStage(): Stage {
    return this.scenario.stages[this.state.currentStageIndex];
  }
  
  // Advance to next stage. Returns null if simulation complete.
  advanceStage(): Stage | null {
    if (this.state.currentStageIndex >= this.scenario.stages.length - 1) {
      this.state.completed = true;
      return null;
    }
    this.state.currentStageIndex++;
    return this.getCurrentStage();
  }
  
  // Record a decision and update score
  makeDecision(decisionId: string): DecisionResult {
    const stage = this.getCurrentStage();
    const decision = stage.decisions.find(d => d.id === decisionId);
    if (!decision) throw new Error(`Invalid decision: ${decisionId}`);
    
    this.state.score = Math.max(0, Math.min(100, 
      this.state.score + decision.scoreImpact
    ));
    
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
    };
  }
  
  // Compute final grade
  getGrade(): Grade {
    return scoreEngine.computeGrade(this.state.score, this.state.decisionLog);
  }
  
  // Serialize state for report storage
  serialize(): CompletedRun { ... }
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
  | 'physical'
  | 'supply-chain'
  | 'insider'
  | 'natural';
 
export interface Scenario {
  id: string;
  name: string;
  shortDescription: string;
  category: ThreatCategory;
  severity: Severity;
  difficulty: 1 | 2 | 3 | 4 | 5;
  estimatedDuration: number;          // minutes
  affectedSystems: SystemType[];
  stages: Stage[];
  educational: EducationalContent;
  globeConfig: GlobeScenarioConfig;   // what the 3D scene should show
}
 
export interface Stage {
  id: string;
  name: string;
  duration: number;                   // seconds for countdown
  narrative: string;                  // incident story text
  events: TimelineEvent[];            // attack timeline log entries
  decisions: Decision[];
  educationalNote: string;            // sidebar content for this stage
  globeState: GlobeStageState;        // which satellites/stations to highlight
}
 
export interface Decision {
  id: string;
  text: string;                       // action label
  hint: string;                       // revealed on hover
  consequence: string;                // shown after selection
  isOptimal: boolean;
  scoreImpact: number;                // -20 to +15
}
 
export interface EducationalContent {
  title: string;
  definition: string;
  realWorldExample: string;
  howItWorks: string;
  defenseStrategies: string[];
  keyTerms: Record<string, string>;
  furtherReading: string[];           // fictional titles/authors
}
 
export interface GlobeScenarioConfig {
  targetSatellites: string[];         // satellite IDs to highlight
  targetGroundStations: string[];
  signalPaths: SignalPathConfig[];
  attackType: AttackVisualizationType;
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
  accuracy: number;                   // 0–1
  breakdown: StageScore[];
}
 
export function computeGrade(
  score: number, 
  log: DecisionRecord[]
): ScoreBreakdown { ... }
 
// Grade boundaries
const GRADE_BOUNDARIES = {
  S: 90,
  A: 75,
  B: 60,
  C: 45,
} as const;
```
 
---
 
## 🗃 State Management
 
All global state is managed with **Zustand** — no Context API boilerplate, no Redux overhead.
 
### `useSimStore`
 
```typescript
// store/useSimStore.ts
 
interface SimState {
  // State
  activeScenario: Scenario | null;
  engine: SimulationEngine | null;
  currentStageIndex: number;
  score: number;
  isRunning: boolean;
  isPaused: boolean;
  decisionMade: boolean;             // whether a decision was made this stage
  completedScenarios: CompletedRun[];
 
  // Actions
  startScenario: (scenarioId: string) => void;
  advanceStage: () => void;
  makeDecision: (decisionId: string) => DecisionResult;
  pauseSimulation: () => void;
  resumeSimulation: () => void;
  endScenario: () => void;
  clearActiveScenario: () => void;
}
```
 
### `useAlertStore`
 
```typescript
// store/useAlertStore.ts
 
interface AlertState {
  alerts: Alert[];
  unreadCount: number;
 
  // Actions
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
  scenarioId?: string;              // links to a scenario if applicable
  read: boolean;
}
```
 
### `useUIStore`
 
```typescript
// store/useUIStore.ts
 
interface UIState {
  sidebarOpen: boolean;
  sidebarCollapsed: boolean;
  educationalSidebarOpen: boolean;
  educationalSidebarPinned: boolean;
  globeFocusTarget: string | null;  // satellite ID or null
  activeModal: string | null;
  transitionPlaying: boolean;
 
  // Actions
  toggleSidebar: () => void;
  setGlobeFocus: (satelliteId: string | null) => void;
  openModal: (modalId: string) => void;
  closeModal: () => void;
  setTransitionPlaying: (playing: boolean) => void;
}
```
 
---
 
## 🎬 Animation System
 
### Animation Catalog
 
| Trigger | Component | Library | Duration | Notes |
|---|---|---|---|---|
| App boot typewriter | `BootPage` | GSAP | ~3500ms | `staggerTo` per character, 18ms |
| Route transition | `DiagonalSlash` | Framer Motion | 600ms | Three panels, stagger 80ms |
| Dashboard mount | `HUDPanel` | Framer Motion | 400ms | Stagger 60ms per panel |
| New alert | `AlertFeed` | Framer Motion | 300ms | `x: 80 → 0`, spring |
| Metric count-up | `MetricCard` | GSAP | 1200ms | `to({ innerText: value })` |
| Radar sweep | `ThreatRadar` | CSS | ∞ | `animation: spin 4s linear` |
| Blip pulse | `ThreatRadar` | CSS | ∞ | `animation: ping 2s ease-out` |
| Card hover | `ScenarioCard` | Framer Motion | 200ms | `y: -4`, shimmer |
| Stage advance | `StageProgress` | Framer Motion | 500ms | Line fill + chip scale |
| Decision selected | `DecisionPanel` | Framer Motion | 400ms | Border color + opacity |
| Wrong decision | `DecisionPanel` | Framer Motion | 500ms | Shake + red border |
| Satellite attack | `SatelliteSwarm` | Three.js | 800ms | Instance color + particle |
| Score arc fill | `ProgressArc` | Framer Motion | 1500ms | `strokeDashoffset` ease-out |
| Grade slam | `OutcomeScreen` | Framer Motion | 400ms | `scale: 3→1`, rotation spring |
| Data stream | `DataStream` | CSS | ∞ | `translateY` linear |
| Globe rotation | `Earth` | Three.js | ∞ | 0.0005 rad/frame |
| Camera lerp | `CameraController` | Three.js | 1200ms | `lerpVectors` toward target |
 
### Reduced Motion
 
All animations respect `prefers-reduced-motion`. A Zustand action `setReducedMotion(true)` disables all decorative animations while preserving functional state changes.
 
```typescript
// In every Framer Motion component:
const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
 
const variants = {
  hidden: prefersReduced ? {} : { opacity: 0, y: 12 },
  visible: { opacity: 1, y: 0 },
};
```
 
---
 
## 🛡 Simulation Scenarios
 
### 1. GPS Signal Spoofing
- **Category:** Signal Attack
- **Severity:** Critical
- **Difficulty:** ★★★★☆
- **Systems:** GPS, Navigation, Timing
- **Summary:** A malicious actor transmits counterfeit GPS signals that override legitimate satellite broadcasts, causing navigation systems aboard civilian and military vessels to report false positions. The attack is silent, requiring no physical access.
- **Stages:** `Normal Operation → Signal Anomaly Detected → Source Investigation → Mitigation → Recovery → Lessons`
- **Key Teaching:** How GPS authentication (Galileo OSNMA, GPS III NMA) works and why unsigned civil GPS signals are vulnerable.
### 2. Satellite Signal Jamming
- **Category:** Signal Attack
- **Severity:** High
- **Difficulty:** ★★★☆☆
- **Systems:** Communications, Telemetry, GPS
- **Summary:** A powerful broadband jammer in the target satellite's downlink frequency range overwhelms the receiver, cutting communication between the satellite and its ground station. Unlike spoofing, jamming is detectable but hard to counter instantly.
- **Key Teaching:** Spread-spectrum techniques, frequency hopping, anti-jam antennas, and how militaries harden comms against jamming.
### 3. Ground Station Malware Infection
- **Category:** Malware
- **Severity:** Critical
- **Difficulty:** ★★★★★
- **Systems:** Ground Control, Uplink, Command
- **Summary:** A spear-phishing email targeting a mission control engineer delivers a remote access trojan. Attackers gain persistent access to the ground segment network, pivot to uplink systems, and begin probing satellite command interfaces.
- **Key Teaching:** Network segmentation, zero-trust architecture, air-gapping critical systems, and incident response playbooks.
### 4. Mission Control Ransomware
- **Category:** Malware
- **Severity:** Critical
- **Difficulty:** ★★★★★
- **Systems:** All Ground Systems
- **Summary:** Ransomware deployed through a compromised supply-chain software update encrypts mission control workstations simultaneously. Satellite operations are halted. The attackers demand payment to restore access to encrypted satellite command files.
- **Key Teaching:** Offline backups, immutable infrastructure, ransomware negotiation strategy, recovery time objectives.
### 5. Solar Flare Interference
- **Category:** Natural Hazard
- **Severity:** High
- **Difficulty:** ★★☆☆☆
- **Systems:** Communications, Solar Power, Radiation
- **Summary:** A X-class solar flare releases a coronal mass ejection (CME) that reaches Earth within 18 hours. The resulting geomagnetic storm disrupts satellite communications, degrades GPS accuracy, and threatens solar panel efficiency through radiation damage.
- **Key Teaching:** Space weather monitoring, safe mode procedures, radiation hardening, and why CMEs cause such widespread disruption.
### 6. Communication Blackout
- **Category:** Signal Attack
- **Severity:** Medium
- **Difficulty:** ★★☆☆☆
- **Systems:** Communications, Telemetry
- **Summary:** A coordinated attack targeting multiple ground stations simultaneously cuts communication with the primary satellite constellation. Operating teams cannot send commands or receive telemetry. Satellites begin autonomously entering contingency modes.
- **Key Teaching:** Redundant ground station networks, TDRS relay satellites, autonomous satellite contingency modes.
### 7. Supply Chain Compromise
- **Category:** Supply Chain
- **Severity:** Critical
- **Difficulty:** ★★★★★
- **Systems:** Software, Firmware, Hardware
- **Summary:** A firmware update distributed by a trusted third-party vendor contains a backdoor inserted during the software build process. The update is cryptographically signed (the vendor's key was compromised). After installation, an attacker can execute arbitrary commands via a covert uplink channel.
- **Key Teaching:** Software supply chain security, reproducible builds, HSM-based signing, firmware verification.
### 8. Telemetry Data Manipulation
- **Category:** Data Integrity
- **Severity:** High
- **Difficulty:** ★★★★☆
- **Systems:** Telemetry, Monitoring, Data Pipelines
- **Summary:** An attacker who gained read-write access to the telemetry processing pipeline begins injecting falsified sensor readings. The satellite appears healthy while actually experiencing a slow orbital decay. Operators are flying blind on fabricated data.
- **Key Teaching:** Data provenance, cryptographic telemetry signing, anomaly detection in time-series sensor data.
### 9. Authentication Failure
- **Category:** Authentication
- **Severity:** High
- **Difficulty:** ★★★☆☆
- **Systems:** Ground Control, Command Interface
- **Summary:** An attacker exploits a weak authentication implementation in the mission control web portal — credential stuffing from a leaked password database grants access to an operator account. The account is used to send unauthorized commands to a communications satellite.
- **Key Teaching:** MFA, hardware security keys, least-privilege access, command authentication codes (CAC) for satellite uplinks.
### 10. Insider Threat
- **Category:** Insider
- **Severity:** Critical
- **Difficulty:** ★★★★★
- **Systems:** All Systems
- **Summary:** A disgruntled employee with administrator-level access to satellite command systems begins exfiltrating mission data and planting logic bombs — code set to trigger on a future date. The attacker has legitimate credentials and their behavior is subtle enough to evade standard monitoring.
- **Key Teaching:** Behavioral analytics, privileged access management (PAM), separation of duties, insider threat programs.
---
 
## 📚 Educational Framework
 
Every scenario follows the **DEFINE → EXPLAIN → APPLY → REINFORCE** model:
 
| Phase | Content | Trigger |
|---|---|---|
| **DEFINE** | What is this attack? One-paragraph plain-English definition | Scenario select screen |
| **EXPLAIN** | How does it work technically? Step-by-step breakdown | Stage 1 (Detection) educational sidebar |
| **APPLY** | You're in it — what do you do? | Decision Panel throughout |
| **REINFORCE** | What were the optimal choices? What do organizations do in reality? | Outcome Screen + Full Report |
 
### Key Terminology Glossary (Built-In)
 
Each scenario includes a `keyTerms` dictionary. The educational sidebar renders these as hoverable tooltip definitions when terms appear in the narrative text, allowing analysts to build vocabulary contextually.
 
Examples:
- **Spoofing** — Broadcasting counterfeit signals designed to impersonate a legitimate source
- **Jamming** — Overpowering a legitimate signal with noise to make the receiver unable to decode it
- **OSNMA** — Open Service Navigation Message Authentication (Galileo's broadcast authentication system)
- **CME** — Coronal Mass Ejection; a large expulsion of plasma and magnetic field from the Sun
- **PAM** — Privileged Access Management; tools and policies that control and monitor administrator-level access
---
 
## 🗺 Implementation Milestones
 
### M1 — Design System & AppShell
**Goal:** The visual foundation everything else depends on.
 
Files to create:
- `tailwind.config.ts` — custom tokens (colors, fonts, animation)
- `src/index.css` — Tailwind directives + CSS custom properties
- `src/components/ui/HUDPanel.tsx`
- `src/components/ui/DiagonalSlash.tsx`
- `src/components/ui/GlowBadge.tsx`
- `src/components/ui/DataStream.tsx`
- `src/components/ui/Scanline.tsx`
- `src/components/layout/AppShell.tsx`
- `src/components/layout/Sidebar.tsx`
- `src/components/layout/TopBar.tsx`
- `src/components/layout/PageTransition.tsx`
- `src/lib/cn.ts`
**Definition of Done:** AppShell renders with Sidebar and TopBar. HUDPanel and DiagonalSlash demo in isolation. All design tokens documented.
 
---
 
### M2 — Boot Sequence & Routing
**Goal:** First impression and navigation architecture.
 
Files to create:
- `src/router/AppRouter.tsx`
- `src/features/boot/BootPage.tsx`
- GSAP typewriter sequence
- Route scaffolding for all 7 routes
**Definition of Done:** App opens to boot sequence, completes with DiagonalSlash wipe, lands on empty Dashboard. All routes navigate without errors.
 
---
 
### M3 — Dashboard Shell
**Goal:** The operational home base, minus the 3D globe.
 
Files to create:
- `src/features/dashboard/DashboardPage.tsx`
- `src/features/dashboard/components/MetricCard.tsx`
- `src/features/dashboard/components/AlertFeed.tsx`
- `src/features/dashboard/components/ThreatRadar.tsx`
- `src/features/dashboard/components/SystemHealthBar.tsx`
- `src/features/dashboard/components/MissionTimeline.tsx`
- `src/store/useAlertStore.ts`
- Alert generation logic (random intervals, seeded)
**Definition of Done:** Dashboard renders all panels. Metrics count up on mount. Alert feed receives and displays simulated alerts. Radar renders and animates.
 
---
 
### M4 — 3D Globe
**Goal:** The cinematic Earth visualization.
 
Files to create:
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
**Definition of Done:** Full globe renders with orbiting satellites, ground stations, animated signal paths. Camera lerps to selected satellite. Atmosphere glow visible. Performance >60fps.
 
---
 
### M5 — Simulation Engine
**Goal:** The pure-TypeScript brain of the application.
 
Files to create:
- `src/engine/types.ts`
- `src/engine/SimulationEngine.ts`
- `src/engine/scoreEngine.ts`
- `src/engine/scenarios/index.ts`
- All 10 scenario files (complete data for all stages, decisions, educational content)
- `src/store/useSimStore.ts`
- `src/hooks/useSimulation.ts`
**Definition of Done:** All 10 scenarios instantiate without errors. Engine advances stages, records decisions, computes accurate scores. Full Vitest test suite passes.
 
---
 
### M6 — Scenario Select
**Goal:** The threat library browser.
 
Files to create:
- `src/features/scenarios/ScenarioSelectPage.tsx`
- `src/features/scenarios/components/ScenarioCard.tsx`
- Filter bar component
- Category icons mapping
**Definition of Done:** All 10 scenario cards render with correct data. Filter works. Hover animations play. Clicking triggers DiagonalSlash + navigation.
 
---
 
### M7 — Scenario Runner
**Goal:** The core interactive simulation experience.
 
Files to create:
- `src/features/scenarios/ScenarioRunnerPage.tsx`
- `src/features/scenarios/components/StageProgress.tsx`
- `src/features/scenarios/components/DecisionPanel.tsx`
- `src/features/scenarios/components/EducationalSidebar.tsx`
- `src/features/scenarios/components/AttackTimeline.tsx`
- `src/features/scenarios/components/NarrativeBox.tsx`
- `src/features/scenarios/components/OutcomeScreen.tsx`
- `src/features/globe/AttackOverlay.tsx`
- `src/hooks/useCountdown.ts`
- Globe integration (attack state drives R3F overlays)
**Definition of Done:** Full end-to-end scenario run works for all 10 scenarios. Decisions recorded. Score updates. Globe shows attack visualization. Outcome screen appears at completion.
 
---
 
### M8 — Reports
**Goal:** Mission debrief and history.
 
Files to create:
- `src/features/reports/ReportsPage.tsx`
- `src/features/reports/components/IncidentReport.tsx`
- `src/features/reports/components/ScoreBreakdown.tsx`
- Zustand persistence (completed runs)
**Definition of Done:** Completed runs appear in reports. Each report expands to show decision review. Score breakdown is accurate.
 
---
 
### M9 — Globe Full View & Polish Pass
**Goal:** Standalone globe + all micro-animations + final visual details.
 
Tasks:
- Complete `/globe` standalone route with satellite inspection
- Add `OrbitalMinimap` to Dashboard (compact embedded globe)
- Add `Scanline` CRT overlay to boot and radar
- Add `ProgressArc` animation to outcome screen
- Complete all hover micro-interactions on every card
- Add sound effects (opt-in, muted by default)
- Animate all page mount sequences
**Definition of Done:** Every screen feels polished. No animation placeholders remain.
 
---
 
### M10 — Production Polish
**Goal:** Portfolio-ready quality.
 
Tasks:
- Full responsive audit (desktop, laptop, tablet — no mobile target since this is a SOC application)
- Accessibility pass (keyboard navigation, focus indicators, ARIA labels, reduced motion)
- Lighthouse performance audit; optimize textures, lazy-load R3F canvas
- Error boundary components for the 3D scene
- Loading states for all async operations
- 404 page (mission control themed)
- Final README + deployment configuration
- Vercel/Netlify deploy
**Definition of Done:** Lighthouse score ≥90 performance, ≥90 accessibility. Zero console errors or warnings in production build.
 
---
 
## 🚀 Getting Started
 
### Prerequisites
 
- Node.js 20+
- npm 10+ or pnpm 9+
- A modern browser with WebGL support (Chrome 120+, Firefox 121+, Safari 17+)
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
 
On first load, you'll see the **Boot Sequence** (~3.5s). Press any key or click to skip. You'll land on the Operations Dashboard. No account or login is required — all data is local.
 
To run your first simulation:
1. Click **Scenarios** in the left sidebar
2. Select any scenario card
3. Read the overview, then click **LAUNCH SIMULATION**
4. Make decisions at each stage using the Decision Panel
5. Review your outcome and score
---
 
## 🔐 Environment Variables
 
Orbital Shield has **no required environment variables** — it runs entirely locally with no external API calls.
 
Optional variables for future extension:
 
```env
# .env.local (optional)
 
# Enable debug overlays (orbital paths, FPS counter, state inspector)
VITE_DEBUG_MODE=false
 
# Disable the boot sequence for faster development iteration
VITE_SKIP_BOOT=false
 
# Seed for random alert generation (default: random per session)
VITE_ALERT_SEED=12345
```
 
---
 
## 📜 Scripts Reference
 
```bash
# Development
npm run dev           # Start Vite dev server with HMR
npm run dev:debug     # Start with VITE_DEBUG_MODE=true
 
# Building
npm run build         # TypeScript check + Vite production build
npm run preview       # Preview the production build locally
 
# Testing
npm run test          # Run Vitest in watch mode
npm run test:run      # Run all tests once (CI mode)
npm run test:ui       # Open Vitest browser UI
 
# Code Quality
npm run lint          # ESLint check
npm run lint:fix      # ESLint auto-fix
npm run format        # Prettier format all files
npm run typecheck     # tsc --noEmit (type check only)
 
# Combined
npm run check         # typecheck + lint + test:run (pre-commit)
```
 
---
 
## 🤝 Contributing
 
This is a personal portfolio project but PRs for bug fixes, new scenarios, or educational content improvements are welcome.
 
```bash
# Fork and clone
git clone https://github.com/YOUR_USERNAME/orbital-shield.git
 
# Create a feature branch
git checkout -b feature/new-scenario-laser-interference
 
# Make changes, then run the full check suite
npm run check
 
# Commit with conventional commits
git commit -m "feat(scenarios): add laser interference scenario"
 
# Push and open a PR
git push origin feature/new-scenario-laser-interference
```
 
### Adding a New Scenario
 
1. Create `src/engine/scenarios/yourScenario.ts`
2. Implement the `Scenario` interface from `src/engine/types.ts`
3. Register it in `src/engine/scenarios/index.ts`
4. Add a globe config in `GlobeScenarioConfig`
5. Write at least 5 Vitest unit tests for decision scoring
---
 
## 🙏 Acknowledgements
 
- **NASA** — Earth texture maps sourced from NASA Visible Earth (public domain)
- **Three.js community** — R3F ecosystem, drei helpers, and shader examples
- **Atlus / Persona 5** — Interface philosophy inspiration (no assets used)
- **CISA** — Space Systems Critical Infrastructure Security guidance
- **ESA & SpaceX** — Public documentation on satellite operations and cybersecurity
---
 
<div align="center">
**Built by [Genesis](https://github.com/seventyoseven) // Mystic707**  
*Space Security Operations Center — Educational Simulation Platform*
 
```
[ALL SYSTEMS NOMINAL] // ORBITAL SHIELD v2.1.0 // READY
```
 
</div>
 
