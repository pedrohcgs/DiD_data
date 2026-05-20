# Zaklan (2023) — Coase and Cap-and-Trade

## Citation

Zaklan, Aleksandar. 2023. "Coase and Cap-and-Trade: Evidence on the Independence Property from the European Carbon Market." *American Economic Journal: Economic Policy* 15(2): 526–558.

DOI: [10.1257/pol.20200649](https://doi.org/10.1257/pol.20200649)

## Files

- `estimation_data_firm_level.dta` (1.3 MB, 3,465 firm-year observations × 59 variables)
- `estimation_data_installation_level.dta` (2.6 MB, finer installation-level panel for Table 7 robustness)

## Source

AEA replication package, openICPSR project 152861: <https://www.openicpsr.org/openicpsr/project/152861/version/V1/view>. Source files `replication_package/data/estimation_data_firm_level.dta` and `estimation_data_installation_level.dta`. This mirror preserves the files byte-for-byte; no transformations were applied. Stata encoding is `latin1` (must pass `encoding="latin1"` to `haven::read_dta`).

## Variable summary (firm-level panel)

- `firm_num` — anonymized firm identifier (panel unit)
- `account_holder`, `registry_code` — firm metadata
- `year` — 2009–2017 (4 pre-treatment years + 5 post-treatment years)
- `treated` — 1 if firm subject to the Phase III auction-allocation regime change, 0 if always-free-allocation
- `post_treatment` — 1 if year ≥ 2013 (post-Phase-III-start)
- **`interact_post_treatment_treated`** = `treated × post_treatment` — main DiD treatment indicator (binary 0/1, single shock 2013)
- `post_treatment_2009` … `post_treatment_2017` — year-by-year event-time dummies
- `inter_post_treat_treated_2009` … `inter_post_treat_treated_2017` — event-time × treated interactions for event-study leads/lags
- **`ln_emissions`** — log emissions per firm-year (primary outcome)
- `RE` (renewable energy share), `final_electricity_consumption`, `GDP`, `net_exports`, `Coal_EUR_MWh`, `Gas_EUR_MWh`, `EUA_price` — country-year covariates (added in alternative specifications)

## Setting (Ch 4 framing)

The European Union Emissions Trading System (EU ETS) Phase III (2013–2020) introduced auctioning of CO₂ allowances for power-generation firms while continuing free allocation for energy-intensive trade-exposed manufacturing. Zaklan tests the Coase independence property: if firms can freely trade allowances, the *method* of initial allocation (free vs auction) should not affect emissions outcomes.

This is a multi-period 2×T DiD: single binary shock (Phase III start, 2013), binary treatment (power firms vs trade-exposed industry firms), 9-year firm panel. Table 3 column 1 — the canonical no-covariates spec — runs `feols(ln_emissions ~ interact_post_treatment_treated | firm_num + year, cluster = ~firm_num)`. Columns 2–3 add country-year fixed effects and country-year-global covariates as robustness.

## Headline replication target (Chapter 4, Table 3 Spec 1)

`feols(ln_emissions ~ interact_post_treatment_treated | firm_num + year, cluster = ~firm_num)`

| Quantity | Replicated value |
|---|---|
| `interact_post_treatment_treated` coefficient | **−0.0953** (SE 0.0404) |
| N observations | 3,465 |
| N firm clusters | (firm-level panel) |

Auctioning treated firms reduced log emissions by about 10% relative to free-allocation control firms after 2013 — a *rejection* of the Coase independence property in practice. The paper's preferred specifications (columns 2–3) add country-year fixed effects (β = -0.099) and a country-year global-control battery (β = -0.094), both within rounding of the no-covariates baseline. **Coefficient is stable across all 3 specs at ~10% drift.**

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2023 *AEJ:EP* paper.
