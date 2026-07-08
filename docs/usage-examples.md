# Usage Examples

Practical, copy-paste examples for MeteoraBot's **public, read-only** API. No API key is required. For the full endpoint list, see the [API Reference](api-reference.md); for the product tour, see the [Usage Guide](usage.md).

> **Base URL:** `https://meteorabot.com`
>
> Responses below are **illustrative** — values change constantly and schemas may evolve. Trim your requests to the fields you need.

---

## 1. Leaderboard — top weather traders

Fetch the current public leaderboard.

```bash
curl -s https://meteorabot.com/api/leaderboard
```

**Response (trimmed):**

```json
{
  "traders": [
    {
      "address": "0xb40e…7cc9",
      "name": "Poligarch",
      "rank": 1,
      "totalPnl": 177093.47,
      "winRate": "100.0",
      "totalPositions": 200,
      "activePositions": 200,
      "volume": 23760663,
      "pnlHistory": [
        { "time": "2026-06-30", "pnl": 196.35 },
        { "time": "2026-07-08", "pnl": 1513.41 }
      ]
    }
  ]
}
```

**Get the top trader's name and P&L with [`jq`](https://jqlang.github.io/jq/):**

```bash
curl -s https://meteorabot.com/api/leaderboard \
  | jq '.traders[0] | {name, totalPnl, winRate}'
```

```json
{ "name": "Poligarch", "totalPnl": 177093.47, "winRate": "100.0" }
```

**Top 5 traders by P&L:**

```bash
curl -s https://meteorabot.com/api/leaderboard \
  | jq -r '.traders[:5][] | "\(.rank)\t\(.name)\t$\(.totalPnl)"'
```

---

## 2. Public signals — the live scan feed

Returns recent AI trade decisions plus a summary of the latest scan.

```bash
curl -s https://meteorabot.com/api/public/signals
```

**Response (trimmed):**

```json
{
  "lastScanAt": 1783507589977,
  "nextScanAt": 1783525589977,
  "scanning": false,
  "aiReady": true,
  "stats": { "scanned": 20, "signals": 17, "skipped": 3, "avgEdge": 17.5, "topEdge": 40 },
  "analyses": [
    {
      "marketId": "2825782",
      "question": "Will the highest temperature in London be 33°C on July 9?",
      "decision": "BUY_YES",
      "confidence": "HIGH",
      "market_price": "23.5¢",
      "edge_pct": 35
    }
  ]
}
```

**List every current signal as `decision · question · edge`:**

```bash
curl -s https://meteorabot.com/api/public/signals \
  | jq -r '.analyses[] | "\(.decision)\t\(.edge_pct)%\t\(.question)"'
```

**Only high-confidence buys:**

```bash
curl -s https://meteorabot.com/api/public/signals \
  | jq '.analyses[] | select(.confidence == "HIGH" and (.decision | startswith("BUY")))'
```

**When does the next scan run?** (`nextScanAt` is epoch **milliseconds**):

```bash
curl -s https://meteorabot.com/api/public/signals \
  | jq -r '.nextScanAt / 1000 | "next scan: \(strftime("%Y-%m-%d %H:%M UTC"))"'
```

---

## 3. HKO gauge — Hong Kong running-max temperature

A tiny endpoint powering the Hong Kong resolution indicator.

```bash
curl -s https://meteorabot.com/api/hko
```

**Response:**

```json
{ "runningMax": 31, "lastTemp": 29, "date": "2026-07-08", "ts": 1783509196567 }
```

**Just the running max:**

```bash
curl -s https://meteorabot.com/api/hko | jq '.runningMax'
```

---

## Language snippets

### JavaScript (fetch)

```js
const res = await fetch("https://meteorabot.com/api/public/signals");
const { analyses } = await res.json();

const buys = analyses.filter((a) => a.decision.startsWith("BUY"));
console.log(`${buys.length} active buy signals`);
for (const a of buys) {
  console.log(`${a.decision}  ${a.edge_pct}%  ${a.question}`);
}
```

### Python (requests)

```python
import requests

r = requests.get("https://meteorabot.com/api/leaderboard", timeout=10)
r.raise_for_status()
traders = r.json()["traders"]

top5 = sorted(traders, key=lambda t: t["totalPnl"], reverse=True)[:5]
for t in top5:
    print(f'{t["name"]:<20} ${t["totalPnl"]:,.2f}  ({t["winRate"]}% win)')
```

### Python (poll for the next scan)

```python
import requests, time

s = requests.get("https://meteorabot.com/api/public/signals", timeout=10).json()
wait = s["nextScanAt"] / 1000 - time.time()
print(f"next scan in ~{max(0, wait) / 60:.0f} min")
```

---

## Notes & etiquette

- These endpoints are **read-only** and return **public** data — no keys, no account, no wallet.
- Please keep request volume light; poll on the order of minutes, not seconds. `nextScanAt` tells you when new signals are due, so there's rarely a reason to poll faster.
- Timestamps (`ts`, `lastScanAt`, `nextScanAt`) are **epoch milliseconds**.
- Response schemas may change without notice. Anything beyond casual read-only use should be validated against the live site.
- Account, wallet, trading, and admin endpoints are authenticated and are **not** part of the public API.
