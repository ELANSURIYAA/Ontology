# OSI Semantic Model

## 1. Validation Summary

| Validation Item | Status | Details |
| --- | --- | --- |
| Duplicate entities | PASS | No duplicate entities identified across the 8 discovered tables. |
| Duplicate measures | PASS | No duplicate measure names identified in the fact model. |
| Circular relationships | PASS | No circular relationships identified; the model is a hub-and-spoke star schema. |
| Missing glossary mappings | WARNING | Some business definitions are inferred from supplied business documents because native database comments are unavailable. |
| Missing keys | PASS | All entities have primary keys; fact table has 7 foreign keys to dimensions. |
| Orphan entities | PASS | No orphan entities structurally; all dimensions participate in a semantic relationship with `fact_bookings`. |
| Data-backed validation | WARNING | All tables are empty, so runtime validation of domains and instance-level integrity is not possible. |

## 2. Domains

| Domain Name | Description |
| --- | --- |
| Sales Transactions | Booking transaction domain capturing order-line booking events and measurable sales outcomes. |
| Customer Management | Customer master and segmentation domain used for customer-centric bookings analysis. |
| Product Management | Product and offer domain used for portfolio, family, and technology analysis. |
| Partner Management | Partner and route-to-market domain used for channel analytics. |
| Geography | Geographic domain used for region, theater, and country rollups. |
| Sales Organization | Sales resource and coverage domain used for rep, role, and team analytics. |
| Contract Management | Contract descriptor domain used for term, coverage, and renewal-related analysis. |
| Time | Calendar and fiscal time domain used for period-based reporting and trend analysis. |

## 3. Entities

### 3.1 Booking Transaction

| Property | Value |
| --- | --- |
| Business Name | Booking Transaction Fact |
| Technical Table Name | `ontology.fact_bookings` |
| Description | Central fact table capturing booking transactions at order-line grain with financial and operational measures. |
| Domain | Sales Transactions |
| Entity Type | Fact Table |
| Business Key | `booking_id` |
| Primary Key | `booking_id` |
| Grain | One row per booking transaction at order-line grain |
| Inference Note | Grain and business interpretation are explicitly supported by supplied metadata and business process documents. |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Booking ID | `booking_id` | integer | Unique identifier for a booking transaction record. | Primary Key |
| Order Number | `order_number` | character varying(20) | Business order number associated with the booking transaction. | Degenerate Dimension Attribute |
| Order Line Number | `order_line_number` | integer | Line number within the order representing the booking grain. | Grain Attribute |
| Booking Date Key | `date_key` | integer | Foreign key linking the booking to the date dimension. | Foreign Key |
| Booking Customer Key | `customer_key` | integer | Foreign key linking the booking to the customer dimension. | Foreign Key |
| Booking Product Key | `product_key` | integer | Foreign key linking the booking to the product dimension. | Foreign Key |
| Booking Partner Key | `partner_key` | integer | Foreign key linking the booking to the partner dimension. | Foreign Key |
| Booking Geography Key | `geography_key` | integer | Foreign key linking the booking to the geography dimension. | Foreign Key |
| Booking Sales Representative Key | `sales_rep_key` | integer | Foreign key linking the booking to the sales representative dimension. | Foreign Key |
| Booking Contract Key | `contract_key` | integer | Foreign key linking the booking to the contract dimension. | Foreign Key |
| Booking Type | `booking_type` | character varying(15) | Classification of the booking event such as New, Renewal, or Upsell. | Transaction Attribute |
| Renewal Indicator | `is_renewal` | integer | Indicator showing whether the booking represents a renewal transaction. | Transaction Indicator |
| Quantity Sold | `quantity` | integer | Number of units, licenses, or items booked on the order line. | Additive Measure Support Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type | Confidence |
| --- | --- | --- | --- | --- |
| Quantity Sold | `quantity` | Number of units, licenses, or items booked on the order line. | Sum | 0.97 |
| Unit List Price USD | `unit_list_price_usd` | Standard list price per unit in U.S. dollars before discounts. | Sum / Average with governance caution | 0.92 |
| Discount Percentage | `discount_pct` | Percentage discount applied relative to list price. | Average with governance caution | 0.90 |
| Booking Amount USD | `booking_amount_usd` | Net booked transaction amount in U.S. dollars. | Sum | 0.99 |
| Annual Contract Value USD | `acv_usd` | Annualized value of the contract or subscription associated with the booking in U.S. dollars. | Sum | 0.97 |
| Total Contract Value USD | `tcv_usd` | Total value of the contract associated with the booking in U.S. dollars over the full contract term. | Sum | 0.98 |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `booking_id` |
| Foreign Key | `date_key` → `ontology.dim_date.date_key` |
| Foreign Key | `customer_key` → `ontology.dim_customer.customer_key` |
| Foreign Key | `product_key` → `ontology.dim_product.product_key` |
| Foreign Key | `partner_key` → `ontology.dim_partner.partner_key` |
| Foreign Key | `geography_key` → `ontology.dim_geography.geography_key` |
| Foreign Key | `sales_rep_key` → `ontology.dim_sales_rep.sales_rep_key` |
| Foreign Key | `contract_key` → `ontology.dim_contract.contract_key` |

