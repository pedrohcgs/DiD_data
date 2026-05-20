# Moser & Voena (2012) — Compulsory Licensing TWEA

## Citation

Moser, Petra, and Alessandra Voena. 2012. "Compulsory Licensing: Evidence from the Trading with the Enemy Act." *American Economic Review* 102(1): 396–427.

DOI: [10.1257/aer.102.1.396](https://doi.org/10.1257/aer.102.1.396)

## File

- `chem_patents_maindataset.dta` (25 MB, Stata `.dta` format; 471,120 subclass-year rows × 23 variables)

## Source

AEA replication package, openICPSR project 112497: <https://www.openicpsr.org/openicpsr/project/112497/version/V1/view>. Source file `compulsory_licensing_replication/chem_patents_maindataset.dta`. This mirror preserves the file byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

- `uspto_class` — USPTO chemistry patent class (panel unit identifier in raw form)
- `class_id` — numeric class identifier (the FE unit used in regressions; 7,248 distinct classes)
- `grntyr` — patent grant year (the panel's time variable; 1875–1939 in the main sample; the corpus R replication renames to `grn` after read)
- `count_usa` — count of US-assignee patents granted in this subclass-year (primary outcome)
- `count_for`, `count_for_2`, `count_for_noger`, `count_noger` — count of foreign patents (controls)
- `count`, `count_france`, `count_germany` — total patents and per-country breakdowns
- `count_cl` — count of compulsorily licensed patents in this subclass (continuous treatment-intensity version)
- `licensed_class` — 1 if class had at least one compulsorily licensed patent (binary treatment proxy)
- `confiscated_class` — 1 if class had confiscated patents under TWEA
- `year_conf`, `year_conf_2`, `year_conf_itt` — year of confiscation (event-study covariates)
- **`treat`** — main binary treatment indicator: 1 if subclass had a German patent compulsorily licensed under TWEA (1918–1919), 0 otherwise
- `itt`, `count_cl_itt`, `count_cl_2`, `main`, `subcl` — alternative treatment definitions / panel-structure variables

## Setting (Ch 4 framing)

The Trading with the Enemy Act of 1917 allowed the US government to seize and compulsorily license German-owned patents during World War I. Moser and Voena exploit this WWI shock to study how compulsory licensing affects domestic innovation. Treated chemistry subclasses are those with at least one German patent licensed; control subclasses are those without. The panel spans 1875–1939 (42 pre-war years + 22 post-war years).

This is a multi-period 2×T DiD with a single binary shock period (TWEA 1918–1919). The paper's Table 2 column 3 spec is `xtreg count_usa treat td_*, fe i(class_id) robust cluster(class_id)` — class FE + year dummies + class-clustered SE — *with no covariates beyond the FE*. Columns 1, 2, 4–9 add controls progressively (`count_for_2`, `count_for`, `count_cl`, etc.) as robustness.

## Headline replication target (Chapter 4)

Table 2 — DiD on US chemistry patenting, 1876–1939 subclass-year panel of 7,248 classes, class-clustered SE:

**Column 3 (no-covariates baseline):**

`feols(count_usa ~ treat | class_id + grn, cluster = ~class_id)`

| Quantity | Replicated value | Notes |
|---|---|---|
| `treat` coefficient | **+0.257** (SE 0.038) | Reproduced from corpus's R replication of the deposited Stata source-run |
| N observations | 463,872 | (subset to 1876–1939) |
| N classes | 7,248 | |

Treated chemistry subclasses (those with German patents compulsorily licensed under TWEA) saw US domestic patenting **rise** by about 0.26 patents per class-year relative to non-licensed control classes after 1918. The shock unlocked innovation in technologies that had previously been monopolized by German firms.

The paper's preferred column 1 adds `count_for_2` as a control; columns 4–9 layer in additional regressors. Coefficient is stable across all columns at the displayed precision per the published Table 2.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2012 *AER* paper.
