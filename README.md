# Quantium Data Analytics Job Simulation - Experimentation and Uplift Testing

This project is contiounation of [Retail Sales Analysis](https://github.com/AlifSafwan01/retail-sales-analysis), where the Category Manager of Chips has asked us to test the impact of the new trial layouats with a data driven recommendation to wether or not the trial layout should be rolled out to all their stores.

The objective of this project is as follows :-
1. Define metrics to select best control stores for each trial stores.
2. Analyze trial stores against controls.
3. Perform statistical analysis to assess sales differences and formulate recommendations.

## Chip Data

Chip data used where this data from [Retail Sales Analysis](https://github.com/AlifSafwan01/retail-sales-analysis) that already cleaned and prepared version.

For a recall, this data contains 13 variables and 251,158 observations :-

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

The Category Manager asked us to test the impact of trial store with STORE_NBR 77, 86 and 88 for trial duration from February 2019 until April 2019.

## Evaluation Metrics for Control Stores

To find best control stores for each trial stores, the evaluation metrics created by evaluating each store slaes performance during each pre-trial months which is from July 2018 until January 2019.

The evaluation metrics involved as follow :-
1. Monthly total sales
2. Monthly unique customer
3. Monthly average transaction per customer
4. Monthly average quantity purchased per transaction

From this evaluation metrics, best control store evaluate using euclidean distance each store compare to trial store. Since, in the evaluation have 4 criterias, then dimension for euclidean is 4D. The store that shortest distance with trial store is the best control store.

euclidean distance between trial and control, $d = \sqrt{(x_t - x_c)^2 + (y_t - y_c)^2 + (z_t - z_c)^2 + (w_t - w_c)^2}$.

After evaluation, the trial and selected control store as follow :-

| Trial Store | Control Store |
| --- | --- |
| 77 | 233 |
| 86 | 155 |
| 88 | 237 |

## Statisticals Analysis

Monthly total sales and Monthly number of customer will be tested for each trial and control store. Then the monthly total sales and monthly number of customer of control store need to scale to make it almost same as trial.

$\text{Scaled Control Sales}_t = \text{Control Sales}_t \times \frac{\sum \text{Trial Sales}}{\sum \text{Control Sales}}$

$\text{Scaled Control Number of Customer}_t = \text{Control Number of Customer}_t \times \frac{\sum \text{Trial Number of Customer}}{\sum \text{Control Number of Customer}}$
