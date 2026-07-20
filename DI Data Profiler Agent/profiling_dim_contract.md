# Profiling Report: ontology.dim_contract

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_contract |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 5 |
| Primary Key | contract_key |
| Duplicate Primary Key Count | 0 |
| Profiling Timestamp Context | Generated from live PostgreSQL metadata and table profiling queries |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| contract_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| contract_type | character varying | max length 40 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| term_months | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| auto_renew_flag | character | max length 1 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| coverage_level | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| contract_key | No values available; table is empty |
| contract_type | No values available; table is empty |
| term_months | No values available; table is empty |
| auto_renew_flag | No values available; table is empty |
| coverage_level | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| contract_key | N/A | N/A | N/A |
| term_months | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| contract_type | min_len=null, max_len=null, avg_len=null |
| auto_renew_flag | min_len=null, max_len=null, avg_len=null |
| coverage_level | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 5 |
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
| Structural Nullable Columns | contract_type, term_months, auto_renew_flag, coverage_level |
| Structurally Required Columns | contract_key |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | contract_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Column Metadata Availability | PASS | All 5 columns profiled |
| Distribution Analysis | WARNING | No distributions available because table is empty |

## Overall Profiling Summary

The `ontology.dim_contract` table is structurally well-defined with 5 columns and a primary key on `contract_key`, but it currently contains no data. As a result, distribution, completeness, and statistical profiling are limited to schema-level observations only. This table is ready for downstream analytical use once records are loaded.