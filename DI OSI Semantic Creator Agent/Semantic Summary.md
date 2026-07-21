# Semantic Summary

## Semantic Overview

| Item | Value |
| --- | --- |
| Business Subject Area | Cisco Sales Bookings and Revenue Analytics |
| Data Domain Description | A Kimball-style star schema centered on booking transactions at order-line grain, with conformed dimensions for customer, product, partner, geography, sales representative, contract, and date. |
| Business Value Proposition | Provides a governed analytical foundation for bookings, renewal, partner, product, customer, geography, sales, and fiscal performance analysis using consistent dimensional context and reusable business terminology. |
| Business Capabilities Enabled | Total bookings reporting; renewal analysis; ACV and TCV analysis; customer segmentation analysis; product portfolio performance; partner contribution analysis; regional performance reporting; sales representative performance; fiscal period reporting; pricing and discount analysis. |
| Business Question 1 | What is total booking amount by fiscal quarter, product family, and geography? |
| Business Question 2 | How do renewal bookings compare with net-new bookings by customer segment and sales team? |
| Business Question 3 | Which partners and route-to-market paths contribute the most booking amount, ACV, and TCV? |

## Input Validation

| Validation Check | Status | Details |
| --- | --- | --- |
| Data Dictionary readability | PASS | Enriched data dictionary content was provided and readable. |
| Business Glossary availability | PASS | Business glossary definitions were embedded in the enriched data dictionary. |
| Business Process document readability | PASS | `Cisco_Bookings_Data_Model_and_Process.docx` was readable. |
| Business Domain Context readability | PASS | `Business Domain Context.txt` was readable. |
| Missing tables | PASS | 8 expected tables identified; no missing tables evidenced in supplied metadata. |
| Duplicate tables | PASS | No duplicate table names reported in schema `ontology`. |
| Duplicate glossary terms | PASS WITH NOTE | No exact duplicate glossary terms were evidenced; some repeated technical terms such as key names appear across table and column contexts as expected. |
| Invalid column definitions | PASS | Column names, data types, nullability, PK/FK annotations, and DDL were structurally valid. |
| Missing primary keys | PASS | All 8 tables have primary keys. |
| Broken foreign keys | PASS | All 7 declared foreign keys resolve to existing dimension primary keys. |
| Invalid glossary mappings | PASS WITH NOTE | Mappings are metadata-supported; confidence varies for inferred business synonyms and some process-aligned interpretations because all tables are empty. |
| Data availability for profiling | WARNING | All 8 tables are empty, so semantic reasoning is metadata-driven rather than data-distribution-driven. |

## Schema Discovery

| Category | Count | Details |
| --- | ---: | --- |
| Total Tables | 8 | 1 fact table and 7 dimension tables identified. |
| Total Columns | 61 | Across all discovered tables. |
| Primary Keys | 8 | One primary key per table. |
| Foreign Keys | 7 | All located on `fact_bookings`. |
| Fact Tables | 1 | `fact_bookings` |
| Dimension Tables | 7 | `dim_contract`, `dim_customer`, `dim_date`, `dim_geography`, `dim_partner`, `dim_product`, `dim_sales_rep` |
| Lookup Tables | 0 | None explicitly modeled. |
| Bridge Tables | 0 | None explicitly modeled. |
| Constraints | 28 | 8 PK, 7 FK, 13 not-null enforcement checks. |

## Semantic Domain Discovery

| Domain Name | Description | Business Purpose | Tables |
| --- | --- | --- | --- |
| Bookings & Revenue | Core transactional domain capturing recognized bookings and commercial value metrics at booking transaction/order-line grain. | Supports headline bookings, ACV, TCV, pricing, discount, and booking classification analysis. | `fact_bookings` |
| Customer Management | Customer account context including identifiers, segmentation, industry, and HQ geography. | Supports customer performance, segmentation, and account-based analysis. | `dim_customer` |
| Product Portfolio | Product, offer, technology, and internal business entity context. | Supports product-family mix, offer-type, technology, and portfolio reporting. | `dim_product` |
| Partner & Channel | Partner identity, partner classification, tiering, and route-to-market context. | Supports channel contribution, partner effectiveness, and route-to-market analysis. | `dim_partner` |
| Sales Organization | Sales ownership and coverage context for bookings. | Supports seller, role, team, and covered segment reporting. | `dim_sales_rep` |
| Geography | Selling geography hierarchy. | Supports regional, theater, and country performance analysis. | `dim_geography` |
| Contract & Renewal | Contract structure and service coverage context linked to bookings and renewals. | Supports term-based analysis, coverage-level analysis, and renewal planning. | `dim_contract` |
| Time & Fiscal Reporting | Calendar and fiscal time context. | Supports period-based reporting, trend analysis, and fiscal rollups. | `dim_date` |

## Semantic Metrics

### Overall Metrics

| Metric | Value |
| --- | ---: |
| Total Tables | 8 |
| Total Columns | 61 |
| Total Relationships | 7 |
| Total Domains | 8 |
| Total Measures | 8 |
| Total Glossary Terms | 69 |
| Mapped Terms | 69 |
| Glossary Coverage Percentage | 100.00% |

### Per-Domain Metrics

