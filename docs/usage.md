# Usage Guide

A tour of MeteoraBot's trading modes and dashboard. For setup, see [Getting Started](getting-started.md).

## Trading modes

MeteoraBot ships three modes, inspired by how the best wallets operate:

| Mode | Behavior |
|---|---|
| **Continuous** | The engine runs its Scan → Reason → Strike loops continuously, finding and trading mispriced weather markets until you stop it. |
| **Burst** | A set-and-forget mode that deploys a bounded burst of capital, then idles. |
| **Manual** | You trigger individual scans/actions and stay in control of each step. |

Switch modes any time from the dashboard.

## The dashboard

| Panel | What it shows |
|---|---|
| **P&L Hero** | Live realized/unrealized profit and loss, equity curve. |
| **AI Engine** | The latest AI verdicts (YES / NO / SKIP) and confidence. |
| **Signals** | Active edges the engine has found. |
| **Positions** | Open positions and their status. |
| **Markets / Ticks** | Discovered weather markets and live price ticks. |
| **Leaderboard** | Top weather traders on Polymarket. |
| **Maps** | Live earthquake and precipitation maps. |
| **Live Weather** | Current conditions for tracked cities. |

## Mini-games

- **Spin** — a live-weather jackpot side game.
- **Bet** — a lightweight weather side bet.

Both are optional and separate from the core trading engine.

## Fees

MeteoraBot has **no subscription and no upfront fee**. You choose a per-trade model:

- **$0.015** on every executed order (regardless of outcome), **or**
- **$0.03** on winners only.

Standard Polymarket/Polygon network costs apply as usual.

## Tips

- Keep the browser tab open while trading — a heartbeat keeps your session alive.
- Fund the wallet with pUSD before starting.
- Weather books move slowly; most positions resolve over 24–48 hours. This is not a fast-flip strategy.
