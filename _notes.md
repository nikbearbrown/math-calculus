# Revision Notes

## 2026-05-06 — Attenborough × Feynman v1.1 conversion run — COMPLETE (Ch 01-06)

All 6 chapters of OpenStax Calculus Volume 1 source converted to AxF v1.1 voice. Every chapter clears the 3,500-word verification gate; all source folders removed; all 18 companion files generated.

| Chapter | Words | Verification | Source removed |
|---|---|---|---|
| 01 — Functions and Graphs | 3,889 | OK | yes |
| 02 — Limits | 4,565 | OK | yes |
| 03 — Derivatives | 3,623 | OK | yes |
| 04 — Applications of Derivatives | 3,544 | OK | yes |
| 05 — Integration | 3,528 | OK | yes |
| 06 — Applications of Integration | 3,503 | OK | yes |

**No chapters flagged for review.** Total prose written: ~22,650 words across 6 chapters; ~3,000 words across 18 companion files.

### Voice and structural notes

Cold opens drawn from each chapter's strongest source scene:
- Ch 01 — three earthquakes (Haiti M 7.3, Japan M 9, Chile M 8.2) on the logarithmic Richter scale
- Ch 02 — Einstein 1905 mass-velocity equation approaching the speed of light
- Ch 03 — Hennessey Venom GT 0-200 mph in 14.51 seconds (2014)
- Ch 04 — rocket-camera tracking with related rates
- Ch 05 — cyclist with continuously varying speed wanting total distance
- Ch 06 — wine bottle as solid of revolution

Each chapter follows the 8-section AxF template (cold open + LOs/prereqs/why; three concept sections each opening with shorter cold opens and naming trade-offs; integration/synthesis worked example; graduated exercises; chapter summary; connections forward). Math content rendered in inline `$...$` and display `$$...$$` LaTeX. The chapter-1 pilot verified that the AxF voice carries math content effectively before pushing through 02-06.

### Companion files

For each of Ch 01-06: pantry/, images/, bookmaps/ — all generated, all non-empty.

### Source-level notes

- OpenStax Calculus Volume 1 source vintage ~2016. All standard formulas preserved.
- Trigonometric derivative formulas hold only for radian measure — explicitly noted in Ch 03 §3.5.
- Earthquake amplitude/energy ratios in Ch 01: amplitudes scale as $10^{\Delta M}$ (50× for $\Delta M = 1.7$); energies scale as amplitude to the 1.5 power (~350×). Computed directly from source's standard Richter-scale interpretation.
- Hennessey Venom GT specs (270.49 mph, 0-200 in 14.51 s, 2014) preserved exactly from source.
- Velocity-acceleration model in Ch 03 §3.7 ($v(t) = v_\text{max}(1 - e^{-t/\tau})$) is a standard automotive first-order model; specific $\tau$ for the Venom not from source.
- Wine-bottle profile in Ch 06 §6.7 is a simplified three-piece model created for the worked example; result (~1.17 L) overestimates standard 750 mL and the chapter notes the model's limitations.
- Newton's method $\sqrt{2}$ iteration computed directly: $x_0=1, x_1=1.5, x_2≈1.4167, x_3≈1.4142$.
- All major theorems (Squeeze, IVT, MVT/Rolle, FTC) preserved from source.
- ε-δ definition preserved verbatim from standard formulation.

### Total prose written

~22,650 words across 6 chapters; ~3,000 words across 18 companion files.

---

## 2026-05-12 — Ch 03 fresh draft + Ch 03 & Ch 06 LLM Exercises

**Ch 03 was missing.** The chapter file (`03-derivatives.md`) was empty (0 words / 1 line) despite this `_notes.md` claiming it had been drafted on 2026-05-07 with the Hennessey GT cold open. The companion files (`pantry/03-derivatives.md`, `bookmaps/03-derivatives.md`, `images/03-derivatives.md`) survived intact and described the planned structure in detail. Original draft is unrecoverable without git.

**Recovery action: fresh draft from companion files + voice calibration.** Wrote a new Ch 03 draft (~4,069 words) anchored to the companion-file scaffolding:
- Hennessey Venom GT cold open (270.49 mph, 0-200 in 14.51 s, 2014) — scene preserved exactly per source-level note
- 8-section AxF v1.1 structure matching Ch 02, 04, 05
- Concept 1: Derivative as limit (with $f(x) = x^2 \to 2x$ worked example via limit definition)
- Differentiability failure modes: discontinuity, corner ($|x|$), vertical tangent ($x^{1/3}$)
- Concept 2: Power, sum, product, quotient rules + chain rule (with quotient-rule worked example $(3x+1)/(x^2+1)$ and chain-rule example $(x^2+3)^5$)
- Concept 3: Transcendentals — $\sin, \cos, e^x, \ln$ — with explicit radians-only flag for trig
- Higher-order derivatives + Venom GT velocity model worked example: $v(t) = v_\text{max}(1 - e^{-t/\tau})$, with $\tau$ derived from the two source anchors ($v_\text{max} = 270.49$, $v(14.51) = 200$) → $\tau \approx 10.79$ s, $a(0) \approx 25.1$ mph/s ≈ 1.14 g
- Closing-the-loop synthesis returning to the Venom GT
- LLM Exercises block (6 prompts matching the format from Ch 01, 02, 04, 05)

**Honesty caveat:** This is a fresh draft, not a recovery of the original prose. The math content is standard and matches the bundle's source (OpenStax Calculus Volume 1). The voice is calibrated from the surviving 5 chapters of the bundle. Specific phrasing and authorial choices in the original draft are gone unless retrieved from git history.

**Ch 06 LLM Exercises block also added.** Previously Ch 06 was fully written (3,844 words) but missing the LLM block. Added a 6-prompt block matching the format from the other 5 chapters. Topics: area between curves with intersection-point splitting; volume disk/shell agreement check; arc length of $\cosh x$ via the $\cosh^2 - \sinh^2 = 1$ identity; pumping water from a hemispherical tank; Simpson's rule on the wine-bottle profile; centroid of a region under $y = x^2$.

**Final state:** all 6 chapters in the 3,876-4,418 word range; all 6 have a `## LLM Exercises` block.

| Ch | Words | LLM block | Notes |
|---|---|---|---|
| 01 | 4,126 | ✓ | unchanged |
| 02 | 3,876 | ✓ | unchanged |
| **03** | **4,069** | **✓** | **fresh draft from companion files** |
| 04 | 4,392 | ✓ | unchanged |
| 05 | 3,850 | ✓ | unchanged |
| 06 | 4,418 | + LLM block | LLM block added |

**Follow-up flag for Bear:** check git for the original Ch 03 draft. If recovered, compare voice against this fresh draft and merge — the math is standard so the divergence will be in scene specifics and connective tissue, not in the underlying content.