#### Relationships

| Relationship Name | Parent Entity | Child Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- | --- |
| Booking Occurs On Date | Date Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 1.00 |
| Customer Places Booking | Customer Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.99 |
| Product Appears In Booking | Product Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.99 |
| Partner Participates In Booking | Partner Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.98 |
| Geography Classifies Booking | Geography Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.98 |
| Sales Representative Owns Booking | Sales Representative Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.98 |
| Contract Classifies Booking | Contract Dimension | Booking Transaction Fact | Dimensional | One-to-Many | 0.97 |

---

### 3.2 Customer Dimension

| Property | Value |
| --- | --- |
| Business Name | Customer Dimension |
| Technical Table Name | `ontology.dim_customer` |
| Description | Dimension table containing descriptive customer master data used to analyze bookings by customer identity, segment, industry, and headquarters location. |
| Domain | Customer Management |
| Entity Type | Dimension Table |
| Business Key | `customer_id` |
| Primary Key | `customer_key` |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Customer Key | `customer_key` | integer | Surrogate key that uniquely identifies a customer dimension record. | Primary Key |
| Customer ID | `customer_id` | character varying(20) | Business identifier assigned to a customer account. | Business Key |
| Customer Name | `customer_name` | character varying(80) | Official name of the customer account. | Descriptive Attribute |
| Customer Segment | `segment` | character varying(30) | Market segment to which the customer belongs. | Dimension Attribute |
| Customer Industry | `industry` | character varying(40) | Industry classification of the customer. | Dimension Attribute |
| Account Tier | `account_tier` | character varying(20) | Tier classification assigned to the customer account. | Dimension Attribute |
| Headquarters Country | `hq_country` | character varying(40) | Country where the customer's headquarters is located. | Geography Attribute |
| Headquarters Region | `hq_region` | character varying(20) | Region where the customer's headquarters is located. | Geography Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Customer dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `customer_key` |
| Business Key | `customer_id` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Customer Places Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.99 |

---

### 3.3 Product Dimension

| Property | Value |
| --- | --- |
| Business Name | Product Dimension |
| Technical Table Name | `ontology.dim_product` |
| Description | Dimension table containing Cisco product master attributes such as product family, technology domain, offer type, and business entity. |
| Domain | Product Management |
| Entity Type | Dimension Table |
| Business Key | `product_id` |
| Primary Key | `product_key` |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Product Key | `product_key` | integer | Surrogate key that uniquely identifies a product dimension record. | Primary Key |
| Product ID | `product_id` | character varying(30) | Business identifier assigned to a Cisco product or offer. | Business Key |
| Product Name | `product_name` | character varying(80) | Business name of the product or offer. | Descriptive Attribute |
| Product Family | `product_family` | character varying(30) | Higher-level product grouping used to categorize related offers. | Hierarchy Attribute |
| Technology Domain | `technology_domain` | character varying(40) | Technology category or solution domain associated with the product. | Hierarchy Attribute |
| Offer Type | `offer_type` | character varying(30) | Commercial type of the product offer. | Dimension Attribute |
| Business Entity | `business_entity` | character varying(30) | Internal Cisco business entity or portfolio owning the product. | Dimension Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Product dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `product_key` |
| Business Key | `product_id` |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Product Portfolio Hierarchy | `business_entity` → `technology_domain` → `product_family` → `product_name` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Product Appears In Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.99 |

