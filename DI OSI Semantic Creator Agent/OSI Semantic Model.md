# OSI Semantic Model

## 1. Domains

| Domain Name | Description |
|---|---|
| Sales Transactions | Semantic domain for booking transaction facts, commercial classifications, and measurable booking outcomes. |
| Customer Management | Semantic domain for customer identity, segmentation, and headquarters location context. |
| Product Management | Semantic domain for product identifiers, portfolio classifications, technology alignment, and commercial offer structure. |
| Partner Management | Semantic domain for partner identity, channel classification, program tier, and route-to-market context. |
| Geography | Semantic domain for regional sales geography classifications including region, theater, and country. |
| Sales Organization | Semantic domain for seller identity, role, team, and segment coverage context. |
| Contract Management | Semantic domain for contract structure, term, renewal behavior, and coverage characteristics. |
| Time Management | Semantic domain for calendar and fiscal reporting attributes used in time intelligence and trend analysis. |

## 2. Entities

### 2.1 Booking Transaction

| Field | Value |
|---|---|
| Business Name | Booking Transaction |
| Technical Table Name | `fact_bookings` |
| Description | Central fact entity recording booking transactions at order-line grain with financial measures and links to conformed dimensions. |
| Entity Type | Fact |
| Explicit Grain | One row per booking transaction / order line |
| Business Keys | `booking_id` (surrogate primary key); inferred transactional identifier: `order_number` + `order_line_number` |
| Confidence on Inferred Business Key | 0.84 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Booking ID | `booking_id` | Surrogate key that uniquely identifies a booking transaction row. | integer | Primary Key |
| Order Number | `order_number` | Sales order number associated with the booking transaction. | character varying(20) | Degenerate Dimension Attribute |
| Order Line Number | `order_line_number` | Line item number within the sales order. | integer | Degenerate Dimension Attribute |
| Booking Date Key | `date_key` | Foreign key linking the booking to the Date entity. | integer | Foreign Key |
| Customer Key | `customer_key` | Foreign key linking the booking to the Customer entity. | integer | Foreign Key |
| Product Key | `product_key` | Foreign key linking the booking to the Product entity. | integer | Foreign Key |
| Partner Key | `partner_key` | Foreign key linking the booking to the Partner entity. | integer | Foreign Key |
| Geography Key | `geography_key` | Foreign key linking the booking to the Geography entity. | integer | Foreign Key |
| Sales Representative Key | `sales_rep_key` | Foreign key linking the booking to the Sales Representative entity. | integer | Foreign Key |
| Contract Key | `contract_key` | Foreign key linking the booking to the Contract entity. | integer | Foreign Key |
| Booking Type | `booking_type` | Classification of the booking event such as New, Renewal, or Upsell. | character varying(15) | Analytical Attribute |
| Renewal Indicator | `is_renewal` | Indicator showing whether the booking is associated with a contract renewal. | integer | Analytical Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type | Data Type |
|---|---|---|---|---|
| Quantity Sold | `quantity` | Number of units, licenses, or subscriptions included in the booking line. | SUM | integer |
| Unit List Price USD | `unit_list_price_usd` | Standard list price per unit in USD before discounts. | SUM / AVG | numeric(12,2) |
| Discount Percentage | `discount_pct` | Percentage discount applied relative to list price. | AVG | numeric(5,2) |
| Booking Amount USD | `booking_amount_usd` | Net booked value of the transaction line in USD. | SUM | numeric(14,2) |
| Annual Contract Value USD | `acv_usd` | Annualized contract value of the booking in USD. | SUM | numeric(14,2) |
| Total Contract Value USD | `tcv_usd` | Total contract value of the booking over the full term in USD. | SUM | numeric(14,2) |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `booking_id` |
| Foreign Keys | `date_key`, `customer_key`, `product_key`, `partner_key`, `geography_key`, `sales_rep_key`, `contract_key` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Booking Transaction occurs on Date | Date | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction is for Customer | Customer | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction includes Product | Product | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction involves Partner | Partner | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction is assigned to Geography | Geography | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction is owned by Sales Representative | Sales Representative | Many-to-One from fact to dimension | Many-to-One | 1.00 |
| Booking Transaction is governed by Contract | Contract | Many-to-One from fact to dimension | Many-to-One | 1.00 |

### 2.2 Customer

