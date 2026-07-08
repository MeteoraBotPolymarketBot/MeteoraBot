# MeteoraBot — AI Polymarket Weather Trading Bot

> Atmospheric volatility, traded systematically. MeteoraBot is an AI-driven trading engine for the **weather markets on [Polymarket](https://polymarket.com)** — it fuses multiple institutional forecast models, reasons over each market with AI, and executes on Polymarket's CLOB on Polygon.

**Live:** [meteorabot.com](https://meteorabot.com) · **App:** [meteorabot.com/app](https://meteorabot.com/app) · **Blog / Field Notes:** [meteorabot.com/blog](https://meteorabot.com/blog)

> ℹ️ **This repository is documentation only.** It contains the README, usage guide, public API reference, FAQ, and release notes. It does **not** contain the trading engine, strategy internals, or any user data.

---

## What is MeteoraBot?

MeteoraBot is a purpose-built **Polymarket trading bot** focused on one category: **weather prediction markets** (e.g. "Will the high temperature in NYC on March 20 fall between 52–53°F?"). Instead of babysitting dozens of contracts by hand, MeteoraBot runs the whole workflow as a single automated loop — it discovers the markets, aggregates forecasts, estimates fair probability, finds mispricing, and routes the order.

- 🌩️ **Weather-specialized** — covers **67+ cities** worldwide, from NYC and London to Tokyo, Paris, and Hong Kong.
- 🧠 **AI reasoning** — every candidate trade is reviewed by AI (Claude & Gemini) before any capital moves.
- 🛰️ **Multi-model consensus** — blends several institutional meteorological sources into one forecast.
- ⚡ **Lightning-fast execution** — a persistent socket into Polymarket's CLOB; sub-second from signal to order.
- 🎛️ **Risk-managed** — disciplined position sizing with a hard per-trade cap.
- 🔒 **Non-custodial** — you pair your own Polygon wallet; MeteoraBot only manages the positions it opens.

## Features

| | |
|---|---|
| **Markets** | Polymarket weather books (temperature, precipitation) across 67+ cities |
| **Chain** | Polygon (chain ID 137), settled through Polymarket's CLOB |
| **Reasoning** | AI sign-off (Claude & Gemini) on every candidate |
| **Modes** | Continuous, burst, and manual trading modes |
| **Dashboard** | Live P&L, positions, signals, leaderboard, weather maps |
| **Mini-games** | Spin & Bet — live-weather side games |

## How it works (high level)

MeteoraBot runs three concurrent loops — **Scan → Reason → Strike**:

1. **Scan** — discover active weather markets and pull live forecasts for each city/date.
2. **Reason** — build a consensus forecast, estimate a fair probability for each outcome, and have the AI review the case.
3. **Strike** — when a market's price disagrees with the model, size the position and route the order; a set of automated exits manages the position afterward.

> The exact forecasting math, model weightings, sizing coefficients, and exit thresholds are proprietary and are **not** published here.

## Documentation

- 📘 [Getting Started](docs/getting-started.md) — connect a wallet and place your first trade
- 🧭 [Usage Guide](docs/usage.md) — trading modes and the dashboard
- 🔌 [Public API Reference](docs/api-reference.md) — read-only public endpoints
- ❓ [FAQ](docs/faq.md) — fees, safety, wallets, troubleshooting
- 🗒️ [Changelog / Release Notes](CHANGELOG.md)

## Quick links

- Website — https://meteorabot.com
- Launch the app — https://meteorabot.com/app
- Leaderboard — https://meteorabot.com/leaderboard
- FAQ — https://meteorabot.com/faq
- Blog — https://meteorabot.com/blog

## Disclaimer

MeteoraBot is trading software for prediction markets. **Nothing here is financial advice, and no returns are guaranteed.** Prediction-market trading carries risk of loss. You are responsible for your own wallet, funds, and jurisdiction's rules. Access may be restricted in some regions.

---

<sub>Keywords: Polymarket bot · Polymarket weather trading · AI Polymarket trading bot · automated prediction market trading · Polygon trading bot · weather prediction markets · algorithmic trading · CLOB trading bot.</sub>
