# Profiling Report: ontology.dim_product

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema | ontology |
| Table Name | dim_product |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Type | Dimension |
| Row Count | 0 |
| Column Count | 7 |
| Primary Key | product_key |
| Duplicate Primary Key Count | 0 |

## Column Profile Summary

| Column Name | Data Type | Length / Precision | Nullable | Primary Key | Distinct Count | Null Count | Null % | Duplicate Value Count | Min Value | Max Value | Avg Value | String Length Statistics |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| product_key | integer | precision 32, scale 0 | NO | YES | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | N/A |
| product_id | character varying | max length 30 | NO | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| product_name | character varying | max length 80 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| product_family | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| technology_domain | character varying | max length 40 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| offer_type | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |
| business_entity | character varying | max length 30 | YES | NO | 0 | 0 | N/A (empty table) | 0 | N/A | N/A | N/A | min_len=null, max_len=null, avg_len=null |

## Data Distribution Summary

| Column Name | Distribution / Top Values |
| --- | --- |
| product_key | No values available; table is empty |
| product_id | No values available; table is empty |
| product_name | No values available; table is empty |
| product_family | No values available; table is empty |
| technology_domain | No values available; table is empty |
| offer_type | No values available; table is empty |
| business_entity | No values available; table is empty |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| product_key | N/A | N/A | N/A |

## Date Statistics

| Column Name | Min Date | Max Date |
| --- | --- | --- |
| None | N/A | N/A |

## Text Statistics

| Column Name | Length Statistics |
| --- | --- |
| product_id | min_len=null, max_len=null, avg_len=null |
| product_name | min_len=null, max_len=null, avg_len=null |
| product_family | min_len=null, max_len=null, avg_len=null |
| technology_domain | min_len=null, max_len=null, avg_len=null |
| offer_type | min_len=null, max_len=null, avg_len=null |
| business_entity | min_len=null, max_len=null, avg_len=null |

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
| Structural Nullable Columns | product_name, product_family, technology_domain, offer_type, business_entity |
| Structurally Required Columns | product_key, product_id |

## Data Quality Summary

| Quality Check | Status | Details |
| --- | --- | --- |
| Table Exists | PASS | Verified in schema ontology |
| Primary Key Defined | PASS | product_key |
| Duplicate Primary Keys | PASS | 0 duplicates found |
| Data Presence | WARNING | Table contains 0 rows |
| Column Metadata Availability | PASS | All 7 columns profiled |
| Distribution Analysis | WARNING | No distributions available because table is empty |

## Overall Profiling Summary

The `ontology.dim_product` table is structurally consistent with product dimension modeling standards and includes a valid primary key. However, because it contains no rows, profiling is limited to metadata and structural quality checks.