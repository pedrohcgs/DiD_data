# DiTella & Schargrodsky (2004) — AMIA Attack and Police Reduce Crime

## Citation

Di Tella, Rafael, and Ernesto Schargrodsky. 2004. "Do Police Reduce Crime? Estimates Using the Allocation of Police Forces After a Terrorist Attack." *American Economic Review* 94(1): 115–133.

DOI: [10.1257/000282804322970733](https://doi.org/10.1257/000282804322970733)

## Files

- `MonthlyPanel.dta` (754 KB) — block-month panel of car thefts, April–December 1994; **the headline analysis file**
- `WeeklyPanel.dta` (2.7 MB) — block-week panel for higher-frequency robustness checks
- `CrimebyBlock.dta` (953 KB) — block-level cross-section with itemized crime details

## Source

Authors' original 2004 replication archive `march2004_ditella_data.zip` (deposited shortly after AER publication). This predates the AEA's mandatory openICPSR deposit policy (which started ~2005); the archive is publicly available via the authors' websites and Universidad Torcuato Di Tella / Universidad de San Andrés departmental pages. This mirror preserves the three `.dta` files byte-for-byte; no transformations were applied.

## Variable summary (`MonthlyPanel.dta`, the headline panel)

- `observ` — block unique identifier (876 distinct blocks)
- `barrio` — neighborhood (Belgrano, Once, V. Crespo — the three Buenos Aires neighborhoods with Jewish/Muslim institutions)
- `calle`, `altura` — street name and address number
- `institu1` — 1 if block has a Jewish/Muslim/embassy institution that received police protection after the AMIA bombing; 0 otherwise
- `institu3` — 1 if block is within 1 block of a protected institution (`institu3 - institu1` identifies one-block-away blocks)
- `distanci` — distance in blocks from the nearest protected institution (0 = same block; 1 = adjacent; 2 = two blocks away; …)
- `edpub`, `estserv`, `banco` — public-building, gas-station, bank indicators (covariates from secondary specifications)
- `totrob` — total car thefts on the block during the month (paper's primary outcome)
- `mes` — month: 4 (April) … 12 (December) of 1994, plus 72 and 73 (split-July codes for the pre-attack 1–17 and post-attack 18–31 half-months)

## Setting (Ch 4 framing)

On July 18, 1994, a terrorist car bomb destroyed the Asociación Mutual Israelita Argentina (AMIA, the Jewish community center) in Buenos Aires, killing 85 people. Within days, the Argentine government deployed federal police to protect every Jewish, Muslim, and Catholic institution and embassy in the city. DiTella and Schargrodsky exploit this near-immediate police deployment to identify the effect of police presence on car theft: blocks directly in front of a protected institution gained 24/7 police presence, blocks one block away gained intermittent presence, blocks two or more blocks away gained nothing. The pre-attack period (April–July 17, 1994) is the control window; the post-attack period (July 18–December 1994) is the treated window.

This is the cleanest possible short-panel 2×T DiD: single binary shock date (July 18, 1994), three nested binary treatment-intensity indicators, 9-month panel with block and month fixed effects, no covariates in the paper's headline spec.

## Headline replication target (Chapter 4, Table 3.C)

`areg totrob inst1p inst3_1p cuad2p month*, absorb(observ) robust`

| Coefficient | Paper value | Replicated | Match |
|---|---|---|---|
| `inst1p` (same-block × post, treated) | **−0.0808** (SE 0.0229) | **−0.0808** (SE 0.0229) | exact |
| `inst3_1p` (one-block × post) | **−0.0140** (SE 0.0145) | **−0.0140** (SE 0.0145) | exact |
| `cuad2p` (two-block × post) | −0.0022 (SE 0.0123) | −0.0022 (SE 0.0123) | exact |

N = 7,884 block-month observations across 876 blocks and 9 months (April–December 1994, excluding the half-month transition codes mes ∈ {72, 73}). Heteroskedasticity-robust standard errors. Block fixed effects (`absorb(observ)`); month fixed effects (`month*` dummies).

Headline finding: blocks directly in front of a protected institution saw 0.081 fewer car thefts per month after the AMIA bombing relative to far-away blocks — about 75% of the pre-attack mean. One-block-away blocks saw no spillover effect (p = 0.34); two-block-away blocks saw no spillover (p = 0.86). The clean spatial decay validates the single-block treatment-intensity interpretation.

**Why this is a perfect Ch 4 application**: the paper's headline spec is *already* no-covariates (just block FE + month FE + the three nested treatment indicators). The same `inst1p` coefficient appears in Table 3.A (alone), 3.B (with `inst3_1p`), and 3.C (with both spillover indicators), with magnitude stable in the −0.0775 to −0.0808 range across columns — perfect robustness across "controls" by construction. Pedagogically the cleanest single-shock binary DiD in the corpus.

## License note

Replication data publicly distributed by the authors for research and teaching, predating the AEA's openICPSR deposit policy. This mirror adds no additional restrictions. When citing, cite the original 2004 *AER* paper.
