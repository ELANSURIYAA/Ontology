# Semantic Summary

## 1. Semantic Overview

| Item | Value |
|---|---|
| Business Subject Area | Cisco Sales Bookings and Revenue Analytics |
| Data Domain Description | A Kimball star schema centered on booking transactions at order-line grain, used to analyze Cisco sales demand across customers, products, partners, geography, sales representatives, contracts, and time. |
| Business Value Proposition | Provides a governed semantic foundation for consistent booking analytics, renewal tracking, partner performance analysis, product mix reporting, forecasting, and executive decision-making. |
| Business Capabilities Enabled | Total bookings reporting; net-new vs renewal analysis; ACV/TCV analysis; partner contribution analysis; product-family mix analysis; regional sales analysis; sales rep performance analysis; contract and renewal analytics |
| Business Question 1 | What is total booking amount by fiscal year, fiscal quarter, region, and product family? |
| Business Question 2 | How do renewal bookings compare to new bookings by customer segment, partner, and sales team? |
| Business Question 3 | Which products, partners, and geographies contribute most to ACV and TCV? |

## 2. Input Validation

| Validation Item | Status | Details |
|---|---|---|
| Data Dictionary Readability | PASS | Validated technical metadata was provided and readable. |
| Business Glossary Availability | PASS | Enriched business glossary data dictionary was provided and readable. |
| Business Process / Metrics / Relationships Document Readability | PASS | `Business Domain Context.txt` and `Cisco_Bookings_Data_Model_and_Process.docx` were read successfully. |
| Missing Tables | PASS | No expected tables were missing from the supplied star schema. |
| Duplicate Tables | PASS | No duplicate table names detected. |
| Duplicate Glossary Terms | PASS | No duplicate glossary terms were explicitly identified in supplied metadata. |
| Invalid Column Definitions | PASS | No invalid column definitions were detected in supplied metadata. |
| Missing Primary Keys | PASS | All 8 tables have primary keys. |
| Broken Foreign Keys | PASS | All 7 declared foreign keys reference valid parent dimension keys. |
| Invalid Glossary Mappings | PASS | Supplied glossary mappings are structurally consistent with technical metadata. |
| Data Availability | WARNING | All discovered tables were empty at profiling time; semantic interpretation relies on metadata and business documentation rather than observed values. |

## 3. Schema Discovery Summary

| Category | Count | Details |
|---|---:|---|
| Total Tables | 8 | 7 dimensions and 1 fact table |
| Fact Tables | 1 | `fact_bookings` |
| Dimension Tables | 7 | `dim_contract`, `dim_customer`, `dim_date`, `dim_geography`, `dim_partner`, `dim_product`, `dim_sales_rep` |
| Lookup Tables | 0 | None explicitly identified |
| Bridge Tables | 0 | None identified |
| Total Columns | 61 | Across all discovered tables |
| Primary Keys | 8 | One per table |
| Foreign Keys | 7 | All on `fact_bookings` |
| Constraints | 15 | 8 PK + 7 FK |

## 4. Semantic Domain Discovery

| Domain Name | Domain Description | Business Purpose | Tables |
|---|---|---|---|
| Sales Transactions | Captures booking events and transaction-level classification attributes and measures. | Support demand reporting, bookings analysis, growth/retention analysis, and financial aggregation. | `fact_bookings` |
| Customer Management | Describes customer identity, segmentation, and headquarters geography. | Support account-based analysis and customer segmentation. | `dim_customer` |
| Product Management | Describes products, portfolios, offer types, and technology domains. | Support product mix and portfolio performance analysis. | `dim_product` |
| Partner Management | Describes partner identity, type, tier, and route to market. | Support channel and indirect sales analysis. | `dim_partner` |
| Geography | Describes region, theater, and country context. | Support geographic rollups and regional sales analysis. | `dim_geography` |
| Sales Organization | Describes seller identity, role, team, and coverage segment. | Support sales performance and organizational analysis. | `dim_sales_rep` |
| Contract Management | Describes contract type, term, renewal behavior, and coverage level. | Support renewal and contract-structure analysis. | `dim_contract` |
| Time Management | Provides conformed calendar and fiscal time attributes. | Support time-series, fiscal, and period-over-period reporting. | `dim_date` |

