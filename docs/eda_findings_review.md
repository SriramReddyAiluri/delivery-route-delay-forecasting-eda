# EDA Findings and Review Limitations

## Purpose and dataset

This report brings together the descriptive findings from the approved `amazon_delivery_cleaned_updated.csv` supplied on 2026-11-24. The file contains 43,739 records and 28 columns and remains in the user's Downloads folder rather than this repository. The source file profile, detailed group comparisons, and numeric relationships are documented in the [dataset quality and univariate analysis](quality_univariate_analysis.md), [delivery duration comparisons](delivery_duration_by_factors.md), and [numeric relationship analysis](numeric_relationship_analysis.md).

`Delivery_Time` is treated as delivery duration, but its unit remains unspecified because it has not been verified. `Pickup_Delay_Minutes` means order-to-pickup duration in minutes. The dataset has no promised delivery time, actual delivery timestamp, or delivery status; accordingly, this report does not calculate on-time, late, completion, or promise-based delay rates.

## Strongest supported patterns

- **Traffic groups differ descriptively.** Median `Delivery_Time` is 100 for Low traffic (`n=14,999`) and 150 for Jam (`n=13,725`). The High group median is 135 (`n=4,296`), so the pattern does not increase steadily through every traffic label.
- **Observed order period and weather groups also differ.** Evening has a median of 140 (`n=17,797`) compared with 100 for Morning (`n=7,674`). Weather medians range from 100 for Sunny (`n=7,078`) to 140 for Cloudy (`n=7,288`).
- **Duration tends to be higher in longer estimated-distance bands.** Median duration ranges from 105 in the shortest distance quartile (`n=10,069`) to 140 in the longest (`n=10,049`). Across valid coordinate pairs, estimated straight-line distance has a Spearman correlation of 0.282 with `Delivery_Time` (`n=40,234`).
- **The strongest selected numeric associations are modest.** Spearman correlations are 0.282 for estimated straight-line distance (`n=40,234`), 0.274 for `Agent_Age` (`n=43,739`), and -0.259 for `Agent_Rating` (`n=43,739`). Correlations for `Order_Hour` (0.090, `n=43,648`), `Pickup_Delay_Minutes` (-0.008, `n=43,648`), and `Order_DayOfWeek` (0.006, `n=43,739`) are smaller or near zero.
- **Some group summaries warrant particular caution.** The Semi-Urban area median is 245 with only 152 records, and the bicycle vehicle group has only 15 records. Grocery has a median of 26, while other product categories have medians from 125 to 130; the large difference merits a definition and data-generation review before operational interpretation.

These findings describe this dataset and its recorded fields. They do not establish that any factor caused a delivery-duration difference or predict an individual delivery outcome.

## Caveats and review limitations

- `Delivery_Time` ranges from 10 to 270 in the recorded scale, but the unit is unverified. Do not add a time unit to labels or prose until source documentation confirms it.
- Pickup duration is a separate measure: `Pickup_Delay_Minutes` is order-to-pickup time in minutes, not a promised-time delivery delay.
- Group comparisons and Spearman correlations are unadjusted. The factors may overlap, and the reported relationships are not causal effects.
- There are 91 rows with missing order-time, weather, traffic, and dependent timing fields. Relevant group comparisons and correlations use complete pairs and disclose their sample sizes; missing values were not imputed.
- Straight-line distance is a great-circle estimate in kilometers, not road distance or route length. Distance analysis includes 40,234 valid coordinate pairs; 188 estimated distances above 50 km were retained, including a maximum of 19,692.70 km, because no exclusion rule was approved.
- Small groups, especially Semi-Urban and bicycle, have less stable summaries. Category sample sizes are shown in the comparison tables and charts.
- The data cannot identify whether a delivery was completed, late, or on time against a promise. Those outcomes require fields and business rules that are absent here.

## Open questions for the next review

1. What is the source-documented unit and definition of `Delivery_Time`?
2. What does one row represent, and what operational process produces the unusually low Grocery duration values?
3. Should coordinate anomalies or other extreme observations be excluded under an agreed rule, or retained with sensitivity analysis?
4. Which additional fields would be available for adjusted analysis or forecasting, including promised and actual delivery timestamps and delivery status?

## Chart and artifact review

The existing factor charts use descriptive titles, label the outcome as `Delivery_Time` without assigning an unverified unit, and include group sample counts in category labels. The distance chart labels estimated straight-line distance in kilometers and identifies its scale. Numeric relationship plots label the axes, report pair counts and correlations in panel titles, distinguish the plotted scatter sample from the full pair count, and label distance in kilometers where applicable. Each correlation heatmap cell reports its Spearman coefficient and pairwise sample size. Figure captions in the detailed analysis notes state the relevant populations and exclusions.

Reproducible artifacts are available in the [numeric relationship notebook](../Notebooks/numeric_relationship_analysis.ipynb) and the [delivery duration comparison notebook](../Notebooks/delivery_duration_by_factors.ipynb). Supporting charts are in [`outputs/`](../outputs/).
