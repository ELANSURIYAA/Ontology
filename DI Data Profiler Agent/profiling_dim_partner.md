# Profiling Report: ontology.dim_partner

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_partner |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 6 |
| Primary Key | partner_key |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| partner_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| partner_id | character varying | max length 20 | NO | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| partner_name | character varying | max length 60 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| partner_type | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| partner_tier | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| route_to_market | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| partner_key | No values available; table is empty |
| partner_id | No values available; table is empty |
| partner_name | No values available; table is empty |
| partner_type | No values available; table is empty |
| partner_tier | No values available; table is empty |
| route_to_market | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| partner_key | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| partner_id | min_len=null, max_len=null, avg_len=null |
| partner_name | min_len=null, max_len=null, avg_len=null |
| partner_type | min_len=null, max_len=null, avg_len=null |
| partner_tier | min_len=null, max_len=null, avg_len=null |
| route_to_market | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 6 |
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
| Structural Nullable Columns | partner_name, partner_type, partner_tier, route_to_market |
| Structurally Required Columns | partner_key, partner_id |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | partner_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Column Metadata Availability | PASS | All 6 columns profiled |
| Distribution Analysis | WARNING | No distributions available because table is empty |

## Overall Profiling Summary

The `ontology.dim_partner` table has the expected partner dimension structure and a valid primary key, but it currently contains no data. Profiling verifies schema quality only; data distribution and completeness metrics will become meaningful after data load.