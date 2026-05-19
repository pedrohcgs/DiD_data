# Medicaid County Mortality Panel (JEL DiD Practitioner's Guide replication)

## Citation (replication data)

Baker, Andrew, David Callaway, Scott Cunningham, Andrew Goodman-Bacon, and Pedro H.C. Sant'Anna. 2025. "Difference-in-Differences: A Practitioner's Guide." *Journal of Economic Literature*, forthcoming.

## Underlying causal study

Miller, Sarah, Norman Johnson, and Laura R. Wherry. 2021. "Medicaid and Mortality: New Evidence from Linked Survey and Administrative Data." *Quarterly Journal of Economics* 136(3): 1783–1829.

## File

- `county_mortality_data.csv` (~6 MB)

## Source

Mirror of the file at:

```
https://github.com/pedrohcgs/JEL-DiD/blob/7c60bf753434cddaa24c1f0bb0ef2852777f6d55/data/county_mortality_data.csv
```

byte-for-byte. The upstream `pedrohcgs/JEL-DiD` repository is the primary distribution; this folder exists so `DiD_data` is a single source of truth for the book's data dependencies.

## Variable summary

- `fips_county` — 5-digit county FIPS
- `year` — calendar year
- `mortality_rate_per_100k` — crude all-cause mortality, ages 20–64, per 100,000
- `population` — county population (ages 20–64)
- `treated` — 1 if county is in a state that expanded Medicaid in January 2014; 0 if state never expanded through 2019
- Other covariates used in the JEL guide (per-capita income, percent uninsured, percent female, percent white, percent Black, percent Hispanic — see upstream repository for definitions)

## Headline replication targets (book Ch 3, 2 × 2 cut, 2013 vs 2014)

Sample restrictions (matching the JEL replication):

- Drop DC and pre-2014 expansion states (DE, MA, NY, VT)
- Keep counties with full mortality data 2009–2019
- Treated = 24 states that expanded in January 2014; comparison = 19 never-expansion states (through 2019)

| Spec | DiD | SE (state-clustered) | Notes |
|---|---|---|---|
| Unweighted | **+0.12 per 100k** | **3.72** | ATT on the average treated county |
| Population-weighted | **−2.56 per 100k** | **1.98** | ATT on the average treated person |

The sign flip across weighting schemes is real and is the pedagogical centerpiece of the Ch 3 weights section.

## License note

The CSV is publicly distributed via the upstream `JEL-DiD` repository under that repository's terms. When citing, cite the JEL guide (forthcoming, 2025) and the Miller-Johnson-Wherry (2021) *QJE* paper.
