# ODE Pool Framework: Case Study

Case study for the pool model paper. It contains parameter estimation, model
selection and profile likelihood code for a bacterial co-culture ODE model,
with and without pH influence.

The code was originally part of
[fusion_model](https://github.com/polinagaindrik/fusion_model). It now runs on
its own: `pool_paper_casestudy/fusion_core` contains the small set of
`fusion_model` functions the case study needs, so neither `fusion_model` nor
`pybis` has to be installed.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

The code was developed with Python 3.11. To reproduce the exact environment
used for the paper, install `requirements-lock.txt` instead.

## Data

The experimental data is **not** included in this repository. To run the
scripts, place the data in `pool_paper_casestudy/data/` like this:

```
pool_paper_casestudy/data/
├── CCD_results_counts_Part 2.xlsx   # cell counts (sheet R9_rep)
├── 7_LA/RUN_09.xlsx                 # lactic acid production
└── 8_BA/BA_09.xlsx                  # bacteriocin production
```

Results are written to `pool_paper_casestudy/out/`. That folder is also
excluded from version control.

## Usage

Run the scripts from the repository root, so that `pool_paper_casestudy` can
be imported as a package:

```bash
python pool_paper_casestudy/global_optimization_5exps.py   # global calibration
python pool_paper_casestudy/local_optimization.py          # local refinement
python pool_paper_casestudy/profile_likelihood.py          # profile likelihood
python pool_paper_casestudy/plot_profile_from_csv.py       # plot profiles
python pool_paper_casestudy/model_selection_pH_vs_noPH.py  # model comparison
python pool_paper_casestudy/plot_final_result.py           # final figures
```

`pool_paper_casestudy/other/` contains older, exploratory scripts.

## License

MIT, see [LICENSE](LICENSE).
