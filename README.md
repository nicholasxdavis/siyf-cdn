# siyf-cdn

Static JSON and media for [Sports In Your Face](https://github.com/nicholasxdavis/siyf-cdn). Production serves via [jsDelivr](https://www.jsdelivr.com/?docs=gh).

## What lives here (immutable / slow-changing)

| Path | Contents |
|------|----------|
| `teams/*.json` | Team names, abbreviations, ESPN IDs, colors, CDN logo paths |
| `media/logos/{sport}/*.png` | Team logos (mirrored from ESPN once) |
| `meta/team-aliases.json` | Abbreviation aliases (GSW→GS, etc.) |
| `meta/soccer-leagues.json` | League slug labels |
| `meta/special-events.json` | All-Star / Finals badges |
| `meta/manifest.json` | Last sync time + asset inventory |
| `players/nba-index.json` | Player headshots + bbref slugs (optional sync) |
| `stats/bbref/*.json` | Archived season stat lines — **never change retroactively** |

## jsDelivr URLs

```
https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/<path>
```

Examples:

| Asset | URL |
|-------|-----|
| NBA teams | `…/teams/nba.json` |
| LAL logo | `…/media/logos/nba/lal.png` |
| LeBron bbref stats | `…/stats/bbref/jamesle01.json` |

Local dev: the app reads `../siyf-cdn` at `/siyf-cdn/…`.

## Sync from APIs (run from repo root)

One-time / occasional pull from ESPN (and optional BDL + Basketball-Reference):

```bash
# Teams + download logo PNGs for NBA, NFL, EPL, MLB, NHL
node scripts/sync-cdn.mjs

# One sport only
node scripts/sync-cdn.mjs --sport nba

# JSON only (no logo download)
node scripts/sync-cdn.mjs --skip-logos

# NBA rosters → players/nba-index.json
node scripts/sync-cdn.mjs --with-rosters

# Also archive bbref season stats (slow, ~350ms/player)
node scripts/sync-cdn.mjs --with-rosters --with-bbref
```

Optional: `BDL_API_KEY=… node scripts/sync-cdn.mjs` merges BallDontLie team IDs into `teams/nba.json`.

Validate, then push:

```bash
node scripts/validate-cdn-data.mjs
cd siyf-cdn && git add -A && git commit -m "Sync CDN assets" && git push
```

Changes on `main` appear on jsDelivr within a few minutes.

## App behavior

The extension **loads teams/logos/stats from CDN first**. ESPN team endpoints are only hit if CDN data is missing or incomplete. Live scores still come from ESPN via `siyf-api`.
