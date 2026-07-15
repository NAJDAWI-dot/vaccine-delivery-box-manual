# Evidence (consolidated from 3 subagent reports)

Line numbers reference `index.html` at commit 2f4fa28 unless noted.

## Structural
- ~81 static interactive elements: 19 anchors (skip link L553 + 18 nav items L640–672), 12 buttons, 21 inputs, 18 clickable section dots (L1856–1873), 11 div-based checklist toggles (L1030–1039). Plus runtime-generated wizard/resume-banner buttons (L2540–2545, L2863).
- Content nesting depth ≈ 6 levels; sane.
- Repeated patterns: **two full navigations for the same 18 sections** (sidebar L615–677 vs dot rail L1855–1874); HTU logo `<img>` 3× same URL (L630, 691, 1844); two separate close-button implementations (L582, L2863).
- 18 sections ↔ 18 nav items, 1:1, no orphans.
- Extras inventory: splash loader (L556–564), cursor glow (L567, JS L2913–2935), particle canvas (L569, JS L2582–2790), shooting stars (L2950), 3D tilt (L2929) — **all decorative JS is dead code, early-`return`ed** (L2578, 2910, 2928, 2948); reading progress, resume banner, offline banner, search (Ctrl+K), lang/dark/font controls, PCM timer (L1042), battery calculator (L1649), troubleshooting wizard (L1548), print button, NFC/serial-gated live monitoring (L576–612, module L2977–3186).
- i18n: `data-i18n` dictionary (63 attrs, complete EN/AR, L1921–1948) + free-text `arTextMap` (~283 pairs, L1954–2244) applied to a selector list (L2248) that **excludes `#main td`, `.spec-val`, the cover H1, and SVG text** — table data and embedded-graphic labels stay English in Arabic mode.
- Service worker IS registered (inline Blob, L2846–2851, caches only the HTML shell). README wrongly attributes offline to `manifest.json` and calls the troubleshooting wizard a "setup wizard".

## Visual / thoroughness / accessibility (INFERRED from source)
- Spacing: ~34 distinct px values (1–90), loosely 4px-ish but ad-hoc (5, 7, 9, 11, 13, 22, 26, 34, 84, 90 present); no spacing tokens.
- Type: ~23 distinct font sizes incl. half-px (11.5 L141, 13.5 L135, 14.5 L199, 15.5 L167); no size tokens. Fonts loaded: Figtree, Noto Sans, Noto Sans Mono (12 faces). **Orphan references never loaded:** 'DM Serif Display' (L631), 'DM Mono' (L1503, 2468), 'DM Sans' (L1023).
- Color: ~35 `:root` tokens but ~40+ off-token hardcoded hexes duplicating the status palette (L200–243, 322, 345, 424, 499–502) + inline style attrs (L830, 1308, 1503, 1742–1745) + JS-injected (L2441, 2466–2468) + ~20 rgba white-alpha variants.
- Contrast failures: dark mode never overrides `--green/--amber/--red/--purple` inks (L42–45 vs overrides L465–471) → **≈2:1 on dark status panels** (`.led-status` L240–243, `.callout-label` L201–210). Light mode `--faint #64748B` on `--bg #F0FDFA` ≈ 4.3:1 for small text. Sidebar `.nav-label` rgba(255,255,255,.55) ≈ 4.4:1; placeholder ≈ 3.7:1.
- Dark mode is class-based opt-in only; ignores `prefers-color-scheme`. Hardcoded light-only leftovers: `.qr-panel.ye-p #FFFBEB` (L276), borders `#A5E8F2` (L206, 317), inline dark-ink list items (L1742–1745).
- States: focus-visible ✓ (L81), hover ✓, print ✓ (L536–543); disabled only on NFC button (L386); no timer error state; search empty state is bare text (L2397).
- Reduced motion: well gated overall; ungated smooth `scrollIntoView` in JS (L2395, 2405), timer-bar transition (L324).
- A11y gaps: checklist toggles are plain `<div onclick>` — no keyboard/AT access (L1038); calculator labels not associated (L1652–1663); toggles lack `aria-pressed/expanded`; `dir="rtl"` never set — RTL via `body.ar` CSS class only (L484, JS L2311); skip-link not RTL-mirrored (L75); h2→h4 heading skips in illus panels (L712).

## Copy honesty / weight
- Inflations: "the only cold box in its price range" (L1583); "ensuring 2°C–8°C under any condition" (L1133); "tamper-evident record" 3× (L1236, 1460, 1975) while the Firebase RTDB is world-readable (`box/.read=true`, website-widget.html L4); compliance table rows read as achieved compliance (L1717–1723) under green check-circle badges (L1674–1710); "Designed to satisfy WHO, JFDA, UNICEF, EU Ecodesign, NSPE, IEEE… simultaneously" (L1678). Honest counter-example kept: DS18B20 ±0.5°C is the real datasheet spec (L1625).
- Auth gate: "Access to live monitoring is restricted. Verify your access to continue." (L587) — but `VALID_SERIALS = ['1']` (L2994) and hardcoded NFC UIDs (L2995–2998), all client-side, and the gated data is publicly readable anyway. `?nfc=<uid>` URL auto-unlock with cosmetic URL strip (L3158–3170). Security theater.
- EN/AR content mismatch: English "aluminum cold plates (direct conduction)" vs Arabic "copper heat pipes" (L1967).
- Jargon: "Peltier PWM duty" (L1662), "PCM Pre-conditioning" (L1929), LED "Excursion" (L1926), "cold-chain reached" (L3040).
- Weight: index.html 264 KB; ~538 lines CSS, ~1,309 lines JS. ~7 external endpoints on load incl. **eager Firebase SDK imports (L2978–2980) for a feature behind an unlock gate**; Chart.js correctly lazy (L3007–3014). Fake staged-progress splash loader, up to 3.5 s (L2884–2901). Idle animation: 1–2 gated pulsing dots only.
- No dark patterns found.