---

### 3.4 Partner Dimension

| Property | Value |
| --- | --- |
| Business Name | Partner Dimension |
| Technical Table Name | `ontology.dim_partner` |
| Description | Dimension table containing channel partner master data including type, tier, and route-to-market attributes. |
| Domain | Partner Management |
| Entity Type | Dimension Table |
| Business Key | `partner_id` |
| Primary Key | `partner_key` |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Partner Key | `partner_key` | integer | Surrogate key that uniquely identifies a partner dimension record. | Primary Key |
| Partner ID | `partner_id` | character varying(20) | Business identifier assigned to a partner organization. | Business Key |
| Partner Name | `partner_name` | character varying(60) | Official name of the partner organization. | Descriptive Attribute |
| Partner Type | `partner_type` | character varying(30) | Classification of the partner organization. | Dimension Attribute |
| Partner Tier | `partner_tier` | character varying(30) | Tier or level assigned to the partner within the partner program. | Hierarchy Attribute |
| Route to Market | `route_to_market` | character varying(20) | Selling motion or channel path through which the booking was transacted. | Dimension Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Partner dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `partner_key` |
| Business Key | `partner_id` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Partner Participates In Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.98 |

---

### 3.5 Geography Dimension

| Property | Value |
| --- | --- |
| Business Name | Geography Dimension |
| Technical Table Name | `ontology.dim_geography` |
| Description | Dimension table containing geographic attributes such as region, theater, and country for sales analysis. |
| Domain | Geography |
| Entity Type | Dimension Table |
| Business Key | Inferred composite business geography context |
| Primary Key | `geography_key` |
| Inference Note | No explicit natural business identifier is present; business-level uniqueness is inferred from geographic attributes. |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Geography Key | `geography_key` | integer | Surrogate key that uniquely identifies a geography dimension record. | Primary Key |
| Region | `region` | character varying(20) | Broad geographic region associated with the booking or business activity. | Hierarchy Attribute |
| Theater | `theater` | character varying(30) | Intermediate sales geography grouping used within Cisco regional organization structures. | Hierarchy Attribute |
| Country | `country` | character varying(40) | Country associated with the geography dimension row. | Hierarchy Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Geography dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `geography_key` |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Sales Geography Hierarchy | `region` → `theater` → `country` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Geography Classifies Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.98 |

---

### 3.6 Sales Representative Dimension

| Property | Value |
| --- | --- |
| Business Name | Sales Representative Dimension |
| Technical Table Name | `ontology.dim_sales_rep` |
| Description | Dimension table containing sales representative master data and coverage attributes. |
| Domain | Sales Organization |
| Entity Type | Dimension Table |
| Business Key | `rep_id` |
| Primary Key | `sales_rep_key` |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Sales Representative Key | `sales_rep_key` | integer | Surrogate key that uniquely identifies a sales representative dimension record. | Primary Key |
| Sales Representative ID | `rep_id` | character varying(20) | Business identifier assigned to a sales representative. | Business Key |
| Sales Representative Name | `rep_name` | character varying(60) | Full name of the sales representative. | Descriptive Attribute |
| Sales Role | `sales_role` | character varying(40) | Role performed by the sales representative in the sales organization. | Dimension Attribute |
| Sales Team | `sales_team` | character varying(40) | Team or organizational unit to which the sales representative belongs. | Hierarchy Attribute |
| Covered Segment | `segment_covered` | character varying(30) | Customer segment or market segment assigned to the sales representative for coverage. | Dimension Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Sales representative dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `sales_rep_key` |
| Business Key | `rep_id` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Sales Representative Owns Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.98 |