## 5. Glossary Mapping Summary

| Business Term | Technical Mapping | Preferred Name | Synonyms | Business Domain | Mapping Confidence |
|---|---|---|---|---|---:|
| Bookings Fact | `fact_bookings` | Bookings Fact | Booking Transactions, Bookings Fact Table | Sales Transactions | 1.00 |
| Customer Dimension | `dim_customer` | Customer Dimension | Account Dimension, Customer Master | Customer Management | 1.00 |
| Product Dimension | `dim_product` | Product Dimension | Offer Dimension, Product Master | Product Management | 1.00 |
| Partner Dimension | `dim_partner` | Partner Dimension | Channel Partner Dimension, Partner Master | Partner Management | 1.00 |
| Geography Dimension | `dim_geography` | Geography Dimension | Geo Dimension, Location Dimension | Geography | 0.98 |
| Sales Representative Dimension | `dim_sales_rep` | Sales Representative Dimension | Seller Dimension, Rep Dimension | Sales Organization | 1.00 |
| Contract Dimension | `dim_contract` | Contract Dimension | Contract Master, Agreement Dimension | Contract Management | 1.00 |
| Date Dimension | `dim_date` | Date Dimension | Calendar Dimension, Time Dimension | Time Management | 1.00 |
| Booking Amount USD | `fact_bookings.booking_amount_usd` | Booking Amount USD | Total Bookings USD, Net Booked Value | Sales Measures | 1.00 |
| Annual Contract Value USD | `fact_bookings.acv_usd` | Annual Contract Value USD | ACV | Sales Measures | 1.00 |
| Total Contract Value USD | `fact_bookings.tcv_usd` | Total Contract Value USD | TCV, Total Value | Sales Measures | 1.00 |
| Quantity Sold | `fact_bookings.quantity` | Quantity Sold | Units Booked | Sales Measures | 1.00 |
| Discount Percentage | `fact_bookings.discount_pct` | Discount Percentage | Discount Rate | Sales Measures | 0.99 |
| Route to Market | `dim_partner.route_to_market` | Route to Market | RTM, Go-to-Market Route | Partner Management | 0.98 |
| Theater | `dim_geography.theater` | Theater | Sales Theater | Geography | 0.85 |
| Booking Type | `fact_bookings.booking_type` | Booking Type | Booking Classification | Sales Transactions | 0.97 |
| Renewal Indicator | `fact_bookings.is_renewal` | Renewal Indicator | Renewal Flag | Sales Transactions | 0.95 |

### Glossary Mapping Exceptions

| Exception Type | Item | Observation |
|---|---|---|
| Unmapped Columns | None | All columns were assigned business-friendly terms in the supplied enriched glossary. |
| Duplicate Mappings | None observed | No duplicate technical-to-business mappings requiring resolution were identified. |
| Ambiguous Mappings | `dim_geography.theater` | Meaning is supported by Cisco sales context but remains partially inferred due to lack of populated data. |
| Ambiguous Mappings | `fact_bookings.is_renewal` | Treated as an indicator/flag based on metadata and glossary; value domain not observed in data. |
| Ambiguous Mappings | `dim_contract.auto_renew_flag` | Interpreted as an indicator/flag based on naming and business context; value domain not observed in data. |

## 6. Business Entity Discovery Summary

