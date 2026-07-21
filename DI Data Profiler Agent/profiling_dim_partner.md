# Profiling Report: ontology.dim_partner

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_partner |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 6 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| partner_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| partner_id | character varying | NO | 20 |  |  | 0 | 0 | 0.00% |
| partner_name | character varying | YES | 60 |  |  | 0 | 0 | 0.00% |
| partner_type | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| partner_tier | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| route_to_market | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | partner_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| partner_key | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| partner_id | N/A (no data) | N/A (no data) | N/A (no data) |
| partner_name | N/A (no data) | N/A (no data) | N/A (no data) |
| partner_type | N/A (no data) | N/A (no data) | N/A (no data) |
| partner_tier | N/A (no data) | N/A (no data) | N/A (no data) |
| route_to_market | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| partner_type | No rows available for distribution profiling |
| partner_tier | No rows available for distribution profiling |
| route_to_market | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate partner_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_partner` is available and structurally valid, but it is empty. The model is ready to support channel and partner performance analysis, including partner type, partner tier, and route-to-market segmentation, once data is loaded.
