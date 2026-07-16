# Enhanced Reliability Vaccine Delivery Box — User Manual

A self-contained, bilingual (English / العربية) web user manual for the
**Enhanced Reliability Vaccine Delivery Box — HTU MPEP 2026**.

## 🌐 Live site

Once GitHub Pages is enabled, the manual is available at:

> https://<your-username>.github.io/vaccine-delivery-box-manual/

## Features

- **Command palette & tour** — Ctrl+K opens a command palette (jump to any section,
  toggle theme/language, print, start the guided tour); Driver.js gives first-time
  visitors a 30-second tour; glossary terms show tooltip definitions on hover;
  the sidebar search is typo-tolerant (Fuse.js) with a ranked results panel.
- **Pro monitoring dashboard** — ECharts temperature history with zoom/pan and a
  2–8°C safe band, a live gauge, an hourly out-of-range strip, excursion events,
  CSV export, and alerts (toast + beep + browser notification) on state changes.
- **Scroll-driven 3D** — the box rotates and opens its lid as you scroll past it
  (GSAP ScrollTrigger + Lenis smooth scrolling), and a topbar gear lets you pick
  the animated background style (aurora, network, snow, fireflies, off).
- **Animated main menu** — the site opens on a centered, fully animated menu
  (aurora background, staggered entrance) with three doors: The Device, User
  Manual, and Live Monitoring. The topbar brand button returns to it.
- **Three sections** — **The Device** (cover, interactive 3D model, description,
  diagrams, specs, photo gallery), **User Manual** (the full document with sidebar
  navigation and search), and **Live Monitoring** — a full dashboard behind the
  serial/NFC gate: stat tiles (current temp, cold-chain state, max since cold,
  last update), a temperature chart with a 2–8°C safe band and 1h/6h/24h ranges,
  min/avg/max, an excursion-event log, and CSV export.
- **Interactive 3D model** — a Three.js scene of the box (drag/zoom, open lid, exploded
  view, X-ray, click-a-part inspector) with a React control bar. It renders a built-in
  procedural model; drop a real scan/CAD export at `models/box.glb` and it loads instead.
  (Three.js and React load from CDNs, so the 3D viewer needs a network connection.)
- **Single-file app** — `index.html` is fully self-contained (inline CSS + JS); no build step.
- **Bilingual** — English and Arabic with true `dir="rtl"` right-to-left support,
  including translated table content.
- **Installable PWA** — `manifest.json` provides the install manifest; an inline
  service worker in `index.html` caches the page shell for offline reading.
- **Accessible** — WCAG-AA oriented design, keyboard navigation (including the
  interactive checklists), visible focus states, and `prefers-reduced-motion` support.
- **Interactive helpers** — troubleshooting wizard, PCM pre-chill timer, and
  battery runtime estimator.
- **Light / dark theme** — follows the OS preference, with a manual toggle.

## Files

| File            | Purpose                                            |
| --------------- | -------------------------------------------------- |
| `index.html`    | The complete site — manual, device, live tabs      |
| `manifest.json` | PWA manifest (name, icons, theme, start URL)       |
| `photos/`       | Optional device photos (`device-01.jpg` … `device-06.jpg`) shown in The Device tab; the gallery hides itself while the folder is empty |
| `models/box.glb` | Optional real 3D model; replaces the built-in procedural box in the 3D viewer |

## Local preview

Just open `index.html` in any modern browser. To exercise the PWA / service worker,
serve it over HTTP (service workers are blocked on `file://`):

```bash
# Python
py -m http.server 8000
# then visit http://localhost:8000/
```

## Deployment

Hosted on **GitHub Pages** from the `main` branch (root). Any push to `main`
publishes the updated manual automatically.
