# Exploratory Data Analysis Plan

## Project

- Project: Delivery Route Delay Forecasting & Logistics Performance Analytics
- Role: Srirami - Exploratory Data Analysis
- Status: Duration-by-factor comparisons and numeric relationship analysis completed using Darshan's approved updated cleaned CSV; the `Delivery_Time` unit remains unconfirmed

## Purpose

Explore delivery duration and examine how it varies with time, estimated distance, traffic, weather, and other available factors. The supplied dataset has no promised delivery time, actual delivery timestamp, or delivery status, so it cannot support promise-based delay or on-time performance measures. The analysis will describe patterns in the selected dataset and provide visualizations for the project team.

This document records the EDA plan and KPI boundaries. Data quality findings and duration comparisons are documented in their respective analysis notes.

## Objectives

- Understand the dataset's time period, size, fields, and delivery records.
- Describe the scale and distribution of delivery duration and pickup delay where their definitions support analysis.
- Compare delivery outcomes across available time, route, distance, traffic, and weather categories.
- Identify data limitations that could affect interpretation.
- Prepare visualizations and observations for the project's modeling, evaluation, and dashboard work.

## Questions to investigate

1. How does delivery duration vary across the available observations?
2. Do delivery durations differ by order date/time, estimated distance, traffic, weather, or other available categories?
3. How does the engineered order-to-pickup duration vary, and how is it associated with delivery duration?
4. Are missing, inconsistent, or unusual values limiting the analysis?

## Planned KPIs

Calculate a KPI only when the selected dataset has the required fields and documented meanings. For the supplied dataset snapshot, describe duration rather than promise-based delay. `Delivery_Time` is documented as delivery duration, but its unit is not confirmed; do not label it as minutes until the original source documentation confirms that unit.

| KPI | Planned definition | Fields needed |
|---|---|---|
| Delivery record count | Number of observed rows overall or within a reported group | One row per delivery or a delivery identifier; grouping field as applicable |
| Mean / median / 90th percentile delivery duration | Summary of `Delivery_Time`; report the unit as unspecified unless verified | `Delivery_Time`; source documentation for unit labeling |
| Mean / median pickup delay | Summary of the order-to-pickup duration in minutes | `Pickup_Delay_Minutes` |
| Estimated straight-line distance | Great-circle distance estimated from store and drop coordinates; not road distance | Valid store and drop coordinates |
| On-time / late delivery rate | Not supported by this dataset: it has no promised time, actual delivery timestamp, delivery status, or on-time rule | Not available in the supplied dataset |
| Promise-based delay duration | Not supported by this dataset: scheduled and actual delivery timestamps are absent | Not available in the supplied dataset |

### Eligibility and interpretation

- The dataset has no delivery status field, so cancelled, incomplete, or pending records cannot be identified from status.
- Do not treat missing values as on-time or infer completion status.
- State units and time zone only when verified; the `Delivery_Time` unit is currently unconfirmed.

## Analysis approach

1. Inspect the data dictionary and confirm field meanings, units, and time zone. The approved updated cleaned CSV was selected for EDA.
2. Review record counts, date coverage, missing values, duplicate records, and plausible value ranges. Data quality and univariate results are documented in `docs/quality_univariate_analysis.md` and `Notebooks/quality_univariate_analysis.ipynb`.
3. Confirm the definition and unit of `Delivery_Time`; do not derive a promise-based delay without scheduled and actual delivery times.
4. Calculate applicable KPIs overall, then compare them across available categories.
5. Include group sizes with rates and averages so small groups are not overinterpreted.
6. Record assumptions, exclusions, and limitations with the results.

Data cleaning and preparation belong to the preprocessing workstream. Coordinate with Darshan on the cleaned dataset and agreed exclusions before final analysis.

## Planned visualizations

- KPI summary for delivery record count and supported duration summaries.
- Histogram or box plot of delivery duration and pickup delay.
- Delivery volume and duration over time, if dates are suitable for grouping.
- Bar chart of duration by location or category, where group sizes are adequate.
- Scatter plot of estimated straight-line distance and delivery duration, if coordinates are valid.
- Comparison of delivery duration across traffic and weather categories.

Use clear units, labels, and sample sizes. An association does not by itself prove that a factor caused a delay.

## Expected deliverables

- This EDA plan and KPI definitions.
- A Jupyter notebook documenting data checks, calculations, and analysis after the dataset is finalized.
- Labeled visualizations saved in `outputs/`.
- A concise summary of findings, assumptions, and limitations based on the actual dataset.

Completed notebooks and labeled charts are saved in `Notebooks/` and `outputs/` following the existing repository layout. Numeric relationship findings are documented in `docs/numeric_relationship_analysis.md` and reproducible in `Notebooks/numeric_relationship_analysis.ipynb`.

## Dependencies and limitations

- The updated cleaned CSV was approved for EDA and provided by Darshan; the file is not committed to this repository.
- The `Delivery_Time` unit and any additional outlier treatment or exclusions still need source/workstream confirmation.
- Traffic, weather, route, or distance analysis requires relevant fields in the dataset.
- EDA describes patterns in available data; it does not establish causation.

## Document status

Data quality and univariate analysis, duration-by-factor comparisons, and numeric relationship analysis were completed against the approved updated cleaned CSV. Quality findings are in `docs/quality_univariate_analysis.md` and `Notebooks/quality_univariate_analysis.ipynb`. Duration findings and group comparisons are in `docs/delivery_duration_by_factors.md` and `Notebooks/delivery_duration_by_factors.ipynb`; charts are saved in `outputs/`. Numeric relationships are documented in `docs/numeric_relationship_analysis.md` and `Notebooks/numeric_relationship_analysis.ipynb`. Distance analysis excludes missing store coordinates and labels the derived measure estimated straight-line distance. The `Delivery_Time` unit remains unconfirmed.
