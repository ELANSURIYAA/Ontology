# Ontology PostgreSQL Data Dictionary

## 1. Validation Summary

| Validation Check | Status | Details |
| --- | --- | --- |
| Database type supported | PASS | PostgreSQL detected |
| Connectivity verified | PASS | Connected successfully to database `ontology` |
| Required connection parameters present | PASS | Connection established through configured query runner |
| Output format valid | PASS | Markdown tabular format generated |
| Metadata query generation | PASS | PostgreSQL system catalog and information schema queries executed |
| DDL extraction | PASS WITH NOTE | Table and constraint DDL extracted successfully; no views, routines, triggers, or sequences found |

## 2. Source Context

### Business Domain
Cisco Sales Bookings and Revenue Analytics

### Business Summary
This database models Cisco sales booking operations using a Kimball-style star schema. The central fact table records booking transactions and is surrounded by conformed dimensions for customer, product, partner, geography, sales representative, contract, and date.

## 3. Database Overview

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Database Version | PostgreSQL 16.14 on x86_64-pc-linux-gnu, compiled by gcc (GCC) 13.2.0, 64-bit |
| Authenticated User | ontologyuser1 |
| Current Schema | ontology |
| Platform | PostgreSQL |

## 4. Schema List

| Schema | Owner |
| --- | --- |
| ontology | ontologyuser1 |
| public | azure_pg_admin |

## 5. Object Inventory

| Schema | Object Name | Object Type | Owner |
| --- | --- | --- | --- |
| ontology | dim_contract | BASE TABLE | ontologyuser1 |
| ontology | dim_customer | BASE TABLE | ontologyuser1 |
| ontology | dim_date | BASE TABLE | ontologyuser1 |
| ontology | dim_geography | BASE TABLE | ontologyuser1 |
| ontology | dim_partner | BASE TABLE | ontologyuser1 |
| ontology | dim_product | BASE TABLE | ontologyuser1 |
| ontology | dim_sales_rep | BASE TABLE | ontologyuser1 |
| ontology | fact_bookings | BASE TABLE | ontologyuser1 |

## 6. Structural Metadata - Tables and Columns

