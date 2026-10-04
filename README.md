# Criteo Uplift Study

An experimental study of response prediction, treatment effects, uplift ranking, policy value, and sensitivity analysis using the Criteo uplift modeling benchmark. The six notebooks contain the analysis; `src/` holds shared configuration, hashing, statistical, and visualization helpers.

## Setup

Install [uv](https://docs.astral.sh/uv/getting-started/installation/) if needed, then from the repository root:

```powershell
uv sync
uv run jupyter lab
```

Open the notebooks in order:

1. `01_preprocessing.ipynb` — data checks and exploratory analysis
2. `02_response_prediction.ipynb` — response prediction
3. `03_ate_exposure.ipynb` — average treatment effects and exposure analysis
4. `04_uplift_cate_models.ipynb` — CATE models and validation
5. `05_policy_value_eval_testset_uplift.ipynb` — policy-value comparison
6. `06_sensitivity_segments_expdesign.ipynb` — sensitivity, segments, and experiment design

The notebooks locate the repository root by searching parent directories for `pyproject.toml`. Run them from the repository or its `notebooks/` directory.

## Data

The raw data is not included. Download the debiased Criteo Uplift Prediction Dataset v2.1 from the [official Criteo AI Lab page](https://ailab.criteo.com/criteo-uplift-prediction-dataset/) (download link: [criteo-research-uplift-v2.1.csv.gz](http://go.criteo.net/criteo-research-uplift-v2.1.csv.gz)) and save it as:

```text
data/criteo-research-uplift-v2.1.csv.gz
```

The current notebooks read a prepared, hashed Parquet file at `data/criteo_uplift_v2_hashed.parquet`; the raw CSV download is **not** converted automatically by this repository. The modeling notebooks also use intermediate artifacts generated during analysis, including `data/interim/e2_best_visit_model.joblib` and `data/interim/e4_val_uplift_scores.parquet`. These datasets and generated artifacts are excluded from Git.