---

### 3.7 Contract Dimension

| Property | Value |
| --- | --- |
| Business Name | Contract Dimension |
| Technical Table Name | `ontology.dim_contract` |
| Description | Dimension table containing descriptive attributes of service, support, or subscription contracts associated with bookings. |
| Domain | Contract Management |
| Entity Type | Dimension Table |
| Business Key | Inferred contract business context; no separate natural identifier supplied |
| Primary Key | `contract_key` |
| Inference Note | Only surrogate key is present in metadata; no distinct business identifier column was provided. |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Contract Key | `contract_key` | integer | Surrogate key that uniquely identifies a contract dimension record. | Primary Key |
| Contract Type | `contract_type` | character varying(40) | Classification of the commercial or service agreement associated with a booking. | Dimension Attribute |
| Contract Term Months | `term_months` | integer | Number of months covered by the contract term. | Dimension Attribute |
| Auto Renew Indicator | `auto_renew_flag` | character(1) | Flag indicating whether the contract is configured to renew automatically. | Transaction Indicator |
| Coverage Level | `coverage_level` | character varying(20) | Service or support coverage level associated with the contract. | Dimension Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Contract dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `contract_key` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Contract Classifies Booking | Booking Transaction Fact | Parent to Child | One-to-Many | 0.97 |

---

### 3.8 Date Dimension

| Property | Value |
| --- | --- |
| Business Name | Date Dimension |
| Technical Table Name | `ontology.dim_date` |
| Description | Dimension table containing calendar and fiscal attributes for time-based analysis of bookings. |
| Domain | Time |
| Entity Type | Dimension Table |
| Business Key | `full_date` |
| Primary Key | `date_key` |

#### Attributes

| Attribute Name | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Date Key | `date_key` | integer | Surrogate key that uniquely identifies a date dimension record. | Primary Key |
| Full Date | `full_date` | date | Actual calendar date represented by the date dimension row. | Business Key |
| Month Name | `month_name` | character varying(12) | Name of the calendar month for the date. | Hierarchy Attribute |
| Calendar Year | `calendar_year` | integer | Calendar year associated with the date. | Hierarchy Attribute |
| Fiscal Year | `fiscal_year` | character varying(6) | Cisco fiscal year associated with the date. | Hierarchy Attribute |
| Fiscal Quarter | `fiscal_quarter` | character varying(10) | Fiscal quarter associated with the date. | Hierarchy Attribute |
| Fiscal Period Sequence | `fiscal_period_seq` | integer | Sequential numeric ordering of fiscal periods. | Ordering Attribute |

#### Measures

| Measure Name | Technical Column | Business Definition | Aggregation Type |
| --- | --- | --- | --- |
| None | N/A | Date dimension contains descriptive attributes only. | N/A |

#### Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `date_key` |
| Business Key | `full_date` |

#### Hierarchies

| Hierarchy Name | Levels |
| --- | --- |
| Calendar Hierarchy | `calendar_year` → `month_name` → `full_date` |
| Fiscal Hierarchy | `fiscal_year` → `fiscal_quarter` → `full_date` |

#### Relationships

| Relationship Name | Related Entity | Relationship Type | Cardinality | Confidence Score |
| --- | --- | --- | --- | --- |
| Booking Occurs On Date | Booking Transaction Fact | Parent to Child | One-to-Many | 1.00 |

## 4. Relationships

