# Charoenwong, Kwan & Umar (2019) — Dodd-Frank and Investment-Adviser Regulation

## Citation

Charoenwong, Ben, Alan Kwan, and Tarik Umar. 2019. "Does Regulatory Jurisdiction Affect the Quality of Investment-Adviser Regulation?" *American Economic Review* 109(10): 3681–3712.

DOI: [10.1257/aer.20180412](https://doi.org/10.1257/aer.20180412)

## Files

- `firm_panel.fst` (1.1 MB, 60,998 firm-year observations × 11 variables)
- `individual_panel.fst` (17 MB, 569,999 individual-year observations × 12 variables)

Both files are stored in [Fast Serialization Format](https://www.fstpackage.org/) (`.fst`); load with `fst::read_fst(path)` which returns a data.frame.

## Source

AEA replication package, openICPSR project 116210: <https://www.openicpsr.org/openicpsr/project/116210/version/V1/view>. Source files `data/data_for_distribution/firm_panel.fst` and `individual_panel.fst`. This mirror preserves the files byte-for-byte; no transformations were applied. The deposited replication package is R-based (not Stata) and ships analysis data in `.fst` rather than `.dta`.

## Variable summary

### `firm_panel.fst` (Panel A, firm-level)

- `firmcrd` — firm CRD identifier
- `year` — 2008–2015 (3 pre-treatment years + 5 post-treatment years; main analysis window `2009:2014`)
- `N` — number of investment advisers at the firm
- `state.final` — state of primary regulation (cluster variable)
- `n_complaints` — count of complaints filed against the firm in the year (primary outcome family)
- `n_complaints_total` — cumulative complaints
- `n_reg` — number of regulatory examinations
- `aum2` — assets under management
- **`treated1`, `treated2`, `treated3`** — three alternative definitions of treated firms (those whose regulator shifted federal→state under Dodd-Frank Title IV)

### `individual_panel.fst` (Panel B, individual-level)

- `crd` — individual CRD identifier
- `year` — same window
- `firmcrd` — employer firm CRD
- **`treated1`, `treated2`, `treated3`** — treatment indicator at individual level
- `state.final` — state regulator
- `aum2011_median` — pre-treatment firm AUM (control)
- `branchclean` — branch identifier
- **`complaint.sign`** — primary outcome: indicator for individual having at least one complaint filed
- `complaint.lag`, `complaint.reg` — alternative outcome definitions

## Setting (Ch 4 framing)

Dodd-Frank Title IV (Investment Advisers Act amendments, effective mid-2012) shifted regulatory jurisdiction of investment advisers with AUM between $25–100M from the federal SEC to state regulators. Charoenwong-Kwan-Umar use this jurisdictional shift to test whether the *level* of regulator (federal vs state) affects regulatory quality, measured by client complaint outcomes.

This is a multi-period 2×T DiD: single binary shock (Dodd-Frank Title IV implementation, 2011–2012), binary treatment (advisers in the AUM range shifted to state vs those that stayed federal or were always state), 6–8 year panel. The paper reports both firm-level (Panel A) and individual-level (Panel B) analyses with various FE structures.

## Headline replication target (Chapter 4, Table 2 Panel B)

Panel B (individual-level) is the cleaner no-covariates specification, since Panel A (firm-level) includes cubic-in-log(N) firm-size controls in the headline column. The Panel B specs differ in *fixed-effect structure*, not in covariate inclusion:

`feols(I(sign2(complaint.sign)) ~ treated × post | firmcrd + year, cluster = state.final)`

| Spec | Description | `treated:post` β | SE | Sig? |
|---|---|---|---|---|
| **c01** | firm + year FE | **+0.339** | 0.104 | p = 0.002 |
| c02 | firm + state-post FE | +0.294 | 0.115 | p = 0.014 |
| c03 | firm + branch-post + year FE | +0.384 | 0.130 | p = 0.005 |
| c04 | firm + branch-post + state-year FE | +0.278 | 0.137 | p = 0.047 |
| c05 | individual FE | +0.295 | 0.113 | p = 0.012 |

Range: 0.278 to 0.384 (~28% spread across FE structures). **All p < 0.05.** No sign flip, no significance loss. The simplest no-cov spec c01 sits in the middle of the range — the richer FE specs neither raise nor lower the coefficient systematically, confirming that the headline effect (treated advisers receiving more complaints) is robust.

Caveat: Panel A (firm-level) headline includes `log(N) + log(N)^2 + log(N)^3` firm-size controls — if you want the firm-level analysis, you have to either drop those controls (which materially shifts the coefficient) or accept the cubic-in-size adjustment. Panel B is preferable for Chapter 4 because it identifies the same effect on individual complaints without the firm-size adjustment.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2019 *AER* paper.
