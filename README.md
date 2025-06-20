# Quantium Data Analytics Job Simulation - Experimentation and Uplift Testing

This project is contiounation of [Retail Sales Analysis](https://github.com/AlifSafwan01/retail-sales-analysis), where the Category Manager of Chips has asked us to test the impact of the new trial layouats with a data driven recommendation to wether or not the trial layout should be rolled out to all their stores.

The objective of this project is as follows :-
1. Define metrics to select best control stores for each trial stores.
2. Analyze trial stores against controls.
3. Perform statistical analysis to assess sales differences and formulate recommendations.

## Chip Data

Chip data used where this data from [Retail Sales Analysis]((https://github.com/AlifSafwan01/retail-sales-analysis) that already cleaned and prepared version.

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

## Evaluations Metrics