| Field | Value |
|---|---|
| Business Name | Customer |
| Technical Table Name | `dim_customer` |
| Description | Dimension entity describing customer identity, segment, industry, account tier, and headquarters geography. |
| Entity Type | Dimension |
| Business Keys | `customer_key` (surrogate primary key); `customer_id` (business identifier) |
| Confidence on Business Identifier | 1.00 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Customer Key | `customer_key` | Surrogate key that uniquely identifies a customer dimension record. | integer | Primary Key |
| Customer ID | `customer_id` | Business identifier assigned to a customer account. | character varying(20) | Business Key |
| Customer Name | `customer_name` | Name of the customer organization. | character varying(80) | Attribute |
| Customer Segment | `segment` | Market segment to which the customer belongs. | character varying(30) | Attribute |
| Industry | `industry` | Industry classification of the customer organization. | character varying(40) | Attribute |
| Account Tier | `account_tier` | Tier or strategic classification assigned to the customer account. | character varying(20) | Attribute |
| Headquarters Country | `hq_country` | Country in which the customer's headquarters is located. | character varying(40) | Attribute |
| Headquarters Region | `hq_region` | Broad regional classification for the customer's headquarters location. | character varying(20) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Customer is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `customer_key` |
| Business Key | `customer_id` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Customer has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.3 Product

| Field | Value |
|---|---|
| Business Name | Product |
| Technical Table Name | `dim_product` |
| Description | Dimension entity describing Cisco products, product families, technology domains, offer types, and business entities. |
| Entity Type | Dimension |
| Business Keys | `product_key` (surrogate primary key); `product_id` (business identifier) |
| Confidence on Business Identifier | 1.00 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Product Key | `product_key` | Surrogate key that uniquely identifies a product dimension record. | integer | Primary Key |
| Product ID | `product_id` | Business identifier assigned to a Cisco product, SKU, or offer. | character varying(30) | Business Key |
| Product Name | `product_name` | Descriptive name of the Cisco product or offer. | character varying(80) | Attribute |
| Product Family | `product_family` | Family or portfolio grouping to which the product belongs. | character varying(30) | Attribute |
| Technology Domain | `technology_domain` | Technology area associated with the product. | character varying(40) | Attribute |
| Offer Type | `offer_type` | Commercial offer classification such as hardware, software, SaaS, subscription, or support. | character varying(30) | Attribute |
| Business Entity | `business_entity` | Internal Cisco business organization or portfolio owner associated with the product. | character varying(30) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Product is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `product_key` |
| Business Key | `product_id` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Product has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.4 Partner

| Field | Value |
|---|---|
| Business Name | Partner |
| Technical Table Name | `dim_partner` |
| Description | Dimension entity describing channel partner identity, type, tier, and route-to-market characteristics. |
| Entity Type | Dimension |
| Business Keys | `partner_key` (surrogate primary key); `partner_id` (business identifier) |
| Confidence on Business Identifier | 1.00 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Partner Key | `partner_key` | Surrogate key that uniquely identifies a partner dimension record. | integer | Primary Key |
| Partner ID | `partner_id` | Business identifier assigned to a partner. | character varying(20) | Business Key |
| Partner Name | `partner_name` | Name of the partner organization involved in the booking. | character varying(60) | Attribute |
| Partner Type | `partner_type` | Classification of the partner organization such as distributor, VAR, or systems integrator. | character varying(30) | Attribute |
| Partner Tier | `partner_tier` | Program or performance tier assigned to the partner. | character varying(30) | Attribute |
| Route to Market | `route_to_market` | Sales route through which the booking was transacted, such as direct, two-tier, or reseller-led. | character varying(20) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Partner is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `partner_key` |
| Business Key | `partner_id` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Partner has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.5 Geography

| Field | Value |
|---|---|
| Business Name | Geography |
| Technical Table Name | `dim_geography` |
| Description | Dimension entity describing sales geography classifications including region, theater, and country. |
| Entity Type | Dimension |
| Business Keys | `geography_key` (surrogate primary key) |
| Confidence on Business Identifier | 0.90 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Geography Key | `geography_key` | Surrogate key that uniquely identifies a geography dimension record. | integer | Primary Key |
| Region | `region` | High-level geographic region associated with a booking or account. | character varying(20) | Attribute |
| Theater | `theater` | Intermediate Cisco geographic grouping between region and country. | character varying(30) | Attribute |
| Country | `country` | Country associated with the geography dimension record. | character varying(40) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Geography is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `geography_key` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Geography has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.6 Sales Representative

