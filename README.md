# AI Agent — Environment Explorer

A browser-based simulation where an autonomous AI agent navigates a grid environment in real time — perceiving its surroundings, reasoning about its next move, and acting to collect goals while avoiding hazards.

## What It Does

The agent starts at the top-left of a 10×9 grid and tries to collect all goal tiles (★) while managing its health, score, and internal state. You can watch it think, pathfind, and react — or take over the controls yourself.

## Grid Elements

| Symbol | Type | Effect |
|--------|------|--------|
| ◉ | Agent | You / the AI |
| ★ | Goal | +100 pts, +10 HP |
| ✕ | Hazard | −25–40 HP, −20 pts |
| ◆ | Bonus | +30 pts, curiosity boost |
| ░ | Wall | Impassable |

## Agent Behaviour (Auto Mode)

The agent uses a priority-based decision loop each step:

1. **Adjacent goal?** → Move directly to it
2. **Adjacent bonus?** → Detour if score is low
3. **BFS pathfinding** → Navigate toward the nearest remaining goal
4. **Explore** → Move to an unvisited, safe cell
5. **Backtrack** → Revisit a safe cell if fully explored
6. **Last resort** → Accept a hazardous path if no other option exists

The agent also tracks three internal stats — **Health**, **Curiosity**, and **Confidence** — which shift based on what it encounters.

## Controls

| Control | Action |
|---------|--------|
| **Pause / Play** | Stop or resume the agent |
| **Step** | Advance one move at a time |
| **Mode** | Toggle between Auto (AI) and Manual (arrow keys) |
| **Reset** | Start a fresh run |
| **Speed slider** | Adjust simulation speed (1 = slow, 10 = fast) |

In **Manual mode**, use arrow keys (↑ ↓ ← →) to move the agent yourself.

## UI Panels

- **Perception (3×3)** — The agent's immediate sensory field around its current position
- **Internal State** — Live bars for Health, Curiosity, and Confidence
- **Thought Log** — A rolling feed of the agent's reasoning each step

## Running It

Just open `index.html` in any modern browser — no build step, no dependencies, no server required.

```
open index.html
```

## Win / Lose Conditions

- **Mission Complete** — All 3 goals collected
- **Terminated** — Health reaches 0
