# Business Glossary Data Dictionary - Ontology PostgreSQL

## 1. Input Validation

| Validation Item | Status | Details |
| --- | --- | --- |
| Data Dictionary provided | PASS | Validated Data Dictionary for Ontology PostgreSQL was supplied in readable Markdown form. |
| Business context provided | PASS | `Business Domain Context.txt` was read successfully. |
| Additional business reference provided | PASS | `Cisco_Bookings_Data_Model_and_Process.docx` was read successfully. |
| Profiling results provided | PASS | Profiling reports for all 8 tables were supplied and readable. |
| GitHub credentials provided | PASS | Repository, branch, token, folder, and target file parameters were provided. |
| Required inputs completeness | PASS | All required inputs for glossary generation were available. |

## 2. Business Domain Summary

| Item | Value |
| --- | --- |
| Domain Name | Cisco Sales Bookings and Revenue Analytics |
| Analytical Model | Kimball-style star schema |
| Central Fact | `ontology.fact_bookings` |
| Grain | Order-line booking transaction |
| Core Dimensions | Customer, Product, Partner, Geography, Sales Representative, Contract, Date |
| Key Measures | Booking Amount, ACV, TCV, Quantity Sold, Unit List Price, Discount Percentage |
| Core Business Uses | Revenue forecasting, renewal planning, partner evaluation, sales performance, executive reporting |

## 3. Profiling-Based Observations

| Observation Area | Result |
| --- | --- |
| Table population | All 8 tables are currently empty. |
| Profiling impact | Value distributions, completeness, uniqueness behavior, and business domain validation cannot be empirically confirmed from data. |
| Metadata quality | Structural metadata is complete enough to generate a business glossary and enriched data dictionary. |
| Remarks policy | Business definitions below are inferred from schema metadata and supplied business documentation, not from populated source data. |

## 4. Table-Level Business Glossary

| Table Name | Technical Name | Business Term | Business Definition | Business Description | Business Category | Synonyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | ontology.dim_contract | Contract Dimension | Dimension table containing descriptive attributes of service, support, or subscription contracts associated with bookings. | Used to analyze booking transactions by contract type, duration, renewal behavior, and coverage level. | Contract Management | Contract Master; Agreement Dimension | Table currently empty based on profiling. |
| dim_customer | ontology.dim_customer | Customer Dimension | Dimension table containing descriptive customer master data used to analyze bookings by customer identity, segment, industry, and headquarters location. | Supports customer-centric reporting and segmentation analysis across Cisco bookings. | Customer Management | Account Dimension; Customer Master | Table currently empty based on profiling. |
| dim_date | ontology.dim_date | Date Dimension | Dimension table containing calendar and fiscal attributes for time-based analysis of bookings. | Enables analysis by day, month, year, fiscal year, and fiscal quarter. | Time | Calendar Dimension; Time Dimension | Table currently empty based on profiling. |
| dim_geography | ontology.dim_geography | Geography Dimension | Dimension table containing geographic attributes such as region, theater, and country for sales analysis. | Supports geographic slicing of bookings and regional performance reporting. | Geography | Location Dimension; Regional Dimension | Table currently empty based on profiling. |
| dim_partner | ontology.dim_partner | Partner Dimension | Dimension table containing channel partner master data including type, tier, and route-to-market attributes. | Used to analyze indirect sales performance and partner contribution to bookings. | Partner Management | Channel Partner Dimension; Partner Master | Table currently empty based on profiling. |
| dim_product | ontology.dim_product | Product Dimension | Dimension table containing Cisco product master attributes such as product family, technology domain, offer type, and business entity. | Supports product mix, portfolio, and technology performance analysis. | Product Management | Offer Dimension; Product Master | Table currently empty based on profiling. |
| dim_sales_rep | ontology.dim_sales_rep | Sales Representative Dimension | Dimension table containing sales representative master data and coverage attributes. | Used for sales performance analysis by representative, role, team, and covered segment. | Sales Organization | Sales Rep Dimension; Seller Dimension | Table currently empty based on profiling. |
| fact_bookings | ontology.fact_bookings | Booking Transaction Fact | Central fact table capturing booking transactions at order-line grain with financial and operational measures. | Stores the measurable business events used for bookings, ACV, TCV, renewal, partner, and sales analytics. | Sales Transactions | Bookings Fact; Booking Fact Table | Central fact table; currently empty based on profiling. |

## 5. Relationship Summary