| Field | Value |
|---|---|
| Business Name | Sales Representative |
| Technical Table Name | `dim_sales_rep` |
| Description | Dimension entity describing seller identity and sales organizational context including role, team, and segment coverage. |
| Entity Type | Dimension |
| Business Keys | `sales_rep_key` (surrogate primary key); `rep_id` (business identifier) |
| Confidence on Business Identifier | 1.00 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Sales Representative Key | `sales_rep_key` | Surrogate key that uniquely identifies a sales representative dimension record. | integer | Primary Key |
| Sales Representative ID | `rep_id` | Business identifier assigned to a sales representative. | character varying(20) | Business Key |
| Sales Representative Name | `rep_name` | Name of the sales representative responsible for the booking. | character varying(60) | Attribute |
| Sales Role | `sales_role` | Role of the sales representative within the sales organization. | character varying(40) | Attribute |
| Sales Team | `sales_team` | Team or organizational unit to which the sales representative belongs. | character varying(40) | Attribute |
| Covered Segment | `segment_covered` | Customer segment or market coverage assigned to the sales representative. | character varying(30) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Sales Representative is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `sales_rep_key` |
| Business Key | `rep_id` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Sales Representative has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.7 Contract

| Field | Value |
|---|---|
| Business Name | Contract |
| Technical Table Name | `dim_contract` |
| Description | Dimension entity describing commercial agreement structure, term, renewal behavior, and support coverage. |
| Entity Type | Dimension |
| Business Keys | `contract_key` (surrogate primary key) |
| Confidence on Business Identifier | 0.88 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Contract Key | `contract_key` | Surrogate key that uniquely identifies a contract dimension record. | integer | Primary Key |
| Contract Type | `contract_type` | Classification of the commercial agreement associated with the booking. | character varying(40) | Attribute |
| Contract Term Months | `term_months` | Duration of the contract in months. | integer | Attribute |
| Auto Renew Indicator | `auto_renew_flag` | Indicator showing whether the contract renews automatically at end of term. | character(1) | Attribute |
| Coverage Level | `coverage_level` | Level of service or support coverage provided under the contract. | character varying(20) | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Contract is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `contract_key` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Contract has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

### 2.8 Date

| Field | Value |
|---|---|
| Business Name | Date |
| Technical Table Name | `dim_date` |
| Description | Conformed time dimension supporting both calendar and Cisco fiscal reporting. |
| Entity Type | Dimension |
| Business Keys | `date_key` (surrogate primary key); `full_date` (natural date identifier) |
| Confidence on Business Identifier | 0.99 |

**Attributes**

| Attribute Name | Technical Column | Description | Data Type | Role |
|---|---|---|---|---|
| Date Key | `date_key` | Surrogate key that uniquely identifies a date dimension record. | integer | Primary Key |
| Full Date | `full_date` | Actual calendar date represented by the date record. | date | Business Key |
| Month Name | `month_name` | Textual name of the calendar month. | character varying(12) | Attribute |
| Calendar Year | `calendar_year` | Gregorian calendar year for the date. | integer | Attribute |
| Fiscal Year | `fiscal_year` | Cisco fiscal year associated with the date. | character varying(6) | Attribute |
| Fiscal Quarter | `fiscal_quarter` | Cisco fiscal quarter associated with the date. | character varying(10) | Attribute |
| Fiscal Period Sequence | `fiscal_period_seq` | Relative ordering of fiscal periods. | integer | Attribute |

**Measures**

| Measure Name | Technical Column | Business Definition | Aggregation Type |
|---|---|---|---|
| None | N/A | Date is a descriptive dimension entity and contains no additive measures. | N/A |

**Keys**

| Key Type | Columns |
|---|---|
| Primary Key | `date_key` |
| Business Key | `full_date` |

**Relationships**

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
|---|---|---|---|---:|
| Date has Booking Transactions | Booking Transaction | Dimension-to-Fact | One-to-Many | 1.00 |

## 3. Relationships

