# Hoynes, Miller & Simon (2015) — EITC and Infant Health

## Citation

Hoynes, Hilary W., Doug L. Miller, and David Simon. 2015. "Income, the Earned Income Tax Credit, and Infant Health." *American Economic Journal: Economic Policy* 7(1): 172–211.

DOI: [10.1257/pol.20120179](https://doi.org/10.1257/pol.20120179)

## File

- `parametricdd9mon_4pl_ncits.rds` (24 MB, R serialized, xz-compressed)

This is the deposited Stata `.dta` file from the openICPSR archive, converted to RDS for size. The original 256 MB `.dta` exceeds GitHub's 100 MB single-file limit; the RDS preserves all 484,290 rows × 228 variables byte-equivalently after deserialization, and `as.data.frame(readRDS(...))` gives the same data frame as `haven::read_dta(...)` on the source.

## Source

AEA replication package, openICPSR project 114553: <https://www.openicpsr.org/openicpsr/project/114553/version/V1/view>. Source file `20120179_data/data/parametricdd9mon_4pl_ncits.dta` from the deposited archive. This mirror preserves the data byte-equivalently; the only transformation is the .dta → .rds container change.

## Variable summary (analysis sample)

- `stateres` — state of residence (FIPS code)
- `race`, `ethnic`, `marital`, `parvar`, `agevar`, `dmeducgrp` — categorical maternal characteristics used for cell construction
- `effective` — birth year, 1981–1999 in the raw data; the paper's main analysis uses 1991–1998
- `dbirwt` — birth weight in grams
- `lowbirth` — indicator for birth weight < 2500g (paper's primary outcome)
- `verylow` — indicator for birth weight < 1500g
- `preterm`, `bw2000`, `bw3000`, `bw3500`, `bw4000` — alternative birth-weight outcomes
- `treat1` — primary treatment indicator: 1 if mother has 2+ children at the time of birth (the cohort whose EITC eligibility was differentially expanded by OBRA-1993, phased in 1994–1996)
- `other`, `black`, `age2`, `age3`, `high`, `hispanic`, `hispanicmiss`, `racemiss` — demographic dummies used as controls
- `reform` — state-year welfare-reform indicator (PRWORA waivers; potential collider, dropped in conditional specifications)
- `cellnum` — analytic cell weight (count of births in each stateres × race × parvar × agevar cell)

## Setting (Ch 4 framing)

OBRA-1993 expanded the federal Earned Income Tax Credit substantially for tax filers with 2+ children relative to those with 1 child, phased in 1994–1996. HMS use a difference-in-differences design comparing mothers of 2+ children (treated) to mothers of 1 child (control) before vs after the expansion, with state and demographic-cell fixed effects. Outcome: birth weight (continuous) and low-birth-weight indicators (binary).

This is a multi-period 2×T DiD: single binary treatment dimension (2+ kids vs 1 kid), single phase-in window (1993 → 1996), multi-period event-study panel (pre 1991–1993, post 1994–1998).

## Headline replication target (Chapter 4)

Event-study coefficients on `lowbirth × 100` (low-birth-weight rate, percentage points), with state FE + cell weights, state-clustered SE:

| Event-time `e` | No-cov coefficient | With-cov coefficient | Robust? |
|---|---|---|---|
| -3 | +0.224 (0.111) | +0.079 (0.092) | Pre-trend shrinks ×3 with covariates |
| -2 | +0.144 (0.078) | +0.055 (0.076) | Pre-trend shrinks ×3 with covariates |
| -1 | 0 (baseline) | 0 (baseline) | — |
| 0 | **−0.160 (0.088)** | −0.135 (0.093) | 16% drift |
| 1 | **−0.273 (0.090)** | −0.238 (0.092) | 13% drift |
| 2 | **−0.364 (0.127)** | −0.323 (0.130) | 11% drift |
| 3 | **−0.550 (0.136)** | −0.489 (0.105) | 11% drift |
| 4 | **−0.668 (0.119)** | −0.608 (0.103) | 9% drift |

Post-period treatment effects robust to dropping covariates (9–16% drift across event-times, no sign flip, all retain significance). Pre-period coefficients shrink visibly with covariates — a useful pedagogical hook for the Chapter 4 → Chapter 5 bridge.

Paper Table 2 model 2 (66-covariate panel) headline ATT estimate: -0.354 (SE 0.074), p < 10⁻⁵, indicating low-birth-weight rate falls by 0.35 percentage points among treated mothers.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2015 *AEJ:EP* paper.
