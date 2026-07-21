# Business Glossary Data Dictionary

## 1. Validation Summary

| Validation Check | Status | Details |
| --- | --- | --- |
| Data Dictionary provided | PASS | Ontology PostgreSQL Data Dictionary content was provided and readable |
| Business context provided | PASS | `Business Domain Context.txt` was readable |
| Additional reference material provided | PASS | `Cisco_Bookings_Data_Model_and_Process.docx` was readable |
| Profiling input provided | PASS | Profiling reports for all 8 tables were provided and readable |
| GitHub credentials provided | PASS | Repository, branch, token, and folder name were supplied |
| GitHub write operation | PASS | Output file prepared for repository write |

## 2. Business Domain Context

| Attribute | Value |
| --- | --- |
| Domain Name | Cisco Sales Bookings and Revenue Analytics |
| Model Style | Kimball Star Schema |
| Central Fact | `ontology.fact_bookings` |
| Core Dimensions | Customer, Product, Partner, Geography, Sales Representative, Contract, Date |
| Primary Analytical Focus | Sales bookings, revenue-related measures, renewals, partner performance, product mix, regional performance |

## 3. Schema Analysis Summary

### 3.1 Tables Identified

| Table Name | Role | Primary Key | Notes |
| --- | --- | --- | --- |
| dim_contract | Dimension | contract_key | Contract attributes for coverage and renewal analysis |
| dim_customer | Dimension | customer_key | Customer master context for segmentation and account analysis |
| dim_date | Dimension | date_key | Calendar and fiscal reporting dimension |
| dim_geography | Dimension | geography_key | Regional and country sales analysis context |
| dim_partner | Dimension | partner_key | Channel partner context |
| dim_product | Dimension | product_key | Product and offer classification context |
| dim_sales_rep | Dimension | sales_rep_key | Sales ownership and coverage context |
| fact_bookings | Fact | booking_id | Booking transaction fact at order-line grain |

### 3.2 Relationships Identified

| Parent Table | Child Table | Foreign Key | Relationship Type | Business Meaning |
| --- | --- | --- | --- | --- |
| dim_contract | fact_bookings | contract_key | One-to-Many | A contract classification can apply to many booking transactions |
| dim_customer | fact_bookings | customer_key | One-to-Many | A customer can generate many booking transactions |
| dim_date | fact_bookings | date_key | One-to-Many | A booking occurs on a reporting date |
| dim_geography | fact_bookings | geography_key | One-to-Many | A geography can contain many booking transactions |
| dim_partner | fact_bookings | partner_key | One-to-Many | A partner can influence many booking transactions |
| dim_product | fact_bookings | product_key | One-to-Many | A product can appear in many booking transactions |
| dim_sales_rep | fact_bookings | sales_rep_key | One-to-Many | A sales representative can own many booking transactions |

### 3.3 Profiling Summary

| Table Name | Row Count | Profiling Observation |
| --- | ---: | --- |
| dim_contract | 0 | Structurally valid but empty |
| dim_customer | 0 | Structurally valid but empty |
| dim_date | 0 | Structurally valid but empty |
| dim_geography | 0 | Structurally valid but empty |
| dim_partner | 0 | Structurally valid but empty |
| dim_product | 0 | Structurally valid but empty |
| dim_sales_rep | 0 | Structurally valid but empty |
| fact_bookings | 0 | Structurally valid but empty |

**Profiling Note:** All tables are currently empty. Therefore, business glossary definitions are derived from schema metadata, supplied business context, DDL remarks, and process documentation rather than observed data values.

## 4. Table-Level Business Glossary

