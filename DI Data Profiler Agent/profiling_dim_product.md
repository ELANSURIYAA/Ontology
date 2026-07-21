# Profiling Report: ontology.dim_product

## Table Information

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Schema Name | ontology |
| Table Name | dim_product |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Table Role | Dimension Table |
| Row Count | 0 |
| Column Count | 7 |
| Profiling Status | Profiled successfully; table exists but contains no rows |

## Column Profile Summary

| Column Name | Data Type | Nullable | Max Length | Precision | Scale | Distinct Values | NULL Count | NULL % |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| product_key | integer | NO |  | 32 | 0 | 0 | 0 | 0.00% |
| product_id | character varying | NO | 30 |  |  | 0 | 0 | 0.00% |
| product_name | character varying | YES | 80 |  |  | 0 | 0 | 0.00% |
| product_family | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| technology_domain | character varying | YES | 40 |  |  | 0 | 0 | 0.00% |
| offer_type | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |
| business_entity | character varying | YES | 30 |  |  | 0 | 0 | 0.00% |

## Duplicate Statistics

| Check | Result |
| --- | --- |
| Primary Key Column | product_key |
| Duplicate Primary Key Count | 0 |

## Numeric Statistics

| Column Name | Min | Max | Average |
| --- | --- | --- | --- |
| product_key | N/A (no data) | N/A (no data) | N/A (no data) |

## Text Statistics

| Column Name | Min Length | Max Length | Avg Length |
| --- | --- | --- | --- |
| product_id | N/A (no data) | N/A (no data) | N/A (no data) |
| product_name | N/A (no data) | N/A (no data) | N/A (no data) |
| product_family | N/A (no data) | N/A (no data) | N/A (no data) |
| technology_domain | N/A (no data) | N/A (no data) | N/A (no data) |
| offer_type | N/A (no data) | N/A (no data) | N/A (no data) |
| business_entity | N/A (no data) | N/A (no data) | N/A (no data) |

## Value Distribution Summary

| Column Name | Distribution Summary |
| --- | --- |
| product_family | No rows available for distribution profiling |
| technology_domain | No rows available for distribution profiling |
| offer_type | No rows available for distribution profiling |
| business_entity | No rows available for distribution profiling |

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
| Primary key duplication | PASS | No duplicate product_key values detected |
| Distribution profiling | WARNING | Not available because row count is zero |
| Numeric profiling | WARNING | Not available because row count is zero |
| Text profiling | WARNING | Not available because row count is zero |

## Overall Profiling Summary

`ontology.dim_product` is structurally ready for use but currently contains no data. The schema is designed to support product family, technology domain, offer type, and business entity analysis; however, no data-driven profiling insights are available until rows are loaded.
