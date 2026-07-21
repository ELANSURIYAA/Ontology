# OSI Semantic Model

## Validation Summary

| Validation Check | Status | Details |
| --- | --- | --- |
| Duplicate entities | PASS | No duplicate entities detected across the 8 identified business entities. |
| Duplicate measures | PASS | No duplicate measures detected in the semantic model. |
| Circular relationships | PASS | No circular relationships identified; all relationships radiate from dimensions to the fact table. |
| Missing glossary mappings | PASS | All included entities, attributes, and measures have glossary-aligned mappings. |
| Missing keys | PASS WITH NOTE | All tables have primary keys; business keys are present for customer, product, partner, and sales representative, but some dimensions do not expose separate business identifiers beyond descriptive attributes. |
| Orphan entities | PASS WITH NOTE | No structurally orphaned entities detected; runtime orphan-row validation is not possible because all tables are empty. |

## Domains

| Domain Name | Description |
| --- | --- |
| Bookings & Revenue | Core booking transaction domain containing commercial events and financial measures at order-line grain. |
| Customer Management | Customer account domain containing segmentation, industry, and headquarters attributes. |
| Product Portfolio | Product and offer domain containing portfolio, technology, and business entity descriptors. |
| Partner & Channel | Channel ecosystem domain containing partner identity, tiering, type, and route-to-market context. |
| Sales Organization | Sales ownership domain containing representative, role, team, and coverage attributes. |
| Geography | Selling geography domain containing region, theater, and country hierarchy attributes. |
| Contract & Renewal | Contract domain containing contract type, term, coverage, and renewal-related attributes. |
| Time & Fiscal Reporting | Time intelligence domain containing calendar and fiscal reporting attributes. |

## Entities

### Booking Transaction

| Property | Value |
| --- | --- |
| Business Name | Booking Transaction Fact |
| Technical Table Name | `fact_bookings` |
| Domain | Bookings & Revenue |
| Description | Central fact table that stores individual booking transactions at booking transaction / order-line grain. |
| Entity Type | Fact Entity |
| Business Keys | `order_number`, `order_line_number` (grain-defining operational identifiers; inferred from metadata and process documentation) |
| Technical Key | `booking_id` |
| Measures | `quantity`, `unit_list_price_usd`, `discount_pct`, `booking_amount_usd`, `acv_usd`, `tcv_usd`, `is_renewal`, `booking_type` |
| Relationships | Booking Date, Booking Customer, Booking Product, Booking Partner, Booking Geography, Booking Sales Representative, Booking Contract |
| Confidence | 0.99 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Booking ID | `booking_id` | Primary Key | integer | Booking ID | 1.00 |
| Order Number | `order_number` | Degenerate Dimension / Business Key Component | character varying(20) | Order Number | 0.99 |
| Order Line Number | `order_line_number` | Degenerate Dimension / Business Key Component | integer | Order Line Number | 0.99 |
| Booking Type | `booking_type` | Descriptive Attribute | character varying(15) | Booking Type | 0.98 |
| Renewal Indicator | `is_renewal` | Descriptive Indicator / Measure-like flag | integer | Renewal Indicator | 0.95 |
| Booking Date Key | `date_key` | Foreign Key | integer | Booking Date Key | 1.00 |
| Customer Key | `customer_key` | Foreign Key | integer | Customer Key | 1.00 |
| Product Key | `product_key` | Foreign Key | integer | Product Key | 1.00 |
| Partner Key | `partner_key` | Foreign Key | integer | Partner Key | 1.00 |
| Geography Key | `geography_key` | Foreign Key | integer | Geography Key | 1.00 |
| Sales Representative Key | `sales_rep_key` | Foreign Key | integer | Sales Representative Key | 1.00 |
| Contract Key | `contract_key` | Foreign Key | integer | Contract Key | 1.00 |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type | Confidence |
| --- | --- | --- | --- | ---: |
| Quantity Sold | `quantity` | Number of units, licenses, or items booked on the transaction line. | SUM | 1.00 |
| Unit List Price USD | `unit_list_price_usd` | Standard list price per unit in U.S. dollars before discount. | AVG / SUM with business rule context | 0.88 |
| Discount Percentage | `discount_pct` | Percentage discount applied relative to list price. | AVG with weighting rules outside metadata scope | 0.86 |
| Booking Amount USD | `booking_amount_usd` | Net booked value recognized for the transaction in U.S. dollars. | SUM | 1.00 |
| Annual Contract Value USD | `acv_usd` | Annualized contract value of the booking in U.S. dollars. | SUM | 0.97 |
| Total Contract Value USD | `tcv_usd` | Total contract value of the booking over its full term in U.S. dollars. | SUM | 0.98 |
| Renewal Indicator | `is_renewal` | Flag indicating whether the booking is associated with a renewal event. | SUM or COUNT with semantic rule context | 0.78 |
| Booking Type | `booking_type` | Classification of booking transaction such as New, Renewal, or Upsell. | COUNT / GROUP BY classification | 0.92 |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `booking_id` | Surrogate identifier for the booking fact row. |
| Inferred Business Key | `order_number`, `order_line_number` | Defines order-line grain operationally according to process and glossary context. |
| Foreign Keys | `date_key`, `customer_key`, `product_key`, `partner_key`, `geography_key`, `sales_rep_key`, `contract_key` | Connect booking transactions to descriptive business dimensions. |

