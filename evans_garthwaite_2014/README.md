# Evans & Garthwaite (2014) — Higher EITC and Maternal Health

## Citation

Evans, William N., and Craig L. Garthwaite. 2014. "Giving Mom a Break: The Impact of Higher EITC Payments on Maternal Health." *American Economic Journal: Economic Policy* 6(2): 258–290.

DOI: [10.1257/pol.6.2.258](https://doi.org/10.1257/pol.6.2.258)

## File

- `BRFSS_Final_Data.dta` (44 MB, Stata `.dta` format; 273,224 woman-year observations × 51 variables, 1993–2001)

## Source

AEA replication package, openICPSR project 114860: <https://www.openicpsr.org/openicpsr/project/114860/version/V1/view>. Source file `AEJ_Data_Programs/brfss/BRFSS_Final_Data.dta`. This mirror preserves the file byte-for-byte; no transformations were applied.

## Variable summary (Table 3 analysis sample)

- `fips`, `month`, `day`, `year` — state (FIPS) and survey date
- `age`, `sex`, `marital`, `kids`, `educ`, `race4` — demographics used for sample restriction
- `srhealth`, `phys_poor`, `mental_poor` — Behavioral Risk Factor Surveillance System (BRFSS) self-reported health outcomes
- `employ`, `inlf`, `working`, `at_work` — labor-force outcomes
- **`twoplus_kids`** — 1 if mother has 2+ children (treated cohort; OBRA-1993 boosted EITC for them)
- **`eitc_expand`** — 1 if year ≥ 1996 (post-EITC-expansion period)
- **`dd_treatment`** = `twoplus_kids × eitc_expand` — main DiD treatment indicator
- `excel_vgood` — derived indicator: excellent/very good self-reported health
- `bad_mental_30`, `bad_phys_30` — binary indicators for any bad-health days in past 30
- `married`, `div_sep_wid`, `single`, `never_married` — marital-status splits
- `white_nh`, `black_nh`, `hispanic`, `other` — race/ethnicity
- `income`, `income1`–`income5`, `incomemiss` — income brackets

## Setting (Ch 4 framing)

OBRA-1993 expanded the federal Earned Income Tax Credit dramatically for filers with 2+ children relative to those with 1 child, phased in 1994–1996. Evans and Garthwaite use BRFSS data to compare maternal health and labor-force outcomes between 2+ child mothers (treated) and 1-child mothers (control), before vs after the expansion's post-1996 implementation. Sample restriction: women aged 21–40, low-education (`educ` ≤ 2), with at least one child, observed 1993–2001.

This is a multi-period 2×T DiD: single shock window (1994–1996 phase-in), binary treatment (2+ vs 1 kid), 9-year panel of repeated cross-sections. Evans-Garthwaite is the maternal-health counterpart to the Hoynes-Miller-Simon (2015) infant-health paper, exploiting the same OBRA-1993 EITC shock with a different outcome family.

## Headline replication target (Chapter 4, Table 3)

Sample restriction (per the paper's `make_brfss_table3_data` filter):
- `year ∈ [1993, 2001]`
- `sex ≠ 1` (female)
- `age ∈ [21, 40]`
- `kids ≠ 0` (mothers with children)
- `educ ≤ 2` (low-education sample)
- Non-missing `race4`, `marital`, `educ`, `fips ≤ 56`

→ 82,907 woman-year observations, 51 state clusters.

| Outcome | Spec | β (no-cov simple_dd) | SE | β (with-cov adjusted_dd) | SE | % drift |
|---|---|---|---|---|---|---|
| **`inlf`** (labor force participation) | LPM | **+0.0232** | 0.0079 | +0.0256 | 0.0079 | **+10%** ✓ |
| `excel_vgood` | LPM | +0.0095 | 0.0079 | +0.0135 | 0.0075 | +42% (both marginal) |
| `mental_poor` | negbin | -0.047 | 0.031 | -0.075 | 0.033 | +59% (sig flips: p=0.12 → 0.022) |
| `phys_poor` | negbin | +0.014 | 0.039 | +0.011 | 0.039 | -25% (both null) |

**The paper's headline finding is the labor-force-participation effect on mothers** (`inlf`): OBRA-1993 EITC raised LFP among 2+ kid mothers by about 2 percentage points relative to 1-kid mothers, robust to dropping the demographic covariate battery (10% drift). Other outcomes are more sensitive to controls — particularly `mental_poor`, where controls move the result from p=0.12 to p=0.022.

This outcome-level heterogeneity is itself a Chapter 4 → Chapter 5 teaching moment: for some health outcomes (`inlf`, `phys_poor`), the unconditional 2×T DiD identifies the same effect as the conditional version; for others (`mental_poor`, `excel_vgood`), conditioning materially shifts the result.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2014 *AEJ:EP* paper.
