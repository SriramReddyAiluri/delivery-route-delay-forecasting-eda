# Exploratory Data Analysis Plan

## Project

- Project: Delivery Route Delay Forecasting & Logistics Performance Analytics
- Role: Srirami - Exploratory Data Analysis
- Status: Initial plan; dataset not yet finalized

## Purpose

Explore delivery performance and examine how delays may relate to time, route or distance, traffic, and weather. The analysis will describe patterns in the selected dataset and provide visualizations for the project team.

This document defines planned analysis only. It does not report findings.

## Objectives

- Understand the dataset's time period, size, fields, and delivery records.
- Measure on-time performance and the scale and distribution of delays.
- Compare delivery outcomes across available time, route, distance, traffic, and weather categories.
- Identify data limitations that could affect interpretation.
- Prepare visualizations and observations for the project's modeling, evaluation, and dashboard work.

## Questions to investigate

1. What share of eligible deliveries are on time or delayed?
2. How large are delays, using typical and high-end delay measures?
3. Do outcomes differ by day, time period, or season, if those fields exist?
4. How do delays vary by route, origin, destination, or distance, if available?
5. Are delays associated with recorded traffic or weather conditions?
6. Are missing, inconsistent, or unusual values limiting the analysis?

## Planned KPIs

Calculate a KPI only when the selected dataset has the required fields. Confirm how the dataset defines "on time," scheduled time, and completed delivery before calculating results.

| KPI | Planned definition | Fields needed |
|---|---|---|
| On-time delivery rate | Eligible completed deliveries meeting the dataset's on-time rule, divided by eligible completed deliveries, times 100 | Delivery status and on-time indicator, or scheduled and actual delivery times |
| Delayed delivery rate | Eligible completed deliveries classified as late, divided by eligible completed deliveries, times 100 | Delivery status and delay indicator, or scheduled and actual delivery times |
| Average delay (minutes) | Mean of actual delivery time minus scheduled delivery time, in minutes | Scheduled and actual delivery times |
| Median delay (minutes) | Median of actual delivery time minus scheduled delivery time, in minutes | Scheduled and actual delivery times |
| 90th percentile delay (minutes) | Delay value at or below which 90 percent of eligible deliveries fall | Scheduled and actual delivery times |
| Delivery volume | Count of eligible delivery records in the selected period or group | Delivery identifier or one row per delivery; date/time for grouping |
| Average delivery distance | Mean recorded distance for eligible deliveries | Distance |
| Completion rate, if supported | Completed deliveries divided by scheduled deliveries, times 100 | Delivery identifier and delivery status |

### Eligibility and interpretation

- Exclude or separately report cancelled, incomplete, or pending deliveries where appropriate.
- Do not treat missing delivery times as on-time.
- Preserve negative time differences as early deliveries unless the dataset's rules specify otherwise.
- State the time zone and units when known.

## Analysis approach

1. Inspect the data dictionary and confirm field meanings, units, time zone, and status codes.
2. Review record counts, date coverage, missing values, duplicate records, and plausible value ranges.
3. Confirm how scheduled and actual delivery times define delay.
4. Calculate applicable KPIs overall, then compare them across available categories.
5. Include group sizes with rates and averages so small groups are not overinterpreted.
6. Record assumptions, exclusions, and limitations with the results.

Data cleaning and preparation belong to the preprocessing workstream. Coordinate with Darshan on the cleaned dataset and agreed exclusions before final analysis.

## Planned visualizations

- KPI summary for delivery volume, on-time rate, delayed rate, and delay duration.
- Histogram or box plot of delay duration.
- Delivery volume and on-time rate over time, if dates are available.
- Bar chart of delay or on-time rate by route or location, where group sizes are adequate.
- Scatter plot of distance and delay, if both fields are available.
- Comparison of delay across traffic and weather categories, if those fields are available.

Use clear units, labels, and sample sizes. An association does not by itself prove that a factor caused a delay.

## Expected deliverables

- This EDA plan and KPI definitions.
- A Jupyter notebook documenting data checks, calculations, and analysis after the dataset is finalized.
- Labeled visualizations saved in `visualizations/`.
- A concise summary of findings, assumptions, and limitations based on the actual dataset.

## Dependencies and limitations

- Dataset selection and field availability depend on Jagan's dataset review.
- KPI definitions may need adjustment to match the selected dataset's documentation.
- Traffic, weather, route, or distance analysis requires relevant fields in the dataset.
- EDA describes patterns in available data; it does not establish causation.

## Document status

Initial EDA plan and KPI definitions prepared for project planning before dataset selection.
