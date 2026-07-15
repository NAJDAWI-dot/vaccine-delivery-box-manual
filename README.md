# Enhanced Reliability Vaccine Delivery Box — User Manual

A self-contained, bilingual (English / العربية) web user manual for the
**Enhanced Reliability Vaccine Delivery Box — HTU MPEP 2026**.

## 🌐 Live site

Once GitHub Pages is enabled, the manual is available at:

> https://<your-username>.github.io/vaccine-delivery-box-manual/

## Features

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
