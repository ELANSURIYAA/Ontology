# Profiling Report: ontology.dim_contract

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_contract |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 5 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| contract_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| contract_type | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| term_months | integer | YES |  | 32 | 0 | 0 | 0 | 0.00% |
| auto_renew_flag | character | YES | 1 |  |  | 0 | 0 | 0.00% |
| coverage_level | character varying | YES | 20 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | contract_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| contract_key | N/A (no data) | N/A (no data) | N/A (no data) |
| term_months | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| contract_type | N/A (no data) | N/A (no data) | N/A (no data) |
| auto_renew_flag | N/A (no data) | N/A (no data) | N/A (no data) |
| coverage_level | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| contract_type | No rows available for distribution profiling |
| auto_renew_flag | No rows available for distribution profiling |
| coverage_level | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate contract_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_contract` is structurally valid and available for analysis, but it currently contains no data. As a result, data distribution, completeness patterns, numeric ranges, and text length behavior cannot be meaningfully evaluated beyond schema-level profiling. This table appears ready for future population as part of the Cisco bookings star schema.
