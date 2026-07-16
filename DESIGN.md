# Design

Visual system of the VDB user manual (`index.html`, single-file, no build). All tokens live in the `:root` block; dark theme re-states every token under `html[data-theme="dark"]`.

## Theme

Clinical field-document register with editorial serif headings. Light by default, follows `prefers-color-scheme`, manual toggle persisted as `localStorage.theme`. Both themes must pass WCAG AA — status inks have per-theme values.

## Color

- **Surfaces:** `--bg #F4F8F9` (cyan-tinted off-white), `--surface #FFF`, `--surface-2/-3` tinted panels. Dark: `#0B1520` / `#101E2C` family.
- **Ink:** `--text #0D2330`, `--muted #3A5766` (7.5:1 on white), `--faint #4E6B7A` (small labels, ≥5:1).
- **Brand:** `--brand #0F2A4A` HTU navy (sidebar, cover, table heads), `--primary #0E7490` cyan-700 (single interactive accent), `--brand-accent #7BE3F0` for accents on navy.
- **Status:** four triplets (`--green/-bg/-bd`, amber, red, purple) — ink/background/border, re-lit in dark mode. Never hardcode status hexes; use the tokens.
- On-navy text uses `--on-brand-muted` (.78 white) minimum; never below .66 alpha.

## Typography

- **Display:** Newsreader (Google Fonts, opsz 6..72, wght 600/700 + italic 600) — headings, section numerals, cover H1, live temperature. Arabic falls back to Noto Sans automatically.
- **Body/UI:** Noto Sans 400/600/700 (covers Arabic).
- **Data:** Noto Sans Mono 400/500.
- Scale: `--fs-xs` 12 → `--fs-3xl` 34 (1.2 modular, rem-based). The A−/A+ controls set the root font-size (14/16/18px); anything that must scale uses rem tokens.
- Section numerals: italic Newsreader in `--primary-2`, baseline-aligned with the h2.

## Spacing & radius

- `--sp-1..8` = 4/8/12/16/24/32/48/64 (4px grid). Micro-gaps may use raw on-grid values.
- Radii: `--r-sm 6`, `--r-md 10`, `--r-lg 14`, `--r-pill`.
- Z-index scale: `--z-nav 100 → --z-chrome 200 → --z-banner 300 → --z-modal 900`.

## Shell

Fixed 56px navy topbar with three tabs (`role=tablist`): **User Manual** (`#main` + sidebar), **The Device** (`#view-device`), **Live Monitoring** (`#view-live`). `switchView()` sets `body[data-view]`; CSS shows/hides the views, manual-only chrome (sidebar, print button, reading progress, resume banner) hides on the other tabs. Active tab persists in `sessionStorage`. The Device tab's photo gallery reads `photos/device-0N.jpg` and hides itself while empty.

## Components

- **Callouts:** full 1px status border + tinted bg + SVG icon + uppercase label. No side-stripe accents anywhere (banned).
- **Illustration panels:** navy "figure plates" (`.illus-panel`, `.danger`, `.night`) stay dark in both themes; `.light` plates stay light in both themes — embedded SVG colors are fixed to their plate.
- **Checklists:** `<button class="cb" aria-pressed>` — keyboard/AT operable.
- **Nav:** single sidebar navigation; active edge indicator uses `border-inline-start`.

## RTL

True `dir="rtl"` set on `<html>` by the language toggle (and pre-paint for saved Arabic). All layout CSS uses logical properties (`inset-inline-*`, `margin-inline-*`, `border-inline-start`, `text-align:start`); no hand-mirrored overrides. `body.ar` only zeroes letter-spacing on Latin-tracked labels.

## Animate UI-style layer

`motion` (motion.dev, the engine behind animate-ui.com, via importmap/jsdelivr) powers a site-wide interaction layer, recreating Animate UI's signature components without React/Tailwind: springy sliding tab indicator (`#tab-ind`, replaces the CSS underline when active), ripple press feedback on every control, counting numbers on dashboard values (`window.motionCount`), typewriter menu subtitle, rising bubble backgrounds on menu + cover, and cursor-spotlight + magnetic spring tilt on menu cards/dashboard tiles. The whole module is skipped under reduced-motion, and if the CDN fails the CSS motion pack still covers the site.

## Motion

Reduced-motion honored on every animation — the full motion pack lives behind `prefers-reduced-motion: no-preference`. With motion allowed: view-enter transitions, staggered cover masthead entrance, scroll reveals (`.rv`/`.rv-in`, JS-added so content is always visible without JS), hover lifts/zooms, tab underline slide, LED pulses. With reduce: everything static, 3D auto-rotate and idle float off.

## 3D viewer (Device tab)

Three.js (v0.170 via importmap/jsdelivr) renders a procedural box — shell, hinged lid with PCM pockets, vials, LED panel, RFID reader, vents, latches, cooling wall — with OrbitControls, exploded view, X-ray, raycast part-picking, and a soft shadow. A React 18 control bar (esm.sh + htm, no build step) drives lid/explode/rotate/X-ray and shows the picked part's name/description in EN/AR (`window.box3dRefresh(lang)` re-renders on language switch). `models/box.glb`, if present, replaces the procedural model via GLTFLoader. WebGL/CDN failure hides the viewer section gracefully.

## Honesty rules (copy)

Compliance items are worded as design targets ("designed with reference to"), never certifications; badge markers are neutral targets, not checkmarks. No unbacked superlatives. The live-monitor gate is described as an unlock convenience, not security.
