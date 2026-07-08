# Getting Started

This guide walks you through connecting a wallet and placing your first trade with MeteoraBot. Everything happens in the browser — there's nothing to install.

> Launch the app: **[meteorabot.com/app](https://meteorabot.com/app)**

## Requirements

- A **Polygon** wallet (chain ID 137) that you control.
- Funds for trading. Polymarket settles in **pUSD** (USDC.e is auto-wrapped at deposit post-CLOB-V2).
- A desktop/landscape screen — the dashboard is designed for landscape.

## 1. Pair your wallet

1. Open the app and go to **Settings → Wallet Connection**.
2. Enter your wallet **Key** and your **Proxy Address**.
3. Confirm the connection shows as complete.

> Orders cannot route until a wallet is paired. MeteoraBot is non-custodial and only manages the positions it opens itself.

## 2. Set your risk

In **Settings**, dial in your risk preferences (position sizing and limits). Sensible defaults are provided; you can adjust them at any time.

## 3. Choose a mode

MeteoraBot offers a few trading modes (see the [Usage Guide](usage.md)):

- **Continuous** — the engine runs its Scan → Reason → Strike loops until you stop it.
- **Burst** — a set-and-forget buy-burst mode.
- **Manual** — you drive individual actions.

## 4. Start

Hit **Start**. From that moment the engine discovers markets, reasons about them, and strikes the order book on your behalf, managing exits automatically.

> **Before you start:** close out any Polymarket positions you opened by hand. MeteoraBot's exit logic only governs positions it opened itself.

## Stopping

You can stop the engine at any time from the dashboard. Open positions continue to be managed by their exit rules unless you close them manually.

## Next steps

- [Usage Guide](usage.md) — modes and dashboard tour
- [FAQ](faq.md) — fees, safety, troubleshooting
- [Public API Reference](api-reference.md)