| Relationship Name | Parent Entity | Child Entity | Technical Mapping | Relationship Type | Cardinality | Confidence Score | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Booking Occurs On Date | Date Dimension | Booking Transaction Fact | `fact_bookings.date_key` → `dim_date.date_key` | Dimensional Foreign Key | One-to-Many | 1.00 | Explicit foreign key in metadata |
| Customer Places Booking | Customer Dimension | Booking Transaction Fact | `fact_bookings.customer_key` → `dim_customer.customer_key` | Dimensional Foreign Key | One-to-Many | 0.99 | Explicit foreign key and business process alignment |
| Product Appears In Booking | Product Dimension | Booking Transaction Fact | `fact_bookings.product_key` → `dim_product.product_key` | Dimensional Foreign Key | One-to-Many | 0.99 | Explicit foreign key and product analysis context |
| Partner Participates In Booking | Partner Dimension | Booking Transaction Fact | `fact_bookings.partner_key` → `dim_partner.partner_key` | Dimensional Foreign Key | One-to-Many | 0.98 | Explicit foreign key and route-to-market process context |
| Geography Classifies Booking | Geography Dimension | Booking Transaction Fact | `fact_bookings.geography_key` → `dim_geography.geography_key` | Dimensional Foreign Key | One-to-Many | 0.98 | Explicit foreign key and regional reporting context |
| Sales Representative Owns Booking | Sales Representative Dimension | Booking Transaction Fact | `fact_bookings.sales_rep_key` → `dim_sales_rep.sales_rep_key` | Dimensional Foreign Key | One-to-Many | 0.98 | Explicit foreign key and role ownership context |
| Contract Classifies Booking | Contract Dimension | Booking Transaction Fact | `fact_bookings.contract_key` → `dim_contract.contract_key` | Dimensional Foreign Key | One-to-Many | 0.97 | Explicit foreign key and contract lifecycle context |

## 5. Measures

| Measure Name | Technical Mapping | Business Definition | Aggregation Type | Additivity | Confidence Score |
| --- | --- | --- | --- | --- | --- |
| Quantity Sold | `ontology.fact_bookings.quantity` | Number of units, licenses, or items booked on the order line. | Sum | Additive across all dimensions | 0.97 |
| Unit List Price USD | `ontology.fact_bookings.unit_list_price_usd` | Standard list price per unit in U.S. dollars before discounts. | Average or derived analytic use preferred; simple sum only with caution | Non-additive/semi-analytic | 0.92 |
| Discount Percentage | `ontology.fact_bookings.discount_pct` | Percentage discount applied relative to list price. | Average or weighted average preferred | Non-additive | 0.90 |
| Booking Amount USD | `ontology.fact_bookings.booking_amount_usd` | Net booked transaction amount in U.S. dollars. | Sum | Additive across all dimensions | 0.99 |
| Annual Contract Value USD | `ontology.fact_bookings.acv_usd` | Annualized value of the contract or subscription associated with the booking in U.S. dollars. | Sum | Additive by transaction, subject to business policy | 0.97 |
| Total Contract Value USD | `ontology.fact_bookings.tcv_usd` | Total value of the contract associated with the booking in U.S. dollars over the full contract term. | Sum | Additive by transaction | 0.98 |

## 6. Glossary Mapping

