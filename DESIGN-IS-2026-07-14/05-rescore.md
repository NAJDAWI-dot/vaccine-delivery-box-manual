# Post-redesign re-score (branch `design-overhaul`, 2026-07-15)

Same anchors as 02-scorecard.md, applied to the rebuilt page. Verified in headless Edge: light/dark × EN/AR × 1440px/390px screenshots, `dir=rtl` confirmed, zero horizontal overflow at 390px, no console errors, all three inline scripts pass `node --check`.

| # | Principle | Before | After | Why |
|---|-----------|:--:|:--:|---|
| 1 | Innovative | 2 | 2 | Same refreshed docs pattern with useful embedded helpers |
| 2 | Useful | 2 | 3 | Fake loader gone (content renders immediately); gate reframed as unlock convenience; single navigation |
| 3 | Aesthetic | 1 | 3 | One token system: 4px-grid spacing tokens, 1.2 modular rem type scale, tokenized status palette, radius/z-index scales, no orphan fonts |
| 4 | Understandable | 1 | 3 | "Cooler power level (PWM)", "Cooling-pack pre-chill timer", "Out of range", "Safe temperature reached" — EN and AR |
| 5 | Unobtrusive | 1 | 3 | No loader, no decorative dead code, no scroll reveals; chrome recedes behind content |
| 6 | Honest | 1 | 3 | Superlatives and "tamper-evident" removed; compliance table = "Design Target" with explicit student-prototype framing; badge ticks → target markers; EN/AR cooling description reconciled (copper heat pipes) |
| 7 | Long-lasting | 2 | 3 | Splash loader (the one dated marker) removed; restrained editorial-clinical language |
| 8 | Thorough | 1 | 2 | Dark status inks AA; native-button checklists with aria-pressed; real dir="rtl" + logical properties; associated calc labels; table `<td>` translated; favicon added. Remaining rough edges: search empty state is text-only, some SVG micro-labels stay English |
| 9 | Environment | 2 | 3 | Firebase deferred to unlock; 8 font faces (was 12); dark mode follows OS; no idle animation beyond gated status pulses |
| 10 | Little design | 1 | 3 | Dot-rail nav, loader, dead canvas/cursor/tilt/stars code (~370 lines), duplicate logo and duplicate progress indicator all removed; file 3,188 → ~2,900 lines with ~150 new lines of Arabic table translations |

**Total: 14/30 → 28/30.** No principle below 2. Verdict criteria for REFINE-grade health (≥20, no zeros) now met with margin.
