# Business Glossary Data Dictionary: Ontology PostgreSQL Schema

## 1. Input Validation

| Validation Item | Status | Details |
| --- | --- | --- |
| Data Dictionary Provided | PASS | Validated Data Dictionary for Ontology PostgreSQL Schema Discovery was supplied in the request context |
| Data Dictionary Readable | PASS | Technical metadata for tables, columns, keys, relationships, data types, and remarks was readable |
| Business Domain Context Provided | PASS | `Business Domain Context.txt` was provided and read successfully |
| Additional Reference Document Provided | PASS | `Cisco_Bookings_Data_Model_and_Process.docx` was provided and read successfully |
| GitHub Repository Provided | PASS | Repository `ELANSURIYAA/Ontology` supplied |
| GitHub Folder Provided | PASS | Folder `DI Glossary Creator Agent` supplied |
| GitHub Token Provided | PASS | Token supplied in request |
| Profiling Output Provided | PASS | DI Data Profiler Agent output for all discovered tables was supplied in the request context |
| Input Completeness | PASS | Required inputs were present to generate the enriched glossary data dictionary |

## 2. Business Domain Summary

| Attribute | Value |
| --- | --- |
| Domain Name | Cisco Sales Bookings and Revenue Analytics |
| Analytical Model | Kimball Star Schema |
| Central Fact | `fact_bookings` |
| Core Dimensions | Customer, Product, Partner, Geography, Sales Representative, Contract, Date |
| Booking Grain | One row per booking transaction / order line |
| Primary Business Measures | Booking Amount, ACV, TCV, Quantity Sold, Unit List Price, Discount Percentage |
| Main Business Outcomes Supported | Revenue forecasting, renewal planning, sales performance analysis, partner evaluation, product mix analysis, executive reporting |

## 3. Schema Analysis Summary

### 3.1 Tables Identified

| Schema | Table Name | Business Role | Primary Key |
| --- | --- | --- | --- |
| ontology | dim_contract | Contract dimension | contract_key |
| ontology | dim_customer | Customer dimension | customer_key |
| ontology | dim_date | Date dimension | date_key |
| ontology | dim_geography | Geography dimension | geography_key |
| ontology | dim_partner | Partner dimension | partner_key |
| ontology | dim_product | Product dimension | product_key |
| ontology | dim_sales_rep | Sales representative dimension | sales_rep_key |
| ontology | fact_bookings | Booking fact table | booking_id |

### 3.2 Foreign Key Relationships

| Parent Table | Parent Column | Child Table | Child Column | Relationship Type | Business Interpretation |
| --- | --- | --- | --- | --- | --- |
| ontology.dim_contract | contract_key | ontology.fact_bookings | contract_key | One-to-Many | One contract profile can describe many booking records |
| ontology.dim_customer | customer_key | ontology.fact_bookings | customer_key | One-to-Many | One customer can have many booking transactions |
| ontology.dim_date | date_key | ontology.fact_bookings | date_key | One-to-Many | One date can relate to many bookings |
| ontology.dim_geography | geography_key | ontology.fact_bookings | geography_key | One-to-Many | One geography classification can apply to many bookings |
| ontology.dim_partner | partner_key | ontology.fact_bookings | partner_key | One-to-Many | One partner can influence many bookings |
| ontology.dim_product | product_key | ontology.fact_bookings | product_key | One-to-Many | One product can appear in many bookings |
| ontology.dim_sales_rep | sales_rep_key | ontology.fact_bookings | sales_rep_key | One-to-Many | One sales representative can own many bookings |

### 3.3 Profiling Summary

| Table Name | Row Count | Profiling Status | Observation |
| --- | --- | --- | --- |
| dim_contract | 0 | WARNING | Structurally valid but empty |
| dim_customer | 0 | WARNING | Structurally valid but empty |
| dim_date | 0 | WARNING | Structurally valid but empty |
| dim_geography | 0 | WARNING | Structurally valid but empty |
| dim_partner | 0 | WARNING | Structurally valid but empty |
| dim_product | 0 | WARNING | Structurally valid but empty |
| dim_sales_rep | 0 | WARNING | Structurally valid but empty |
| fact_bookings | 0 | WARNING | Structurally valid fact table but empty |

