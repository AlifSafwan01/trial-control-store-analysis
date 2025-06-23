# Quantium Data Analytics Job Simulation - Experimentation and Uplift Testing

This project is a continuation of the [Retail Sales Analysis](https://github.com/AlifSafwan01/retail-sales-analysis), where the Category Manager for chips requested an evaluation of new trial store layouts. The goal is to determine, through data-driven analysis, wether these layouts should be rolled out across all stores.

## Project Objectives

1. Define metrics to identify the best control stores for each trial store.
2. Analyze trial stores against their corresponding control stores.
3. Perform statistical analysis to assess sales impact and provide actionable recommendations.

## Chip Data

The dataset used in this project, [Chip Data](chip_data.xlsx), is sourced from the cleaned and prepared version in the [Retail Sales Analysis](https://github.com/AlifSafwan01/retail-sales-analysis) project.

To recap, the dataset contains 13 variables and 251,158 observations :-

| Variable | Description |
| --- | --- |
| DATE | The date of transaction occured|
| STORE_NBR | The unique ID assigned to each store |
| LYLTY_CARD_NBR | The unique ID for each customer |
| TXN_ID | The unique ID for each transaction |
| PROD_NBR | The unique ID for each chip product |
| PROD_NAME | The unfiltered name of chip product |
| PROD_QTY | The quantity purchased by the customer per transaction |
| TOT_SALES | The total price per transaction |
| packed_size | The size of the packaging (g) |
| product_brand | The chip brand |
| product_name | The chip product name |
| LIFESTAGE |  The customer's life stage category (7 groups) |
| PREMIUM_CUSTOMER | The customer's budget category (3 groups) |

The Category Manager selected store numbers 77, 86, 88 as trial stores, with the trial period spanning from February 2019 to April 2019.

## Evaluation Metrics for Control Stores

To identify the most suitable control stores for each trial store, we evaluated sales performance during the pre-trial period (July 2018 to January 2019) using the following metrics :-

1. Monthly total sales
2. Monthly number of unique customers
3. Monthly average transaction per customer
4. Monthly average quantity purchased per transaction

Euclidean distance was calculated across these four dimensions to find the closest mathcing control store for each trial store. The formula is :- 

$$
d = \sqrt{(x_t - x_c)^2 + (y_t - y_c)^2 + (z_t - z_c)^2 + (w_t - w_c)^2}
$$

The closest control store identified were :-

| Trial Store | Control Store |
| --- | --- |
| 77 | 233 |
| 86 | 155 |
| 88 | 237 |

## Statistical Analysis

For each trial and corresponding control store, the following were analyzed :-
- Monthly total sales
- Monthly number of customers

To ensure comparability, control store metrics were scaled :-

$$
\text{Scaled Control Sales}_m = \text{Control Sales}_m \times \frac{\sum \text{Trial Sales}}{\sum \text{Control Sales}}
$$
$$
\text{Scaled Control Customer}_m = \text{Control Customer}_m \times \frac{\sum \text{Trial Customer}}{\sum \text{Control Customer}}
$$

We then calculated the absolute differences :-

$$
\text{Absolute Sales Difference}_m = \left| \text{Scaled Control Sales}_m - \text{Trial Sales}_m \right|
$$
$$
\text{Absolute Customer Difference}_m = \left| \text{Scaled Control Customer}_m - \text{Trial Customer}_m \right|
$$

To determine whether the differences are statistically significant, we formulated the following hypothesis :-

1. Sales Hypothesis

$$
\text{Null Hypothesis, H}_0\text{ \: } \mu\_\text{pre trial sales}  = \text{trial monthly sales}
$$

$$
\text{Alternative Hypothesis, H}_1\text{ \: } \mu\_\text{pre trial sales}  \neq \text{trial monthly sales}
$$

2. Customer Count Hypothesis

$$
\text{Null Hypothesis, H}_0\text{ \: } \mu\_\text{pre-trial customers}  = \text{trial monthly customers}
$$

$$
\text{Alternative Hypothesis, H}_1\text{ \: } \mu\_\text{pre-trial customers}  \neq \text{trial monthly customers}
$$

Assuming normal distribution and unknown variance (with only 7 pre-trial months), we used the t-distribution for our test :-

Let,

$$
\mu = \text{Trial monthly value}
$$

$$\bar{X} = \frac{\sum{\text{Pre-trial values}}}{7}$$

$$
Sd = \sqrt{\frac{\sum{(\text{Pre-trial value} - \bar{X})^2}}{6}}
$$

The test statistic is,

$$
T = \frac{\bar{X}-\mu}{\frac{Sd}{\sqrt{7}}}
$$

We compared the resulting T-value to the critical t-distribution value at a 0.025 significant level with 6 degrees of freedom.

## Analysis and Report

The complete report is available in the following formats.
1. [Trial_Control-Stores-Analysis.Rmd](Trial_Control-Stores-Analysis.Rmd) - R markdown format.
2. [Trial_Control-Stores-Analysis.html](Trial_Control-Stores-Analysis.html) - HTML format.
3. [Trial_Control-Stores-Analysis.pdf](Trial_Control-Stores-Analysis.pdf) - PDF format.
