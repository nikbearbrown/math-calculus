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