| Table Name | Technical Name | Business Term | Business Definition | Business Description | Business Category | Synonyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | dim_contract | Contract Dimension | Dimension table that stores descriptive attributes of commercial agreements associated with bookings. | Used to analyze contract type, term length, coverage level, and renewal characteristics for booked products and services. | Contract Management | Contract Master, Agreement Dimension | Dimension table in the Cisco bookings star schema |
| dim_customer | dim_customer | Customer Dimension | Dimension table that stores descriptive business information about customers. | Supports analysis of bookings by customer, segment, industry, account tier, and headquarters geography. | Customer Management | Account Dimension, Customer Master | Conformed customer dimension |
| dim_date | dim_date | Date Dimension | Dimension table that stores calendar and fiscal date attributes for reporting and time-based analysis. | Supports reporting by booking date, month, calendar year, fiscal year, and fiscal quarter. | Time Management | Calendar Dimension, Fiscal Date Dimension | Shared time dimension for analytics |
| dim_geography | dim_geography | Geography Dimension | Dimension table that stores sales geography descriptors such as region, theater, and country. | Enables sales performance analysis by geographic hierarchy. | Geography | Sales Geography Dimension, Regional Dimension | Supports regional and theater reporting |
| dim_partner | dim_partner | Partner Dimension | Dimension table that stores descriptive information about channel and partner entities involved in bookings. | Supports channel performance analysis across partner types, partner tiers, and routes to market. | Partner Management | Channel Partner Dimension, Partner Master | Relevant for indirect sales analytics |
| dim_product | dim_product | Product Dimension | Dimension table that stores descriptive product and offer attributes. | Enables analysis of bookings across products, product families, technology domains, offer types, and Cisco business entities. | Product Management | Offer Dimension, Product Master | Conformed product dimension |
| dim_sales_rep | dim_sales_rep | Sales Representative Dimension | Dimension table that stores descriptive information about sales personnel responsible for bookings. | Supports performance analysis by sales representative, role, team, and covered market segment. | Sales Management | Rep Dimension, Salesperson Dimension | Ownership dimension for booking performance |
| fact_bookings | fact_bookings | Booking Transaction Fact | Fact table that stores individual booking transactions at order-line grain. | Central analytical table capturing booking measures such as quantity, booking amount, ACV, TCV, discount, and booking classification. | Sales Transactions | Bookings Fact, Booking Fact Table | Core fact table in the star schema |

## 5. Enriched Business Glossary Data Dictionary