---

### Customer

| Property | Value |
| --- | --- |
| Business Name | Customer Dimension |
| Technical Table Name | `dim_customer` |
| Domain | Customer Management |
| Description | Dimension table storing descriptive business information about customers for segmentation and account analysis. |
| Entity Type | Dimension Entity |
| Business Keys | `customer_id` |
| Technical Key | `customer_key` |
| Measures | None explicit |
| Relationships | Customer Generates Booking Transactions |
| Confidence | 1.00 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Customer Key | `customer_key` | Primary Key | integer | Customer Key | 1.00 |
| Customer ID | `customer_id` | Business Key | character varying(20) | Customer ID | 1.00 |
| Customer Name | `customer_name` | Descriptive Attribute | character varying(80) | Customer Name | 1.00 |
| Customer Segment | `segment` | Dimension Attribute | character varying(30) | Customer Segment | 0.99 |
| Customer Industry | `industry` | Dimension Attribute | character varying(40) | Customer Industry | 1.00 |
| Account Tier | `account_tier` | Dimension Attribute | character varying(20) | Account Tier | 1.00 |
| Customer Headquarters Country | `hq_country` | Dimension Attribute | character varying(40) | Customer Headquarters Country | 1.00 |
| Customer Headquarters Region | `hq_region` | Dimension Attribute | character varying(20) | Customer Headquarters Region | 1.00 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Customer Headquarters Geography Hierarchy | Customer Headquarters Region → Customer Headquarters Country → Customer Name |
| Customer Segmentation Hierarchy | Customer Segment → Account Tier → Customer Name |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `customer_key` | Warehouse surrogate key. |
| Business Key | `customer_id` | Operational customer identifier. |

---

### Product

| Property | Value |
| --- | --- |
| Business Name | Product Dimension |
| Technical Table Name | `dim_product` |
| Domain | Product Portfolio |
| Description | Dimension table storing descriptive product and offer attributes for portfolio and commercialization analysis. |
| Entity Type | Dimension Entity |
| Business Keys | `product_id` |
| Technical Key | `product_key` |
| Measures | None explicit |
| Relationships | Product Appears in Booking Transactions |
| Confidence | 1.00 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Product Key | `product_key` | Primary Key | integer | Product Key | 1.00 |
| Product ID | `product_id` | Business Key | character varying(30) | Product ID | 1.00 |
| Product Name | `product_name` | Descriptive Attribute | character varying(80) | Product Name | 1.00 |
| Product Family | `product_family` | Dimension Attribute | character varying(30) | Product Family | 1.00 |
| Technology Domain | `technology_domain` | Dimension Attribute | character varying(40) | Technology Domain | 0.98 |
| Offer Type | `offer_type` | Dimension Attribute | character varying(30) | Offer Type | 1.00 |
| Business Entity | `business_entity` | Dimension Attribute | character varying(30) | Business Entity | 0.94 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Product Portfolio Hierarchy | Business Entity → Technology Domain → Product Family → Product Name |
| Offer Hierarchy | Offer Type → Product Name |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `product_key` | Warehouse surrogate key. |
| Business Key | `product_id` | Operational product identifier. |