| Relationship Name | Parent Entity | Child Entity | Relationship Type | Cardinality | Confidence Score | Evidence |
|---|---|---|---|---|---:|---|
| Date to Booking Transaction | Date | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.date_key -> dim_date.date_key` |
| Customer to Booking Transaction | Customer | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.customer_key -> dim_customer.customer_key` |
| Product to Booking Transaction | Product | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.product_key -> dim_product.product_key` |
| Partner to Booking Transaction | Partner | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.partner_key -> dim_partner.partner_key` |
| Geography to Booking Transaction | Geography | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.geography_key -> dim_geography.geography_key` |
| Sales Representative to Booking Transaction | Sales Representative | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.sales_rep_key -> dim_sales_rep.sales_rep_key` |
| Contract to Booking Transaction | Contract | Booking Transaction | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit FK `fact_bookings.contract_key -> dim_contract.contract_key` |

## 4. Measures

| Measure Name | Technical Mapping | Business Definition | Aggregation Type | Source Entity | Confidence Score |
|---|---|---|---|---|---:|
| Quantity Sold | `fact_bookings.quantity` | Number of units, licenses, or subscriptions included in the booking line. | SUM | Booking Transaction | 1.00 |
| Unit List Price USD | `fact_bookings.unit_list_price_usd` | Standard list price per unit in USD before discounts. | SUM / AVG | Booking Transaction | 0.95 |
| Discount Percentage | `fact_bookings.discount_pct` | Percentage discount applied relative to list price. | AVG | Booking Transaction | 0.99 |
| Booking Amount USD | `fact_bookings.booking_amount_usd` | Net booked value of the transaction line in USD. | SUM | Booking Transaction | 1.00 |
| Annual Contract Value USD | `fact_bookings.acv_usd` | Annualized contract value of the booking in USD, primarily for subscription and SaaS offers. | SUM | Booking Transaction | 1.00 |
| Total Contract Value USD | `fact_bookings.tcv_usd` | Total contract value of the booking over the full contract term in USD. | SUM | Booking Transaction | 1.00 |

## 5. Glossary Mapping

