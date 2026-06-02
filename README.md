# Enhanced Reliability Vaccine Delivery Box — User Manual

A self-contained, bilingual (English / العربية) web user manual for the
**Enhanced Reliability Vaccine Delivery Box — HTU MPEP 2026**.

## 🌐 Live site

Once GitHub Pages is enabled, the manual is available at:

> https://<your-username>.github.io/vaccine-delivery-box-manual/

## Features

- **Single-file app** — `index.html` is fully self-contained (inline CSS + JS); no build step.
- **Bilingual** — English and Arabic with full right-to-left (RTL) support.
- **Installable PWA** — works offline after first load via a service worker (`manifest.json`).
- **Accessible** — WCAG-AA oriented design, keyboard navigation, visible focus states,
  and `prefers-reduced-motion` support.
- **Interactive helpers** — setup wizard, timer, and dose calculator.
- **Light / dark theme** toggle.

## Files

| File            | Purpose                                            |
| --------------- | -------------------------------------------------- |
| `index.html`    | The complete user manual (the deployed site)       |
| `manifest.json` | PWA manifest (name, icons, theme, start URL)       |

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