---

### Partner

| Property | Value |
| --- | --- |
| Business Name | Partner Dimension |
| Technical Table Name | `dim_partner` |
| Domain | Partner & Channel |
| Description | Dimension table storing partner identity and route-to-market information for indirect sales analysis. |
| Entity Type | Dimension Entity |
| Business Keys | `partner_id` |
| Technical Key | `partner_key` |
| Measures | None explicit |
| Relationships | Partner Influences Booking Transactions |
| Confidence | 1.00 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Partner Key | `partner_key` | Primary Key | integer | Partner Key | 1.00 |
| Partner ID | `partner_id` | Business Key | character varying(20) | Partner ID | 1.00 |
| Partner Name | `partner_name` | Descriptive Attribute | character varying(60) | Partner Name | 1.00 |
| Partner Type | `partner_type` | Dimension Attribute | character varying(30) | Partner Type | 1.00 |
| Partner Tier | `partner_tier` | Dimension Attribute | character varying(30) | Partner Tier | 1.00 |
| Route to Market | `route_to_market` | Dimension Attribute | character varying(20) | Route to Market | 1.00 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Partner Classification Hierarchy | Route to Market → Partner Type → Partner Tier → Partner Name |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `partner_key` | Warehouse surrogate key. |
| Business Key | `partner_id` | Operational partner identifier. |

---

### Geography

| Property | Value |
| --- | --- |
| Business Name | Geography Dimension |
| Technical Table Name | `dim_geography` |
| Domain | Geography |
| Description | Dimension table storing selling geography descriptors for regional performance reporting. |
| Entity Type | Dimension Entity |
| Business Keys | None explicit in supplied metadata |
| Technical Key | `geography_key` |
| Measures | None explicit |
| Relationships | Geography Contains Booking Transactions |
| Confidence | 0.98 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Geography Key | `geography_key` | Primary Key | integer | Geography Key | 1.00 |
| Sales Region | `region` | Dimension Attribute | character varying(20) | Sales Region | 1.00 |
| Sales Theater | `theater` | Dimension Attribute | character varying(30) | Sales Theater | 1.00 |
| Sales Country | `country` | Dimension Attribute | character varying(40) | Sales Country | 1.00 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Selling Geography Hierarchy | Sales Region → Sales Theater → Sales Country |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `geography_key` | Warehouse surrogate key. |

---

### Sales Representative

| Property | Value |
| --- | --- |
| Business Name | Sales Representative Dimension |
| Technical Table Name | `dim_sales_rep` |
| Domain | Sales Organization |
| Description | Dimension table storing descriptive information about sales personnel responsible for bookings. |
| Entity Type | Dimension Entity |
| Business Keys | `rep_id` |
| Technical Key | `sales_rep_key` |
| Measures | None explicit |
| Relationships | Sales Representative Owns Booking Transactions |
| Confidence | 1.00 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Sales Representative Key | `sales_rep_key` | Primary Key | integer | Sales Representative Key | 1.00 |
| Sales Representative ID | `rep_id` | Business Key | character varying(20) | Sales Representative ID | 1.00 |
| Sales Representative Name | `rep_name` | Descriptive Attribute | character varying(60) | Sales Representative Name | 1.00 |
| Sales Role | `sales_role` | Dimension Attribute | character varying(40) | Sales Role | 1.00 |
| Sales Team | `sales_team` | Dimension Attribute | character varying(40) | Sales Team | 1.00 |
| Covered Segment | `segment_covered` | Dimension Attribute | character varying(30) | Covered Segment | 0.98 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Sales Organization Hierarchy | Sales Team → Sales Role → Sales Representative Name |
| Coverage Hierarchy | Covered Segment → Sales Representative Name |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `sales_rep_key` | Warehouse surrogate key. |
| Business Key | `rep_id` | Operational sales representative identifier. |

