# Profiling Report: ontology.fact_bookings

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | fact_bookings |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Fact Table |
| Grain | Booking transaction / order-line grain |
| Row Count | 0 |
| Column Count | 18 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| booking_id | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| order_number | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |
| order_line_number | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| date_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| customer_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| product_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| partner_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| geography_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| sales_rep_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| contract_key | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| booking_type | character varying | YES | 15 |  |  | 0 | 0 | 0.00% |
| is_renewal | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| quantity | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| unit_list_price_usd | numeric | YES |  | 12 | 2 | 0 | 0 | 0.00% |
| discount_pct | numeric | YES |  | 5 | 2 | 0 | 0 | 0.00% |
| booking_amount_usd | numeric | YES |  | 14 | 2 | 0 | 0 | 0.00% |
| acv_usd | numeric | YES |  | 14 | 2 | 0 | 0 | 0.00% |
| tcv_usd | numeric | YES |  | 14 | 2 | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | booking_id |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| booking_id | N/A (no data) | N/A (no data) | N/A (no data) |
| order_line_number | N/A (no data) | N/A (no data) | N/A (no data) |
| date_key | N/A (no data) | N/A (no data) | N/A (no data) |
| customer_key | N/A (no data) | N/A (no data) | N/A (no data) |
| product_key | N/A (no data) | N/A (no data) | N/A (no data) |
| partner_key | N/A (no data) | N/A (no data) | N/A (no data) |
| geography_key | N/A (no data) | N/A (no data) | N/A (no data) |
| sales_rep_key | N/A (no data) | N/A (no data) | N/A (no data) |
| contract_key | N/A (no data) | N/A (no data) | N/A (no data) |
| is_renewal | N/A (no data) | N/A (no data) | N/A (no data) |
| quantity | N/A (no data) | N/A (no data) | N/A (no data) |
| unit_list_price_usd | N/A (no data) | N/A (no data) | N/A (no data) |
| discount_pct | N/A (no data) | N/A (no data) | N/A (no data) |
| booking_amount_usd | N/A (no data) | N/A (no data) | N/A (no data) |
| acv_usd | N/A (no data) | N/A (no data) | N/A (no data) |
| tcv_usd | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| order_number | N/A (no data) | N/A (no data) | N/A (no data) |
| booking_type | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| booking_type | No rows available for distribution profiling |
| is_renewal | No rows available for distribution profiling |

## Missing Data Statistics

| Metric | Value |
| --- | --- |
| Total Rows | 0 |
| Columns with Missing Data | 0 observable from data because table is empty |
| Missing Data Assessment | No populated rows available to assess missingness patterns |

## Data Quality Summary

| Indicator | Status | Details |
| --- | --- | --- |
| Table existence | PASS | Table verified in schema ontology |
| Structural metadata availability | PASS | Column definitions discovered successfully |
| Row presence | WARNING | Table is empty |
| Primary key duplication | PASS | No duplicate booking_id values detected |
| Metric profiling | WARNING | Financial and quantity metrics cannot be assessed because row count is zero |
| Distribution profiling | WARNING | Not available because row count is zero |
| Referential profiling readiness | PASS | Foreign-key-bearing columns are present for dimensional joins |

## Overall Profiling Summary

`ontology.fact_bookings` is the central fact table in the Cisco bookings star schema and is structurally ready for analytical use, but it currently contains no rows. Because the table is empty, no measures such as booking amount, ACV, TCV, quantity, discount, or booking type mix can be evaluated. Once populated, this table will support demand, renewal, partner, product, and time-based booking analytics.
