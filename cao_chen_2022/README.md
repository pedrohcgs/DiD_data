# Cao & Chen (2022) — Grand Canal Abandonment and Rebellions

## Citation

Cao, Yiming, and Shuo Chen. 2022. "Rebel on the Canal: Disrupted Trade Access and Social Conflict in China, 1650–1911." *American Economic Review* 112(5): 1555–1590.

DOI: [10.1257/aer.20201283](https://doi.org/10.1257/aer.20201283)

## File

- `analysis_panel_core.rds` (1.0 MB, R serialized, xz-compressed; 150,650 county-year rows × 80 variables)

This is the R-built analysis panel from the corpus's verified replication. The original deposited package distributes a raw `Data/Raw/rawrebellion.dta` (1.7 MB, 7 variables) plus geographic and climate inputs that get merged into the final panel by the paper's Stata `Analysis/generalsetup.do` script; the corresponding R re-build is at `output/derived/analysis_panel_core.csv` (96 MB CSV in the corpus). This RDS preserves that built panel byte-equivalently at 1 MB after xz compression — far below GitHub's 100 MB single-file limit.

## Source

AEA replication package, openICPSR project 157781: <https://www.openicpsr.org/openicpsr/project/157781/version/V1/view>. The book ships the *built* analysis panel because the paper's headline regressions read this panel, not the raw inputs.

## Variable summary (analysis sample)

- `OBJECTID` — county unique identifier (526 counties in the panel)
- `year` — calendar year, 1650–1911 (262 years)
- `alongcanal` — 1 if county is along the Grand Canal route, 0 otherwise
- `reform` — 1 if year ≥ 1826 (post-Grand-Canal abandonment when grain shipments shifted to sea routes)
- **`interaction1`** = `alongcanal × reform` — main DiD treatment indicator
- `ashonset_cntypop1600` — rebellion onsets per 1600 county population (primary outcome)
- `ashattack_cntypop1600`, `ashretreat_cntypop1600` — alternative outcomes for direct attack vs. retreat episodes
- `ashprerebels` — pre-reform rebelliousness rate (for trend interactions in robustness specs)
- `provid`, `prefid`, `lev2id` — province / prefecture / Level-2 administrative unit IDs (for richer FE structures)
- `distance_canal`, `distance_coast`, `distance_huang`, `distance_yangtze`, `distance_courier` — distance covariates (used in Chapter 5-style robustness; not in headline)
- Climate / geographic / amount-shipped covariates (~50 additional variables used in alternative specifications)

## Setting (Ch 4 framing)

The Grand Canal — the artery transporting grain from southern China to Beijing for centuries — was abandoned around 1826 as the Yellow River silted up and sea-route shipping became cheaper. Cao and Chen identify counties along the canal route (treated) vs all other counties (control), and study rebellion onsets before vs after the 1826 abandonment.

This is a multi-period 2×T DiD on an *extreme* time-window: 175 years pre-treatment + 86 years post-treatment. The headline regression is `feols(ashonset_cntypop1600 ~ alongcanal × reform | OBJECTID + year, cluster = ~OBJECTID)` with no covariates in Model 1. Models 2–5 add pre-reform rebelliousness interactions, province-by-year FE, prefecture-specific trends, and the full control set.

## Headline replication target (Chapter 4)

Table 3 — DiD on rebellion-onset rate, 1650–1911 panel of 526 counties, county-clustered SE:

| Model | Description | β (interaction1) | SE | p-value |
|---|---|---|---|---|
| **1** | County + year FE (**no covariates**) | **+0.0380** | 0.0166 | 0.023 |
| 2 | + pre-reform rebelliousness × year | +0.0369 | 0.0172 | 0.034 |
| 3 | + province × year FE | +0.0453 | 0.0173 | 0.009 |
| 4 | + prefecture-specific linear trends | +0.0427 | 0.0172 | 0.013 |
| 5 | + full control set | +0.0340 | 0.0166 | 0.041 |

Reproduced exactly from the corpus source-run benchmark (R-translated; matches deposited Stata Table 3 to ≤ 1e-4 precision). Range across all 5 specifications: 0.034 to 0.045 (12% spread). **All significant at p ≤ 0.05.** No sign flips, no significance loss. Dropping covariates from the paper's preferred Model 5 to the canonical Model 1 changes the estimate from 0.034 to 0.038 — about 12%.

**Pedagogical hook**: this paper's 175-year pre-period makes parallel trends a substantive claim about world-historical processes, not a statistical assumption verified by pre-trend plots. The paper restricts its pre-trend test to 1776–1825 (the 50 years before the shock); that methodological choice is itself a Chapter 4 teaching moment about pre-trend windows on long panels.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2022 *AER* paper.