## 4. Table-Level Business Glossary

| Table Name | Technical Name | Business Term | Business Definition | Business Description | Business Category | Synonyms | Common Acronyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | dim_contract | Contract Dimension | A reference dimension that stores descriptive attributes about commercial agreements attached to bookings, including contract type, term, renewal behavior, and support coverage. | Used to analyze bookings by contract structure and service agreement characteristics. | Contract Management | Contract Master, Agreement Dimension | N/A | Empty table at profiling time |
| dim_customer | dim_customer | Customer Dimension | A reference dimension that stores customer identity and classification attributes such as customer identifier, segment, industry, account tier, and headquarters geography. | Supports analysis of bookings by customer account and market segmentation. | Customer Management | Account Dimension, Customer Master | N/A | Empty table at profiling time |
| dim_date | dim_date | Date Dimension | A conformed calendar and fiscal date dimension used to support time-based slicing of bookings across calendar and fiscal reporting periods. | Enables period-over-period reporting and alignment to Cisco fiscal calendars. | Time Management | Calendar Dimension, Time Dimension | N/A | Empty table at profiling time |
| dim_geography | dim_geography | Geography Dimension | A reference dimension that stores regional geographic classifications such as region, theater, and country for booking analysis. | Supports geographic reporting and regional sales performance analysis. | Geography | Geo Dimension, Location Dimension | N/A | Empty table at profiling time |
| dim_partner | dim_partner | Partner Dimension | A reference dimension that stores partner identity and classification details, including partner type, tier, and route to market. | Enables channel performance and indirect sales analysis. | Partner Management | Channel Partner Dimension, Partner Master | N/A | Empty table at profiling time |
| dim_product | dim_product | Product Dimension | A reference dimension that stores product identifiers and descriptive classifications such as product family, technology domain, offer type, and Cisco business entity. | Supports analysis of booking mix across Cisco products and portfolios. | Product Management | Offer Dimension, Product Master | N/A | Empty table at profiling time |
| dim_sales_rep | dim_sales_rep | Sales Representative Dimension | A reference dimension that stores sales representative identity and organizational attributes such as role, team, and covered segment. | Enables performance analysis by seller, team, and coverage model. | Sales Organization | Seller Dimension, Rep Dimension | N/A | Empty table at profiling time |
| fact_bookings | fact_bookings | Bookings Fact | The central fact table that records individual booking transactions at order-line grain along with financial measures and foreign keys to descriptive dimensions. | Used as the core source for booking analytics, forecasting, renewals, partner contribution, and sales reporting. | Sales Transactions | Booking Transactions, Bookings Fact Table | ACV, TCV | Grain: one row per booking transaction / order line; empty table at profiling time |

## 5. Enriched Business Glossary Data Dictionary

