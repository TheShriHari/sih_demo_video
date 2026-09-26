# SIH Demo Video — Remotion Source & Deliverables (Problem Statement 26037)

Programmatic motion graphics, video explainer engine, and rendered deliverables for **Smart India Hackathon (SIH) — Indian Road Pathfinder**.

Built with [Remotion](https://www.remotion.dev/) (React 19 + TypeScript + SVG Canvas).

---

## 🎬 Video Deliverables (`out/`)

| File | Resolution | Duration | Frames | Description |
| :--- | :--- | :--- | :--- | :--- |
| **[`out/final_production_ready.mp4`](out/final_production_ready.mp4)** | 1080p (1920x1080) @ 30 FPS | **95.0s** | 2,850 | **Official Final Production Video**. Complete 7-step autonomous pathfinding breakdown, behavioral FSM, Monte Carlo KPI proofs, and live scenarios. |
| **[`out/production_iteration.mp4`](out/production_iteration.mp4)** | 1080p (1920x1080) @ 30 FPS | 95.0s | 2,850 | Pre-release iteration render with burnt-in 10-fps telemetry checkpoints. |
| **[`out/draft.mp4`](out/draft.mp4)** | 1080p (1920x1080) @ 30 FPS | 114.0s | 3,420 | Initial long-form composition draft. |
| **[`out/proof_of_concept.mp4`](out/proof_of_concept.mp4)** | 1080p (1920x1080) @ 30 FPS | ~5.0s | 150 | Motion graphics proof-of-concept for ego vehicle path planning. |

---

## 🛠️ Quick Start & Local Preview

### 1. Install Dependencies
```bash
npm install
```

### 2. Launch Remotion Studio Preview
```bash
npm start
```
Studio runs at `http://localhost:3000` or `http://localhost:3001` with interactive timeline scrubbing, frame stepping, and component inspection.

### 3. Headless Production Render
```bash
npx remotion render src/index.ts PS26037Explainer out/final_production_ready.mp4 --concurrency=6
```

### 4. 10-FPS Second-by-Second Visual Audit
Extract 10 frames for any specified second with burnt-in timestamp telemetry overlay:
```bash
python scripts/extract_second_slice.py "out/final_production_ready.mp4" 42 ".tmp/audit_sec42"
```

---

## 📐 Composition Pipeline Architecture (95s / 2,850 Frames)

| Segment | Timestamp | Frames | Component | Pipeline Stage |
| :--- | :--- | :--- | :--- | :--- |
| **01** | `00:00–00:05` | 0–150 | `RealityIntro.tsx` | Unstructured Indian traffic dynamics (potholes, jaywalkers, lane drift) |
| **02** | `00:05–00:11` | 150–330 | `AssumptionBreakdown.tsx` | Why lane-centric Western autonomy fails on Indian roads |
| **03** | `00:11–00:15` | 330–450 | `TitleCard.tsx` | PS26037 Problem Statement & Indian Road Pathfinder title |
| **04** | `00:15–00:24` | 450–720 | `PerceptionScan.tsx` | **Step 1:** 360° LiDAR/Camera Sensor Fusion (35m range, 140° FOV) |
| **05** | `00:24–00:33` | 720–990 | `MotionPrediction.tsx` | **Step 2:** Probabilistic Motion Prediction (Cow, rickshaw, pedestrian) |
| **06** | `00:33–00:43` | 990–1290 | `CostmapBuild.tsx` | **Step 3:** Cellular Costmap & Free-Space Bloom |
| **07** | `00:43–00:52` | 1290–1560 | `CorridorCheck.tsx` | **Step 4:** Clearance Corridor Check (`MIN CLEARANCE: 2.55m`, Stop Line Engaged) |
| **08** | `00:52–00:59` | 1560–1770 | `PathPlanning.tsx` | **Step 5:** Trajectory Spline & Directional Smoothing |
| **09** | `00:59–01:10` | 1770–2100 | `BehaviorFSM.tsx` | **Step 6:** Behavioral Finite State Machine (Exact `0.0 km/h` Yield Clamp) |
| **10** | `01:10–01:15` | 2100–2250 | `SteeringControl.tsx` | **Step 7:** Steering & Actuation Gauges (Throttle & Brake pedals) |
| **11** | `01:15–01:23` | 2250–2490 | `ScenarioGrid.tsx` | Multi-Scenario Validation Matrix (5 complex edge cases) |
| **12** | `01:23–01:30` | 2490–2700 | `RigorKPIs.tsx` | Rigorous KPIs & Monte Carlo Trial Statistics |
| **13** | `01:30–01:35` | 2700–2850 | `ClosingBranding.tsx` | Closing & Team IIT Kharagpur Attribution |

---

## 📁 Repository Structure
```
sih_demo_video/
├── out/                        # Rendered MP4 video deliverables
│   ├── final_production_ready.mp4
│   ├── production_iteration.mp4
│   ├── proof_of_concept.mp4
│   └── draft.mp4
├── scripts/                    # Headless inspection & slicing tools
│   ├── extract_second_slice.py # 10-FPS burnt-in frame slicer
│   └── extract_frames.py       # Keyframe extractor & contact sheet builder
├── src/
│   ├── components/             # React/Remotion scene components (13 scenes)
│   ├── compositions/           # Full composition timeline assembly
│   ├── Root.tsx                # Remotion composition registry
│   ├── index.ts                # Entry point
│   ├── theme.ts                # Typography, color tokens, and timing constants
│   ├── telemetry.ts            # Speed, acceleration, and state telemetry models
│   └── audio.ts                # Audio cue sequencing
├── remotion.config.ts          # Remotion rendering config
├── tsconfig.json               # TypeScript configuration
├── package.json                # Project dependencies and npm scripts
└── README.md                   # Documentation
```
