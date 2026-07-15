# Handoff

````
/make-plan Redesign the Vaccine Delivery Box user manual (index.html, single-file bilingual EN/AR PWA). Current design failed audit at 14/30 with critical gaps in principles #3 aesthetic, #4 understandable, #5 unobtrusive, #6 honest, #8 thorough, #10 as-little-design.

Verdict paragraph (quoted from 03-verdict.md):
> The manual scores 14/30 — below the 20-point REFINE threshold — because its sound information architecture and useful helpers are wrapped in an undisciplined visual system, overstated claims, and unfinished details, so the design must be rebuilt from tokens and honest copy up rather than patched.

Why redesign and not refine: total is 14/30, well below the 20-point threshold, with six principles at 1/3.

Preserve from current design:
- HTU navy #0F2A4A + cyan accent brand identity (index.html:38, :32)
- The 18-section IA and all content; 1:1 sidebar nav (index.html:615–677)
- Helpers: search Ctrl+K (617), troubleshooting wizard (1548), battery calculator (1649), PCM timer (1042), checklists, print (1853)
- Focus-visible discipline (81), skip link (553), print stylesheet (536), service worker (2846), manifest, resume/offline banners
- Single-file no-build architecture (GitHub Pages)

Discard:
- Splash loader with fake staged progress (556–564, 2884–2901). Caused failure on #5, #7.
- Dead decorative JS: canvas particles (2582–2790), cursor glow (2913), tilt (2929), stars (2950). Caused failure on #5, #9, #10.
- Duplicate bottom dot-rail nav (1855–1874). Caused failure on #10.
- Off-token hardcoded colors / half-px type / ad-hoc spacing / orphan fonts. Caused failure on #3.
- "Restricted access" security-theater framing of live monitoring (587, 2994). Caused failure on #6.

Top moves from the audit (verbatim): see 03-verdict.md moves 1–5, inlined in the plan.

Redesign principles in priority order:
1. #6 Honest — every claim maps to what a student prototype actually does; compliance = design targets.
2. #3 Aesthetic — one token system: 4/8px spacing, modular integer type scale, single status palette valid in light and dark.
3. #8 Thorough — AA contrast in both themes, keyboard access to every control, real dir switching, full-table translation.
4. #10 Little design — delete loader, dead code, duplicate nav; defer Firebase until unlock.
5. #4 Understandable — plain-language control labels in EN and AR.

Deliverables: rebuilt index.html (same single-file architecture), corrected README, states checklist complete, migration = direct replacement on a PR branch (main auto-deploys).
````

**Status: executed in this same session** — plan approved by user 2026-07-14 (full overhaul, refined-clinical + bolder-editorial direction); implementation on branch `design-overhaul`.