---

### Contract

| Property | Value |
| --- | --- |
| Business Name | Contract Dimension |
| Technical Table Name | `dim_contract` |
| Domain | Contract & Renewal |
| Description | Dimension table storing descriptive attributes of commercial agreements associated with bookings. |
| Entity Type | Dimension Entity |
| Business Keys | None explicit in supplied metadata |
| Technical Key | `contract_key` |
| Measures | None explicit |
| Relationships | Contract Classifies Booking Transactions |
| Confidence | 0.98 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Contract Key | `contract_key` | Primary Key | integer | Contract Key | 1.00 |
| Contract Type | `contract_type` | Dimension Attribute | character varying(40) | Contract Type | 1.00 |
| Contract Term Months | `term_months` | Dimension Attribute | integer | Contract Term Months | 1.00 |
| Auto Renew Indicator | `auto_renew_flag` | Dimension Attribute | character(1) | Auto Renew Indicator | 0.95 |
| Coverage Level | `coverage_level` | Dimension Attribute | character varying(20) | Coverage Level | 1.00 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Contract Coverage Hierarchy | Contract Type → Coverage Level |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `contract_key` | Warehouse surrogate key. |

---

### Date

| Property | Value |
| --- | --- |
| Business Name | Date Dimension |
| Technical Table Name | `dim_date` |
| Domain | Time & Fiscal Reporting |
| Description | Dimension table storing calendar and fiscal date attributes for reporting and time-based analysis. |
| Entity Type | Dimension Entity |
| Business Keys | `full_date` |
| Technical Key | `date_key` |
| Measures | None explicit |
| Relationships | Date Organizes Booking Transactions |
| Confidence | 1.00 |

#### Attributes

| Attribute Name | Technical Column | Role | Data Type | Glossary Mapping | Confidence |
| --- | --- | --- | --- | --- | ---: |
| Date Key | `date_key` | Primary Key | integer | Date Key | 1.00 |
| Full Date | `full_date` | Business Key / Date Attribute | date | Full Date | 1.00 |
| Month Name | `month_name` | Dimension Attribute | character varying(12) | Month Name | 1.00 |
| Calendar Year | `calendar_year` | Dimension Attribute | integer | Calendar Year | 1.00 |
| Fiscal Year | `fiscal_year` | Dimension Attribute | character varying(6) | Fiscal Year | 1.00 |
| Fiscal Quarter | `fiscal_quarter` | Dimension Attribute | character varying(10) | Fiscal Quarter | 1.00 |
| Fiscal Period Sequence | `fiscal_period_seq` | Dimension Attribute | integer | Fiscal Period Sequence | 1.00 |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Calendar Hierarchy | Calendar Year → Month Name → Full Date |
| Fiscal Hierarchy | Fiscal Year → Fiscal Quarter → Fiscal Period Sequence → Full Date |

#### Keys

| Key Type | Column(s) | Meaning |
| --- | --- | --- |
| Primary Key | `date_key` | Warehouse surrogate key. |
| Business Key | `full_date` | Actual reporting date. |

## Relationships

| Relationship Name | Parent Entity | Child Entity | Relationship Type | Cardinality | Technical Basis | Confidence Score |
| --- | --- | --- | --- | --- | --- | ---: |
| Booking Date | Date Dimension | Booking Transaction Fact | One-to-Many | One Date to Many Booking Transactions | `fact_bookings.date_key` → `dim_date.date_key` | 1.00 |
| Booking Customer | Customer Dimension | Booking Transaction Fact | One-to-Many | One Customer to Many Booking Transactions | `fact_bookings.customer_key` → `dim_customer.customer_key` | 1.00 |
| Booking Product | Product Dimension | Booking Transaction Fact | One-to-Many | One Product to Many Booking Transactions | `fact_bookings.product_key` → `dim_product.product_key` | 1.00 |
| Booking Partner | Partner Dimension | Booking Transaction Fact | One-to-Many | One Partner to Many Booking Transactions | `fact_bookings.partner_key` → `dim_partner.partner_key` | 1.00 |
| Booking Geography | Geography Dimension | Booking Transaction Fact | One-to-Many | One Geography to Many Booking Transactions | `fact_bookings.geography_key` → `dim_geography.geography_key` | 1.00 |
| Booking Sales Representative | Sales Representative Dimension | Booking Transaction Fact | One-to-Many | One Sales Representative to Many Booking Transactions | `fact_bookings.sales_rep_key` → `dim_sales_rep.sales_rep_key` | 1.00 |
| Booking Contract | Contract Dimension | Booking Transaction Fact | One-to-Many | One Contract Classification to Many Booking Transactions | `fact_bookings.contract_key` → `dim_contract.contract_key` | 1.00 |

