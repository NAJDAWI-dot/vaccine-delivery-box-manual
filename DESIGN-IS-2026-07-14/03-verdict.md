# Verdict: REDESIGN

The manual scores 14/30 — below the 20-point REFINE threshold — because its sound information architecture and useful helpers are wrapped in an undisciplined visual system, overstated claims, and unfinished details, so the design must be rebuilt from tokens and honest copy up rather than patched.

## Highest-leverage moves

1. **#3 Aesthetic — rebuild the design system on real tokens.** One 4/8 px spacing scale, one modular integer type scale (~8 steps replacing 23 sizes), one tokenized status palette with light+dark variants replacing ~40 raw hexes, a radius scale, and removal of orphan font references. Evidence: 01-evidence §Visual; L135–167, L200–243, L499–502, L631/1023/1503/2468.
2. **#6 Honest — rewrite every unbacked claim.** "Only cold box in its price range" (L1583), "under any condition" (L1133), "tamper-evident" ×3 (L1236/1460/1975) → design-intent wording; compliance table (L1717–1723) and check badges (L1674–1710) → "designed with reference to / design target"; reframe the live-monitor gate copy (L587) as convenience unlock, not security; fix the EN/AR cold-plates vs heat-pipes mismatch (L1967).
3. **#8 Thorough — finish the details.** Override dark-mode status inks (≈2:1 → AA), make checklists keyboard/AT-accessible, set `dir="rtl"` and translate table `<td>` content, associate calculator labels, honor `prefers-color-scheme`, add missing disabled/empty states.
4. **#10/#5 Less design — delete what doesn't serve the task.** Splash loader, ~800 lines of dead decorative JS, duplicate dot-rail nav, duplicate logo loads; defer Firebase import until unlock.
5. **#4 Understandable — plain language on every control.** "Peltier PWM duty" → "Cooler power level (%)", "PCM Pre-conditioning" → "Cooling-pack pre-chill (PCM)", "Excursion" → "Out of range", "cold-chain reached" → "Safe temperature reached" (EN + AR).
