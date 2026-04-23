# UIDAI Hackathon 2026

Comprehensive analytics pipeline for UIDAI Aadhaar authentication and enrolment data. The project standardizes raw geographic fields, reconciles duplicate entities, performs exploratory and anomaly analysis, generates 2026 forecasts, and exports dashboard-ready deliverables for reporting and operational review.

## Project Overview

The notebook in this repository analyzes biometric authentication, demographic authentication, and enrolment datasets with a focus on:

- improving operational visibility across states, districts, and pincodes,
- identifying suspicious or unusual authentication patterns,
- standardizing messy geographic fields into auditable mapping tables,
- forecasting future authentication and enrolment demand for capacity planning,
- producing CSV, PNG, and HTML outputs that can be shared with stakeholders.

The full analysis covers about 4.9 million source records across 12 CSV files spanning March to December 2025.

## Key Findings

- Geographic standardization reduced heterogeneous state names to 36 official values and consolidated duplicate districts into a cleaner hierarchy.
- The analysis identified a complete August 2025 data gap across all three datasets, which materially affects time-series continuity.
- Authentication volumes show a pronounced post-July decline and a strong Tuesday spike pattern, both of which are relevant for workload planning.
- Dual anomaly-detection methods were used to flag suspicious districts and pincodes for follow-up investigation.
- Forecasting outputs project biometric, demographic, and enrolment demand for 2026 to support infrastructure and service planning.

## Repository Layout

```text
UIDAI-Hackathon-2026/
├── Data/
│   ├── api_data_aadhar_biometric.zip
│   ├── api_data_aadhar_demographic.zip
│   └── api_data_aadhar_enrolment.zip
├── Documentaion/
│   └── UIDAI Aadhaar Hackathon Documentation.docx
├── Notebook/
│   └── UIDAI Dataset Analysis.ipynb
├── api_data_aadhar_biometric/
├── api_data_aadhar_demographic/
├── api_data_aadhar_enrolment/
├── outputs/
│   ├── data/
│   ├── figures/
│   └── UIDAI_Interactive_Dashboard.html
├── LICENSE
└── README.md
```

## Data Notes

- The source-of-truth raw inputs are the ZIP archives under `Data/`.
- The extracted folders at the repository root mirror those archives and are retained for compatibility with folder-based workflows.
- The notebook has been updated to detect the project root automatically and read directly from the ZIP archives when available.

## Main Notebook

The end-to-end workflow lives in `Notebook/UIDAI Dataset Analysis.ipynb` and is organized into phases that cover:

- data loading and merging,
- exploratory data analysis,
- temporal pattern analysis,
- geographic normalization and hierarchy cleanup,
- clustering and anomaly detection,
- 2026 forecasting,
- dashboard and submission artifact export.

## Generated Deliverables

### Data Exports

Files under `outputs/data/` include:

- `anomalous_districts_dbscan.csv`
- `biometric_forecast_2026.csv`
- `cross_validated_anomalies.csv`
- `data_quality_report.csv`
- `district_standardization_mapping.csv`
- `enrolment_forecast_2026.csv`
- `predictions_2026_monthly.csv`
- `quarterly_forecast_2026.csv`
- `state_level_summary.csv`
- `state_standardization_mapping.csv`

### Figures

Files under `outputs/figures/` include:

- `age_split_analysis_all_datasets.png`
- `anomaly_pattern_analysis.png`
- `auth_enrol_comparison.png`
- `conversion_funnel_all_datasets.png`
- `district_clustering_analysis.png`
- `pareto_pincode_all_datasets.png`
- `pincode_spike_analysis.png`
- `population_normalized_comparison.png`
- `state_performance_heatmap.png`
- `temporal_trends_all_datasets.png`

### Dashboard

- `outputs/UIDAI_Interactive_Dashboard.html` is a standalone interactive dashboard for stakeholder review.

## Environment Requirements

Use a Python environment with the libraries required by the notebook, including:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scipy`
- `scikit-learn`
- `prophet`
- `plotly`
- `jupyter`
- `ipykernel`

Python 3.10+ is a reasonable baseline for this workflow.

## Running The Analysis

### Option 1: Open the notebook interactively

1. Activate your Python environment.
2. Open `Notebook/UIDAI Dataset Analysis.ipynb` in Jupyter or VS Code.
3. Run the notebook from top to bottom.

### Option 2: Execute from the command line

From the repository root:

```bash
jupyter nbconvert --to notebook --execute --inplace \
	--ExecutePreprocessor.timeout=0 \
	--ExecutePreprocessor.kernel_name=python3 \
	"Notebook/UIDAI Dataset Analysis.ipynb"
```

This updates the notebook in place and regenerates the exported outputs.

## Output Summary

The repository already includes:

- archived raw datasets,
- extracted CSV copies,
- the executed analysis notebook,
- exported CSV deliverables,
- exported figures,
- the standalone HTML dashboard,
- the hackathon documentation document.

## Operational Relevance

The outputs are intended to support UIDAI-style operational use cases such as:

- fraud and misuse monitoring,
- capacity planning for authentication services,
- enrolment inclusion analysis,
- state and district performance comparisons,
- reporting and dashboard integration.

## License

This repository is distributed under the terms of the included `LICENSE` file.