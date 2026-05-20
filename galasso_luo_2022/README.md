# Galasso & Luo (2022) — Medical Implant Liability and Innovation

## Citation

Galasso, Alberto, and Hong Luo. 2022. "When Does Product Liability Risk Chill Innovation? Evidence from Medical Implants." *American Economic Journal: Economic Policy* 14(2): 366–401.

DOI: [10.1257/pol.20190757](https://doi.org/10.1257/pol.20190757)

## File

- `patent_reg_01.dta` (4.7 MB, Stata `.dta` format)

## Source

AEA replication package, openICPSR project 142501: <https://www.aeaweb.org/articles?id=10.1257/pol.20190757>. This mirror preserves the analysis file byte-for-byte from the deposited `Analysis codes and datasets/patent_reg_01.dta`; no transformations were applied.

## Variable summary (analysis sample)

- `id` — USPTO medical-device subclass identifier (panel unit)
- `year` — calendar year (1970–2010 in raw; book Ch 3 restricts to 1985–1995)
- `patents` — count of granted patents filed in subclass `id` in year `year`
- `implant` — 1 if subclass is an implant technology (≥ 80% of patents 1975–2015 are implant patents), 0 otherwise
- `implantXafter1990` — interaction `implant × 1{year ≥ 1990}`; the DiD treatment indicator
- `implantfractionXafter1990` — continuous treatment-intensity version (subclass implant-share × post)
- `pat_no_both`, `pat_US_assignee`, `pat_US_inventors` — outcome decompositions used in Tables 3–5
- `mixed2` — flag for "mixed" subclasses; spec 3 drops these

## Setting (Ch 3 framing)

Late-1980s litigation against TMJ and silicone breast implants triggered a sharp tightening of product-liability exposure for upstream polymer suppliers (DuPont, Dow Chemicals, and others) starting around 1990. Suppliers withdrew from the medical-implant market, and downstream patenting in implant subclasses fell relative to non-implant medical devices. This is a textbook 2×2: one treated cohort (implant subclasses), one shock date (1990), two periods (pre-1990 and 1990+), with non-implant subclasses as the comparison group.

## Headline replication target (Chapter 3 spec)

Table 2 column 1: TWFE on the balanced 1985–1995 subclass-year panel, clustered at subclass:

| Quantity | Value |
|---|---|
| **DiD coefficient on `implantXafter1990`** | **−0.5328 patents/subclass-year** |
| **SE (subclass-clustered)** | **0.0882** |
| t-statistic | −6.04 |
| p-value | 1.7e-9 |
| N (subclass-year) | 29,733 |
| Implant subclasses | 241 |
| Non-implant subclasses | 2,462 |

The DiD-by-hand on raw means matches the TWFE coefficient at machine precision (no covariates → 2×2 equivalence). The paper reports this as "implant patenting decreased by 35 percent relative to non-implant medical devices after 1990" (Galasso & Luo 2022, abstract).

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2022 *AEJ:EP* paper.
