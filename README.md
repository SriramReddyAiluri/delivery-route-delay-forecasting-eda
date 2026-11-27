# Delivery Route Delay Forecasting - EDA

This repository contains Srirami Reddy Ailuri's contribution to the Exploratory Data Analysis (EDA) work for the Delivery Route Delay Forecasting & Logistics Performance Analytics project.

## EDA responsibility

The EDA work will examine delivery performance and, where the selected dataset supports it, explore patterns related to time, routes or distance, traffic, and weather. It will define and calculate relevant performance KPIs, prepare visualizations, and document assumptions and limitations.

## Current status

The initial EDA plan and KPI definitions are documented in `docs/eda_plan.md`. The dataset was initially profiled and later rechecked against Darshan's approved updated cleaned CSV; the CSV is not committed to this repository. Data quality and univariate findings are documented in `docs/quality_univariate_analysis.md`, with reproducible checks in `Notebooks/quality_univariate_analysis.ipynb`. Delivery-duration comparisons are documented in `docs/delivery_duration_by_factors.md`, with reproducible analysis in `Notebooks/delivery_duration_by_factors.ipynb` and charts in `outputs/`. Numeric relationships and correlations are documented in `docs/numeric_relationship_analysis.md`, with calculations and visualizations in `Notebooks/numeric_relationship_analysis.ipynb`. The consolidated [EDA findings and review limitations](docs/eda_findings_review.md) summarizes supported patterns, caveats, and open questions. The `Delivery_Time` unit remains unconfirmed.

## Repository layout

| Folder | Purpose |
|---|---|
| `docs/` | EDA plan, dataset scope, KPI definitions, and written analysis notes |
| `Notebooks/` | Jupyter notebooks for dataset inspection and EDA |
| `data/` | Project-approved dataset files or data documentation |
| `outputs/` | EDA charts and other analysis outputs |
| `src/` | Reusable code supporting the EDA |

## Planned workflow

1. Confirm the selected dataset, data dictionary, and available fields.
2. Coordinate with the preprocessing workstream on the cleaned dataset and agreed exclusions.
3. Complete the EDA notebook and calculate only KPIs supported by the data.
4. Save labeled visualizations and summarize evidence-based findings and limitations in the [review report](docs/eda_findings_review.md).

The folder layout follows the team project's repository conventions. Data quality checks, feature distributions, delivery-duration comparisons, and numeric relationship analysis are recorded in their respective notebooks and findings notes.
