# Day 2: Data Quality and Univariate Analysis

## Dataset and method

This profile uses the approved cleaned file `amazon_delivery_cleaned_updated.csv`, supplied by Darshan on 2026-11-24. The source CSV is not committed to this repository. The notebook reads it from the user's Downloads folder. This is a descriptive profile of the supplied dataset; it does not independently verify upstream collection or cleaning steps.

## Dataset quality

- **Rows:** 43,739
- **Columns:** 28
- **Order date coverage:** 2022-02-11 through 2022-04-06 (44 distinct dates)
- **Exact duplicate rows:** 0
- **Duplicate `Order_ID` values:** 0
- **Missing `Delivery_Time`:** 0

No exact duplicate rows or repeated `Order_ID` values were found. This is a file-level check; uniqueness does not by itself establish what one row represents.

### Missing values

| Field | Missing records | Share of all records |
|---|---:|---:|
| `Store_Latitude` | 3,505 | 8.01% |
| `Store_Longitude` | 3,505 | 8.01% |
| `Order_Time` | 91 | 0.21% |
| `Weather` | 91 | 0.21% |
| `Traffic` | 91 | 0.21% |
| `Order_Hour` | 91 | 0.21% |
| `Order_Minute` | 91 | 0.21% |
| `Pickup_Delay_Minutes` | 91 | 0.21% |
| `Order_Time_Period` | 91 | 0.21% |

The 91 records missing `Order_Time`, `Weather`, and `Traffic` also lack the dependent order-time fields `Order_Hour`, `Order_Minute`, `Pickup_Delay_Minutes`, and `Order_Time_Period`. Store latitude and longitude are both missing on the same 3,505 records. Darshan said these values were retained because reliable replacements were unavailable; coordinates originally coded as `(0,0)` were converted to missing. The `Store_Location_Missing` and `Order_Time_Missing` flags agree with the corresponding missing values in all rows; no records have only one of the two store coordinates missing.

## Numeric feature distributions

| Field | Non-missing | Missing | Mean | Std. dev. | Min | 25th pct. | Median | 75th pct. | 90th pct. | Max |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `Agent_Age` | 43,739 | 0 | 29.58 | 5.80 | 20.00 | 25.00 | 30.00 | 35.00 | 38.00 | 50.00 |
| `Agent_Rating` | 43,739 | 0 | 4.63 | 0.33 | 1.00 | 4.50 | 4.70 | 4.90 | 4.90 | 5.00 |
| `Delivery_Time` | 43,739 | 0 | 124.91 | 51.92 | 10.00 | 90.00 | 125.00 | 160.00 | 195.00 | 270.00 |
| `Pickup_Delay_Minutes` | 43,648 | 91 | 9.99 | 4.09 | 5.00 | 5.00 | 10.00 | 15.00 | 15.00 | 15.00 |

`Delivery_Time` is treated as delivery duration; its unit is still unconfirmed, so the values above have no time unit label. `Pickup_Delay_Minutes` is the order-to-pickup duration in minutes. The `Agent_Age` and `Agent_Rating` summaries are descriptive only and do not establish data validity.

## Categorical feature distributions


### `Weather`

| Value | Records | Share |
|---|---:|---:|
| Fog | 7,440 | 17.01% |
| Stormy | 7,374 | 16.86% |
| Cloudy | 7,288 | 16.66% |
| Sandstorms | 7,245 | 16.56% |
| Windy | 7,223 | 16.51% |
| Sunny | 7,078 | 16.18% |
| Missing | 91 | 0.21% |
### `Traffic`

| Value | Records | Share |
|---|---:|---:|
| Low | 14,999 | 34.29% |
| Jam | 13,725 | 31.38% |
| Medium | 10,628 | 24.30% |
| High | 4,296 | 9.82% |
| Missing | 91 | 0.21% |
### `Vehicle`

| Value | Records | Share |
|---|---:|---:|
| motorcycle | 25,527 | 58.36% |
| scooter | 14,639 | 33.47% |
| van | 3,558 | 8.13% |
| bicycle | 15 | 0.03% |
### `Area`

| Value | Records | Share |
|---|---:|---:|
| Metropolitian | 32,698 | 74.76% |
| Urban | 9,751 | 22.29% |
| Other | 1,138 | 2.60% |
| Semi-Urban | 152 | 0.35% |
### `Order_Time_Period`

| Value | Records | Share |
|---|---:|---:|
| Evening | 17,797 | 40.69% |
| Night | 14,148 | 32.35% |
| Morning | 7,674 | 17.54% |
| Afternoon | 4,029 | 9.21% |
| Missing | 91 | 0.21% |
### `Category`

| Value | Records | Share |
|---|---:|---:|
| Electronics | 2,849 | 6.51% |
| Books | 2,824 | 6.46% |
| Jewelry | 2,802 | 6.41% |
| Toys | 2,781 | 6.36% |
| Skincare | 2,772 | 6.34% |
| Snacks | 2,770 | 6.33% |
| Outdoors | 2,747 | 6.28% |
| Apparel | 2,726 | 6.23% |
| Sports | 2,719 | 6.22% |
| Grocery | 2,691 | 6.15% |
| Pet Supplies | 2,690 | 6.15% |
| Home | 2,685 | 6.14% |
| Cosmetics | 2,677 | 6.12% |
| Kitchen | 2,673 | 6.11% |
| Clothing | 2,667 | 6.10% |
| Shoes | 2,666 | 6.10% |

## Interpretation and limits

- The most frequent observed `Order_Time_Period` is Evening (17,797 records); 91 records have no period because order-time inputs are missing.
- `Delivery_Time` is a duration, not delay against a promised time. This dataset has no promised delivery time, actual delivery timestamp, or delivery status; on-time rate, late rate, completion rate, and promise-based delay are unsupported.
- Do not call `Delivery_Time` minutes until its unit is confirmed from original source documentation.
- These are univariate summaries. They do not explain causes or compare delivery duration across groups.
- Values in this report are calculated from the approved CSV and should be refreshed if the analysis file changes.
