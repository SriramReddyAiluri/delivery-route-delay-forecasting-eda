# Day 1: Dataset Scope and EDA Boundaries

## Status and source

This is a Day 1 profile of the supplied file `amazon_delivery_cleaned.csv`. The file is available locally for inspection but is not committed to this repository. Confirm with Darshan and Jagan that this exact snapshot is the finalized dataset before using these counts as the baseline for the remaining EDA days. The profile describes the supplied file; it does not certify the dataset's provenance or cleaning quality.

## Snapshot profile

- **Rows:** 43,739
- **Columns:** 28
- **Order date coverage:** 2022-02-11 through 2022-04-06
- **Exact duplicate rows:** 0
- **`Delivery_Time` observed range:** 10 to 270; Darshan defines this as delivery duration, but its unit remains unconfirmed.
- **`Pickup_Delay_Minutes`:** engineered order-to-pickup duration in minutes; 91 values are missing. Among the nonmissing values in this file, the range is 5 to 15 minutes.

These values were read from the supplied CSV. A zero count of exact duplicate rows does not establish that every record is semantically unique; the meaning and uniqueness of `Order_ID` should be confirmed as part of data quality review.

## Available fields by analysis use

- **Record identifier:** `Order_ID`.
- **Delivery and pickup durations:** `Delivery_Time`, `Pickup_Delay_Minutes`.
- **Coordinates:** `Store_Latitude`, `Store_Longitude`, `Drop_Latitude`, `Drop_Longitude`; store coordinates are missing for 3,505 records. Straight-line distance can be estimated only when both locations are valid, and must not be presented as road distance.
- **Order timing:** `Order_Date`, `Order_Time`, `Pickup_Time`, year/month/day/day-of-week/hour/minute fields, and `Order_Time_Period`; order-time-derived fields are missing for 91 records.
- **Context categories:** `Weather`, `Traffic`, `Vehicle`, `Area`, and `Category`.
- **Agent fields:** `Agent_Age`, `Agent_Rating`.
- **Missingness indicators:** `Store_Location_Missing`, `Order_Time_Missing`.

The complete column list is in the field-inspection notebook. The supplied file contains 91 rows with missing `Order_Time`, `Weather`, and `Traffic`; the dependent order-time fields `Order_Hour`, `Order_Minute`, `Pickup_Delay_Minutes`, and `Order_Time_Period` are also missing for those rows. Darshan advised retaining these missing values because reliable replacements are unavailable. Store-coordinate missingness is represented as missing rather than the original `(0,0)` values.

## Target and KPI boundaries

`Delivery_Time` is the available outcome for descriptive analysis and potential modeling, subject to confirmation of its unit and final target definition. It is a delivery duration, not a delay relative to a promised time.

The dataset has no promised delivery time, actual delivery timestamp, or delivery status. Therefore, this dataset cannot support on-time rate, late rate, completion rate, or promise-based delay calculations. Do not label `Delivery_Time` as minutes until original source documentation confirms the unit. `Pickup_Delay_Minutes` is the order-to-pickup duration in minutes and is distinct from delivery duration.

Supported descriptive measures include record counts, delivery-duration summaries (with unit unspecified until verified), pickup-delay summaries in minutes, and comparisons across observed features. Coordinate-based analysis must exclude records with missing store coordinates and state that estimated straight-line distance differs from road distance. Associations in EDA do not establish causation.

## Day 1 follow-up

Before interpreting results, ask Darshan/Jagan to confirm:

1. Whether this exact CSV is the finalized dataset approved for EDA.
2. The original source documentation and unit for `Delivery_Time`.
3. The cleaning steps and whether any remaining outlier treatment or exclusions are planned.
4. Whether `Order_ID` is expected to be unique and what one row represents.