| Business Term | Technical Mapping | Preferred Name | Synonyms | Business Domain | Confidence Score | Mapping Type |
| --- | --- | --- | --- | --- | --- | --- |
| Booking Transaction Fact | `ontology.fact_bookings` | Booking Transaction Fact | Bookings Fact; Booking Fact Table | Sales Transactions | 1.00 | Explicit table-to-glossary mapping |
| Customer Dimension | `ontology.dim_customer` | Customer Dimension | Account Dimension; Customer Master | Customer Management | 1.00 | Explicit table-to-glossary mapping |
| Product Dimension | `ontology.dim_product` | Product Dimension | Offer Dimension; Product Master | Product Management | 1.00 | Explicit table-to-glossary mapping |
| Partner Dimension | `ontology.dim_partner` | Partner Dimension | Channel Partner Dimension; Partner Master | Partner Management | 1.00 | Explicit table-to-glossary mapping |
| Geography Dimension | `ontology.dim_geography` | Geography Dimension | Location Dimension; Regional Dimension | Geography | 1.00 | Explicit table-to-glossary mapping |
| Sales Representative Dimension | `ontology.dim_sales_rep` | Sales Representative Dimension | Sales Rep Dimension; Seller Dimension | Sales Organization | 1.00 | Explicit table-to-glossary mapping |
| Contract Dimension | `ontology.dim_contract` | Contract Dimension | Contract Master; Agreement Dimension | Contract Management | 1.00 | Explicit table-to-glossary mapping |
| Date Dimension | `ontology.dim_date` | Date Dimension | Calendar Dimension; Time Dimension | Time | 1.00 | Explicit table-to-glossary mapping |
| Booking Amount USD | `ontology.fact_bookings.booking_amount_usd` | Booking Amount USD | Net Booking Value; Total Bookings Amount | Sales Measures | 0.99 | Explicit column-to-glossary mapping |
| Annual Contract Value USD | `ontology.fact_bookings.acv_usd` | Annual Contract Value USD | ACV | Sales Measures | 0.99 | Explicit column-to-glossary mapping |
| Total Contract Value USD | `ontology.fact_bookings.tcv_usd` | Total Contract Value USD | TCV | Sales Measures | 0.99 | Explicit column-to-glossary mapping |
| Quantity Sold | `ontology.fact_bookings.quantity` | Quantity Sold | Units Sold | Sales Measures | 0.98 | Explicit column-to-glossary mapping |
| Unit List Price USD | `ontology.fact_bookings.unit_list_price_usd` | Unit List Price USD | List Price; Unit Price USD | Sales Measures | 0.97 | Explicit column-to-glossary mapping |
| Discount Percentage | `ontology.fact_bookings.discount_pct` | Discount Percentage | Discount Rate | Sales Measures | 0.97 | Explicit column-to-glossary mapping |
| Booking Type | `ontology.fact_bookings.booking_type` | Booking Type | Booking Classification | Sales Transactions | 0.98 | Explicit column-to-glossary mapping |
| Renewal Indicator | `ontology.fact_bookings.is_renewal` | Renewal Indicator | Renewal Flag | Sales Transactions | 0.95 | Inferred coded-field mapping |
| Route to Market | `ontology.dim_partner.route_to_market` | Route to Market | RTM; Sales Channel Route | Partner Management | 0.98 | Explicit column-to-glossary mapping |
| Product Family | `ontology.dim_product.product_family` | Product Family | Family | Product Management | 0.98 | Explicit column-to-glossary mapping |
| Technology Domain | `ontology.dim_product.technology_domain` | Technology Domain | Technology Category; Solution Domain | Product Management | 0.96 | Inferred column-to-glossary mapping |
| Fiscal Year | `ontology.dim_date.fiscal_year` | Fiscal Year | FY | Time | 0.99 | Explicit column-to-glossary mapping |
| Fiscal Quarter | `ontology.dim_date.fiscal_quarter` | Fiscal Quarter | FQ; Quarter | Time | 0.99 | Explicit column-to-glossary mapping |
| Customer Segment | `ontology.dim_customer.segment` | Customer Segment | Market Segment | Customer Management | 0.97 | Inferred column-to-glossary mapping |
| Account Tier | `ontology.dim_customer.account_tier` | Account Tier | Customer Tier; Account Classification | Customer Management | 0.95 | Inferred column-to-glossary mapping |
| Theater | `ontology.dim_geography.theater` | Theater | Sales Theater | Geography | 0.94 | Inferred column-to-glossary mapping |
| Coverage Level | `ontology.dim_contract.coverage_level` | Coverage Level | Support Coverage Level | Contract Management | 0.94 | Inferred column-to-glossary mapping |

## 7. Validation Warnings

| Warning Type | Severity | Details |
| --- | --- | --- |
| Inferred semantic definitions | Medium | Several business definitions rely on glossary inference because native database comments are not present. |
| Empty source tables | High | Instance-level validation for code values, data quality, and measure distributions cannot be performed. |
| Natural key gaps | Medium | `dim_contract` and `dim_geography` do not expose explicit natural business identifiers in supplied metadata. |
| Non-additive metric caution | Medium | `discount_pct` and `unit_list_price_usd` should not be blindly summed in downstream analytics. |
| Coded indicator ambiguity | Medium | `is_renewal` and `auto_renew_flag` require business-approved code-set documentation. |

---
Generated as a validated OSI Semantic Model from the supplied Data Dictionary, Business Glossary, Business Domain Context, and Cisco Bookings process reference.