| Parent Table | Child Table | Key | Relationship Type | Business Meaning |
| --- | --- | --- | --- | --- |
| dim_contract | fact_bookings | contract_key | One-to-Many | One contract descriptor can classify many booking transactions. |
| dim_customer | fact_bookings | customer_key | One-to-Many | One customer can have many booking transactions. |
| dim_date | fact_bookings | date_key | One-to-Many | One date dimension row can relate to many bookings. |
| dim_geography | fact_bookings | geography_key | One-to-Many | One geography definition can apply to many bookings. |
| dim_partner | fact_bookings | partner_key | One-to-Many | One partner can contribute to many bookings. |
| dim_product | fact_bookings | product_key | One-to-Many | One product can appear in many booking transactions. |
| dim_sales_rep | fact_bookings | sales_rep_key | One-to-Many | One sales representative can own or influence many bookings. |

## 6. Enriched Business Glossary Data Dictionary

| Table Name | Column Name | Technical Name | Business Term | Business Definition | Business Description | Data Type | Business Category | Synonyms | Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| dim_contract | contract_key | contract_key | Contract Key | Surrogate key that uniquely identifies a contract dimension record. | Technical identifier used to join booking transactions to contract attributes. | integer | Key / Identifier | Contract Dimension Key | Primary key; table empty in profiling. |
| dim_contract | contract_type | contract_type | Contract Type | Classification of the commercial or service agreement associated with a booking. | Indicates whether the contract is a support, subscription, service, or similar agreement type. | character varying(40) | Contract Management | Agreement Type | Inferred from schema and business context. |
| dim_contract | term_months | term_months | Contract Term Months | Number of months covered by the contract term. | Used to evaluate contract duration and support ACV/TCV interpretation for time-bound offers. | integer | Contract Management | Contract Duration Months; Term Length | Inferred from schema and business process documentation. |
| dim_contract | auto_renew_flag | auto_renew_flag | Auto Renew Indicator | Flag indicating whether the contract is configured to renew automatically. | Supports renewal planning and recurring revenue analysis. | character(1) | Contract Management | Auto Renewal Flag; Renewal Flag | Likely coded flag such as Y/N; not validated due to empty table. |
| dim_contract | coverage_level | coverage_level | Coverage Level | Service or support coverage level associated with the contract. | Describes the breadth or tier of entitlement, support, or protection under the agreement. | character varying(20) | Contract Management | Support Coverage Level | Inferred from contract and entitlement context. |
| dim_customer | customer_key | customer_key | Customer Key | Surrogate key that uniquely identifies a customer dimension record. | Technical identifier used to join bookings to customer attributes. | integer | Key / Identifier | Customer Dimension Key | Primary key; table empty in profiling. |
| dim_customer | customer_id | customer_id | Customer ID | Business identifier assigned to a customer account. | Stable customer-level identifier used for operational and analytical reference. | character varying(20) | Customer Management | Account ID; Customer Number | Not null in metadata; business identifier. |
| dim_customer | customer_name | customer_name | Customer Name | Official name of the customer account. | Used for business-facing customer reporting and account analysis. | character varying(80) | Customer Management | Account Name | Inferred business-friendly description. |
| dim_customer | segment | segment | Customer Segment | Market segment to which the customer belongs. | Supports segmentation analysis such as enterprise, commercial, or other go-to-market segments. | character varying(30) | Customer Management | Market Segment | Exact domain values not available due to empty table. |
| dim_customer | industry | industry | Customer Industry | Industry classification of the customer. | Used to analyze bookings across industry verticals. | character varying(40) | Customer Management | Industry Vertical | Inferred from schema and business objectives. |
| dim_customer | account_tier | account_tier | Account Tier | Tier classification assigned to the customer account. | Represents account importance or strategic classification for sales coverage and prioritization. | character varying(20) | Customer Management | Customer Tier; Account Classification | Inferred from sales coverage context. |
| dim_customer | hq_country | hq_country | Headquarters Country | Country where the customer's headquarters is located. | Supports geographic rollups based on customer home location. | character varying(40) | Geography | HQ Country | Inferred from column name. |
| dim_customer | hq_region | hq_region | Headquarters Region | Region where the customer's headquarters is located. | Enables regional segmentation of customers by headquarters location. | character varying(20) | Geography | HQ Region | Inferred from column name. |
| dim_date | date_key | date_key | Date Key | Surrogate key that uniquely identifies a date dimension record. | Technical date dimension identifier used to join bookings to calendar and fiscal attributes. | integer | Key / Identifier | Time Key; Date Dimension Key | Primary key; table empty in profiling. |
| dim_date | full_date | full_date | Full Date | Actual calendar date represented by the date dimension row. | Core date attribute for daily time analysis. | date | Time | Calendar Date | Not null in metadata. |
| dim_date | month_name | month_name | Month Name | Name of the calendar month for the date. | Used in month-level reporting and business-friendly time displays. | character varying(12) | Time | Calendar Month Name | Inferred from standard date dimension design. |
| dim_date | calendar_year | calendar_year | Calendar Year | Calendar year associated with the date. | Supports yearly analysis using standard calendar periods. | integer | Time | Year | Inferred from standard date dimension design. |
| dim_date | fiscal_year | fiscal_year | Fiscal Year | Cisco fiscal year associated with the date. | Supports enterprise reporting aligned to fiscal accounting and management periods. | character varying(6) | Time | FY | Common acronym: FY. |
| dim_date | fiscal_quarter | fiscal_quarter | Fiscal Quarter | Fiscal quarter associated with the date. | Used for quarterly performance and executive reporting. | character varying(10) | Time | FQ; Quarter | Common acronym: FQ. |
| dim_date | fiscal_period_seq | fiscal_period_seq | Fiscal Period Sequence | Sequential numeric ordering of fiscal periods. | Enables ordered period analysis and time-series calculations across fiscal periods. | integer | Time | Fiscal Sequence | Inferred from date-dimension conventions. |
| dim_geography | geography_key | geography_key | Geography Key | Surrogate key that uniquely identifies a geography dimension record. | Technical identifier used to join bookings to geographic attributes. | integer | Key / Identifier | Geography Dimension Key | Primary key; table empty in profiling. |
| dim_geography | region | region | Region | Broad geographic region associated with the booking or business activity. | High-level geographic classification used for regional performance reporting. | character varying(20) | Geography | Sales Region | Exact values unavailable due to empty table. |
| dim_geography | theater | theater | Theater | Intermediate sales geography grouping used within Cisco regional organization structures. | Supports management reporting below region and above country. | character varying(30) | Geography | Sales Theater | Business term inferred from Cisco sales geography usage. |
| dim_geography | country | country | Country | Country associated with the geography dimension row. | Supports country-level bookings and territory analysis. | character varying(40) | Geography | Nation | Inferred from column name. |
| dim_partner | partner_key | partner_key | Partner Key | Surrogate key that uniquely identifies a partner dimension record. | Technical identifier used to join bookings to partner attributes. | integer | Key / Identifier | Partner Dimension Key | Primary key; table empty in profiling. |
| dim_partner | partner_id | partner_id | Partner ID | Business identifier assigned to a partner organization. | Stable identifier used to reference channel partners across systems and reports. | character varying(20) | Partner Management | Channel Partner ID | Not null in metadata; business identifier. |
| dim_partner | partner_name | partner_name | Partner Name | Official name of the partner organization. | Used in business-facing partner reporting and channel performance analysis. | character varying(60) | Partner Management | Channel Partner Name | Inferred from schema and channel context. |
| dim_partner | partner_type | partner_type | Partner Type | Classification of the partner organization. | Distinguishes partner models such as distributor, reseller, VAR, or systems integrator. | character varying(30) | Partner Management | Channel Type | Domain examples derived from business context. |
| dim_partner | partner_tier | partner_tier | Partner Tier | Tier or level assigned to the partner within the partner program. | Used to analyze partner performance by program level or strategic status. | character varying(30) | Partner Management | Channel Tier | Inferred from Cisco partner program context. |
| dim_partner | route_to_market | route_to_market | Route to Market | Selling motion or channel path through which the booking was transacted. | Indicates whether a deal was sold direct, through two-tier distribution, reseller channels, or similar paths. | character varying(20) | Partner Management | RTM; Sales Channel Route | Common acronym: RTM. |
| dim_product | product_key | product_key | Product Key | Surrogate key that uniquely identifies a product dimension record. | Technical identifier used to join bookings to product attributes. | integer | Key / Identifier | Product Dimension Key | Primary key; table empty in profiling. |
| dim_product | product_id | product_id | Product ID | Business identifier assigned to a Cisco product or offer. | Stable product-level identifier used across operational and analytical processes. | character varying(30) | Product Management | SKU ID; Product Code | Not null in metadata; inferred as product business identifier. |
| dim_product | product_name | product_name | Product Name | Business name of the product or offer. | Used for product reporting and portfolio analysis. | character varying(80) | Product Management | Offer Name | Inferred from schema. |
| dim_product | product_family | product_family | Product Family | Higher-level product grouping used to categorize related offers. | Supports portfolio and mix analysis across families such as networking, security, collaboration, or other Cisco groupings. | character varying(30) | Product Management | Family | Product-family mix is a documented KPI. |
| dim_product | technology_domain | technology_domain | Technology Domain | Technology category or solution domain associated with the product. | Enables analysis across technology areas such as networking, security, observability, or collaboration. | character varying(40) | Product Management | Technology Category; Solution Domain | Inferred from business context. |
| dim_product | offer_type | offer_type | Offer Type | Commercial type of the product offer. | Distinguishes hardware, software, SaaS, subscription, service, or similar offer structures. | character varying(30) | Product Management | Commercial Offer Type | Inferred from bookings business process. |
| dim_product | business_entity | business_entity | Business Entity | Internal Cisco business entity or portfolio owning the product. | Supports reporting across internal product organizations or business portfolios. | character varying(30) | Product Management | Product Business Unit; Portfolio Entity | Inferred from business objectives. |
| dim_sales_rep | sales_rep_key | sales_rep_key | Sales Representative Key | Surrogate key that uniquely identifies a sales representative dimension record. | Technical identifier used to join bookings to seller attributes. | integer | Key / Identifier | Sales Rep Dimension Key | Primary key; table empty in profiling. |
| dim_sales_rep | rep_id | rep_id | Sales Representative ID | Business identifier assigned to a sales representative. | Stable identifier used to reference a seller in operational and analytical systems. | character varying(20) | Sales Organization | Rep ID; Seller ID | Not null in metadata. |
| dim_sales_rep | rep_name | rep_name | Sales Representative Name | Full name of the sales representative. | Used in sales performance and coverage reporting. | character varying(60) | Sales Organization | Seller Name; Account Executive Name | Inferred from business process roles. |
| dim_sales_rep | sales_role | sales_role | Sales Role | Role performed by the sales representative in the sales organization. | Examples may include account executive or other sales coverage roles. | character varying(40) | Sales Organization | Seller Role | Exact values unavailable due to empty table. |
| dim_sales_rep | sales_team | sales_team | Sales Team | Team or organizational unit to which the sales representative belongs. | Supports hierarchical reporting and team-level performance analysis. | character varying(40) | Sales Organization | Seller Team | Inferred from schema and reporting use case. |
| dim_sales_rep | segment_covered | segment_covered | Covered Segment | Customer segment or market segment assigned to the sales representative for coverage. | Used to analyze bookings by sales coverage model and responsibility area. | character varying(30) | Sales Organization | Coverage Segment | Inferred from business process description. |
| fact_bookings | booking_id | booking_id | Booking ID | Unique identifier for a booking transaction record. | Primary transaction identifier for the fact table at order-line grain. | integer | Sales Transactions | Booking Transaction ID | Primary key; fact table empty in profiling. |
| fact_bookings | order_number | order_number | Order Number | Business order number associated with the booking transaction. | Identifies the customer or partner order from which the booking was recognized. | character varying(20) | Sales Transactions | Sales Order Number; PO Reference | Source remarks indicate business order number. |
| fact_bookings | order_line_number | order_line_number | Order Line Number | Line number within the order representing the booking grain. | Distinguishes individual booked line items within an order. | integer | Sales Transactions | Order Line ID; Line Number | Grain-related attribute. |
| fact_bookings | date_key | date_key | Booking Date Key | Foreign key linking the booking transaction to the date dimension. | Associates each booking with calendar and fiscal time attributes. | integer | Time | Transaction Date Key | Foreign key to `dim_date`. |
| fact_bookings | customer_key | customer_key | Booking Customer Key | Foreign key linking the booking to the customer dimension. | Associates each booking with the customer account that purchased the product or service. | integer | Customer Management | Customer Reference Key | Foreign key to `dim_customer`. |
| fact_bookings | product_key | product_key | Booking Product Key | Foreign key linking the booking to the product dimension. | Associates each booking with the booked product or offer. | integer | Product Management | Product Reference Key | Foreign key to `dim_product`. |
| fact_bookings | partner_key | partner_key | Booking Partner Key | Foreign key linking the booking to the partner dimension. | Associates each booking with the partner involved in the transaction, where applicable. | integer | Partner Management | Partner Reference Key | Foreign key to `dim_partner`. |
| fact_bookings | geography_key | geography_key | Booking Geography Key | Foreign key linking the booking to the geography dimension. | Associates each booking with the applicable sales geography context. | integer | Geography | Geography Reference Key | Foreign key to `dim_geography`. |
| fact_bookings | sales_rep_key | sales_rep_key | Booking Sales Representative Key | Foreign key linking the booking to the sales representative dimension. | Associates each booking with the responsible or credited seller. | integer | Sales Organization | Seller Reference Key | Foreign key to `dim_sales_rep`. |
| fact_bookings | contract_key | contract_key | Booking Contract Key | Foreign key linking the booking to the contract dimension. | Associates each booking with related contract characteristics such as term and coverage. | integer | Contract Management | Contract Reference Key | Foreign key to `dim_contract`. |
| fact_bookings | booking_type | booking_type | Booking Type | Classification of the booking event. | Indicates whether the booking is new business, a renewal, an upsell, or another governed booking category. | character varying(15) | Sales Transactions | Booking Classification | Source metadata provides examples: New, Renewal, Upsell. |
| fact_bookings | is_renewal | is_renewal | Renewal Indicator | Indicator showing whether the booking represents a renewal transaction. | Supports retention, renewal mix, and recurring revenue analysis. | integer | Sales Transactions | Renewal Flag | Likely binary flag; exact coded values not validated due to empty table. |
| fact_bookings | quantity | quantity | Quantity Sold | Number of units, licenses, or items booked on the order line. | Used with pricing and booking metrics for sales volume analysis. | integer | Sales Measures | Units Sold | Source metadata indicates quantity sold. |
| fact_bookings | unit_list_price_usd | unit_list_price_usd | Unit List Price USD | Standard list price per unit in U.S. dollars before discounts. | Supports discount and pricing analysis at order-line level. | numeric(12,2) | Sales Measures | List Price; Unit Price USD | Currency explicitly USD. |
| fact_bookings | discount_pct | discount_pct | Discount Percentage | Percentage discount applied relative to list price. | Used to assess pricing strategy, deal structure, and commercial concessions. | numeric(5,2) | Sales Measures | Discount Rate | Source metadata indicates discount percentage. |
| fact_bookings | booking_amount_usd | booking_amount_usd | Booking Amount USD | Net booked transaction amount in U.S. dollars. | Headline booked value used in total bookings reporting and demand analysis. | numeric(14,2) | Sales Measures | Net Booking Value; Total Bookings Amount | Core KPI from business documentation. |
| fact_bookings | acv_usd | acv_usd | Annual Contract Value USD | Annualized value of the contract or subscription associated with the booking in U.S. dollars. | Used for recurring revenue analysis, especially for subscription and SaaS offers. | numeric(14,2) | Sales Measures | ACV | Common acronym: ACV. |
| fact_bookings | tcv_usd | tcv_usd | Total Contract Value USD | Total value of the contract associated with the booking in U.S. dollars over the full contract term. | Used to measure total committed value of subscription or service agreements. | numeric(14,2) | Sales Measures | TCV | Common acronym: TCV. |