| Table Name | Column Name | Technical Name | Business Term | Business Definition | Business Description | Data Type | Business Category | Synonyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | contract_key | contract_key | Contract Key | Surrogate key that uniquely identifies a contract record in the contract dimension. | Technical identifier used to join contract details to booking transactions. | integer | Key / Identifier | Contract Surrogate Key | Primary Key; required column |
| dim_contract | contract_type | contract_type | Contract Type | The classification of the commercial agreement associated with the booking, such as support, subscription, or service agreement type. | Used to distinguish different kinds of contractual arrangements. | character varying(40) | Contract Management | Agreement Type | Nullable; empty table prevented value profiling |
| dim_contract | term_months | term_months | Contract Term Months | The duration of the contract expressed in months. | Indicates the contractual length for support or subscription arrangements. | integer | Contract Management | Contract Duration, Term Length | Nullable; empty table prevented value profiling |
| dim_contract | auto_renew_flag | auto_renew_flag | Auto Renew Indicator | Indicator showing whether the contract is configured to renew automatically at the end of its term. | Supports renewal planning and recurring revenue analysis. | character(1) | Contract Management | Auto Renewal Flag, Renewal Flag | Nullable; likely indicator field based on naming and domain context |
| dim_contract | coverage_level | coverage_level | Coverage Level | The level of service or support coverage provided under the contract. | Used to analyze support entitlements and service agreement scope. | character varying(20) | Contract Management | Support Coverage Level | Nullable; empty table prevented value profiling |
| dim_customer | customer_key | customer_key | Customer Key | Surrogate key that uniquely identifies a customer record in the customer dimension. | Technical identifier used to join customer attributes to bookings. | integer | Key / Identifier | Customer Surrogate Key | Primary Key; required column |
| dim_customer | customer_id | customer_id | Customer ID | Business identifier assigned to a customer account. | Stable customer-facing or source-system identifier for the customer entity. | character varying(20) | Customer Management | Customer Number, Account ID | Required column; business identifier |
| dim_customer | customer_name | customer_name | Customer Name | The name of the customer organization associated with a booking. | Used for account-level reporting and business user recognition. | character varying(80) | Customer Management | Account Name, Customer Account Name | Nullable; empty table prevented value profiling |
| dim_customer | segment | segment | Customer Segment | The market segment to which the customer belongs. | Supports segmentation analysis such as enterprise, commercial, or SMB reporting. | character varying(30) | Customer Management | Market Segment | Nullable; empty table prevented value profiling |
| dim_customer | industry | industry | Industry | The industry classification of the customer organization. | Used to analyze booking patterns by industry vertical. | character varying(40) | Customer Management | Industry Vertical | Nullable; empty table prevented value profiling |
| dim_customer | account_tier | account_tier | Account Tier | The tier or strategic classification assigned to the customer account. | Helps prioritize and analyze customers based on account importance. | character varying(20) | Customer Management | Customer Tier, Account Classification | Nullable; empty table prevented value profiling |
| dim_customer | hq_country | hq_country | Headquarters Country | The country in which the customer's headquarters is located. | Supports customer domicile and regional account analysis. | character varying(40) | Geography / Customer | HQ Country | Nullable; empty table prevented value profiling |
| dim_customer | hq_region | hq_region | Headquarters Region | The broad regional classification for the customer's headquarters location. | Used for customer rollups by major geography. | character varying(20) | Geography / Customer | HQ Region | Nullable; empty table prevented value profiling |
| dim_date | date_key | date_key | Date Key | Surrogate key that uniquely identifies a date record in the date dimension. | Technical join key for linking bookings to calendar and fiscal time attributes. | integer | Key / Identifier | Date Surrogate Key | Primary Key; required column |
| dim_date | full_date | full_date | Full Date | The actual calendar date represented by the date dimension row. | Base reporting date used for time-series analysis. | date | Time Management | Calendar Date | Required column |
| dim_date | month_name | month_name | Month Name | The textual name of the calendar month for the date. | Supports month-based reporting labels. | character varying(12) | Time Management | Reporting Month Name | Nullable; empty table prevented value profiling |
| dim_date | calendar_year | calendar_year | Calendar Year | The calendar year associated with the date. | Used for standard Gregorian calendar reporting. | integer | Time Management | Year | Nullable; empty table prevented value profiling |
| dim_date | fiscal_year | fiscal_year | Fiscal Year | The Cisco fiscal year associated with the date. | Used for corporate reporting aligned to Cisco fiscal periods. | character varying(6) | Time Management | FY | Nullable; acronym: FY |
| dim_date | fiscal_quarter | fiscal_quarter | Fiscal Quarter | The Cisco fiscal quarter associated with the date. | Enables quarter-based financial and sales performance reporting. | character varying(10) | Time Management | FQ, Fiscal Qtr | Nullable; acronym: FQ |
| dim_date | fiscal_period_seq | fiscal_period_seq | Fiscal Period Sequence | Numeric sequence representing the relative order of fiscal periods. | Useful for sorting and period-over-period fiscal analysis. | integer | Time Management | Fiscal Sequence | Nullable; empty table prevented value profiling |
| dim_geography | geography_key | geography_key | Geography Key | Surrogate key that uniquely identifies a geography record in the geography dimension. | Technical identifier used to join geography attributes to bookings. | integer | Key / Identifier | Geography Surrogate Key | Primary Key; required column |
| dim_geography | region | region | Region | High-level geographic region associated with a booking or account. | Supports regional sales and revenue analysis. | character varying(20) | Geography | Sales Region | Nullable; empty table prevented value profiling |
| dim_geography | theater | theater | Theater | Intermediate geographic grouping used in Cisco sales reporting between region and country. | Enables theater-level performance tracking and management reporting. | character varying(30) | Geography | Sales Theater | Nullable; business term inferred from Cisco sales structure |
| dim_geography | country | country | Country | Country associated with the geography dimension record. | Supports country-level performance and localization reporting. | character varying(40) | Geography | Sales Country | Nullable; empty table prevented value profiling |
| dim_partner | partner_key | partner_key | Partner Key | Surrogate key that uniquely identifies a partner record in the partner dimension. | Technical identifier used to join partner attributes to bookings. | integer | Key / Identifier | Partner Surrogate Key | Primary Key; required column |
| dim_partner | partner_id | partner_id | Partner ID | Business identifier assigned to a channel or sales partner. | Stable identifier for distributors, resellers, or integrators. | character varying(20) | Partner Management | Channel Partner ID | Required column |
| dim_partner | partner_name | partner_name | Partner Name | Name of the partner organization involved in the booking. | Used for channel reporting and partner performance analysis. | character varying(60) | Partner Management | Channel Partner Name | Nullable; empty table prevented value profiling |
| dim_partner | partner_type | partner_type | Partner Type | Classification of the partner organization, such as distributor, VAR, or systems integrator. | Supports analysis by partner business model. | character varying(30) | Partner Management | Channel Type | Nullable; informed by business context |
| dim_partner | partner_tier | partner_tier | Partner Tier | Program or performance tier assigned to the partner. | Used to assess channel maturity and partner status. | character varying(30) | Partner Management | Channel Tier | Nullable; empty table prevented value profiling |
| dim_partner | route_to_market | route_to_market | Route to Market | The sales route through which the booking was transacted, such as direct, two-tier, or reseller-led. | Key field for direct versus indirect channel analysis. | character varying(20) | Partner Management | RTM, Go-to-Market Route | Nullable; acronym: RTM |
| dim_product | product_key | product_key | Product Key | Surrogate key that uniquely identifies a product record in the product dimension. | Technical identifier used to join product attributes to bookings. | integer | Key / Identifier | Product Surrogate Key | Primary Key; required column |
| dim_product | product_id | product_id | Product ID | Business identifier assigned to a Cisco product, SKU, or offer. | Stable product code used for mapping source transactions to product master data. | character varying(30) | Product Management | SKU, Product Code | Required column |
| dim_product | product_name | product_name | Product Name | The descriptive name of the Cisco product or offer. | Used for reporting and business-friendly product identification. | character varying(80) | Product Management | Offer Name | Nullable; empty table prevented value profiling |
| dim_product | product_family | product_family | Product Family | The family or portfolio grouping to which the product belongs. | Supports product mix and family-level performance analysis. | character varying(30) | Product Management | Portfolio Family | Nullable; examples in reference document include Catalyst, Meraki, Splunk |
| dim_product | technology_domain | technology_domain | Technology Domain | The technology area associated with the product, such as networking, security, collaboration, or observability. | Supports strategic analysis by technology portfolio. | character varying(40) | Product Management | Technology Area | Nullable; informed by business context |
| dim_product | offer_type | offer_type | Offer Type | Commercial offer classification for the product, such as hardware, software, SaaS, subscription, or support. | Used to distinguish monetization and delivery models. | character varying(30) | Product Management | Commercial Offer Type | Nullable; informed by business process document |
| dim_product | business_entity | business_entity | Business Entity | Internal Cisco business organization or portfolio owner associated with the product. | Supports reporting across internal business units. | character varying(30) | Product Management | Business Unit | Nullable; empty table prevented value profiling |
| dim_sales_rep | sales_rep_key | sales_rep_key | Sales Representative Key | Surrogate key that uniquely identifies a sales representative record in the sales rep dimension. | Technical identifier used to join seller attributes to bookings. | integer | Key / Identifier | Sales Rep Surrogate Key | Primary Key; required column |
| dim_sales_rep | rep_id | rep_id | Sales Representative ID | Business identifier assigned to a sales representative. | Stable identifier for salesperson-level reporting and source mapping. | character varying(20) | Sales Organization | Seller ID, Rep ID | Required column |
| dim_sales_rep | rep_name | rep_name | Sales Representative Name | Name of the sales representative responsible for the opportunity or booking. | Used for seller performance reporting and business recognition. | character varying(60) | Sales Organization | Seller Name, Rep Name | Nullable; empty table prevented value profiling |
| dim_sales_rep | sales_role | sales_role | Sales Role | The role of the sales representative within the sales organization. | Distinguishes account executive, overlay specialist, manager, or other sales roles. | character varying(40) | Sales Organization | Seller Role | Nullable; informed by business process roles |
| dim_sales_rep | sales_team | sales_team | Sales Team | The team or organizational unit to which the sales representative belongs. | Supports analysis of bookings by team structure. | character varying(40) | Sales Organization | Selling Team | Nullable; empty table prevented value profiling |
| dim_sales_rep | segment_covered | segment_covered | Covered Segment | The customer segment or market coverage responsibility assigned to the sales representative. | Supports analysis of seller performance by coverage model. | character varying(30) | Sales Organization | Coverage Segment | Nullable; empty table prevented value profiling |
| fact_bookings | booking_id | booking_id | Booking ID | Surrogate key that uniquely identifies an individual booking transaction row. | Technical primary key for the fact table at booking transaction grain. | integer | Key / Identifier | Booking Transaction Key | Primary Key; required column |
| fact_bookings | order_number | order_number | Order Number | The sales order number associated with the booking transaction. | Used to group booking lines under a common customer order. | character varying(20) | Sales Transactions | Sales Order Number | Nullable; empty table prevented value profiling |
| fact_bookings | order_line_number | order_line_number | Order Line Number | The line item number within the sales order. | Defines the line-level grain of the booking fact. | integer | Sales Transactions | Sales Order Line | Nullable; supports order-line grain |
| fact_bookings | date_key | date_key | Booking Date Key | Foreign key linking the booking transaction to the date dimension. | Connects each booking to calendar and fiscal reporting attributes. | integer | Foreign Key / Time | Date FK | Foreign Key to dim_date |
| fact_bookings | customer_key | customer_key | Customer Key | Foreign key linking the booking transaction to the customer dimension. | Connects each booking to customer account attributes. | integer | Foreign Key / Customer | Customer FK | Foreign Key to dim_customer |
| fact_bookings | product_key | product_key | Product Key | Foreign key linking the booking transaction to the product dimension. | Connects each booking to product attributes and portfolio classifications. | integer | Foreign Key / Product | Product FK | Foreign Key to dim_product |
| fact_bookings | partner_key | partner_key | Partner Key | Foreign key linking the booking transaction to the partner dimension. | Connects bookings to channel and route-to-market analysis. | integer | Foreign Key / Partner | Partner FK | Foreign Key to dim_partner |
| fact_bookings | geography_key | geography_key | Geography Key | Foreign key linking the booking transaction to the geography dimension. | Connects bookings to regional and country analysis. | integer | Foreign Key / Geography | Geography FK | Foreign Key to dim_geography |
| fact_bookings | sales_rep_key | sales_rep_key | Sales Representative Key | Foreign key linking the booking transaction to the sales representative dimension. | Connects bookings to seller and team performance analysis. | integer | Foreign Key / Sales Organization | Sales Rep FK | Foreign Key to dim_sales_rep |
| fact_bookings | contract_key | contract_key | Contract Key | Foreign key linking the booking transaction to the contract dimension. | Connects bookings to contract term, coverage, and renewal analysis. | integer | Foreign Key / Contract | Contract FK | Foreign Key to dim_contract |
| fact_bookings | booking_type | booking_type | Booking Type | Classification of the booking event, such as New, Renewal, or Upsell. | Key business measure attribute used to distinguish growth and retention activity. | character varying(15) | Sales Transactions | Booking Classification | Nullable; domain context explicitly references New, Renewal, Upsell |
| fact_bookings | is_renewal | is_renewal | Renewal Indicator | Indicator showing whether the booking is associated with a contract renewal. | Supports renewal mix and retention analysis. | integer | Sales Transactions | Renewal Flag | Nullable; likely 0/1 indicator based on naming |
| fact_bookings | quantity | quantity | Quantity Sold | The number of units, licenses, or subscription quantities included in the booking line. | Core operational measure for volume analysis. | integer | Sales Measures | Units Booked | Nullable; empty table prevented value profiling |
| fact_bookings | unit_list_price_usd | unit_list_price_usd | Unit List Price USD | Standard list price per unit in U.S. dollars before discounts. | Supports pricing analysis and discount calculations. | numeric(12,2) | Sales Measures | List Price USD | Nullable; currency measure |
| fact_bookings | discount_pct | discount_pct | Discount Percentage | Percentage discount applied relative to list price. | Used to evaluate pricing strategy and discounting behavior. | numeric(5,2) | Sales Measures | Discount Rate | Nullable; percentage measure |
| fact_bookings | booking_amount_usd | booking_amount_usd | Booking Amount USD | Net booked value of the transaction line in U.S. dollars. | Primary measure used for booking performance reporting. | numeric(14,2) | Sales Measures | Total Bookings USD, Net Booked Value | Nullable; key KPI in business context |
| fact_bookings | acv_usd | acv_usd | Annual Contract Value USD | Annualized contract value of the booking in U.S. dollars, primarily relevant for subscription and SaaS offerings. | Supports recurring revenue and annualized subscription analysis. | numeric(14,2) | Sales Measures | ACV | Nullable; acronym: ACV |
| fact_bookings | tcv_usd | tcv_usd | Total Contract Value USD | Total contract value of the booking over the full contract term in U.S. dollars. | Supports long-term contract valuation and subscription booking analysis. | numeric(14,2) | Sales Measures | TCV, Total Value | Nullable; acronym: TCV |

