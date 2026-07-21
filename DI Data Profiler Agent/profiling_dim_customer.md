# Profiling Report: ontology.dim_customer

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_customer |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 8 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| customer_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| customer_id | character varying | NO | 20 |  |  | 0 | 0 | 0.00% |
| customer_name | character varying | YES | 80 |  |  | 0 | 0 | 0.00% |
| segment | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| industry | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| account_tier | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |
| hq_country | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| hq_region | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | customer_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| customer_key | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| customer_id | N/A (no data) | N/A (no data) | N/A (no data) |
| customer_name | N/A (no data) | N/A (no data) | N/A (no data) |
| segment | N/A (no data) | N/A (no data) | N/A (no data) |
| industry | N/A (no data) | N/A (no data) | N/A (no data) |
| account_tier | N/A (no data) | N/A (no data) | N/A (no data) |
| hq_country | N/A (no data) | N/A (no data) | N/A (no data) |
| hq_region | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| segment | No rows available for distribution profiling |
| industry | No rows available for distribution profiling |
| account_tier | No rows available for distribution profiling |
| hq_country | No rows available for distribution profiling |
| hq_region | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate customer_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_customer` is structurally valid and available for profiling, but it contains no rows. The schema supports analysis of customer segmentation, industry, account tier, and headquarters geography; however, there is currently no underlying data to evaluate completeness, cardinality behavior, or business value distributions.