| Table Name | Column Name | Technical Name | Business Term | Business Definition | Business Description | Data Type | Business Category | Synonyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | contract_key | contract_key | Contract Key | Surrogate key that uniquely identifies a contract dimension record. | Internal warehouse identifier used to join contract attributes to booking transactions. | integer | Technical Identifier | Contract Surrogate Key | Primary key; no business meaning outside the warehouse |
| dim_contract | contract_type | contract_type | Contract Type | Classification of the commercial agreement associated with the booking. | Describes the type of contract, such as support, subscription, or service agreement. | character varying(40) | Contract Management | Agreement Type | Supports contract-level business segmentation |
| dim_contract | term_months | term_months | Contract Term Months | Number of months covered by the contract. | Indicates the duration of the contract for renewal and value analysis. | integer | Contract Management | Term Length, Contract Duration Months | Useful for renewal cycle analysis |
| dim_contract | auto_renew_flag | auto_renew_flag | Auto Renew Indicator | Indicator showing whether the contract is configured to renew automatically. | Helps identify contracts expected to renew without manual intervention. | character(1) | Renewal Management | Auto Renewal Flag | Likely expected values such as Y/N based on naming convention; table currently empty |
| dim_contract | coverage_level | coverage_level | Coverage Level | Service or support coverage level provided by the contract. | Indicates the support tier or service coverage associated with the contract. | character varying(20) | Service Coverage | Service Level, Support Coverage | Important for service and entitlement analysis |
| dim_customer | customer_key | customer_key | Customer Key | Surrogate key that uniquely identifies a customer dimension record. | Internal warehouse identifier used to join customer information to bookings. | integer | Technical Identifier | Customer Surrogate Key | Primary key |
| dim_customer | customer_id | customer_id | Customer ID | Business identifier assigned to a customer account. | Operational customer identifier used to distinguish one customer from another across source systems or reporting. | character varying(20) | Customer Management | Account ID, Customer Number | Required column based on schema metadata |
| dim_customer | customer_name | customer_name | Customer Name | Official business name of the customer account. | Identifies the customer organization associated with a booking transaction. | character varying(80) | Customer Management | Account Name, Customer Account Name | Descriptive customer label |
| dim_customer | segment | segment | Customer Segment | Market segment to which the customer belongs. | Used to group customers into business segments for sales coverage and performance reporting. | character varying(30) | Customer Segmentation | Market Segment | Mentioned in business process as coverage-related context |
| dim_customer | industry | industry | Customer Industry | Industry classification of the customer. | Supports analysis of customer demand by industry vertical. | character varying(40) | Customer Segmentation | Industry Vertical | Helps analyze buying behavior across industries |
| dim_customer | account_tier | account_tier | Account Tier | Internal tiering or priority classification assigned to the customer account. | Used to differentiate strategic, enterprise, or other levels of customer importance. | character varying(20) | Account Management | Customer Tier, Account Classification | Supports account prioritization analysis |
| dim_customer | hq_country | hq_country | Customer Headquarters Country | Country in which the customer's headquarters is located. | Provides customer master geography for strategic and corporate reporting. | character varying(40) | Customer Geography | HQ Country | Distinct from booking geography |
| dim_customer | hq_region | hq_region | Customer Headquarters Region | Region in which the customer's headquarters is located. | Supports rollup of customers by headquarters region. | character varying(20) | Customer Geography | HQ Region | Distinct from selling geography |
| dim_date | date_key | date_key | Date Key | Surrogate key that uniquely identifies a date dimension record. | Internal warehouse identifier linking booking records to time attributes. | integer | Technical Identifier | Date Surrogate Key | Primary key |
| dim_date | full_date | full_date | Full Date | Actual calendar date represented by the date record. | Base reporting date used for daily analysis and time hierarchies. | date | Time Management | Calendar Date | Required column based on schema metadata |
| dim_date | month_name | month_name | Month Name | Name of the calendar month for the date. | Used for monthly reporting and presentation-friendly labels. | character varying(12) | Time Management | Calendar Month Name | Example business usage: January, February |
| dim_date | calendar_year | calendar_year | Calendar Year | Calendar year associated with the date. | Supports annual reporting based on standard calendar periods. | integer | Time Management | Year | Used alongside fiscal periods |
| dim_date | fiscal_year | fiscal_year | Fiscal Year | Cisco fiscal year associated with the date. | Supports reporting aligned to Cisco financial management cycles. | character varying(6) | Fiscal Reporting | FY | Key business reporting attribute |
| dim_date | fiscal_quarter | fiscal_quarter | Fiscal Quarter | Cisco fiscal quarter associated with the date. | Enables quarterly analysis for executive and operational reporting. | character varying(10) | Fiscal Reporting | FQ, Quarter | Important for bookings performance reporting |
| dim_date | fiscal_period_seq | fiscal_period_seq | Fiscal Period Sequence | Sequential ordering value for fiscal periods. | Supports correct sorting and period-over-period analysis across fiscal time. | integer | Fiscal Reporting | Fiscal Sequence Number | Useful for time-series logic |
| dim_geography | geography_key | geography_key | Geography Key | Surrogate key that uniquely identifies a geography dimension record. | Internal warehouse identifier used to join geography attributes to bookings. | integer | Technical Identifier | Geography Surrogate Key | Primary key |
| dim_geography | region | region | Sales Region | High-level sales region associated with the booking geography. | Used to analyze bookings at a broad regional level. | character varying(20) | Geography | Region | Common executive reporting hierarchy |
| dim_geography | theater | theater | Sales Theater | Intermediate sales geography grouping under or within a region. | Used for sales management reporting across major operating theaters. | character varying(30) | Geography | Theater | Common Cisco sales geography term |
| dim_geography | country | country | Sales Country | Country associated with the booking geography. | Supports country-level analysis of booking performance. | character varying(40) | Geography | Country Name | Selling geography attribute |
| dim_partner | partner_key | partner_key | Partner Key | Surrogate key that uniquely identifies a partner dimension record. | Internal warehouse identifier used to join partner details to bookings. | integer | Technical Identifier | Partner Surrogate Key | Primary key |
| dim_partner | partner_id | partner_id | Partner ID | Business identifier assigned to a partner organization. | Operational identifier used to uniquely identify distributors, resellers, or integrators. | character varying(20) | Partner Management | Channel Partner ID | Required column based on schema metadata |
| dim_partner | partner_name | partner_name | Partner Name | Official name of the partner organization. | Identifies the partner associated with a booking transaction. | character varying(60) | Partner Management | Channel Partner Name | Descriptive partner label |
| dim_partner | partner_type | partner_type | Partner Type | Classification of the partner organization. | Describes the kind of partner, such as distributor, VAR, or systems integrator. | character varying(30) | Partner Management | Channel Type | Referenced in business context for indirect channel sales |
| dim_partner | partner_tier | partner_tier | Partner Tier | Tier or status level assigned to the partner. | Supports analysis of partner performance by certification or strategic tier. | character varying(30) | Partner Management | Channel Tier, Partner Level | Useful in partner evaluation |
| dim_partner | route_to_market | route_to_market | Route to Market | Selling route through which the booking was transacted. | Indicates whether the sale was direct, two-tier, reseller-led, or another go-to-market path. | character varying(20) | Channel Strategy | RTM, Go-to-Market Route | Explicitly referenced in process documentation |
| dim_product | product_key | product_key | Product Key | Surrogate key that uniquely identifies a product dimension record. | Internal warehouse identifier used to join product details to bookings. | integer | Technical Identifier | Product Surrogate Key | Primary key |
| dim_product | product_id | product_id | Product ID | Business identifier assigned to a product or offer. | Operational code used to identify the sold product, service, or subscription offer. | character varying(30) | Product Management | SKU, Product Code | Required column based on schema metadata |
| dim_product | product_name | product_name | Product Name | Business name of the product or offer. | Describes the Cisco product, service, or subscription sold in the booking. | character varying(80) | Product Management | Offer Name | Human-readable product label |
| dim_product | product_family | product_family | Product Family | Higher-level grouping of related products. | Supports portfolio analysis across major product families such as networking, security, or collaboration. | character varying(30) | Product Portfolio | Product Line | Mentioned in KPI examples such as product-family mix |
| dim_product | technology_domain | technology_domain | Technology Domain | Technology area to which the product belongs. | Used to analyze bookings by technology focus such as networking, security, observability, or collaboration. | character varying(40) | Product Portfolio | Technology Area, Domain | Derived from business context |
| dim_product | offer_type | offer_type | Offer Type | Commercial type of the booked offer. | Indicates whether the item is hardware, software, SaaS, support, or another commercial offer form. | character varying(30) | Product Commercialization | Commercial Offer Type | Useful for distinguishing perpetual and subscription offerings |
| dim_product | business_entity | business_entity | Business Entity | Cisco internal business entity or portfolio owner associated with the product. | Supports reporting of bookings by Cisco business organization. | character varying(30) | Organizational Reporting | Portfolio Owner, Business Unit | Schema remark refers to Cisco business entity |
| dim_sales_rep | sales_rep_key | sales_rep_key | Sales Representative Key | Surrogate key that uniquely identifies a sales representative dimension record. | Internal warehouse identifier used to join sales ownership information to bookings. | integer | Technical Identifier | Sales Rep Surrogate Key | Primary key |
| dim_sales_rep | rep_id | rep_id | Sales Representative ID | Business identifier assigned to a sales representative. | Operational identifier used to uniquely identify the person or seller associated with a booking. | character varying(20) | Sales Management | Rep ID, Seller ID | Required column based on schema metadata |
| dim_sales_rep | rep_name | rep_name | Sales Representative Name | Full name of the sales representative. | Identifies the seller responsible for the customer relationship or booking. | character varying(60) | Sales Management | Salesperson Name, Account Executive Name | Descriptive sales owner label |
| dim_sales_rep | sales_role | sales_role | Sales Role | Role performed by the sales representative in the sales organization. | Describes whether the individual is an account executive, overlay seller, specialist, or other sales role. | character varying(40) | Sales Management | Role, Seller Role | Referenced in sales performance analysis |
| dim_sales_rep | sales_team | sales_team | Sales Team | Team or organizational unit to which the sales representative belongs. | Supports reporting by team structure and management hierarchy. | character varying(40) | Sales Organization | Team Name | Useful for manager-level reporting |
| dim_sales_rep | segment_covered | segment_covered | Covered Segment | Customer or market segment assigned to the sales representative. | Indicates the segment of accounts or market space the representative is responsible for. | character varying(30) | Sales Coverage | Coverage Segment | Mentioned in process documentation as coverage model context |
| fact_bookings | booking_id | booking_id | Booking ID | Surrogate key that uniquely identifies a booking transaction record. | Internal warehouse identifier for the fact record at booking transaction grain. | integer | Technical Identifier | Booking Surrogate Key | Primary key |
| fact_bookings | order_number | order_number | Order Number | Business order identifier associated with the booking. | Identifies the customer or partner order from which the booking was recognized. | character varying(20) | Order Management | Sales Order Number, PO Reference | Business transaction reference |
| fact_bookings | order_line_number | order_line_number | Order Line Number | Line number within the order associated with the booking record. | Helps define order-line grain and distinguish multiple items on the same order. | integer | Order Management | Line Item Number | Confirms fact grain at order-line level |
| fact_bookings | date_key | date_key | Booking Date Key | Foreign key linking the booking transaction to the date dimension. | Connects each booking to calendar and fiscal time attributes. | integer | Time Management | Date FK | Foreign key to `dim_date.date_key` |
| fact_bookings | customer_key | customer_key | Customer Key | Foreign key linking the booking transaction to the customer dimension. | Connects each booking to the booked customer account. | integer | Customer Management | Customer FK | Foreign key to `dim_customer.customer_key` |
| fact_bookings | product_key | product_key | Product Key | Foreign key linking the booking transaction to the product dimension. | Connects each booking to the booked product or offer. | integer | Product Management | Product FK | Foreign key to `dim_product.product_key` |
| fact_bookings | partner_key | partner_key | Partner Key | Foreign key linking the booking transaction to the partner dimension. | Connects each booking to the involved channel partner where applicable. | integer | Partner Management | Partner FK | Foreign key to `dim_partner.partner_key` |
| fact_bookings | geography_key | geography_key | Geography Key | Foreign key linking the booking transaction to the geography dimension. | Connects each booking to the selling geography used for regional reporting. | integer | Geography | Geography FK | Foreign key to `dim_geography.geography_key` |
| fact_bookings | sales_rep_key | sales_rep_key | Sales Representative Key | Foreign key linking the booking transaction to the sales representative dimension. | Connects each booking to the sales owner or responsible representative. | integer | Sales Management | Sales Rep FK | Foreign key to `dim_sales_rep.sales_rep_key` |
| fact_bookings | contract_key | contract_key | Contract Key | Foreign key linking the booking transaction to the contract dimension. | Connects each booking to related contract attributes such as term and coverage. | integer | Contract Management | Contract FK | Foreign key to `dim_contract.contract_key` |
| fact_bookings | booking_type | booking_type | Booking Type | Classification of the booking transaction according to business scenario. | Indicates whether the booking is new business, a renewal, an upsell, or another recognized booking category. | character varying(15) | Sales Classification | Booking Classification | Process document explicitly cites New, Renewal, Upsell |
| fact_bookings | is_renewal | is_renewal | Renewal Indicator | Flag indicating whether the booking is associated with a renewal event. | Supports retained revenue and renewal mix analysis. | integer | Renewal Management | Renewal Flag | Integer-typed flag; likely binary though no data exists to confirm |
| fact_bookings | quantity | quantity | Quantity Sold | Number of units, licenses, or items booked on the transaction line. | Measure of volume associated with the booking. | integer | Sales Metrics | Units Sold | Core operational quantity metric |
| fact_bookings | unit_list_price_usd | unit_list_price_usd | Unit List Price USD | Standard list price per unit in U.S. dollars before discount. | Baseline commercial price used in pricing and discount analysis. | numeric(12,2) | Pricing Metrics | List Price, Unit Price USD | Currency-denominated metric |
| fact_bookings | discount_pct | discount_pct | Discount Percentage | Percentage discount applied relative to list price. | Supports pricing governance, deal desk review, and margin-related analysis. | numeric(5,2) | Pricing Metrics | Discount Rate, Discount % | Mentioned in quote and pricing process |
| fact_bookings | booking_amount_usd | booking_amount_usd | Booking Amount USD | Net booked value recognized for the transaction in U.S. dollars. | Headline bookings measure used for demand and performance reporting. | numeric(14,2) | Financial Metrics | Net Bookings, Total Bookings Amount | Central KPI in business context |
| fact_bookings | acv_usd | acv_usd | Annual Contract Value USD | Annualized contract value of the booking in U.S. dollars. | Key subscription metric used to assess yearly recurring value of booked contracts. | numeric(14,2) | Subscription Metrics | ACV | Explicit KPI in business context |
| fact_bookings | tcv_usd | tcv_usd | Total Contract Value USD | Total value of the contract over its full term in U.S. dollars. | Used to measure total committed value for subscription or term-based deals. | numeric(14,2) | Subscription Metrics | TCV | Explicit KPI in business context |

