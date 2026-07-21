# Profiling Report: ontology.dim_sales_rep

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_sales_rep |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 6 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| sales_rep_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| rep_id | character varying | NO | 20 |  |  | 0 | 0 | 0.00% |
| rep_name | character varying | YES | 60 |  |  | 0 | 0 | 0.00% |
| sales_role | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| sales_team | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| segment_covered | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | sales_rep_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| sales_rep_key | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| rep_id | N/A (no data) | N/A (no data) | N/A (no data) |
| rep_name | N/A (no data) | N/A (no data) | N/A (no data) |
| sales_role | N/A (no data) | N/A (no data) | N/A (no data) |
| sales_team | N/A (no data) | N/A (no data) | N/A (no data) |
| segment_covered | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| sales_role | No rows available for distribution profiling |
| sales_team | No rows available for distribution profiling |
| segment_covered | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate sales_rep_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_sales_rep` is structurally present but empty. It is designed to support analysis by sales role, team, and covered segment, but no actual data is available to evaluate completeness, variability, or distribution quality.
