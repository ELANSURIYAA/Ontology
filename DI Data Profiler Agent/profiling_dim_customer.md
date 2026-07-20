# Profiling Report: ontology.dim_customer

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_customer |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 8 |
| Primary Key | customer_key |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| customer_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| customer_id | character varying | max length 20 | NO | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| customer_name | character varying | max length 80 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| segment | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| industry | character varying | max length 40 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| account_tier | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| hq_country | character varying | max length 40 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| hq_region | character varying | max length 20 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| customer_key | No values available; table is empty |
| customer_id | No values available; table is empty |
| customer_name | No values available; table is empty |
| segment | No values available; table is empty |
| industry | No values available; table is empty |
| account_tier | No values available; table is empty |
| hq_country | No values available; table is empty |
| hq_region | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| customer_key | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| customer_id | min_len=null, max_len=null, avg_len=null |
| customer_name | min_len=null, max_len=null, avg_len=null |
| segment | min_len=null, max_len=null, avg_len=null |
| industry | min_len=null, max_len=null, avg_len=null |
| account_tier | min_len=null, max_len=null, avg_len=null |
| hq_country | min_len=null, max_len=null, avg_len=null |
| hq_region | min_len=null, max_len=null, avg_len=null |

## NULL Statistics

| Metric | Value |
| --- | --- |
| Columns With Observed NULLs | 0 |
| Note | Table is empty, so NULL percentages are not computable from data |

## Distinct Value Statistics

| Metric | Value |
| --- | --- |
| Total Columns Profiled | 8 |
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
| Structural Nullable Columns | customer_name, segment, industry, account_tier, hq_country, hq_region |
| Structurally Required Columns | customer_key, customer_id |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | customer_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Column Metadata Availability | PASS | All 8 columns profiled |
| Distribution Analysis | WARNING | No distributions available because table is empty |

## Overall Profiling Summary

The `ontology.dim_customer` table has a valid dimensional structure with 8 columns and primary key `customer_key`, but it currently contains no records. Profiling confirms schema integrity and no duplicate primary keys, while all data-driven statistics remain unavailable until the table is populated.