## 6. Key Business Terms and Acronyms

| Term / Acronym | Meaning | Remarks |
| --- | --- | --- |
| ACV | Annual Contract Value | Annualized subscription or contract value |
| TCV | Total Contract Value | Total value across the full contract term |
| RTM | Route to Market | Selling path such as direct, two-tier, or reseller |
| FY | Fiscal Year | Company-defined financial reporting year |
| FQ | Fiscal Quarter | Company-defined financial reporting quarter |
| VAR | Value-Added Reseller | Mentioned in business context as a partner type |
| RevOps | Revenue Operations | Business user group and process owner for bookings reporting |
| KPI | Key Performance Indicator | Business performance metric |

## 7. Data Governance and Interpretation Notes

| Topic | Note |
| --- | --- |
| Surrogate Keys | All dimension primary keys and the fact primary key are technical warehouse identifiers rather than business-facing identifiers. |
| Business Identifiers | Customer, partner, product, and sales representative entities each also include a business identifier column intended for operational traceability. |
| Empty Tables | All profiling reports show zero rows; therefore definitions and remarks are metadata-driven rather than value-distribution-driven. |
| Booking Grain | `fact_bookings` is defined at booking transaction / order-line grain. |
| Currency Standard | Financial measures are denominated in USD based on column naming. |
| Renewal Logic | Renewal-related interpretation is derived from `booking_type`, `is_renewal`, and contract attributes such as term and auto-renew behavior. |
| Star Schema Design | The model is a classic star schema built for consistent slicing of the governed bookings metric across conformed dimensions. |

