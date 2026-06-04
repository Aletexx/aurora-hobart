# 🌌 Aurora Australis Tracker — Hobart, Tasmania

A lightweight, single-file web app that shows real-time aurora australis visibility conditions for Hobart, Tasmania. No backend, no API keys, no build tools — just one HTML file hosted for free on GitHub Pages.

**Live site:** `https://aletexx.github.io/aurora-hobart/`

---

## What it does

- Fetches the live **Kp planetary index** from NOAA's Space Weather Prediction Center
- Fetches a **3-day Kp forecast** and plots it on a chart with Hobart's visibility thresholds marked
- Fetches current **cloud cover** for Hobart from wttr.in
- Shows a **contextual status badge** — daytime labels read as a forecast ("Low activity — check back tonight"), night-time labels reflect current conditions ("Quiet — unlikely right now")
- Shows a **geomagnetic storm alert banner** when Kp reaches photographic (≥ 5) or naked-eye (≥ 7) thresholds
- Auto-refreshes every **15 minutes**, with a manual refresh button

---

## Visibility thresholds for Hobart

Hobart sits at approximately **42.9°S geographic / 49.5°S magnetic latitude**, which means it needs stronger geomagnetic activity than higher-latitude cities to see aurora.

| Kp | What to expect in Hobart |
|----|--------------------------|
| 0 – 3 | Quiet — no aurora expected |
| 4 | Marginal — possible glow low on the horizon |
| 5 – 6 | **Photographic** — camera on a tripod can capture it, likely invisible to the naked eye |
| 7 – 8 | **Naked-eye visible** — should be visible from dark sky sites |
| 9 | **Extreme storm** — potentially visible from inside the city |

> We are currently near **Solar Cycle 25 maximum (2024–2026)**, which means above-average aurora activity. A great window to watch.

---

## Data sources

| Data | Source | Update frequency |
|------|--------|-----------------|
| Current Kp index | [NOAA SWPC](https://www.swpc.noaa.gov) | Every 3 hours |
| 3-day Kp forecast | [NOAA SWPC](https://services.swpc.noaa.gov/products/noaa-planetary-k-index-forecast.json) | Every 3 hours |
| Cloud cover | [wttr.in](https://wttr.in) | Real-time |

All APIs are called directly from the browser — no server required, no API keys needed.

---

## Best viewing spots near Hobart

- **South Arm Peninsula** — dark skies, wide southern horizon
- **Clifton Beach** — easy access, good horizon
- **Cape Bruny** — outstanding darkness, worth the drive on active nights
- **Mount Wellington / kunanyi** — elevated, away from city glow

Aim to be at least 20–30 min from Hobart's city lights. Face south.

---

## Photography tips

- **ISO:** 800–3200
- **Aperture:** f/2.8 or wider
- **Shutter:** 10–20 seconds
- **Lens:** Wide angle (14–24mm)
- Use a **tripod** — even at Kp 5 a camera will capture what eyes cannot see
- Shoot during a **new moon** for the darkest sky

---

## Project structure

```
aurora-hobart/
└── index.html    ← the entire app (HTML + CSS + JS, self-contained)
```

No dependencies to install. No build step. Open `index.html` in any browser and it works.

**Libraries loaded via CDN (no install needed):**
- [Chart.js 4.4.1](https://www.chartjs.org/) — forecast chart
- [DM Sans + DM Serif Display](https://fonts.google.com/) — typography

---

## How to update the site

1. Edit `index.html` locally (or directly on GitHub)
2. Commit and push to the `main` branch
3. GitHub Pages picks up the change within ~1 minute

---

## How to run locally

Just open `index.html` in a browser. No server needed — all API calls go directly from your browser to NOAA and wttr.in.

> **Note:** If you open the file via `file://` on some browsers, CORS may block the API calls. If that happens, serve it with any local server, e.g.:
> ```bash
> npx serve .
> # or
> python3 -m http.server 8080
> ```

---

## Hosting

Hosted on **GitHub Pages** (free). The `main` branch root is the publish source.

Settings → Pages → Branch: `main` → Folder: `/ (root)`

---

## Known limitations

- Cloud cover from wttr.in can occasionally be unavailable — the app handles this gracefully and shows "N/A" without breaking the aurora data
- NOAA Kp data is published every 3 hours; the app shows the most recent confirmed reading, not a real-time magnetometer feed
- The forecast chart shows predicted Kp values which NOAA updates periodically — actual activity can differ significantly from forecasts during sudden solar events

---

## License

MIT — do whatever you like with it.

---

*Built with [NOAA Space Weather Prediction Center](https://www.swpc.noaa.gov) data · Hobart, Tasmania, Australia*
