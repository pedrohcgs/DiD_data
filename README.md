# DiD_data

Public data mirror for the book **"DiD and Beyond"** (in progress; companion materials at [pedrohcgs/Econ-730---Causal-Panel-Data](https://github.com/pedrohcgs/Econ-730---Causal-Panel-Data)).

This repository hosts the raw `.dta` and `.csv` files that the book's R scripts load. Scripts fetch each file by **pinned commit SHA** through `raw.githubusercontent.com`, so the published numbers in the book remain reproducible even if this repository is updated later.

## How book scripts use this repository

Each book-facing R script under `scripts/book/` in the companion repo defines a `DID_DATA_COMMIT <- "<sha>"` constant and constructs URLs like:

```
https://raw.githubusercontent.com/pedrohcgs/DiD_data/<sha>/<paper_folder>/<file>
```

Downloads are cached under `~/.cache/econ730-data/<sha>/` on the user's machine so the script only hits GitHub on first run.

## Papers currently mirrored (v0.1)

| Folder | Paper | File(s) | Source |
|---|---|---|---|
| `card_krueger_1994/` | Card, D. & Krueger, A.B. (1994). "Minimum Wages and Employment: A Case Study of the Fast-Food Industry in New Jersey and Pennsylvania." *AER* 84(4): 772–793. | `Card_Krueger_1994_public_dataset.dta` (14 KB) | David Card's Berkeley page (public dataset) |
| `medicaid_jel_mirror/` | County-level mortality panel used in the JEL DiD Practitioner's Guide (Baker, Callaway, Cunningham, Goodman-Bacon, Sant'Anna 2025). Underlying paper: Miller, Johnson, Wherry (2021), *QJE*. | `county_mortality_data.csv` (~6 MB) | Mirror of [pedrohcgs/JEL-DiD@7c60bf7](https://github.com/pedrohcgs/JEL-DiD/blob/7c60bf753434cddaa24c1f0bb0ef2852777f6d55/data/county_mortality_data.csv) |

## Pending papers (v0.2 — urgent next)

These four are referenced by Chapter 3 book scripts and will be added once their AEA replication archives are restored locally:

| Target folder | Paper | Used by |
|---|---|---|
| `huet_vaughn_2019/` | Huet-Vaughn, E. (2019). "Stimulating the Vote: ARRA Road Spending and Vote Share." *AEJ:EP* 11(1): 292–316. | `scripts/book/ch03_huet_vaughn.R` |
| `cheng_raina_xiong_2014/` | Cheng, I.-H., Raina, S., & Xiong, W. (2014). "Wall Street and the Housing Bubble." *AER* 104(9): 2797–2829. | `scripts/book/ch03_wall_street.R` |
| `juhasz_2018/` | Juhász, R. (2018). "Temporary Protection and Technology Adoption: Evidence from the Napoleonic Blockade." *AER* 108(11): 3339–76. | `scripts/book/ch03_juhasz_blockade.R` (reserved for Ch 16) |
| `okeke_2023/` | Okeke, E.N. (2023). "When a Doctor Falls from the Sky: The Impact of Easing Doctor Supply Constraints on Mortality." *AER* 113(3): 585–627. | `scripts/book/ch03_okeke_doctors.R` (reserved for Ch 12) |

## Licensing posture

Each subfolder mirrors data originally distributed publicly under the original authors' / publishers' terms. The per-folder `README.md` records the upstream source URL and license note. This repository adds no additional restrictions beyond the upstream terms; downstream users should consult the per-folder notes.

## Version log

- **v0.1** (2026-05-19) — Card-Krueger 1994 + Medicaid (JEL replication mirror).
