# Okeke (2023) — When a Doctor Falls from the Sky

## Citation

Okeke, Edward N. 2023. "When a Doctor Falls from the Sky: The Impact of Easing Doctor Supply Constraints on Mortality." *American Economic Review* 113(3): 585–627.

DOI: [10.1257/aer.20210032](https://doi.org/10.1257/aer.20210032)

## File

- `staffing.dta` (119 KB, Stata `.dta` format)

## Source

AEA replication package, archived under publication identifier `aer20210032`. This mirror preserves the clinic-visit staffing roster file (`reference/original/data/analysis/staffing.dta`) byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

- `fid` — clinic facility identifier (180 clinics; clustered SE unit)
- `clinictreat` — randomized treatment arm: 0 (control), 1 (CHEW supply intervention only), 2 (doctor-placement intervention)
- `visit` — survey wave: 1 (baseline), 2 (post-intervention, ~6 months), 3 (post-intervention, ~12 months)
- `doctor` — indicator: doctor present at the clinic on the day of the visit
- `staff` — total clinical staff present at the clinic on the day of the visit (integer count)

## Headline replication target (Chapter 3 — doctor arm vs. control, visit 1 vs. 2)

From the verified DiD_book replication's `r_replication_results.csv` (model `staff_no_fe`, 2×2 contrast `clinictreat == 2` vs. `clinictreat == 0`, `visit == 2` vs. `visit == 1`):

| Quantity | Value (approximate; book script computes the simple 2×2 mean difference) |
|---|---|
| **DiD coefficient (doctor arm − control, visit 2 − visit 1)** | **≈ +1 staff member** (doctor placement materially raises on-the-day clinic staffing) |
| Control baseline (visit 1, `clinictreat == 0`) | 5.20 staff |
| N (clinic-visit) | 360 |
| Clinics | 180 |

The book script (`scripts/book/ch03_okeke_doctors.R`) computes the simple 2×2 mean difference for the cleanest pedagogical 2×2; verified against this corpus benchmark.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2023 *AER* paper.