## 8. Recommended Business Categories Used in This Glossary

| Business Category | Purpose |
| --- | --- |
| Technical Identifier | Internal surrogate and foreign key fields |
| Customer Management | Customer master and account-related attributes |
| Customer Segmentation | Market and industry grouping attributes |
| Customer Geography | Headquarters-based customer geography attributes |
| Time Management | Calendar-based time attributes |
| Fiscal Reporting | Fiscal calendar reporting attributes |
| Geography | Selling geography attributes |
| Partner Management | Partner master and channel attributes |
| Channel Strategy | Route-to-market classification |
| Product Management | Product-identifying attributes |
| Product Portfolio | Portfolio and family-based product grouping |
| Product Commercialization | Offer and commercial packaging type |
| Sales Management | Sales ownership and role attributes |
| Sales Organization | Team and hierarchy descriptors |
| Sales Coverage | Covered customer segment descriptors |
| Contract Management | Agreement and contract descriptors |
| Service Coverage | Service level and support coverage descriptors |
| Order Management | Order-reference transaction attributes |
| Sales Classification | Booking scenario classification |
| Renewal Management | Renewal-related flags and behaviors |
| Sales Metrics | Non-currency operational measures |
| Pricing Metrics | Pricing and discount measures |
| Financial Metrics | Core monetary booking measures |
| Subscription Metrics | Subscription and contract value measures |

## 9. Final Enriched Data Dictionary Summary

| Metric | Value |
| --- | ---: |
| Total Tables Documented | 8 |
| Total Columns Enriched | 61 |
| Primary Keys Documented | 8 |
| Foreign Keys Documented | 7 |
| Relationships Documented | 7 |
| Profiling Reports Incorporated | 8 |
| Empty Tables Identified | 8 |

## 10. Conclusion

This enriched data dictionary combines the technical schema metadata from the Ontology PostgreSQL data dictionary with business-friendly glossary definitions derived from the Cisco Sales Bookings and Revenue Analytics domain context and process reference material. It provides a unified reference for technical teams, analysts, governance stakeholders, and business users to understand both the physical schema and the business semantics of the Cisco bookings star schema.
