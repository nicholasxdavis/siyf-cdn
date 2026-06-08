# siyf-cdn

Static JSON and media assets for [Sports In Your Face](https://github.com/nicholasxdavis/siyf-cdn). Served in production via [jsDelivr](https://www.jsdelivr.com/?docs=gh).

## jsDelivr URLs

jsDelivr requires a **file path** — the repo root alone is not a valid URL.

```
https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/<path>
```

Examples:

| Asset | URL |
|---|---|
| NBA teams | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/teams/nba.json` |
| Special events | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/meta/special-events.json` |
| NBA Finals logo | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/media/finals-game.png` |
| NBA All-Star logo | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/media/all-star-game.png` |
| Favicon (SVG) | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/favicon/favicon.svg` |
| Favicon (ICO) | `https://cdn.jsdelivr.net/gh/nicholasxdavis/siyf-cdn@main/favicon/favicon.ico` |

In local dev the app reads from `../siyf-cdn` at `/siyf-cdn/…` instead.

## Updating

```bash
cd siyf-cdn
git add -A && git commit -m "Update CDN data" && git push
```

Changes on `main` appear on jsDelivr within a few minutes.
