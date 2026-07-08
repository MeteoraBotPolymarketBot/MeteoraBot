# Public API Reference

MeteoraBot exposes a small set of **read-only, public** JSON endpoints. They require no authentication and return public data (leaderboards, signals, and a live weather gauge).

> **Base URL:** `https://meteorabot.com`
>
> These are the only public endpoints. Account, wallet, trading, and admin endpoints are authenticated and are **not** part of this reference.

> 💡 For copy-paste `curl`, JavaScript, and Python snippets against these endpoints, see [Usage Examples](usage-examples.md).

## Conventions

- All responses are `application/json`.
- Use normal HTTP `GET`. No API key is required.
- Please be considerate with request volume; these endpoints are for light, read-only use.

## Endpoints

### `GET /api/leaderboard`

Returns the current public leaderboard of top weather traders.

```bash
curl https://meteorabot.com/api/leaderboard
```

### `GET /api/public/signals`

Returns the public feed of recent trading signals (read-only).

```bash
curl https://meteorabot.com/api/public/signals
```

### `GET /api/hko`

Returns the live Hong Kong Observatory (HKO) running-max gauge that powers the Hong Kong resolution indicator.

```bash
curl https://meteorabot.com/api/hko
```

## Related public pages

Human-readable public pages (not JSON):

- `/leaderboard` — top traders
- `/winners` — recent weather winners
- `/blog` — release notes and field notes

> Response schemas may change without notice. For anything beyond casual read-only use, check the live site.
