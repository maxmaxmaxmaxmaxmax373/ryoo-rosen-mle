# Engineering Enrollment and Wages: Full-Information Estimation of the Ryoo–Rosen Model

Writing sample by Max Cheong (Guanghua School of Management, Peking University).

The paper estimates the Ryoo–Rosen (2004) model of the market for engineers in a full-information framework. The competitive equilibrium is written as a linear-quadratic planning problem, its solution is put in state-space form together with measurement error, and all parameters are estimated jointly by maximum likelihood with the Kalman filter, using U.S. data for 1968–2010. The paper also compares rational expectations with cobweb expectations within the same likelihood.

- **Paper:** [`paper/writing_sample.pdf`](paper/writing_sample.pdf)
- **Code:** [`rr_estimation.ipynb`](rr_estimation.ipynb) reproduces every number, table, and figure in the paper.

## Repository structure

```
.
├── README.md
├── requirements.txt
├── rr_estimation.ipynb          # data -> model solution -> likelihood -> estimation -> results
├── data_new_engineering/        # input data (annual series, 1962-2025 / 1966-2010)
│   ├── cps_q_n_1962_2025.csv
│   └── pi_nsf_1966_2010.csv
├── cache/                       # saved results of the slow steps (profile likelihood, etc.)
├── figures/                     # figures written by the notebook
└── paper/
    ├── writing_sample.pdf
    └── latex/                   # LaTeX source (compiles with pdflatex + bibtex, e.g. on Overleaf)
```

## How to run

```bash
pip install -r requirements.txt
jupyter notebook rr_estimation.ipynb
```

With the files in `cache/`, the notebook runs in a few minutes. Delete `cache/` to recompute everything from scratch; the profile likelihood then takes about 30–45 minutes.

| Notebook section | Paper |
|---|---|
| 1. Data | Section 3, Figure 1 |
| 2. Solving the model | Section 2, Appendix A |
| 3. The likelihood | Section 4.1, Algorithm 1, Appendix B |
| 4. Estimation | Section 4.2, Table 1, Figure 2 |
| 5. Model fit | Section 4.3, Table 2, Appendix C |
| 6. Dynamics | Section 5, Figure 3, Table 3 |
| 7. Rational expectations versus the cobweb | Section 6, Table 4, Figures 4–5 |

## Data

- `cps_q_n_1962_2025.csv`: annual median earnings and weighted counts of engineers (OCC1990 codes 044–059) and of college graduates (EDUC ≥ 110), computed from IPUMS CPS ASEC microdata. Source: Sarah Flood, Miriam King, Renae Rodgers, Steven Ruggles, J. Robert Warren, et al. *IPUMS CPS: Version 13.0* [dataset]. Minneapolis, MN: IPUMS, 2025. The microdata themselves are not included; they can be obtained from [IPUMS CPS](https://cps.ipums.org/).
- `pi_nsf_1966_2010.csv`: engineering and total bachelor's degrees from National Science Foundation, National Center for Science and Engineering Statistics (2013), *Science and Engineering Degrees: 1966–2010*, Detailed Statistical Tables NSF 13-327, Table 5. The year 1999 is missing in the source and is interpolated in the notebook.