| Database Name | Schema | Table Name | Object Type | Column Name | Data Type | Length | Precision | Scale | Nullable | Default Value | Identity/Auto Increment | Primary Key | Foreign Key | Referenced Table | Referenced Column | Index | Constraint | Description/Remarks | DDL Statement |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | BASE TABLE | contract_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_contract_pkey | dim_contract_pkey | Contract dimension surrogate key | CREATE TABLE ontology.dim_contract (contract_key integer NOT NULL, contract_type character varying(40), term_months integer, auto_renew_flag character(1), coverage_level character varying(20)); |
| ontology | ontology | dim_contract | BASE TABLE | contract_type | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Contract type | CREATE TABLE ontology.dim_contract (contract_key integer NOT NULL, contract_type character varying(40), term_months integer, auto_renew_flag character(1), coverage_level character varying(20)); |
| ontology | ontology | dim_contract | BASE TABLE | term_months | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Contract term in months | CREATE TABLE ontology.dim_contract (contract_key integer NOT NULL, contract_type character varying(40), term_months integer, auto_renew_flag character(1), coverage_level character varying(20)); |
| ontology | ontology | dim_contract | BASE TABLE | auto_renew_flag | character | 1 |  |  | YES |  | NO | NO | NO |  |  |  |  | Auto-renew indicator | CREATE TABLE ontology.dim_contract (contract_key integer NOT NULL, contract_type character varying(40), term_months integer, auto_renew_flag character(1), coverage_level character varying(20)); |
| ontology | ontology | dim_contract | BASE TABLE | coverage_level | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Coverage/service level | CREATE TABLE ontology.dim_contract (contract_key integer NOT NULL, contract_type character varying(40), term_months integer, auto_renew_flag character(1), coverage_level character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | customer_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_customer_pkey | dim_customer_pkey | Customer dimension surrogate key | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | customer_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Customer business identifier | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | customer_name | character varying | 80 |  |  | YES |  | NO | NO | NO |  |  |  |  | Customer name | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | segment | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Market/customer segment | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | industry | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Customer industry | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | account_tier | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Account tier | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | hq_country | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Customer HQ country | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_customer | BASE TABLE | hq_region | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Customer HQ region | CREATE TABLE ontology.dim_customer (customer_key integer NOT NULL, customer_id character varying(20) NOT NULL, customer_name character varying(80), segment character varying(30), industry character varying(40), account_tier character varying(20), hq_country character varying(40), hq_region character varying(20)); |
| ontology | ontology | dim_date | BASE TABLE | date_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_date_pkey | dim_date_pkey | Date dimension surrogate key | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | full_date | date |  |  |  | NO |  | NO | NO | NO |  |  |  |  | Calendar date | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | month_name | character varying | 12 |  |  | YES |  | NO | NO | NO |  |  |  |  | Calendar month name | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | calendar_year | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Calendar year | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_year | character varying | 6 |  |  | YES |  | NO | NO | NO |  |  |  |  | Fiscal year | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_quarter | character varying | 10 |  |  | YES |  | NO | NO | NO |  |  |  |  | Fiscal quarter | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_period_seq | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Fiscal period sequence | CREATE TABLE ontology.dim_date (date_key integer NOT NULL, full_date date NOT NULL, month_name character varying(12), calendar_year integer, fiscal_year character varying(6), fiscal_quarter character varying(10), fiscal_period_seq integer); |
| ontology | ontology | dim_geography | BASE TABLE | geography_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_geography_pkey | dim_geography_pkey | Geography dimension surrogate key | CREATE TABLE ontology.dim_geography (geography_key integer NOT NULL, region character varying(20), theater character varying(30), country character varying(40)); |
| ontology | ontology | dim_geography | BASE TABLE | region | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales region | CREATE TABLE ontology.dim_geography (geography_key integer NOT NULL, region character varying(20), theater character varying(30), country character varying(40)); |
| ontology | ontology | dim_geography | BASE TABLE | theater | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales theater | CREATE TABLE ontology.dim_geography (geography_key integer NOT NULL, region character varying(20), theater character varying(30), country character varying(40)); |
| ontology | ontology | dim_geography | BASE TABLE | country | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Geography country | CREATE TABLE ontology.dim_geography (geography_key integer NOT NULL, region character varying(20), theater character varying(30), country character varying(40)); |
| ontology | ontology | dim_partner | BASE TABLE | partner_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_partner_pkey | dim_partner_pkey | Partner dimension surrogate key | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_partner | BASE TABLE | partner_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Partner business identifier | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_partner | BASE TABLE | partner_name | character varying | 60 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner name | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_partner | BASE TABLE | partner_type | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner type | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_partner | BASE TABLE | partner_tier | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner tier | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_partner | BASE TABLE | route_to_market | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Route-to-market model | CREATE TABLE ontology.dim_partner (partner_key integer NOT NULL, partner_id character varying(20) NOT NULL, partner_name character varying(60), partner_type character varying(30), partner_tier character varying(30), route_to_market character varying(20)); |
| ontology | ontology | dim_product | BASE TABLE | product_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_product_pkey | dim_product_pkey | Product dimension surrogate key | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | product_id | character varying | 30 |  |  | NO |  | NO | NO | NO |  |  |  |  | Product business identifier | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | product_name | character varying | 80 |  |  | YES |  | NO | NO | NO |  |  |  |  | Product name | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | product_family | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Product family | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | technology_domain | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Technology domain | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | offer_type | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Offer type | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_product | BASE TABLE | business_entity | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Cisco business entity | CREATE TABLE ontology.dim_product (product_key integer NOT NULL, product_id character varying(30) NOT NULL, product_name character varying(80), product_family character varying(30), technology_domain character varying(40), offer_type character varying(30), business_entity character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_rep_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_sales_rep_pkey | dim_sales_rep_pkey | Sales rep dimension surrogate key | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | rep_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Sales rep business identifier | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | rep_name | character varying | 60 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales representative name | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_role | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales role | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_team | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales team | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | dim_sales_rep | BASE TABLE | segment_covered | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Covered segment | CREATE TABLE ontology.dim_sales_rep (sales_rep_key integer NOT NULL, rep_id character varying(20) NOT NULL, rep_name character varying(60), sales_role character varying(40), sales_team character varying(40), segment_covered character varying(30)); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_id | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | fact_bookings_pkey | fact_bookings_pkey | Booking transaction surrogate key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | order_number | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Order number | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | order_line_number | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Order line number | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | date_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_date | date_key |  | fk_booking_date | Booking date foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | customer_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_customer | customer_key |  | fk_booking_customer | Customer foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | product_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_product | product_key |  | fk_booking_product | Product foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | partner_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_partner | partner_key |  | fk_booking_partner | Partner foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | geography_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_geography | geography_key |  | fk_booking_geography | Geography foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | sales_rep_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_sales_rep | sales_rep_key |  | fk_booking_sales_rep | Sales representative foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | contract_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_contract | contract_key |  | fk_booking_contract | Contract foreign key | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_type | character varying | 15 |  |  | YES |  | NO | NO | NO |  |  |  |  | Booking classification such as New/Renewal/Upsell | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | is_renewal | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Renewal indicator flag | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | quantity | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Quantity sold | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | unit_list_price_usd | numeric |  | 12 | 2 | YES |  | NO | NO | NO |  |  |  |  | Unit list price in USD | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | discount_pct | numeric |  | 5 | 2 | YES |  | NO | NO | NO |  |  |  |  | Discount percentage | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_amount_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Net booking amount in USD | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | acv_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Annual contract value in USD | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |
| ontology | ontology | fact_bookings | BASE TABLE | tcv_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Total contract value in USD | CREATE TABLE ontology.fact_bookings (booking_id integer NOT NULL, order_number character varying(20), order_line_number integer, date_key integer, customer_key integer, product_key integer, partner_key integer, geography_key integer, sales_rep_key integer, contract_key integer, booking_type character varying(15), is_renewal integer, quantity integer, unit_list_price_usd numeric(12,2), discount_pct numeric(5,2), booking_amount_usd numeric(14,2), acv_usd numeric(14,2), tcv_usd numeric(14,2)); |

## 7. Keys and Constraints

| Schema | Table Name | Constraint Name | Constraint Type | Column Name | Referenced Table | Referenced Column | Constraint Definition |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | PRIMARY KEY | contract_key |  |  | PRIMARY KEY (contract_key) |
| ontology | dim_customer | dim_customer_pkey | PRIMARY KEY | customer_key |  |  | PRIMARY KEY (customer_key) |
| ontology | dim_date | dim_date_pkey | PRIMARY KEY | date_key |  |  | PRIMARY KEY (date_key) |
| ontology | dim_geography | dim_geography_pkey | PRIMARY KEY | geography_key |  |  | PRIMARY KEY (geography_key) |
| ontology | dim_partner | dim_partner_pkey | PRIMARY KEY | partner_key |  |  | PRIMARY KEY (partner_key) |
| ontology | dim_product | dim_product_pkey | PRIMARY KEY | product_key |  |  | PRIMARY KEY (product_key) |
| ontology | dim_sales_rep | dim_sales_rep_pkey | PRIMARY KEY | sales_rep_key |  |  | PRIMARY KEY (sales_rep_key) |
| ontology | fact_bookings | fact_bookings_pkey | PRIMARY KEY | booking_id |  |  | PRIMARY KEY (booking_id) |
| ontology | fact_bookings | fk_booking_contract | FOREIGN KEY | contract_key | dim_contract | contract_key | FOREIGN KEY (contract_key) REFERENCES dim_contract(contract_key) |
| ontology | fact_bookings | fk_booking_customer | FOREIGN KEY | customer_key | dim_customer | customer_key | FOREIGN KEY (customer_key) REFERENCES dim_customer(customer_key) |
| ontology | fact_bookings | fk_booking_date | FOREIGN KEY | date_key | dim_date | date_key | FOREIGN KEY (date_key) REFERENCES dim_date(date_key) |
| ontology | fact_bookings | fk_booking_geography | FOREIGN KEY | geography_key | dim_geography | geography_key | FOREIGN KEY (geography_key) REFERENCES dim_geography(geography_key) |
| ontology | fact_bookings | fk_booking_partner | FOREIGN KEY | partner_key | dim_partner | partner_key | FOREIGN KEY (partner_key) REFERENCES dim_partner(partner_key) |
| ontology | fact_bookings | fk_booking_product | FOREIGN KEY | product_key | dim_product | product_key | FOREIGN KEY (product_key) REFERENCES dim_product(product_key) |
| ontology | fact_bookings | fk_booking_sales_rep | FOREIGN KEY | sales_rep_key | dim_sales_rep | sales_rep_key | FOREIGN KEY (sales_rep_key) REFERENCES dim_sales_rep(sales_rep_key) |

### Check Constraints / Not-Null Enforcement

| Schema | Table Name | Constraint Name | Check Clause |
| --- | --- | --- | --- |
| ontology | dim_contract | 2137232_2137270_1_not_null | contract_key IS NOT NULL |
| ontology | dim_customer | 2137232_2137245_1_not_null | customer_key IS NOT NULL |
| ontology | dim_customer | 2137232_2137245_2_not_null | customer_id IS NOT NULL |
| ontology | dim_date | 2137232_2137240_1_not_null | date_key IS NOT NULL |
| ontology | dim_date | 2137232_2137240_2_not_null | full_date IS NOT NULL |
| ontology | dim_geography | 2137232_2137260_1_not_null | geography_key IS NOT NULL |
| ontology | dim_partner | 2137232_2137255_1_not_null | partner_key IS NOT NULL |
| ontology | dim_partner | 2137232_2137255_2_not_null | partner_id IS NOT NULL |
| ontology | dim_product | 2137232_2137250_1_not_null | product_key IS NOT NULL |
| ontology | dim_product | 2137232_2137250_2_not_null | product_id IS NOT NULL |
| ontology | dim_sales_rep | 2137232_2137265_1_not_null | sales_rep_key IS NOT NULL |
| ontology | dim_sales_rep | 2137232_2137265_2_not_null | rep_id IS NOT NULL |
| ontology | fact_bookings | 2137232_2137275_1_not_null | booking_id IS NOT NULL |

### Unique Constraints
No standalone unique constraints were discovered beyond the unique indexes supporting primary keys.

### Referential Constraints
All discovered referential constraints are implemented on `ontology.fact_bookings` and point to the dimension tables.

## 8. Indexes

| Schema | Table Name | Index Name | Indexed Columns | Index Type | Uniqueness | Index Definition |
| --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | contract_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_contract_pkey ON ontology.dim_contract USING btree (contract_key) |
| ontology | dim_customer | dim_customer_pkey | customer_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_customer_pkey ON ontology.dim_customer USING btree (customer_key) |
| ontology | dim_date | dim_date_pkey | date_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_date_pkey ON ontology.dim_date USING btree (date_key) |
| ontology | dim_geography | dim_geography_pkey | geography_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_geography_pkey ON ontology.dim_geography USING btree (geography_key) |
| ontology | dim_partner | dim_partner_pkey | partner_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_partner_pkey ON ontology.dim_partner USING btree (partner_key) |
| ontology | dim_product | dim_product_pkey | product_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_product_pkey ON ontology.dim_product USING btree (product_key) |
| ontology | dim_sales_rep | dim_sales_rep_pkey | sales_rep_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_sales_rep_pkey ON ontology.dim_sales_rep USING btree (sales_rep_key) |
| ontology | fact_bookings | fact_bookings_pkey | booking_id | btree | UNIQUE | CREATE UNIQUE INDEX fact_bookings_pkey ON ontology.fact_bookings USING btree (booking_id) |

## 9. Relationships

| Parent Table | Child Table | Referenced Columns | Relationship Type |
| --- | --- | --- | --- |
| ontology.dim_contract | ontology.fact_bookings | contract_key -> contract_key | One-to-Many |
| ontology.dim_customer | ontology.fact_bookings | customer_key -> customer_key | One-to-Many |
| ontology.dim_date | ontology.fact_bookings | date_key -> date_key | One-to-Many |
| ontology.dim_geography | ontology.fact_bookings | geography_key -> geography_key | One-to-Many |
| ontology.dim_partner | ontology.fact_bookings | partner_key -> partner_key | One-to-Many |
| ontology.dim_product | ontology.fact_bookings | product_key -> product_key | One-to-Many |
| ontology.dim_sales_rep | ontology.fact_bookings | sales_rep_key -> sales_rep_key | One-to-Many |

## 10. DDL Definitions

### Table DDL

#### ontology.dim_contract
```sql
CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
);
```

#### ontology.dim_customer
```sql
CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
);
```

#### ontology.dim_date
```sql
CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
);
```

#### ontology.dim_geography
```sql
CREATE TABLE ontology.dim_geography (
    geography_key integer NOT NULL,
    region character varying(20),
    theater character varying(30),
    country character varying(40)
);
```

#### ontology.dim_partner
```sql
CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
);
```

#### ontology.dim_product
```sql
CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
);
```

#### ontology.dim_sales_rep
```sql
CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
);
```

#### ontology.fact_bookings
```sql
CREATE TABLE ontology.fact_bookings (
    booking_id integer NOT NULL,
    order_number character varying(20),
    order_line_number integer,
    date_key integer,
    customer_key integer,
    product_key integer,
    partner_key integer,
    geography_key integer,
    sales_rep_key integer,
    contract_key integer,
    booking_type character varying(15),
    is_renewal integer,
    quantity integer,
    unit_list_price_usd numeric(12,2),
    discount_pct numeric(5,2),
    booking_amount_usd numeric(14,2),
    acv_usd numeric(14,2),
    tcv_usd numeric(14,2)
);
```

### Constraint DDL

```sql
ALTER TABLE ontology.dim_contract ADD CONSTRAINT dim_contract_pkey PRIMARY KEY (contract_key);
ALTER TABLE ontology.dim_customer ADD CONSTRAINT dim_customer_pkey PRIMARY KEY (customer_key);
ALTER TABLE ontology.dim_date ADD CONSTRAINT dim_date_pkey PRIMARY KEY (date_key);
ALTER TABLE ontology.dim_geography ADD CONSTRAINT dim_geography_pkey PRIMARY KEY (geography_key);
ALTER TABLE ontology.dim_partner ADD CONSTRAINT dim_partner_pkey PRIMARY KEY (partner_key);
ALTER TABLE ontology.dim_product ADD CONSTRAINT dim_product_pkey PRIMARY KEY (product_key);
ALTER TABLE ontology.dim_sales_rep ADD CONSTRAINT dim_sales_rep_pkey PRIMARY KEY (sales_rep_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fact_bookings_pkey PRIMARY KEY (booking_id);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_contract FOREIGN KEY (contract_key) REFERENCES dim_contract(contract_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_customer FOREIGN KEY (customer_key) REFERENCES dim_customer(customer_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_date FOREIGN KEY (date_key) REFERENCES dim_date(date_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_geography FOREIGN KEY (geography_key) REFERENCES dim_geography(geography_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_partner FOREIGN KEY (partner_key) REFERENCES dim_partner(partner_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_product FOREIGN KEY (product_key) REFERENCES dim_product(product_key);
ALTER TABLE ontology.fact_bookings ADD CONSTRAINT fk_booking_sales_rep FOREIGN KEY (sales_rep_key) REFERENCES dim_sales_rep(sales_rep_key);
```

### Index DDL

```sql
CREATE UNIQUE INDEX dim_contract_pkey ON ontology.dim_contract USING btree (contract_key);
CREATE UNIQUE INDEX dim_customer_pkey ON ontology.dim_customer USING btree (customer_key);
CREATE UNIQUE INDEX dim_date_pkey ON ontology.dim_date USING btree (date_key);
CREATE UNIQUE INDEX dim_geography_pkey ON ontology.dim_geography USING btree (geography_key);
CREATE UNIQUE INDEX dim_partner_pkey ON ontology.dim_partner USING btree (partner_key);
CREATE UNIQUE INDEX dim_product_pkey ON ontology.dim_product USING btree (product_key);
CREATE UNIQUE INDEX dim_sales_rep_pkey ON ontology.dim_sales_rep USING btree (sales_rep_key);
CREATE UNIQUE INDEX fact_bookings_pkey ON ontology.fact_bookings USING btree (booking_id);
```

### Views
No user-defined views discovered.

### Stored Procedures / Functions
No user-defined stored procedures or functions discovered.

### Triggers
No user-defined triggers discovered.

### Sequences
No user-defined sequences discovered.

## 11. Normalized Platform-Independent Metadata Summary

| Canonical Object Type | Source Object Type | Count |
| --- | --- | --- |
| Database | PostgreSQL database | 1 |
| Schema | PostgreSQL schema | 2 |
| Table | BASE TABLE | 8 |
| Column | Table column | 61 |
| Primary Key | PRIMARY KEY | 8 |
| Foreign Key | FOREIGN KEY | 7 |
| Check Constraint | CHECK / NOT NULL enforcement | 13 |
| Index | btree unique index | 8 |
| View | View | 0 |
| Routine | Function/Procedure | 0 |
| Trigger | Trigger | 0 |
| Sequence | Sequence | 0 |

## 12. Metadata Completeness Validation

| Validation Rule | Status | Result |
| --- | --- | --- |
| Every discovered table has column metadata | PASS | 8 of 8 tables have column definitions |
| Primary keys identified | PASS | All 8 tables have primary keys |
| Foreign key relationships identified | PASS | 7 foreign key relationships discovered on fact_bookings |
| Object names unique within schema | PASS | No duplicate table names found in schema ontology |
| DDL extraction for supported objects | PASS WITH NOTE | Table, constraint, and index DDL extracted; no additional supported objects exist |
| Missing metadata reported | PASS | No views, routines, triggers, or sequences found |

## 13. Star Schema Interpretation

| Role in Model | Table |
| --- | --- |
| Fact Table | ontology.fact_bookings |
| Dimension Table | ontology.dim_customer |
| Dimension Table | ontology.dim_product |
| Dimension Table | ontology.dim_partner |
| Dimension Table | ontology.dim_geography |
| Dimension Table | ontology.dim_sales_rep |
| Dimension Table | ontology.dim_contract |
| Dimension Table | ontology.dim_date |

## 14. Notes

1. The database is a clean star schema supporting Cisco bookings analytics.
2. Primary-key-backed unique indexes are the only indexes currently present.
3. No auto-increment/identity columns were detected.
4. No default values were defined on discovered columns.
5. Remarks/descriptions were not available from catalog comments, so business-friendly descriptions were inferred from object names and supplied business context.
