# Implementation of Reinforcement Learning in Chemical Reaction Networks: Application to Phototaxis

This repository contains the code, processed data, and reproducible notebooks for the paper:

**Implementation of reinforcement learning in chemical reaction networks: application to phototaxis as curiosity-driven exploration**

The project studies algal phototaxis through three connected components:

1. a **theoretical POMDP formulation** of subjective phototactic decision making,
2. a **data-driven learning pipeline** for fitting the POMDP and reward structure from experimental trajectories,
3. a **benchmarking pipeline** comparing learned subjective policies against objective Gillespie-style baselines.

## Repository structure

```text
phototaxis-pomdp-crn/
├── data/
│   ├── raw/
│   ├── processed/
│   │   ├── clean_movie_52_with_speed.csv
│   │   └── clean_movie_52_with_speed_and_action.csv
│   └── README.md
├── checkpoints/
│   ├── experiment_checkpoint.pkl
│   └── README.md
├── notebooks/
│   ├── 01_Single_Source_POMDP_and_CRN.ipynb
│   ├── 02_Data_Driven_IRL.ipynb
│   ├── 03_Benchmarking_and_Plots.ipynb
│   └── 90_Additional_Multi_Source_and_Flickering_POMDP_and_CRN.ipynb
├── outputs/
│   ├── figures/
│   ├── trajectories/
│   ├── tables/
│   └── README.md
├── requirements.txt
├── LICENSE
├── CITATION.cff
└── README.md
```

## What each notebook does

### `01_Single_Source_POMDP_and_CRN.ipynb`
Main theoretical notebook for the **single-source** setting used in the paper.

It contains:
- single-source observation and belief-update logic,
- numerical trajectory simulations,
- CRN-ODE construction,
- numerical-versus-ODE comparisons,
- optional single-source curiosity-weight exploration.

This notebook corresponds to the **single-source theoretical and mechanistic part** of the paper.

### `02_Data_Driven_IRL.ipynb`
Main learning notebook.

It contains:
- preprocessing of trajectory data,
- speed / heading / light-center processing,
- action labeling,
- gridded trajectory construction,
- train/test split,
- policy learning,
- IRL reward learning,
- export of processed datasets and the experiment checkpoint.

This notebook produces:
- `data/processed/clean_movie_52_with_speed.csv`
- `data/processed/clean_movie_52_with_speed_and_action.csv`
- `checkpoints/experiment_checkpoint.pkl`

### `03_Benchmarking_and_Plots.ipynb`
Main benchmarking notebook.

It loads the processed data and checkpoint from `02` and reproduces the paper’s benchmark pipeline, including:
- subjective-policy rollouts,
- standard Gillespie baseline rollouts,
- modified Gillespie baseline rollouts,
- alignment-distribution comparisons,
- tumble-ratio calibration and summary statistics,
- export of trajectories, figures, and tables.

This notebook corresponds to the **main benchmark/results section** of the paper.

### `90_Additional_Multi_Source_and_Flickering_POMDP_and_CRN.ipynb`
Supplementary / exploratory notebook.

It contains:
- multi-source observation settings,
- multi-light trajectory simulations,
- flickering-light experiments,
- optional exploratory CRN-ODE extensions.

This notebook is **not part of the main reviewer reproduction path**.

## Quick start

Clone the repository and install dependencies:

```bash
git clone https://github.com/giveyourselfaTRY/phototaxis-pomdp-crn.git
cd phototaxis-pomdp-crn
pip install -r requirements.txt
```

## Recommended execution order

If you want the shortest path to the main results:

1. Run `02_Data_Driven_IRL.ipynb`
2. Run `03_Benchmarking_and_Plots.ipynb`

If you want the full paper-aligned notebook structure:

1. `01_Single_Source_POMDP_and_CRN.ipynb`
2. `02_Data_Driven_IRL.ipynb`
3. `03_Benchmarking_and_Plots.ipynb`
4. `90_Additional_Multi_Source_and_Flickering_POMDP_and_CRN.ipynb`

## Expected artifacts

After running the notebooks, the following artifacts should appear.

### From `02_Data_Driven_IRL.ipynb`
- `data/processed/clean_movie_52_with_speed.csv`
- `data/processed/clean_movie_52_with_speed_and_action.csv`
- `checkpoints/experiment_checkpoint.pkl`

### From `03_Benchmarking_and_Plots.ipynb`
- trajectory CSV files under `outputs/trajectories/`
- benchmark summary tables under `outputs/tables/`
- paper-aligned plots under `outputs/paper_figures/`

## Notes on experimental semantics

The current notebook split is designed to preserve the original experimental logic of the main benchmarking notebook as closely as possible.

In particular:
- held-out trajectory alignment comparisons are evaluated using the benchmark target exported from the learning pipeline,
- tumble-ratio calibration follows the original benchmarking semantics used in the main pipeline,
- the additional notebook is kept separate so that exploratory multi-source and flickering-light experiments do not interfere with the main reproduction path.

## Data and checkpoint notes

- See `data/README.md` for information on raw versus processed data.
- See `checkpoints/README.md` for the contents of the exported checkpoint.
- See `outputs/README.md` for the meaning of generated figures, tables, and trajectory files.

## Citation

If you use this repository, please cite the associated paper. A ready-to-edit citation file is provided in `CITATION.cff`.

## License

A license file is included in this repository. If you want a different license than the draft provided here, update `LICENSE` before final public release.