## 7. Business Acronyms and Synonym Reference

| Business Term | Acronym / Synonym | Meaning |
| --- | --- | --- |
| Annual Contract Value | ACV | Annualized contract value used in recurring revenue analysis. |
| Total Contract Value | TCV | Full contract value across the entire contract term. |
| Fiscal Year | FY | Fiscal reporting year. |
| Fiscal Quarter | FQ | Fiscal reporting quarter. |
| Route to Market | RTM | Sales or channel path through which a deal is transacted. |
| Customer | Account | Business customer or buying organization. |
| Sales Representative | Seller / Account Executive | Sales resource responsible for customer opportunity or booking. |
| Partner | Channel Partner | Indirect sales organization participating in the transaction. |

## 8. Governance and Data Quality Remarks

| Area | Remark |
| --- | --- |
| Source descriptions | Native database comments were not available in source metadata. |
| Business glossary generation | Definitions were inferred from schema metadata, provided business context, and Cisco bookings process reference material. |
| Profiling limitation | All tables are empty, so data-driven validation of domains, code values, null patterns, and distributions is not possible. |
| Recommended next step | Re-profile after data load to validate indicator values, domain values, code sets, and business-rule conformance. |
| Semantic readiness | Schema is highly suitable for business cataloging, semantic modeling, ontology generation, and governed metric definition. |

## 9. Output Status

| Repository | Folder | File Name | Status |
| --- | --- | --- | --- |
| ELANSURIYAA/Ontology | DI Glossary Creator Agent | business_glossary_enriched_data_dictionary.md | Written via GitHub File Writer Tool |

---
Generated by DI Glossary Creator Agent using schema metadata, profiling results, business domain context, and Cisco bookings process reference material.