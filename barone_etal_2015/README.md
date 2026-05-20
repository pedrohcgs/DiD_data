# Barone, D'Acunto & Narciso (2015) — Telecracy

## Citation

Barone, Guglielmo, Francesco D'Acunto, and Gaia Narciso. 2015. "Telecracy: Testing for Channels of Persuasion." *American Economic Journal: Economic Policy* 7(2): 30–60.

DOI: [10.1257/pol.20130318](https://doi.org/10.1257/pol.20130318)

## File

- `Telecracy_Data_AEJPol.dta` (658 KB, Stata `.dta` format)

## Source

AEA replication package, openICPSR project 114587: <https://www.aeaweb.org/articles?id=10.1257/pol.20130318>. This mirror preserves the analysis file byte-for-byte from the deposited `20130318_data/Telecracy_Data_AEJPol.dta`; no transformations were applied.

## Variable summary (analysis sample)

- `istat`, `com` — Italian municipality identifiers
- `provi`, `prov`, `provincia` — province identifiers (used for cluster-robust inference)
- `lat`, `lon` — municipality centroid coordinates
- `dist` — signed kilometers to the digital-switchover treatment boundary (negative = control side, positive = treated side)
- `switchoff` — 1 if municipality is in a province where Mediaset analog signal was switched off ahead of the 2010 regional elections, 0 otherwise
- `vberl05`, `vberl10`, `vberl00`, `vberl95` — Berlusconi-candidate vote share in 2005, 2010, 2000, 1995 regional elections (percent)
- `diffberl1005` — change in Berlusconi vote share 2010 − 2005 (the first-differenced 2×2 outcome)
- `unempl_rate10`, `unempl_rate05`, `unempl01`, `density01`, `male01`, … — 2001 Census sociodemographic and contemporaneous unemployment controls used in the paper's richer specifications

## Setting (Ch 3 framing)

Italy's analog-to-digital television switchover proceeded province-by-province. In several provinces the switchoff occurred *before* the March 2010 regional elections, removing analog Mediaset (Berlusconi-aligned commercial TV) access for households without digital-TV reception. Treated municipalities are those in switched-off provinces; control municipalities are those in provinces that still received the analog signal in 2010. The outcome is the change in Berlusconi-candidate vote share between the 2005 and 2010 regional elections — a first-differenced 2×2 in disguise (one row per municipality, change-on-change).

## Headline replication target (Chapter 3 spec)

Simple first-differenced 2×2 with provincia-clustered SE, no controls:

| Quantity | Value |
|---|---|
| **DiD coefficient on `switchoff`** | **−3.147 percentage points** |
| **SE (provincia-clustered)** | **1.665** |
| t-statistic | −1.89 |
| p-value | 0.10 |
| N (municipalities) | 1,206 |
| Treated (switchoff = 1) | 565 |
| Control (switchoff = 0) | 641 |

The DiD-by-hand on raw means matches the TWFE coefficient at machine precision: $-2.43 - 0.72 = -3.15$ percentage points (treated change minus control change).

The paper's preferred specifications add border-segment fixed effects and a sociodemographic-control battery, narrowing the comparison to municipalities along the same treatment-boundary segment. These richer specifications belong to the conditional-DiD machinery of Chapter 5; here we report the raw 2×2 to illustrate how the canonical design recovers a clean point estimate but a borderline-precise one when comparisons span the full sample.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2015 *AEJ:EP* paper.