## 6. Business Rules and Interpretation Notes

| Area | Observation |
| --- | --- |
| Fact Grain | `fact_bookings` is defined at one row per booking transaction / order line |
| Surrogate Keys | All dimension tables use integer surrogate primary keys |
| Referential Model | The fact table references all seven dimensions through foreign keys |
| Booking Classification | `booking_type` is expected to support values such as New, Renewal, and Upsell based on business documentation |
| Renewal Tracking | `is_renewal`, `contract_key`, `term_months`, and `auto_renew_flag` together support renewal analytics |
| Financial Measures | `booking_amount_usd`, `acv_usd`, and `tcv_usd` are core business measures for demand and subscription analysis |
| Channel Analytics | `partner_key`, `partner_type`, `partner_tier`, and `route_to_market` support partner and channel reporting |
| Time Intelligence | `dim_date` contains both calendar and fiscal attributes for enterprise reporting |
| Data Profiling Limitation | All discovered tables were empty at profiling time, so business meanings were inferred from metadata and supplied domain documentation rather than observed values |

## 7. Data Quality and Documentation Remarks

| Table Name | Remarks |
| --- | --- |
| dim_contract | Structurally documented; business definitions inferred from schema metadata and contract lifecycle context |
| dim_customer | Structurally documented; customer segmentation attributes align with sales analytics use cases |
| dim_date | Structurally documented; suitable for both calendar and fiscal reporting once populated |
| dim_geography | Structurally documented; theater appears to be a Cisco-specific geographic reporting layer |
| dim_partner | Structurally documented; route-to-market and partner tier are important channel analytics fields |
| dim_product | Structurally documented; product family and technology domain support portfolio reporting |
| dim_sales_rep | Structurally documented; role, team, and covered segment support performance management |
| fact_bookings | Structurally documented; central business fact table with booking and contract value measures |

## 8. Final Output Summary

This document enriches the validated technical data dictionary with inferred and context-supported business glossary metadata for all discovered schema elements in the `ontology` schema. It combines technical schema metadata, keys, data types, relationships, and profiling observations with business-friendly terms, definitions, descriptions, categories, and synonyms for governance and discovery use.