## Measures

| Measure Name | Business Definition | Technical Mapping | Aggregation Type | Explicit or Inferred |
| --- | --- | --- | --- | --- |
| Quantity Sold | Number of units, licenses, or items booked on the transaction line. | `fact_bookings.quantity` | SUM | Explicit |
| Unit List Price USD | Standard list price per unit in U.S. dollars before discount. | `fact_bookings.unit_list_price_usd` | AVG / context-specific | Explicit |
| Discount Percentage | Percentage discount applied relative to list price. | `fact_bookings.discount_pct` | AVG / weighted rule inferred | Explicit with aggregation inference |
| Booking Amount USD | Net booked value recognized for the transaction in U.S. dollars. | `fact_bookings.booking_amount_usd` | SUM | Explicit |
| Annual Contract Value USD | Annualized contract value of the booking in U.S. dollars. | `fact_bookings.acv_usd` | SUM | Explicit |
| Total Contract Value USD | Total committed contract value over full term in U.S. dollars. | `fact_bookings.tcv_usd` | SUM | Explicit |
| Renewal Indicator | Flag indicating whether the booking is associated with a renewal event. | `fact_bookings.is_renewal` | SUM / COUNT with semantic rule | Explicit with aggregation inference |
| Booking Type | Classification of booking transaction such as New, Renewal, or Upsell. | `fact_bookings.booking_type` | COUNT / GROUP BY classification | Explicit with semantic usage inference |

## Glossary Mapping

