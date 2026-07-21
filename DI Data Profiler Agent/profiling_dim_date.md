# Profiling Report: ontology.dim_date

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_date |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 7 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| date_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| full_date | date | NO |  |  |  | 0 | 0 | 0.00% |
| month_name | character varying | YES | 12 |  |  | 0 | 0 | 0.00% |
| calendar_year | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| fiscal_year | character varying | YES | 6 |  |  | 0 | 0 | 0.00% |
| fiscal_quarter | character varying | YES | 10 |  |  | 0 | 0 | 0.00% |
| fiscal_period_seq | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | date_key |
| Duplicate Primary Key Count | 0 |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| full_date | N/A (no data) | N/A (no data) |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| date_key | N/A (no data) | N/A (no data) | N/A (no data) |
| calendar_year | N/A (no data) | N/A (no data) | N/A (no data) |
| fiscal_period_seq | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| month_name | N/A (no data) | N/A (no data) | N/A (no data) |
| fiscal_year | N/A (no data) | N/A (no data) | N/A (no data) |
| fiscal_quarter | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| month_name | No rows available for distribution profiling |
| fiscal_year | No rows available for distribution profiling |
| fiscal_quarter | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate date_key values detected |
| Date profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_date` is structurally present but empty. The table design supports both calendar and fiscal analysis, which is important for bookings trend reporting and executive analytics, but no loaded records are currently available to evaluate date coverage, fiscal period consistency, or distribution patterns.
