# Profiling Report: ontology.fact_bookings

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | fact_bookings |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Fact |
| Grain | One row per booking transaction / order line |
| Row Count | 0 |
| Column Count | 18 |
| Primary Key | booking_id |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| booking_id | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| order_number | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| order_line_number | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| date_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| customer_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| product_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| partner_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| geography_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| sales_rep_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| contract_key | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| booking_type | character varying | max length 15 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| is_renewal | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| quantity | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| unit_list_price_usd | numeric | precision 12, scale 2 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| discount_pct | numeric | precision 5, scale 2 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| booking_amount_usd | numeric | precision 14, scale 2 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| acv_usd | numeric | precision 14, scale 2 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| tcv_usd | numeric | precision 14, scale 2 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| booking_id | No values available; table is empty |
| order_number | No values available; table is empty |
| order_line_number | No values available; table is empty |
| date_key | No values available; table is empty |
| customer_key | No values available; table is empty |
| product_key | No values available; table is empty |
| partner_key | No values available; table is empty |
| geography_key | No values available; table is empty |
| sales_rep_key | No values available; table is empty |
| contract_key | No values available; table is empty |
| booking_type | No values available; table is empty |
| is_renewal | No values available; table is empty |
| quantity | No values available; table is empty |
| unit_list_price_usd | No values available; table is empty |
| discount_pct | No values available; table is empty |
| booking_amount_usd | No values available; table is empty |
| acv_usd | No values available; table is empty |
| tcv_usd | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| booking_id | N/A | N/A | N/A |
| order_line_number | N/A | N/A | N/A |
| date_key | N/A | N/A | N/A |
| customer_key | N/A | N/A | N/A |
| product_key | N/A | N/A | N/A |
| partner_key | N/A | N/A | N/A |
| geography_key | N/A | N/A | N/A |
| sales_rep_key | N/A | N/A | N/A |
| contract_key | N/A | N/A | N/A |
| is_renewal | N/A | N/A | N/A |
| quantity | N/A | N/A | N/A |
| unit_list_price_usd | N/A | N/A | N/A |
| discount_pct | N/A | N/A | N/A |
| booking_amount_usd | N/A | N/A | N/A |
| acv_usd | N/A | N/A | N/A |
| tcv_usd | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| order_number | min_len=null, max_len=null, avg_len=null |
| booking_type | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 18 |
| Columns With Non-Zero Distinct Values | 0 |
| Note | Distinct counts are 0 because the table contains no rows |

## Duplicate Statistics

| Metric | Value |
| --- | --- |
| Duplicate Primary Keys | 0 |
| Duplicate Value Observation | No duplicate values observed because the table is empty |

## Missing Data Statistics

| Metric | Value |
| --- | --- |
| Missing Data Assessment | Not measurable from records because row count = 0 |
| Structural Nullable Columns | order_number, order_line_number, date_key, customer_key, product_key, partner_key, geography_key, sales_rep_key, contract_key, booking_type, is_renewal, quantity, unit_list_price_usd, discount_pct, booking_amount_usd, acv_usd, tcv_usd |
| Structurally Required Columns | booking_id |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | booking_id |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Foreign Key Structure Present | PASS | Keys to date, customer, product, partner, geography, sales rep, and contract dimensions |
| Data Presence | WARNING | Table contains 0 rows |
| Measure Profiling | WARNING | No numeric fact values available for statistical analysis |
| Column Metadata Availability | PASS | All 18 columns profiled |

## Overall Profiling Summary

The `ontology.fact_bookings` table is structurally modeled as a fact table at booking transaction grain with 18 columns, a primary key on `booking_id`, and the expected foreign key links to all dimensions. However, the table currently contains no data, so no booking distributions, financial measure statistics, or completeness patterns can be inferred from records at this time.