| Business Term | Technical Mapping | Confidence Score |
| --- | --- | ---: |
| Contract Dimension | `dim_contract` | 1.00 |
| Customer Dimension | `dim_customer` | 1.00 |
| Date Dimension | `dim_date` | 1.00 |
| Geography Dimension | `dim_geography` | 1.00 |
| Partner Dimension | `dim_partner` | 1.00 |
| Product Dimension | `dim_product` | 1.00 |
| Sales Representative Dimension | `dim_sales_rep` | 1.00 |
| Booking Transaction Fact | `fact_bookings` | 1.00 |
| Contract Key | `dim_contract.contract_key`, `fact_bookings.contract_key` | 1.00 |
| Contract Type | `dim_contract.contract_type` | 1.00 |
| Contract Term Months | `dim_contract.term_months` | 1.00 |
| Auto Renew Indicator | `dim_contract.auto_renew_flag` | 0.95 |
| Coverage Level | `dim_contract.coverage_level` | 1.00 |
| Customer Key | `dim_customer.customer_key`, `fact_bookings.customer_key` | 1.00 |
| Customer ID | `dim_customer.customer_id` | 1.00 |
| Customer Name | `dim_customer.customer_name` | 1.00 |
| Customer Segment | `dim_customer.segment` | 0.99 |
| Customer Industry | `dim_customer.industry` | 1.00 |
| Account Tier | `dim_customer.account_tier` | 1.00 |
| Customer Headquarters Country | `dim_customer.hq_country` | 1.00 |
| Customer Headquarters Region | `dim_customer.hq_region` | 1.00 |
| Date Key | `dim_date.date_key` | 1.00 |
| Full Date | `dim_date.full_date` | 1.00 |
| Month Name | `dim_date.month_name` | 1.00 |
| Calendar Year | `dim_date.calendar_year` | 1.00 |
| Fiscal Year | `dim_date.fiscal_year` | 1.00 |
| Fiscal Quarter | `dim_date.fiscal_quarter` | 1.00 |
| Fiscal Period Sequence | `dim_date.fiscal_period_seq` | 1.00 |
| Geography Key | `dim_geography.geography_key`, `fact_bookings.geography_key` | 1.00 |
| Sales Region | `dim_geography.region` | 1.00 |
| Sales Theater | `dim_geography.theater` | 1.00 |
| Sales Country | `dim_geography.country` | 1.00 |
| Partner Key | `dim_partner.partner_key`, `fact_bookings.partner_key` | 1.00 |
| Partner ID | `dim_partner.partner_id` | 1.00 |
| Partner Name | `dim_partner.partner_name` | 1.00 |
| Partner Type | `dim_partner.partner_type` | 1.00 |
| Partner Tier | `dim_partner.partner_tier` | 1.00 |
| Route to Market | `dim_partner.route_to_market` | 1.00 |
| Product Key | `dim_product.product_key`, `fact_bookings.product_key` | 1.00 |
| Product ID | `dim_product.product_id` | 1.00 |
| Product Name | `dim_product.product_name` | 1.00 |
| Product Family | `dim_product.product_family` | 1.00 |
| Technology Domain | `dim_product.technology_domain` | 0.98 |
| Offer Type | `dim_product.offer_type` | 1.00 |
| Business Entity | `dim_product.business_entity` | 0.94 |
| Sales Representative Key | `dim_sales_rep.sales_rep_key`, `fact_bookings.sales_rep_key` | 1.00 |
| Sales Representative ID | `dim_sales_rep.rep_id` | 1.00 |
| Sales Representative Name | `dim_sales_rep.rep_name` | 1.00 |
| Sales Role | `dim_sales_rep.sales_role` | 1.00 |
| Sales Team | `dim_sales_rep.sales_team` | 1.00 |
| Covered Segment | `dim_sales_rep.segment_covered` | 0.98 |
| Booking ID | `fact_bookings.booking_id` | 1.00 |
| Order Number | `fact_bookings.order_number` | 0.99 |
| Order Line Number | `fact_bookings.order_line_number` | 0.99 |
| Booking Date Key | `fact_bookings.date_key` | 1.00 |
| Booking Type | `fact_bookings.booking_type` | 0.98 |
| Renewal Indicator | `fact_bookings.is_renewal` | 0.95 |
| Quantity Sold | `fact_bookings.quantity` | 1.00 |
| Unit List Price USD | `fact_bookings.unit_list_price_usd` | 1.00 |
| Discount Percentage | `fact_bookings.discount_pct` | 1.00 |
| Booking Amount USD | `fact_bookings.booking_amount_usd` | 1.00 |
| Annual Contract Value USD | `fact_bookings.acv_usd` | 1.00 |
| Total Contract Value USD | `fact_bookings.tcv_usd` | 1.00 |

## Unmapped / Ambiguity Review

| Review Type | Result | Detail |
| --- | --- | --- |
| Unmapped columns | None | All 61 columns were mapped to business terms. |
| Duplicate mappings | Acceptable reuse | Shared technical key names appear across dimension PK and fact FK contexts by design. |
| Ambiguous mappings | Limited | `auto_renew_flag`, `is_renewal`, and `business_entity` retain moderate inference because no data values were available for empirical confirmation. |

## Semantic Reasoning Notes

| Topic | Insight |
| --- | --- |
| Explicit metadata | Table structures, keys, foreign keys, measures, and most business term mappings are explicitly supported by the supplied data dictionary and glossary. |
| Inferred semantics | Business hierarchies, domain partitioning, some business keys, and certain aggregation recommendations are inferred from naming conventions, process flow, and glossary definitions. |
| Confidence method | 1.00 indicates explicit schema-plus-glossary support; 0.95–0.99 indicates strong metadata and process alignment; below 0.95 indicates moderate inference where value-level data was unavailable. |
| Model quality | The semantic model is structurally valid, business-aligned, reusable, and suitable for downstream knowledge modeling and analytics, with the primary limitation being lack of populated data for runtime validation. |
