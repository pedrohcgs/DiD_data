# Huet-Vaughn (2019) — ARRA Road Spending and Vote Share

## Citation

Huet-Vaughn, Emiliano. 2019. "Stimulating the Vote: ARRA Road Spending and Vote Share." *American Economic Journal: Economic Policy* 11(1): 292–316.

DOI: [10.1257/pol.20170151](https://doi.org/10.1257/pol.20170151)

## File

- `20170151_ARRA.dta` (1.0 MB, Stata `.dta` format)

## Source

AEA replication package: <https://www.aeaweb.org/articles?id=10.1257/pol.20170151> (openICPSR archive associated with the published paper). This mirror preserves the raw analysis file byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

- `inputid` — county FIPS identifier
- Election-cycle outcome columns (`demo_share`, `Turnoutpc`, ...) for the four pre-/post-ARRA cycles (2004, 2006, 2008, 2010, 2012)
- Treatment intensity: per-capita ARRA road-construction obligations (binary cut at zero, plus continuous distance measure)
- Standard county-level covariates (income, population, demographics) and county-by-time fixed effects supports

## Headline replication target (Chapter 3 binary 2×2 spec)

From the verified DiD_book replication's `r_translation_main_table_estimates.csv`, Table 2 column 1 (binary DiD, no controls, county-clustered SE on 2008–2012 cut):

| Quantity | Value |
|---|---|
| **DiD coefficient on `treat_2012e`** | **+1.6537 ppt Democratic vote share** |
| **SE (county-clustered)** | **0.3655** |
| t-statistic | 4.52 |
| p-value | 7.4e-6 |
| N (county-year) | 2,260 |

The Chapter 3 book script (`scripts/book/ch03_huet_vaughn.R`) reproduces this Table 2 binary_1 spec exactly as a sanity check, then presents the simpler 2008-vs-2012 long-difference cut as the headline.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2019 *AEJ:EP* paper.
