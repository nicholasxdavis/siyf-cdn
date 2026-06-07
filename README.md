# siyf-cdn

Static JSON assets for [Sports In Your Face](https://github.com/nicholasxdavis/siyf-cdn). Served in production via [jsDelivr](https://www.jsdelivr.com/?docs=gh).

**Base URL:** `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main`

## Layout

| Path | Purpose |
|------|---------|
| `teams/` | Team registries (`nba.json`, `nfl.json`, `epl.json`) |
| `meta/team-aliases.json` | Abbreviation aliases per league |
| `meta/soccer-leagues.json` | League slug → display name |
| `meta/special-events.json` | Curated marquee events (Finals, Super Bowl, etc.) |

## Special events

Set `"enabled": true` and optionally `"logo"` only after human verification. The app never attaches logos from pattern matching alone.

## Updating

Edit JSON, commit, push to `main`. jsDelivr may cache for a few minutes; purge at [jsdelivr.com/tools/purge](https://www.jsdelivr.com/tools/purge) if needed.
