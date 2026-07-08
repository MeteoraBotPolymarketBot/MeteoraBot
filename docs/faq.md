# Frequently Asked Questions

The most common questions about MeteoraBot — fees, wallets, safety, and troubleshooting. For the full, always-current FAQ, see [meteorabot.com/faq](https://meteorabot.com/faq).

> Note: the exact forecasting math, model weightings, position-sizing coefficients, and exit thresholds are proprietary and are intentionally not documented here.

## What is MeteoraBot?

An AI-driven trading engine for **weather prediction markets on Polymarket**. It discovers weather markets, builds a consensus forecast from multiple institutional sources, reasons over each market with AI, and executes on Polymarket's CLOB — across 67+ cities.

## Which forecast sources does it use?

MeteoraBot blends several **institutional meteorological models** into a single consensus forecast, with Hong Kong Observatory data used for Hong Kong markets specifically. The blending weights and math are proprietary.

## What blockchain and tokens does it use?

Everything settles on **Polygon** (chain ID 137) through **Polymarket's CLOB**. **pUSD** is the trading asset (Polymarket auto-wraps USDC.e at deposit under CLOB V2).

## Is MeteoraBot free to use?

There's **no subscription and no upfront fee**. You pick a small per-trade model: **$0.015 per executed order**, or **$0.03 on winners only**. Standard Polymarket/Polygon costs apply.

## Is it custodial? Who holds my funds?

MeteoraBot is **non-custodial** — you pair your own Polygon wallet and your funds stay in your control. The engine only manages positions it opens itself.

## I hit Start and nothing has fired yet — what's wrong?

Walk this checklist before assuming anything is broken:

1. **Pair your wallet first** — orders can't route without a paired Polygon wallet (Settings → Wallet Connection).
2. **Fund the wallet** with pUSD.
3. **Keep the tab open** — a heartbeat keeps your session alive.
4. **Give it time** — weather markets are slow; there isn't always a mispriced book to trade right now.
5. **Check your risk settings** aren't filtering everything out.

## Should I unwind open Polymarket positions before starting?

**Yes.** Close anything you opened by hand first. MeteoraBot's exit logic only governs positions it opened itself.

## Are profits guaranteed? Will this make me rich?

**No.** Any tool that promises guaranteed returns is dangerous. Weather books move slowly — most positions resolve over **24–48 hours** — and losses are possible. This is systematic trading software, not a get-rich-quick scheme. Published performance figures are on the live site and are not guarantees.

## What's on the roadmap?

MeteoraBot ships frequently — fixes, new strategies, and deeper instrumentation. Current focus is broadening the strategy library and benchmarking new approaches. See the [Changelog](../CHANGELOG.md) and [blog](https://meteorabot.com/blog).

## Is MeteoraBot available everywhere?

Access may be **restricted in some regions**. Check the live site and your local rules before using it.
