# Cheng, Raina & Xiong (2014) — Wall Street and the Housing Bubble

## Citation

Cheng, Ing-Haw, Sahil Raina, and Wei Xiong. 2014. "Wall Street and the Housing Bubble." *American Economic Review* 104(9): 2797–2829.

DOI: [10.1257/aer.104.9.2797](https://doi.org/10.1257/aer.104.9.2797)

## File

- `hmda_matches.dta` (104 KB, Stata `.dta` format)

## Source

AEA replication package, archived under publication identifier `aer20130297`. This mirror preserves the analysis file (`aer20130297_data/data/hmda_matches.dta`) byte-for-byte; no transformations were applied.

## Variable summary (analysis sample)

The full Wall Street dataset is a panel of 449 securitization-industry professionals matched to HMDA (Home Mortgage Disclosure Act) home-purchase records over 2000–2010. The `hmda_matches.dta` file provides the personal-purchase outcomes (count, intensity, divestiture indicator) by data source (`datsource ∈ {0, 1, 2}` for Mid-level / Vice President / Senior Vice President samples) plus matched HMDA controls.

## Headline result (Chapter 3 — the **null** finding)

The paper's headline DiD compares Wall Street insiders' home-purchase behavior to controls before vs. during the 2004–2006 bubble. **The DiD is not statistically distinguishable from zero**, and that is precisely the paper's contribution: securitization-industry insiders did not avoid the housing-market downturn through any informational advantage.

The Chapter 3 pedagogical point: the same 2×2 DiD machinery used in Card-Krueger or Huet-Vaughn can also produce a null estimate, and statistical insignificance is itself the substantively interesting finding.

The verified DiD_book replication runs the paper's own Stata source code and matches **50 exact checks for Tables 3 and 9 to floating-point tolerance** — confirming the null results are exactly what the published paper reports.

## License note

Distributed under the AEA Data Editor's standard replication-data terms (publicly archived for replication and teaching). This mirror adds no additional restrictions beyond the upstream terms. When citing, cite the original 2014 *AER* paper.
