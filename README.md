# epidemics-art-forecasting

This repository contains experimental notebook code for generating synthetic antiretroviral therapy (ART) drug consumption data and evaluating forecasting approaches for publication-related analysis.

Due to the sensitive nature of the original data, only synthetic data is included. The pipeline is designed so that a user with access to an alternative source dataset can replace the input files and rerun the workflow.

## Repository Structure

- `synthetic-data-generation/`: notebooks and CSV files used to construct monthly synthetic ART drug consumption datasets.
- `synthetic-data-generation/source_data/`: source line-wise and regimen-wise inputs used by the synthetic data workflow.
- `synthetic-data-generation/final_datasets/`: final synthetic monthly consumption datasets used by the forecasting pipeline.
- `prediction-pipeline/`: forecasting notebooks, model comparison outputs, forecast tables, and figures.
- `requirements.txt`: Python dependencies used in the notebook environment.

## Data Scope

The included synthetic datasets cover monthly drug consumption from August 2015 through March 2024. Final datasets are stored as CSV files with the schema:

```text
date,consumption
```

Additional methodology details for the synthetic data generation process are documented in `synthetic-data-generation/documentation.md`. Reproducibility guidance is documented in `REPRODUCIBILITY.md`.

## Setup

Create and activate a Python environment, then install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

The repository intentionally excludes the local `.venv/` directory from version control.

## Notebook Workflow

The code is intentionally kept in notebooks because this is experimental research code and the notebooks preserve the analysis workflow.

Suggested execution order for synthetic data generation:

1. `synthetic-data-generation/baseline_data_gen.ipynb`
2. `synthetic-data-generation/data_interpolation.ipynb`
3. `synthetic-data-generation/derived_booster_data_gen.ipynb`
4. `synthetic-data-generation/final_patient_dataset_gen.ipynb`
5. `synthetic-data-generation/policy_based_dosage_calibration.ipynb`
6. `synthetic-data-generation/post_interpolation_analysis.ipynb`

Forecasting notebooks:

1. `prediction-pipeline/synthetic_forecasting_tool.ipynb`
2. `prediction-pipeline/forecasting-tool.ipynb`

`arima_test.ipynb` is retained as an experimental notebook for ARIMA-related testing.

## Main Outputs

- Final synthetic datasets: `synthetic-data-generation/final_datasets/`
- Forecast tables: `prediction-pipeline/synth_tables/`
- Forecast and comparison figures: `prediction-pipeline/synth_graphs/` and `prediction-pipeline/synth_comparison_graphs/`
- Model comparison summary: `prediction-pipeline/model_results.csv`

## Reproducibility Note

This repository does not include sensitive real-world source data. The included synthetic data and generated outputs are intended to support review of the modeling workflow and publication analysis. Results may differ if notebooks are rerun after changing random seeds, source inputs, package versions, or model configuration.

See `REPRODUCIBILITY.md` for expected data ranges, rerun order, and known sources of variation.