| Business Entity | Technical Table | Entity Type | Business Keys | Key Attributes / Measures | Hierarchies |
|---|---|---|---|---|---|
| Booking Transaction | `fact_bookings` | Fact Entity | `booking_id`; inferred transactional identifier: `order_number` + `order_line_number` | Measures: `quantity`, `unit_list_price_usd`, `discount_pct`, `booking_amount_usd`, `acv_usd`, `tcv_usd` | Time, Customer, Product, Partner, Geography, Sales Rep, Contract |
| Customer | `dim_customer` | Dimension Entity | `customer_key`; business identifier: `customer_id` | `customer_name`, `segment`, `industry`, `account_tier`, `hq_country`, `hq_region` | HQ Region > HQ Country > Customer |
| Product | `dim_product` | Dimension Entity | `product_key`; business identifier: `product_id` | `product_name`, `product_family`, `technology_domain`, `offer_type`, `business_entity` | Business Entity > Technology Domain > Product Family > Product |
| Partner | `dim_partner` | Dimension Entity | `partner_key`; business identifier: `partner_id` | `partner_name`, `partner_type`, `partner_tier`, `route_to_market` | Route to Market > Partner Type > Partner Tier > Partner |
| Geography | `dim_geography` | Dimension Entity | `geography_key` | `region`, `theater`, `country` | Region > Theater > Country |
| Sales Representative | `dim_sales_rep` | Dimension Entity | `sales_rep_key`; business identifier: `rep_id` | `rep_name`, `sales_role`, `sales_team`, `segment_covered` | Sales Team > Sales Role > Sales Representative |
| Contract | `dim_contract` | Dimension Entity | `contract_key` | `contract_type`, `term_months`, `auto_renew_flag`, `coverage_level` | Contract Type > Coverage Level |
| Date | `dim_date` | Dimension Entity | `date_key`; natural date: `full_date` | `month_name`, `calendar_year`, `fiscal_year`, `fiscal_quarter`, `fiscal_period_seq` | Calendar Year > Month > Date; Fiscal Year > Fiscal Quarter > Date |

## 7. Relationship Discovery

| Relationship Name | Parent Entity | Child Entity | Relationship Type | Cardinality | Confidence Score | Basis |
|---|---|---|---|---|---:|---|
| Date to Booking Transaction | Date | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.date_key -> dim_date.date_key` |
| Customer to Booking Transaction | Customer | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.customer_key -> dim_customer.customer_key` |
| Product to Booking Transaction | Product | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.product_key -> dim_product.product_key` |
| Partner to Booking Transaction | Partner | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.partner_key -> dim_partner.partner_key` |
| Geography to Booking Transaction | Geography | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.geography_key -> dim_geography.geography_key` |
| Sales Representative to Booking Transaction | Sales Representative | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.sales_rep_key -> dim_sales_rep.sales_rep_key` |
| Contract to Booking Transaction | Contract | Booking Transaction | Dimensional | One-to-Many | 1.00 | Explicit foreign key `fact_bookings.contract_key -> dim_contract.contract_key` |

## 8. Semantic Metrics

### 8.1 Overall Metrics

| Metric | Value |
|---|---:|
| Total Tables | 8 |
| Total Columns | 61 |
| Total Relationships | 7 |
| Total Domains | 8 |
| Total Measures | 6 |
| Total Glossary Terms | 69 |
| Mapped Terms | 69 |
| Glossary Coverage Percentage | 100.00% |

### 8.2 Per-Domain Metrics

| Domain Name | Entity Count | Attribute Count | Measure Count | Glossary Coverage Percentage | Domain Status |
|---|---:|---:|---:|---:|---|
| Sales Transactions | 1 | 12 | 6 | 100.00% | Structurally complete; data empty |
| Customer Management | 1 | 7 | 0 | 100.00% | Structurally complete; data empty |
| Product Management | 1 | 6 | 0 | 100.00% | Structurally complete; data empty |
| Partner Management | 1 | 5 | 0 | 100.00% | Structurally complete; data empty |
| Geography | 1 | 3 | 0 | 100.00% | Structurally complete; data empty |
| Sales Organization | 1 | 5 | 0 | 100.00% | Structurally complete; data empty |
| Contract Management | 1 | 4 | 0 | 100.00% | Structurally complete; data empty |
| Time Management | 1 | 6 | 0 | 100.00% | Structurally complete; data empty |

