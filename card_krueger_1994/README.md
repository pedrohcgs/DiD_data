# Card & Krueger (1994) — NJ–PA Minimum Wage Study

## Citation

Card, David, and Alan B. Krueger. 1994. "Minimum Wages and Employment: A Case Study of the Fast-Food Industry in New Jersey and Pennsylvania." *American Economic Review* 84(4): 772–793.

## File

- `Card_Krueger_1994_public_dataset.dta` (14 KB, Stata `.dta` format)

## Source

David Card's Berkeley page hosts the public dataset associated with the paper. This mirror preserves the file in its publicly distributed form, byte-for-byte. The paper predates the AEA's standardized replication archives; the dataset has long been used in textbooks and graduate courses as a teaching example.

## Variable summary (analysis sample)

- `state` — NJ (treated) vs. PA (comparison)
- `time` — survey wave: Feb–Apr 1992 (pre) vs. Nov–Dec 1992 (post)
- `fte` — full-time-equivalent employment at the store (full-time + ½ × part-time + ½ × managers)
- Store identifier + chain dummies (BK, KFC, Roy's, Wendy's)

## Headline replication target (from book Ch 3 spec)

Stacked 2 × 2 difference-in-differences regression (treated × post), store-clustered standard errors on the 401-store balanced panel:

| Quantity | Value |
|---|---|
| **DiD coefficient** | **+2.914 FTE** |
| **SE (store-clustered)** | **1.291** |
| t-statistic | 2.26 |
| p-value | 0.024 |
| N stores | 401 |

These numbers match the published Card-Krueger Table 3 column 4 within the small differences attributable to balanced-vs-all-stores subsetting.

## License note

Public dataset distributed by the original author for research and teaching. This mirror adds no additional restrictions. When citing, cite the original 1994 *AER* paper.