| Domain Name | Entity Count | Attribute Count | Measure Count | Glossary Coverage Percentage | Domain Status |
| --- | ---: | ---: | ---: | ---: | --- |
| Bookings & Revenue | 1 | 10 | 8 | 100.00% | Structurally complete; data not loaded |
| Customer Management | 1 | 7 | 0 | 100.00% | Structurally complete; data not loaded |
| Product Portfolio | 1 | 6 | 0 | 100.00% | Structurally complete; data not loaded |
| Partner & Channel | 1 | 5 | 0 | 100.00% | Structurally complete; data not loaded |
| Sales Organization | 1 | 5 | 0 | 100.00% | Structurally complete; data not loaded |
| Geography | 1 | 3 | 0 | 100.00% | Structurally complete; data not loaded |
| Contract & Renewal | 1 | 4 | 0 | 100.00% | Structurally complete; data not loaded |
| Time & Fiscal Reporting | 1 | 6 | 0 | 100.00% | Structurally complete; data not loaded |

## Semantic Quality & Reasoning

### Design Observations

| Observation Type | Detail |
| --- | --- |
| Model Pattern | The schema is a clean star schema with one central fact and seven conformed dimensions. |
| Grain Clarity | `fact_bookings` is explicitly documented at booking transaction / order-line grain. |
| Relationship Pattern | All semantic relationships are classic one-to-many joins from dimensions into the fact table. |
| Business Alignment | The schema strongly aligns to the documented quote-to-booking business process. |
| Metric Readiness | The fact table includes core operational and financial measures needed for bookings analytics. |
| Time Intelligence | `dim_date` supports both calendar and fiscal reporting, enabling executive and finance use cases. |
| Channel Analytics | Partner and route-to-market structures support indirect sales analysis. |
| Renewal Readiness | Renewal semantics are supported through `booking_type`, `is_renewal`, and contract attributes. |

### Glossary Health

| Check | Status | Detail |
| --- | --- | --- |
| Business glossary coverage | GOOD | All tables and columns in scope have glossary definitions or business terms. |
| Preferred naming consistency | GOOD | Business-friendly names consistently mirror glossary terms. |
| Synonym coverage | MODERATE | Many terms include synonyms, though coverage is richer for business-facing columns than for technical keys. |
| Ambiguity risk | LOW TO MODERATE | `business_entity`, `segment`, and some renewal indicators require organizational context for precise interpretation. |
| Data-backed validation | LIMITED | Empty tables prevent validation of expected code values, indicator semantics, and real-world cardinality. |

### Recommendations

| Priority | Recommendation |
| --- | --- |
| High | Populate all tables to validate metric behavior, nullability expectations, and code-set semantics such as `booking_type`, `is_renewal`, and `auto_renew_flag`. |
| High | Add explicit unique constraints on business identifiers where business rules require one active dimensional row per identifier, such as `customer_id`, `product_id`, `partner_id`, and `rep_id`. |
| Medium | Standardize indicator columns (`is_renewal`, `auto_renew_flag`) to documented allowed values and data types. |
| Medium | Add catalog comments or business metadata directly in the database for persistent semantic governance. |
| Medium | Consider a renewal-date or contract-end-date attribute in future iterations if renewal capture-rate analytics are required. |
| Low | Add supporting non-PK indexes to foreign keys on `fact_bookings` if query volume and data size increase. |

### Suggested Join Paths

| Analytical Use Case | Suggested Join Path |
| --- | --- |
| Bookings by customer and time | `fact_bookings` → `dim_customer` and `fact_bookings` → `dim_date` |
| Product performance by fiscal quarter | `fact_bookings` → `dim_product` → `dim_date` |
| Partner contribution by geography | `fact_bookings` → `dim_partner` and `fact_bookings` → `dim_geography` |
| Sales performance by segment | `fact_bookings` → `dim_sales_rep` and `fact_bookings` → `dim_customer` |
| Renewal analysis by contract type | `fact_bookings` → `dim_contract` and `fact_bookings` → `dim_date` |
| Pricing and discount analysis by product | `fact_bookings` → `dim_product` |

### Data Quality Observations

| Observation | Status | Detail |
| --- | --- | --- |
| Table population | WARNING | All tables currently have zero rows. |
| PK integrity | PASS | No duplicate primary keys observed in profiling outputs. |
| FK structural integrity | PASS | All foreign keys are structurally valid. |
| Domain completeness validation | LIMITED | No loaded data exists to confirm distribution, null patterns, or referential population quality. |
| Indicator validation | LIMITED | Binary/flag assumptions for `is_renewal` and `auto_renew_flag` cannot be confirmed from data. |
| Financial metric validation | LIMITED | No values exist to test additive behavior, outliers, or pricing logic. |

## Validation Warnings

| Warning Type | Applies To | Detail |
| --- | --- | --- |
| Empty source data | All tables | Semantic conclusions are structurally valid but cannot be empirically validated against populated data. |
| Inferred meanings | `is_renewal`, `auto_renew_flag`, `business_entity`, `segment_covered` | Semantic definitions are based on glossary, naming, and process documentation rather than actual value inspection. |
| Orphan detection limitation | All entities | Orphan-record analysis cannot be performed because row counts are zero. |
| Circular relationship check | Model-wide | No circular relationships were found structurally; runtime data validation is not applicable due to empty tables. |
