# Juhász (2018) — Temporary Protection and Technology Adoption: Napoleonic Blockade

## Citation

Juhász, Réka. 2018. "Temporary Protection and Technology Adoption: Evidence from the Napoleonic Blockade." *American Economic Review* 108(11): 3339–3376.

DOI: [10.1257/aer.20151730](https://doi.org/10.1257/aer.20151730)

## File

- `department_shortrun_panel.dta` (125 KB, Stata `.dta` format)

## Source

AEA replication package, archived under publication identifier `aer20151730` (with `_update1` data refresh). This mirror preserves the analysis file (`replication_files_20151730_update1/department_shortrun_panel.dta`) byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

- `department` — French department identifier (88 departments, post-1790 administrative boundaries)
- `year` — 1803 (pre-blockade) and 1812 (mid-blockade) — a two-period panel by construction
- `lnshortestLo` — log effective distance from each department to London (continuous treatment intensity; closer = less protection)
- `thspindles` — thousands of mechanized cotton-spinning spindles per capita (outcome)
- `generalite` — pre-revolution administrative super-unit identifier (40 generalités) used for two-way clustering
- Robustness controls: streamflow, coal endowment, market-access proxies, university density, literacy

## Headline replication target (Chapter 3 — continuous treatment preview)

From the paper's Table 1 column 1 (baseline, no controls, department-clustered SE):

| Quantity | Value |
|---|---|
| **DiD coefficient on `lnshortestLo`** | **+33.47 spindles per capita** |
| **SE (department-clustered)** | **9.80** |
| N (department-year) | 176 |
| Departments | 88 |
| Generalités | 40 |

Interpretation: a one-log-unit increase in distance to London is associated with ≈ 33 additional thousand-spindles-per-capita in 1812 relative to 1803.

Used in Chapter 3 as the continuous-treatment 2×2 preview (the chapter flags that the full continuous-DiD theory is developed in Chapter 16 / continuous-DiD chapter, where Juhász is the textbook two-period setup example).

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2018 *AER* paper.
