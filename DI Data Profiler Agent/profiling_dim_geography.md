# Profiling Report: ontology.dim_geography

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_geography |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 4 |
| Primary Key | geography_key |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| geography_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| region | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| theater | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| country | character varying | max length 40 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| geography_key | No values available; table is empty |
| region | No values available; table is empty |
| theater | No values available; table is empty |
| country | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| geography_key | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| region | min_len=null, max_len=null, avg_len=null |
| theater | min_len=null, max_len=null, avg_len=null |
| country | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 4 |
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
| Structural Nullable Columns | region, theater, country |
| Structurally Required Columns | geography_key |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | geography_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Column Metadata Availability | PASS | All 4 columns profiled |
| Distribution Analysis | WARNING | No distributions available because table is empty |

## Overall Profiling Summary

The `ontology.dim_geography` table is structurally valid with a defined primary key and geography attributes, but it currently contains no rows. All profiling outcomes therefore indicate schema readiness rather than populated data quality characteristics.