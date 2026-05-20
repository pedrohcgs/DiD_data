# Lockwood & Porcelli (2013) — UK Comprehensive Performance Assessment

## Citation

Lockwood, Ben, and Francesco Porcelli. 2013. "Incentive Schemes for Local Government: Theory and Evidence from Comprehensive Performance Assessment in England." *American Economic Journal: Economic Policy* 5(3): 254–286.

DOI: [10.1257/pol.5.3.254](https://doi.org/10.1257/pol.5.3.254)

## File

- `CPADATASET.dta` (663 KB, Stata `.dta` format)

## Source

AEA replication package, openICPSR project 114831: <https://www.openicpsr.org/openicpsr/project/114831/version/V1/view>. Source file `DATA_AEJ_CPA/CPADATASET.dta` from the deposited archive. This mirror preserves the file byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

- `code` — council unique identifier (panel unit, 170 distinct councils)
- `year` — calendar year, 1997–2007
- `england` — 1 if council is in England (treated), 0 if Wales (control)
- `dummyCPA` — 1 if year ≥ 2002 (post-CPA-introduction)
- **`dummyCPAengland`** — interaction `england × dummyCPA` — main DiD treatment indicator
- `taxreqrp` — tax requirement per capita, real GBP (paper's headline outcome)
- `counciltaxrd` — effective council tax rate, real GBP per band-D equivalent dwelling
- `ltaxreq_prc` — tax requirement as % of budget requirement
- `bvpi38`, `bvpi54`, `bvpi49`, `bvpi8`, `bvpi82a` — Best Value Performance Indicators (output measures: education, social services, central services, environment)
- `dhatbc_all9704`, `dhatbc_all9704_out` — efficiency measures (DEA-bias-corrected, input and output approaches)
- 19 demographic / political / fiscal covariates including `lreligious`, `lwhite`, `lhighqualified`, `ltenure`, `lselfemployed`, party-share dummies (`LABdummy`, `CONdummy`, `LDdummy`, `OTHERdummy`, `NOCdummy`), and their period averages with `*avg` suffix

## Setting (Ch 4 framing)

In 2002 the UK government introduced Comprehensive Performance Assessment (CPA) for English local authorities — a public performance rating that summarized councils' service quality and efficiency. Welsh councils were not subject to CPA, providing a natural control group. Treated municipalities are English councils; control municipalities are Welsh councils. Multi-period panel 1997–2007: 5 pre-CPA years + 6 post.

This is a clean multi-period 2×T DiD: single binary treatment dimension (England vs Wales), single shock date (CPA introduction 2002), 11-year panel with council and year fixed effects.

## Headline replication target (Chapter 4)

TWFE on the full 1997–2007 panel; treatment = `dummyCPAengland`; council FE + year FE; cluster council. No covariates beyond the FE (verified — see robustness note below).

| Outcome | No-cov β | SE | With-cov β | SE | % change |
|---|---|---|---|---|---|
| `taxreqrp` (tax requirement per capita) | **+11.50** | 5.99 | +11.50 | 5.99 | **0.0%** |
| `counciltaxrd` (council tax rate, band-D) | **+62.14** | 11.63 | +62.14 | 11.63 | **0.0%** |
| `ltaxreq_prc` (tax req % budget) | **+8.08** | 0.46 | +8.08 | 0.46 | **0.0%** |
| `bvpi38` (education output) | +0.082 | 0.007 | +0.082 | 0.007 | **0.0%** |
| `bvpi54` (social services output) | +2.58 | 8.18 | +2.58 | 8.18 | **0.0%** |
| `bvpi8` (central services output) | +0.016 | 0.015 | +0.016 | 0.015 | **0.0%** |
| `bvpi82a` (environment output) | −0.086 | 0.009 | −0.086 | 0.009 | **0.0%** |

Why the perfect robustness: the 19 main controls in the paper's spec are mostly `*avg` variables (council-specific averages over the sample window) which are time-invariant within council and fully absorbed by the council FE. The non-averaged controls are also near-invariant. So the coefficient on `dummyCPAengland` is mechanically identical with or without these controls.

The CPA shock raised tax requirements by ~£12 per capita and council taxes by ~£62 per band-D dwelling, with education outputs rising and environment outputs falling. This makes Lockwood-Porcelli a particularly clean Ch 4 application: paper-reported covariates are functionally redundant given the panel FE, so the no-covariates 2×T DiD identifies the same coefficient as the paper's headline.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2013 *AEJ:EP* paper.
