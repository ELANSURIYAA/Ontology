# Profiling Report: ontology.dim_date

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_date |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 7 |
| Primary Key | date_key |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| date_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| full_date | date | date | NO | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| month_name | character varying | max length 12 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| calendar_year | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| fiscal_year | character varying | max length 6 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| fiscal_quarter | character varying | max length 10 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| fiscal_period_seq | integer | precision 32, scale 0 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| date_key | No values available; table is empty |
| full_date | No values available; table is empty |
| month_name | No values available; table is empty |
| calendar_year | No values available; table is empty |
| fiscal_year | No values available; table is empty |
| fiscal_quarter | No values available; table is empty |
| fiscal_period_seq | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| date_key | N/A | N/A | N/A |
| calendar_year | N/A | N/A | N/A |
| fiscal_period_seq | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| full_date | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| month_name | min_len=null, max_len=null, avg_len=null |
| fiscal_year | min_len=null, max_len=null, avg_len=null |
| fiscal_quarter | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 7 |
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
| Structural Nullable Columns | month_name, calendar_year, fiscal_year, fiscal_quarter, fiscal_period_seq |
| Structurally Required Columns | date_key, full_date |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | date_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Date Profiling Capability | WARNING | No date values available for min/max analysis |
| Column Metadata Availability | PASS | All 7 columns profiled |

## Overall Profiling Summary

The `ontology.dim_date` table is structurally complete and contains standard date-dimension attributes, but it currently has no rows. Because the table is empty, date range analysis, distribution checks, and completeness assessment are limited to metadata-only validation.