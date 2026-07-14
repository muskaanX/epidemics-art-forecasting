# Reproducibility

This repository is structured to support review and rerunning of the synthetic-data forecasting workflow used for publication-related analysis. The original sensitive source data is not included.

## Included Materials

- Synthetic source inputs in `synthetic-data-generation/source_data/`
- Synthetic data generation notebooks in `synthetic-data-generation/`
- Intermediate synthetic CSV outputs in `synthetic-data-generation/baseline_data/`, `synthetic-data-generation/interpolated_data/`, and `synthetic-data-generation/datasets/`
- Final synthetic monthly consumption datasets in `synthetic-data-generation/final_datasets/`
- Forecasting notebooks in `prediction-pipeline/`
- Forecast tables, figures, and model summary outputs in `prediction-pipeline/`
- Python dependency pins in `requirements.txt`

## Excluded Materials

- Sensitive real-world source data
- Local Python environments such as `.venv/`
- Local operating-system and notebook cache files

The synthetic data is intended to provide a shareable substitute for the restricted data while preserving the structure needed to inspect and rerun the modeling workflow.

## Tracked Output Policy

The repository tracks the current generated CSV and PNG outputs because they are small enough for version control and useful for publication review.

Tracked outputs include:

- Source and intermediate synthetic CSVs used to audit the synthetic data construction process
- Final synthetic CSVs used as forecasting inputs
- Forecast tables used to inspect model predictions
- Model comparison summary CSVs
- Forecast and comparison PNG figures used for visual review

Generated outputs should be replaced only when the notebooks are intentionally rerun as part of a documented analysis update. Local environments, notebook checkpoints, cache files, and operating-system files should remain untracked.

## Expected Data Ranges

Final synthetic datasets:

- Location: `synthetic-data-generation/final_datasets/`
- Expected rows per file: 104 monthly observations
- Expected date range: August 2015 through March 2024
- Expected columns: `date`, `consumption`

Forecast tables:

- Location: `prediction-pipeline/synth_tables/`
- Expected rows per file: 18 forecast/evaluation rows
- Expected date range: October 2022 through March 2024

## Rerunning the Workflow

Run notebooks from the repository root so relative paths resolve consistently.

Suggested synthetic data generation order:

1. `synthetic-data-generation/baseline_data_gen.ipynb`
2. `synthetic-data-generation/data_interpolation.ipynb`
3. `synthetic-data-generation/derived_booster_data_gen.ipynb`
4. `synthetic-data-generation/final_patient_dataset_gen.ipynb`
5. `synthetic-data-generation/policy_based_dosage_calibration.ipynb`
6. `synthetic-data-generation/post_interpolation_analysis.ipynb`

Forecasting notebooks:

1. `prediction-pipeline/synthetic_forecasting_tool.ipynb`
2. `prediction-pipeline/forecasting-tool.ipynb`

## Sources of Variation

Rerun outputs may differ if any of the following change:

- Random seeds or stochastic noise/spike generation settings
- Source input CSVs
- Model hyperparameters
- Forecast horizon
- Python package versions
- TimesFM checkpoint or runtime behavior
- Notebook execution order or partially rerun cells

For publication review, use the committed synthetic datasets and generated outputs as the reference artifacts unless intentionally regenerating the pipeline.

## Methodology Documentation

Synthetic data assumptions, dosage calibration, known limitations, and source references are documented in `synthetic-data-generation/documentation.md`.
