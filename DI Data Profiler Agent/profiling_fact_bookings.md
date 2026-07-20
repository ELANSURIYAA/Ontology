# Profiling Report: ontology.fact_bookings

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | fact_bookings |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Central fact table at order-line booking grain |
| Row Count | 0 |
| Column Count | 18 |
| Database Version | PostgreSQL 16.14 |
| Profiling Status | Profiled successfully |
| Data Population Status | Empty table |

## Column Profile Summary

| Ordinal Position | Column Name | Data Type | Nullable | Null Count | Null % | Distinct Count | Duplicate Count |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | booking_id | integer | NO | 0 | N/A* | 0 | 0 |
| 2 | order_number | character varying | YES | 0 | N/A* | 0 | 0 |
| 3 | order_line_number | integer | YES | 0 | N/A* | 0 | 0 |
| 4 | date_key | integer | YES | 0 | N/A* | 0 | 0 |
| 5 | customer_key | integer | YES | 0 | N/A* | 0 | 0 |
| 6 | product_key | integer | YES | 0 | N/A* | 0 | 0 |
| 7 | partner_key | integer | YES | 0 | N/A* | 0 | 0 |
| 8 | geography_key | integer | YES | 0 | N/A* | 0 | 0 |
| 9 | sales_rep_key | integer | YES | 0 | N/A* | 0 | 0 |
| 10 | contract_key | integer | YES | 0 | N/A* | 0 | 0 |
| 11 | booking_type | character varying | YES | 0 | N/A* | 0 | 0 |
| 12 | is_renewal | integer | YES | 0 | N/A* | 0 | 0 |
| 13 | quantity | integer | YES | 0 | N/A* | 0 | 0 |
| 14 | unit_list_price_usd | numeric | YES | 0 | N/A* | 0 | 0 |
| 15 | discount_pct | numeric | YES | 0 | N/A* | 0 | 0 |
| 16 | booking_amount_usd | numeric | YES | 0 | N/A* | 0 | 0 |
| 17 | acv_usd | numeric | YES | 0 | N/A* | 0 | 0 |
| 18 | tcv_usd | numeric | YES | 0 | N/A* | 0 | 0 |

\* Null percentage is not computable because row count is 0.

## Column Data Types Summary

| Data Type | Column Count | Columns |
| --- | --- | --- |
| integer | 10 | booking_id, order_line_number, date_key, customer_key, product_key, partner_key, geography_key, sales_rep_key, contract_key, is_renewal |
| character varying | 2 | order_number, booking_type |
| numeric | 5 | unit_list_price_usd, discount_pct, booking_amount_usd, acv_usd, tcv_usd |
| integer | 1 | quantity |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Total Rows | 0 |
| Columns with Nulls Observed | 0 |
| Columns Fully Populated | 0 observable due to no records |
| Missing Data Assessment | No data available to assess completeness |

## Distinct Value Statistics

| Column Name | Distinct Count | Observation |
| --- | --- | --- |
| booking_id | 0 | No values present |
| order_number | 0 | No values present |
| order_line_number | 0 | No values present |
| date_key | 0 | No values present |
| customer_key | 0 | No values present |
| product_key | 0 | No values present |
| partner_key | 0 | No values present |
| geography_key | 0 | No values present |
| sales_rep_key | 0 | No values present |
| contract_key | 0 | No values present |
| booking_type | 0 | No values present |
| is_renewal | 0 | No values present |
| quantity | 0 | No values present |
| unit_list_price_usd | 0 | No values present |
| discount_pct | 0 | No values present |
| booking_amount_usd | 0 | No values present |
| acv_usd | 0 | No values present |
| tcv_usd | 0 | No values present |

## Duplicate Statistics

| Column Name | Duplicate Count | Assessment |
| --- | --- | --- |
| booking_id | 0 | No rows present; duplicate assessment not meaningful |
| order_number | 0 | No rows present |
| order_line_number | 0 | No rows present |
| date_key | 0 | No rows present |
| customer_key | 0 | No rows present |
| product_key | 0 | No rows present |
| partner_key | 0 | No rows present |
| geography_key | 0 | No rows present |
| sales_rep_key | 0 | No rows present |
| contract_key | 0 | No rows present |
| booking_type | 0 | No rows present |
| is_renewal | 0 | No rows present |
| quantity | 0 | No rows present |
| unit_list_price_usd | 0 | No rows present |
| discount_pct | 0 | No rows present |
| booking_amount_usd | 0 | No rows present |
| acv_usd | 0 | No rows present |
| tcv_usd | 0 | No rows present |

## Numeric Statistics

| Column Name | Min | Max | Avg | Assessment |
| --- | --- | --- | --- | --- |
| booking_id | N/A | N/A | N/A | No rows available |
| order_line_number | N/A | N/A | N/A | No rows available |
| date_key | N/A | N/A | N/A | No rows available |
| customer_key | N/A | N/A | N/A | No rows available |
| product_key | N/A | N/A | N/A | No rows available |
| partner_key | N/A | N/A | N/A | No rows available |
| geography_key | N/A | N/A | N/A | No rows available |
| sales_rep_key | N/A | N/A | N/A | No rows available |
| contract_key | N/A | N/A | N/A | No rows available |
| is_renewal | N/A | N/A | N/A | No rows available |
| quantity | N/A | N/A | N/A | No rows available |
| unit_list_price_usd | N/A | N/A | N/A | No rows available |
| discount_pct | N/A | N/A | N/A | No rows available |
| booking_amount_usd | N/A | N/A | N/A | No rows available |
| acv_usd | N/A | N/A | N/A | No rows available |
| tcv_usd | N/A | N/A | N/A | No rows available |

## Date Statistics

No physical date columns exist in this table. Temporal analysis depends on the foreign key `date_key` to `ontology.dim_date`.

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length | Value Distribution |
| --- | --- | --- | --- | --- |
| order_number | N/A | N/A | N/A | No rows available |
| booking_type | N/A | N/A | N/A | No rows available |

## Value Distribution Summary

| Column Name | Top Values |
| --- | --- |
| booking_type | No rows available |
| is_renewal | No rows available |
| order_number | No rows available |
| customer_key | No rows available |
| product_key | No rows available |
| partner_key | No rows available |

## Missing Data Statistics

| Category | Result |
| --- | --- |
| Row-level missingness | Not assessable because table is empty |
| Column-level missingness | Not observable because table is empty |
| Mandatory column risk | booking_id is structurally mandatory, but no loaded data exists |
| Referential completeness | Cannot evaluate foreign key population without rows |

## Data Quality Summary

| Indicator | Status | Details |
| --- | --- | --- |
| Primary key defined | PASS | booking_id is defined as primary key in metadata |
| Foreign keys defined | PASS | 7 foreign key relationships exist to dimension tables |
| Fact grain documented | PASS | Order-line booking grain documented in metadata |
| Data presence | FAIL | Table contains 0 rows |
| Measure quality assessment | WARNING | Cannot evaluate booking, ACV, TCV, discount, or quantity distributions without data |
| Referential quality assessment | WARNING | Cannot validate populated foreign keys without rows |
| Booking type domain assessment | WARNING | No values available for New/Renewal/Upsell distribution |

## Overall Profiling Summary

The table `ontology.fact_bookings` is the central fact table in the Cisco bookings star schema and was successfully profiled structurally in PostgreSQL. However, it currently contains no booking records. Because of the zero-row state, there are no observable transaction distributions, financial measure statistics, renewal patterns, or referential completeness metrics. The table design is analytically appropriate, but the dataset is not yet loaded.

---
Generated by DI Data Profiler Agent