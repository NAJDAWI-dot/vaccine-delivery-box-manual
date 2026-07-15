# Scorecard — 14/30

1. Good design is innovative — Score: 2/3
   Evidence: standard docs-site pattern refreshed with genuinely useful embedded helpers (wizard L2527, calculator L2453, timer L2426).
   Justification: a clear improvement on a known pattern, but no new pattern — not a 3; more than minor variation — not a 1.

2. Good design makes a product useful — Score: 2/3
   Evidence: search/nav/print serve the primary task; fake 3.5 s splash (L2884–2901) and theatrical auth gate (L587) add steps.
   Justification: primary task completes but adjacent surface adds steps — exactly the 2 anchor.

3. Good design is aesthetic — Score: 1/3
   Evidence: ~34 ad-hoc spacing values, ~23 font sizes incl. half-px, ~40 off-token hexes, 3 orphan font references (01-evidence §Visual).
   Justification: far more than 5 inconsistencies, but a visible token system exists — above 0, below 2.

4. Good design makes a product understandable — Score: 1/3
   Evidence: "Peltier PWM duty" L1662, "PCM" L1929, "Excursion" L1926, "cold-chain reached" L3040.
   Justification: 2–3+ unclear controls with domain jargon — the 1 anchor; primary actions are still identifiable, so not 0.

5. Good design is unobtrusive — Score: 1/3
   Evidence: splash loader with fake progress blocks content (L556–564, 2884–2901); pulsing dots; ~800 lines dead decorative JS.
   Justification: decoration actively competes with (delays) content — 1; chrome does not dominate once loaded, so not 0.

6. Good design is honest — Score: 1/3
   Evidence: 5+ inflations ("only cold box in its price range" L1583, "under any condition" L1133, "tamper-evident" ×3 on a public-read DB), certification-implying check badges (L1674–1710), client-side gate with serial '1' (L2994), EN/AR mechanism mismatch (L1967).
   Justification: well past "2+ inflations" — 1; no manipulative dark-pattern flow (forced continuity / hidden cost / fake scarcity), so not 0.

7. Good design is long-lasting — Score: 2/3
   Evidence: restrained docs aesthetic; the splash loader is the one dated marker.
   Justification: exactly one dated marker — the 2 anchor.

8. Good design is thorough down to the last detail — Score: 1/3
   Evidence: dark-mode status inks ≈2:1 (L42–45 vs L465–471); div-only checklists (L1038); no dir="rtl"; unassociated calc labels; missing disabled/empty/timer states.
   Justification: 2–3 states missing plus multiple rough details — 1; focus/hover/loading/print are present, so not 0.

9. Good design is environmentally friendly — Score: 2/3
   Evidence: motion gated, no idle animation of note, <500 KB total; but eager Firebase for a gated feature (L2978–2980), 12 font faces, dark mode ignores OS preference.
   Justification: fits the 2 anchor (<500 KB, motion gated); misses 3 on dark-mode honoring and wasted requests.

10. Good design is as little design as possible — Score: 1/3
    Evidence: duplicate dot-rail nav (L1855–1874), splash loader, dead decorative code, logo ×3.
    Justification: 3–5 removable elements — 1; content still dominates, so not 0.

**Total: 14/30** (tie-breaker and score-worst rules applied throughout).