| Business Term | Technical Mapping | Confidence Score | Mapping Type | Notes |
|---|---|---:|---|---|
| Contract Dimension | `dim_contract` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Contract Key | `dim_contract.contract_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Contract Type | `dim_contract.contract_type` | 0.98 | Column-to-Business Term | Based on glossary and process context |
| Contract Term Months | `dim_contract.term_months` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Auto Renew Indicator | `dim_contract.auto_renew_flag` | 0.92 | Column-to-Business Term | Indicator semantics inferred from naming and context |
| Coverage Level | `dim_contract.coverage_level` | 0.97 | Column-to-Business Term | Explicit glossary term |
| Customer Dimension | `dim_customer` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Customer Key | `dim_customer.customer_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Customer ID | `dim_customer.customer_id` | 1.00 | Column-to-Business Term | Business identifier |
| Customer Name | `dim_customer.customer_name` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Customer Segment | `dim_customer.segment` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Industry | `dim_customer.industry` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Account Tier | `dim_customer.account_tier` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Headquarters Country | `dim_customer.hq_country` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Headquarters Region | `dim_customer.hq_region` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Date Dimension | `dim_date` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Date Key | `dim_date.date_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Full Date | `dim_date.full_date` | 1.00 | Column-to-Business Term | Natural date identifier |
| Month Name | `dim_date.month_name` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Calendar Year | `dim_date.calendar_year` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Fiscal Year | `dim_date.fiscal_year` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Fiscal Quarter | `dim_date.fiscal_quarter` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Fiscal Period Sequence | `dim_date.fiscal_period_seq` | 0.98 | Column-to-Business Term | Explicit glossary term |
| Geography Dimension | `dim_geography` | 0.98 | Table-to-Business Entity | Supported by glossary |
| Geography Key | `dim_geography.geography_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Region | `dim_geography.region` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Theater | `dim_geography.theater` | 0.85 | Column-to-Business Term | Cisco-specific hierarchy level inferred from documentation |
| Country | `dim_geography.country` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Partner Dimension | `dim_partner` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Partner Key | `dim_partner.partner_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Partner ID | `dim_partner.partner_id` | 1.00 | Column-to-Business Term | Business identifier |
| Partner Name | `dim_partner.partner_name` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Partner Type | `dim_partner.partner_type` | 0.97 | Column-to-Business Term | Supported by business process context |
| Partner Tier | `dim_partner.partner_tier` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Route to Market | `dim_partner.route_to_market` | 0.98 | Column-to-Business Term | Supported by process document |
| Product Dimension | `dim_product` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Product Key | `dim_product.product_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Product ID | `dim_product.product_id` | 1.00 | Column-to-Business Term | Business identifier |
| Product Name | `dim_product.product_name` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Product Family | `dim_product.product_family` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Technology Domain | `dim_product.technology_domain` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Offer Type | `dim_product.offer_type` | 0.98 | Column-to-Business Term | Supported by process document |
| Business Entity | `dim_product.business_entity` | 0.96 | Column-to-Business Term | Internal portfolio ownership term |
| Sales Representative Dimension | `dim_sales_rep` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Sales Representative Key | `dim_sales_rep.sales_rep_key` | 1.00 | Column-to-Business Term | Surrogate key |
| Sales Representative ID | `dim_sales_rep.rep_id` | 1.00 | Column-to-Business Term | Business identifier |
| Sales Representative Name | `dim_sales_rep.rep_name` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Sales Role | `dim_sales_rep.sales_role` | 0.98 | Column-to-Business Term | Supported by role descriptions in process document |
| Sales Team | `dim_sales_rep.sales_team` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Covered Segment | `dim_sales_rep.segment_covered` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Bookings Fact | `fact_bookings` | 1.00 | Table-to-Business Entity | Explicit glossary term |
| Booking ID | `fact_bookings.booking_id` | 1.00 | Column-to-Business Term | Surrogate key |
| Order Number | `fact_bookings.order_number` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Order Line Number | `fact_bookings.order_line_number` | 1.00 | Column-to-Business Term | Explicit glossary term |
| Booking Date Key | `fact_bookings.date_key` | 1.00 | Column-to-Business Term | Foreign key to Date |
| Customer Key | `fact_bookings.customer_key` | 1.00 | Column-to-Business Term | Foreign key to Customer |
| Product Key | `fact_bookings.product_key` | 1.00 | Column-to-Business Term | Foreign key to Product |
| Partner Key | `fact_bookings.partner_key` | 1.00 | Column-to-Business Term | Foreign key to Partner |
| Geography Key | `fact_bookings.geography_key` | 1.00 | Column-to-Business Term | Foreign key to Geography |
| Sales Representative Key | `fact_bookings.sales_rep_key` | 1.00 | Column-to-Business Term | Foreign key to Sales Representative |
| Contract Key | `fact_bookings.contract_key` | 1.00 | Column-to-Business Term | Foreign key to Contract |
| Booking Type | `fact_bookings.booking_type` | 0.97 | Column-to-Business Term | Expected values cited in business documentation |
| Renewal Indicator | `fact_bookings.is_renewal` | 0.95 | Column-to-Business Term | Flag semantics inferred from metadata and process context |
| Quantity Sold | `fact_bookings.quantity` | 1.00 | Measure Mapping | Explicit glossary term |
| Unit List Price USD | `fact_bookings.unit_list_price_usd` | 1.00 | Measure Mapping | Explicit glossary term |
| Discount Percentage | `fact_bookings.discount_pct` | 0.99 | Measure Mapping | Explicit glossary term |
| Booking Amount USD | `fact_bookings.booking_amount_usd` | 1.00 | Measure Mapping | Explicit glossary term |
| Annual Contract Value USD | `fact_bookings.acv_usd` | 1.00 | Measure Mapping | Explicit glossary term |
| Total Contract Value USD | `fact_bookings.tcv_usd` | 1.00 | Measure Mapping | Explicit glossary term |

## 6. Validation

| Validation Item | Status | Details |
|---|---|---|
| Duplicate Entities | PASS | No duplicate entities identified. |
| Duplicate Measures | PASS | No duplicate measures identified. |
| Circular Relationships | PASS | No circular relationships identified. |
| Missing Glossary Mappings | PASS | All tables and columns from the supplied schema are represented in glossary mappings. |
| Missing Keys | PASS | All tables have primary keys; fact table includes all declared foreign keys. |
| Orphan Entities | PASS | No structural orphan entities identified in the star schema. |
| Inference Control | PASS | No unsupported entities, attributes, measures, or relationships were added beyond metadata and documentation. |
| Data Availability Warning | WARNING | All tables were empty at profiling time, so semantic confidence for some inferred fields is lower than for explicit metadata. |
