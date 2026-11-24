# Delivery Route Delay Forecasting - EDA

This repository contains Srirami Reddy Ailuri's contribution to the Exploratory Data Analysis (EDA) work for the Delivery Route Delay Forecasting & Logistics Performance Analytics project.

## EDA responsibility

The EDA work will examine delivery performance and, where the selected dataset supports it, explore patterns related to time, routes or distance, traffic, and weather. It will define and calculate relevant performance KPIs, prepare visualizations, and document assumptions and limitations.

## Current status

The initial EDA plan and KPI definitions are documented in `docs/eda_plan.md`. The dataset scope was first profiled on Day 1 and rechecked on Day 2 against Darshan's approved updated cleaned CSV; the CSV is not committed to this repository. Day 2 data quality and univariate findings are documented in `docs/quality_univariate_analysis.md`, with reproducible checks in `Notebooks/quality_univariate_analysis.ipynb`. The `Delivery_Time` unit remains unconfirmed.

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
4. Save labeled visualizations and summarize evidence-based findings and limitations.

The folder layout follows the team project's repository conventions. Day 2 quality checks and feature distributions are recorded in the notebook and findings note.