## 9. Semantic Quality & Reasoning

### 9.1 Design Observations

| Category | Observation |
|---|---|
| Schema Pattern | The model is a clear Kimball star schema centered on `fact_bookings`. |
| Grain | Fact grain is explicitly defined as one row per booking transaction / order line. |
| Conformance | All dimensions are conformed around the central fact, supporting reusable analytics. |
| Keys | Surrogate integer primary keys are consistently applied across all dimensions and the fact table. |
| Measures | Core commercial measures are concentrated in the fact table and align with business documentation. |
| Time Intelligence | The date dimension supports both calendar and Cisco fiscal reporting. |

### 9.2 Glossary Health

| Category | Assessment |
|---|---|
| Coverage | Strong glossary coverage across tables and columns. |
| Consistency | Business names align well with technical metadata and process documentation. |
| Ambiguity | Limited ambiguity exists for indicator-style fields and Cisco-specific `theater`. |
| Reusability | Terms are reusable for semantic-layer and ontology mapping. |
| Data Evidence | Because all tables are empty, glossary validation against actual values is not yet possible. |

### 9.3 Recommendations

| Priority | Recommendation |
|---|---|
| High | Load representative data to validate indicator domains, business hierarchies, and metric behavior. |
| High | Formalize allowed values for `booking_type`, `is_renewal`, and `auto_renew_flag`. |
| Medium | Add unique constraints on business identifiers such as `customer_id`, `product_id`, `partner_id`, and `rep_id` if required by source system rules. |
| Medium | Consider documenting derived metric formulas such as Total Bookings, Net-New vs Renewal Mix, and ACV/TCV usage rules in the semantic layer. |
| Medium | Add non-PK indexes on fact foreign keys if query performance becomes a concern in production. |
| Low | Extend the semantic model later with renewal date / entitlement data if renewal capture rate is required explicitly. |

### 9.4 Suggested Join Paths

| Use Case | Suggested Join Path |
|---|---|
| Bookings by Time | `fact_bookings` -> `dim_date` |
| Bookings by Customer Segment | `fact_bookings` -> `dim_customer` |
| Bookings by Product Portfolio | `fact_bookings` -> `dim_product` |
| Partner Contribution | `fact_bookings` -> `dim_partner` |
| Regional Sales Analysis | `fact_bookings` -> `dim_geography` |
| Sales Rep Performance | `fact_bookings` -> `dim_sales_rep` |
| Renewal and Contract Analysis | `fact_bookings` -> `dim_contract` |
| Cross-domain Performance Analysis | `fact_bookings` -> `dim_date` + `dim_customer` + `dim_product` + `dim_partner` + `dim_geography` + `dim_sales_rep` + `dim_contract` |

### 9.5 Data Quality Observations

| Observation Type | Details |
|---|---|
| Empty Tables | All 8 tables had row count = 0 at profiling time. |
| Structural Integrity | All discovered tables contain column metadata and valid primary keys. |
| Referential Integrity | All declared foreign keys are structurally valid. |
| Profiling Limitation | Distinct counts, null distributions, and measure distributions could not be validated from data. |
| Orphan Risk | No structural orphan relationships were identified, but row-level orphan testing was not possible because tables are empty. |

## 10. Final Validation Warnings

| Warning Type | Applies | Details |
|---|---|---|
| Duplicate Entities | No | No duplicate entities identified. |
| Duplicate Measures | No | No duplicate measures identified. |
| Circular Relationships | No | No circular relationships identified. |
| Missing Glossary Mappings | No | All schema elements were mapped in the enriched glossary. |
| Missing Keys | No | All tables have primary keys; fact table has all declared foreign keys. |
| Orphan Entities | No structural orphan | All entities participate in the star schema; row-level orphan detection not possible due to empty tables. |
| Evidence Limitation | Yes | Semantic confidence for some inferred fields remains lower because no sample data was available. |
