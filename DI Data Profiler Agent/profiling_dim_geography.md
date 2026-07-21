# Profiling Report: ontology.dim_geography

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_geography |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 4 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| geography_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| region | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |
| theater | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| country | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | geography_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| geography_key | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| region | N/A (no data) | N/A (no data) | N/A (no data) |
| theater | N/A (no data) | N/A (no data) | N/A (no data) |
| country | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| region | No rows available for distribution profiling |
| theater | No rows available for distribution profiling |
| country | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate geography_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_geography` is structurally sound but currently contains no data. The schema supports regional and country-level sales analysis, yet no distributions or completeness trends can be measured until rows are loaded.
