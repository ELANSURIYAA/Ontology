# Validated Data Dictionary - Ontology PostgreSQL

## 1. Input Validation

| Validation Item | Status | Details |
| --- | --- | --- |
| Database credentials complete | PASS | Connectivity validated through query execution against PostgreSQL. Sensitive credentials masked in report. |
| Required connection parameters present | PASS | Active database session returned current database, version, and user context. |
| Database type supported | PASS | PostgreSQL 16.14 detected and supported. |
| Output format valid | PASS | Markdown data dictionary generated in normalized tabular format. |

## 2. Connection Validation

| Item | Value |
| --- | --- |
| Database Name | ontology |
| Database Version | PostgreSQL 16.14 on x86_64-pc-linux-gnu, compiled by gcc (GCC) 13.2.0, 64-bit |
| Authenticated User | ontologyuser1 |
| Connectivity Status | Successful |
| Discovery Timestamp Context | Session validated via metadata query runner |

## 3. Business Context

### Domain
Cisco Sales Bookings and Revenue Analytics

### Summary
This PostgreSQL schema models a Kimball-style star schema for Cisco sales bookings analytics. The central fact table `fact_bookings` stores booking transactions at order-line grain, surrounded by conformed dimensions for customer, product, partner, geography, sales representative, contract, and date. The schema supports bookings analysis, ACV/TCV reporting, renewals, partner contribution, and sales performance analytics.

### Primary Business Entities
- Customer
- Product
- Partner
- Sales Representative
- Geography
- Contract
- Date
- Booking Transaction

## 4. Schema Inventory

| Schema Name |
| --- |
| ontology |
| public |

## 5. Object Inventory

| Database Name | Schema | Object Name | Object Type | Owner |
| --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_customer | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_date | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_geography | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_partner | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_product | BASE TABLE | ontologyuser1 |
| ontology | ontology | dim_sales_rep | BASE TABLE | ontologyuser1 |
| ontology | ontology | fact_bookings | BASE TABLE | ontologyuser1 |

## 6. Table and Column Data Dictionary

| Database Name | Schema | Table Name | Object Type | Column Name | Data Type | Length | Precision | Scale | Nullable | Default Value | Primary Key | Foreign Key | Referenced Table | Referenced Column | Index | Constraint | Description/Remarks | DDL Statement |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | BASE TABLE | contract_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_contract_pkey | PRIMARY KEY (contract_key) |  | CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
); |
| ontology | ontology | dim_contract | BASE TABLE | contract_type | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
); |
| ontology | ontology | dim_contract | BASE TABLE | term_months | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
); |
| ontology | ontology | dim_contract | BASE TABLE | auto_renew_flag | character | 1 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
); |
| ontology | ontology | dim_contract | BASE TABLE | coverage_level | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_contract (
    contract_key integer NOT NULL,
    contract_type character varying(40),
    term_months integer,
    auto_renew_flag character(1),
    coverage_level character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | customer_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_customer_pkey | PRIMARY KEY (customer_key) |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | customer_id | character varying | 20 |  |  | NO |  | NO | NO |  |  |  | customer_id IS NOT NULL |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | customer_name | character varying | 80 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | segment | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | industry | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | account_tier | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | hq_country | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_customer | BASE TABLE | hq_region | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_customer (
    customer_key integer NOT NULL,
    customer_id character varying(20) NOT NULL,
    customer_name character varying(80),
    segment character varying(30),
    industry character varying(40),
    account_tier character varying(20),
    hq_country character varying(40),
    hq_region character varying(20)
); |
| ontology | ontology | dim_date | BASE TABLE | date_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_date_pkey | PRIMARY KEY (date_key) |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | full_date | date |  |  |  | NO |  | NO | NO |  |  |  | full_date IS NOT NULL |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | month_name | character varying | 12 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | calendar_year | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_year | character varying | 6 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_quarter | character varying | 10 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_date | BASE TABLE | fiscal_period_seq | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_date (
    date_key integer NOT NULL,
    full_date date NOT NULL,
    month_name character varying(12),
    calendar_year integer,
    fiscal_year character varying(6),
    fiscal_quarter character varying(10),
    fiscal_period_seq integer
); |
| ontology | ontology | dim_geography | BASE TABLE | geography_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_geography_pkey | PRIMARY KEY (geography_key) |  | CREATE TABLE ontology.dim_geography (
    geography_key integer NOT NULL,
    region character varying(20),
    theater character varying(30),
    country character varying(40)
); |
| ontology | ontology | dim_geography | BASE TABLE | region | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_geography (
    geography_key integer NOT NULL,
    region character varying(20),
    theater character varying(30),
    country character varying(40)
); |
| ontology | ontology | dim_geography | BASE TABLE | theater | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_geography (
    geography_key integer NOT NULL,
    region character varying(20),
    theater character varying(30),
    country character varying(40)
); |
| ontology | ontology | dim_geography | BASE TABLE | country | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_geography (
    geography_key integer NOT NULL,
    region character varying(20),
    theater character varying(30),
    country character varying(40)
); |
| ontology | ontology | dim_partner | BASE TABLE | partner_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_partner_pkey | PRIMARY KEY (partner_key) |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_partner | BASE TABLE | partner_id | character varying | 20 |  |  | NO |  | NO | NO |  |  |  | partner_id IS NOT NULL |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_partner | BASE TABLE | partner_name | character varying | 60 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_partner | BASE TABLE | partner_type | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_partner | BASE TABLE | partner_tier | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_partner | BASE TABLE | route_to_market | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_partner (
    partner_key integer NOT NULL,
    partner_id character varying(20) NOT NULL,
    partner_name character varying(60),
    partner_type character varying(30),
    partner_tier character varying(30),
    route_to_market character varying(20)
); |
| ontology | ontology | dim_product | BASE TABLE | product_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_product_pkey | PRIMARY KEY (product_key) |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | product_id | character varying | 30 |  |  | NO |  | NO | NO |  |  |  | product_id IS NOT NULL |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | product_name | character varying | 80 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | product_family | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | technology_domain | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | offer_type | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_product | BASE TABLE | business_entity | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_product (
    product_key integer NOT NULL,
    product_id character varying(30) NOT NULL,
    product_name character varying(80),
    product_family character varying(30),
    technology_domain character varying(40),
    offer_type character varying(30),
    business_entity character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_rep_key | integer |  | 32 | 0 | NO |  | YES | NO |  |  | dim_sales_rep_pkey | PRIMARY KEY (sales_rep_key) |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | rep_id | character varying | 20 |  |  | NO |  | NO | NO |  |  |  | rep_id IS NOT NULL |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | rep_name | character varying | 60 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_role | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | sales_team | character varying | 40 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | dim_sales_rep | BASE TABLE | segment_covered | character varying | 30 |  |  | YES |  | NO | NO |  |  |  |  |  | CREATE TABLE ontology.dim_sales_rep (
    sales_rep_key integer NOT NULL,
    rep_id character varying(20) NOT NULL,
    rep_name character varying(60),
    sales_role character varying(40),
    sales_team character varying(40),
    segment_covered character varying(30)
); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_id | integer |  | 32 | 0 | NO |  | YES | NO |  |  | fact_bookings_pkey | PRIMARY KEY (booking_id) | Central fact table at order-line booking grain | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | order_number | character varying | 20 |  |  | YES |  | NO | NO |  |  |  |  | Business order number | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | order_line_number | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  | Order line grain identifier | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | date_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_date | date_key |  | FOREIGN KEY (date_key) REFERENCES dim_date(date_key) | Time dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | customer_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_customer | customer_key |  | FOREIGN KEY (customer_key) REFERENCES dim_customer(customer_key) | Customer dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | product_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_product | product_key |  | FOREIGN KEY (product_key) REFERENCES dim_product(product_key) | Product dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | partner_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_partner | partner_key |  | FOREIGN KEY (partner_key) REFERENCES dim_partner(partner_key) | Partner dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | geography_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_geography | geography_key |  | FOREIGN KEY (geography_key) REFERENCES dim_geography(geography_key) | Geography dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | sales_rep_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_sales_rep | sales_rep_key |  | FOREIGN KEY (sales_rep_key) REFERENCES dim_sales_rep(sales_rep_key) | Sales representative dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | contract_key | integer |  | 32 | 0 | YES |  | NO | YES | dim_contract | contract_key |  | FOREIGN KEY (contract_key) REFERENCES dim_contract(contract_key) | Contract dimension reference | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_type | character varying | 15 |  |  | YES |  | NO | NO |  |  |  |  | Booking classification such as New, Renewal, Upsell | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | is_renewal | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  | Renewal indicator | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | quantity | integer |  | 32 | 0 | YES |  | NO | NO |  |  |  |  | Quantity sold | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | unit_list_price_usd | numeric |  | 12 | 2 | YES |  | NO | NO |  |  |  |  | Unit list price in USD | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | discount_pct | numeric |  | 5 | 2 | YES |  | NO | NO |  |  |  |  | Discount percentage | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | booking_amount_usd | numeric |  | 14 | 2 | YES |  | NO | NO |  |  |  |  | Net booking amount in USD | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | acv_usd | numeric |  | 14 | 2 | YES |  | NO | NO |  |  |  |  | Annual Contract Value in USD | CREATE TABLE ontology.fact_bookings (
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
); |
| ontology | ontology | fact_bookings | BASE TABLE | tcv_usd | numeric |  | 14 | 2 | YES |  | NO | NO |  |  |  |  | Total Contract Value in USD | CREATE TABLE ontology.fact_bookings (
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
); |

## 7. Key and Constraint Summary

| Schema | Table | Constraint Name | Constraint Type | Column Name | Referenced Schema | Referenced Table | Referenced Column |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | PRIMARY KEY | contract_key | ontology | dim_contract | contract_key |
| ontology | dim_customer | dim_customer_pkey | PRIMARY KEY | customer_key | ontology | dim_customer | customer_key |
| ontology | dim_date | dim_date_pkey | PRIMARY KEY | date_key | ontology | dim_date | date_key |
| ontology | dim_geography | dim_geography_pkey | PRIMARY KEY | geography_key | ontology | dim_geography | geography_key |
| ontology | dim_partner | dim_partner_pkey | PRIMARY KEY | partner_key | ontology | dim_partner | partner_key |
| ontology | dim_product | dim_product_pkey | PRIMARY KEY | product_key | ontology | dim_product | product_key |
| ontology | dim_sales_rep | dim_sales_rep_pkey | PRIMARY KEY | sales_rep_key | ontology | dim_sales_rep | sales_rep_key |
| ontology | fact_bookings | fact_bookings_pkey | PRIMARY KEY | booking_id | ontology | fact_bookings | booking_id |
| ontology | fact_bookings | fk_booking_contract | FOREIGN KEY | contract_key | ontology | dim_contract | contract_key |
| ontology | fact_bookings | fk_booking_customer | FOREIGN KEY | customer_key | ontology | dim_customer | customer_key |
| ontology | fact_bookings | fk_booking_date | FOREIGN KEY | date_key | ontology | dim_date | date_key |
| ontology | fact_bookings | fk_booking_geography | FOREIGN KEY | geography_key | ontology | dim_geography | geography_key |
| ontology | fact_bookings | fk_booking_partner | FOREIGN KEY | partner_key | ontology | dim_partner | partner_key |
| ontology | fact_bookings | fk_booking_product | FOREIGN KEY | product_key | ontology | dim_product | product_key |
| ontology | fact_bookings | fk_booking_sales_rep | FOREIGN KEY | sales_rep_key | ontology | dim_sales_rep | sales_rep_key |

## 8. Check Constraints

| Schema | Table | Constraint Name | Check Clause |
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

## 9. Index Inventory

| Schema | Table | Index Name | Indexed Columns | Index Type | Uniqueness | Primary Index | DDL Statement |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | contract_key | btree | YES | YES | CREATE UNIQUE INDEX dim_contract_pkey ON ontology.dim_contract USING btree (contract_key) |
| ontology | dim_customer | dim_customer_pkey | customer_key | btree | YES | YES | CREATE UNIQUE INDEX dim_customer_pkey ON ontology.dim_customer USING btree (customer_key) |
| ontology | dim_date | dim_date_pkey | date_key | btree | YES | YES | CREATE UNIQUE INDEX dim_date_pkey ON ontology.dim_date USING btree (date_key) |
| ontology | dim_geography | dim_geography_pkey | geography_key | btree | YES | YES | CREATE UNIQUE INDEX dim_geography_pkey ON ontology.dim_geography USING btree (geography_key) |
| ontology | dim_partner | dim_partner_pkey | partner_key | btree | YES | YES | CREATE UNIQUE INDEX dim_partner_pkey ON ontology.dim_partner USING btree (partner_key) |
| ontology | dim_product | dim_product_pkey | product_key | btree | YES | YES | CREATE UNIQUE INDEX dim_product_pkey ON ontology.dim_product USING btree (product_key) |
| ontology | dim_sales_rep | dim_sales_rep_pkey | sales_rep_key | btree | YES | YES | CREATE UNIQUE INDEX dim_sales_rep_pkey ON ontology.dim_sales_rep USING btree (sales_rep_key) |
| ontology | fact_bookings | fact_bookings_pkey | booking_id | btree | YES | YES | CREATE UNIQUE INDEX fact_bookings_pkey ON ontology.fact_bookings USING btree (booking_id) |

## 10. Relationship Inventory

| Parent Table | Child Table | Referenced Columns | Relationship Type |
| --- | --- | --- | --- |
| ontology.dim_contract | ontology.fact_bookings | contract_key | One-to-Many |
| ontology.dim_customer | ontology.fact_bookings | customer_key | One-to-Many |
| ontology.dim_date | ontology.fact_bookings | date_key | One-to-Many |
| ontology.dim_geography | ontology.fact_bookings | geography_key | One-to-Many |
| ontology.dim_partner | ontology.fact_bookings | partner_key | One-to-Many |
| ontology.dim_product | ontology.fact_bookings | product_key | One-to-Many |
| ontology.dim_sales_rep | ontology.fact_bookings | sales_rep_key | One-to-Many |

## 11. Database Object Coverage

| Object Category | Count | Status | Notes |
| --- | --- | --- | --- |
| Base Tables | 8 | Discovered | All business tables are in schema `ontology`. |
| Views | 0 | None Found | No user-defined views discovered. |
| Stored Procedures | 0 | None Found | No procedures discovered through available metadata queries. |
| Functions | 0 | None Found | No user-defined functions discovered. |
| Triggers | 0 | None Found | No triggers discovered. |
| Sequences | 0 | None Found | No sequences discovered. |
| Materialized Views | 0 | None Found | None discovered. |

## 12. DDL Definitions

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

### Constraint DDL Definitions

```sql
PRIMARY KEY (contract_key)
PRIMARY KEY (customer_key)
PRIMARY KEY (date_key)
PRIMARY KEY (geography_key)
PRIMARY KEY (partner_key)
PRIMARY KEY (product_key)
PRIMARY KEY (sales_rep_key)
PRIMARY KEY (booking_id)
FOREIGN KEY (contract_key) REFERENCES dim_contract(contract_key)
FOREIGN KEY (customer_key) REFERENCES dim_customer(customer_key)
FOREIGN KEY (date_key) REFERENCES dim_date(date_key)
FOREIGN KEY (geography_key) REFERENCES dim_geography(geography_key)
FOREIGN KEY (partner_key) REFERENCES dim_partner(partner_key)
FOREIGN KEY (product_key) REFERENCES dim_product(product_key)
FOREIGN KEY (sales_rep_key) REFERENCES dim_sales_rep(sales_rep_key)
```

## 13. Normalized Platform-Independent Metadata View

| Database Name | Schema | Object Name | Object Type | Parent Object | Attribute Name | Attribute Role | Data Type | Nullable | Key Type | Relationship Target |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | TABLE |  | contract_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_contract | TABLE |  | contract_type | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_contract | TABLE |  | term_months | Descriptive Attribute | integer | YES |  |  |
| ontology | ontology | dim_contract | TABLE |  | auto_renew_flag | Descriptive Attribute | character(1) | YES |  |  |
| ontology | ontology | dim_contract | TABLE |  | coverage_level | Descriptive Attribute | character varying(20) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | customer_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_customer | TABLE |  | customer_id | Natural/Business Identifier | character varying(20) | NO |  |  |
| ontology | ontology | dim_customer | TABLE |  | customer_name | Descriptive Attribute | character varying(80) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | segment | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | industry | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | account_tier | Descriptive Attribute | character varying(20) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | hq_country | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_customer | TABLE |  | hq_region | Descriptive Attribute | character varying(20) | YES |  |  |
| ontology | ontology | dim_date | TABLE |  | date_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_date | TABLE |  | full_date | Core Date Attribute | date | NO |  |  |
| ontology | ontology | dim_date | TABLE |  | month_name | Descriptive Attribute | character varying(12) | YES |  |  |
| ontology | ontology | dim_date | TABLE |  | calendar_year | Descriptive Attribute | integer | YES |  |  |
| ontology | ontology | dim_date | TABLE |  | fiscal_year | Descriptive Attribute | character varying(6) | YES |  |  |
| ontology | ontology | dim_date | TABLE |  | fiscal_quarter | Descriptive Attribute | character varying(10) | YES |  |  |
| ontology | ontology | dim_date | TABLE |  | fiscal_period_seq | Descriptive Attribute | integer | YES |  |  |
| ontology | ontology | dim_geography | TABLE |  | geography_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_geography | TABLE |  | region | Descriptive Attribute | character varying(20) | YES |  |  |
| ontology | ontology | dim_geography | TABLE |  | theater | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_geography | TABLE |  | country | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_partner | TABLE |  | partner_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_partner | TABLE |  | partner_id | Natural/Business Identifier | character varying(20) | NO |  |  |
| ontology | ontology | dim_partner | TABLE |  | partner_name | Descriptive Attribute | character varying(60) | YES |  |  |
| ontology | ontology | dim_partner | TABLE |  | partner_type | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_partner | TABLE |  | partner_tier | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_partner | TABLE |  | route_to_market | Descriptive Attribute | character varying(20) | YES |  |  |
| ontology | ontology | dim_product | TABLE |  | product_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_product | TABLE |  | product_id | Natural/Business Identifier | character varying(30) | NO |  |  |
| ontology | ontology | dim_product | TABLE |  | product_name | Descriptive Attribute | character varying(80) | YES |  |  |
| ontology | ontology | dim_product | TABLE |  | product_family | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_product | TABLE |  | technology_domain | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_product | TABLE |  | offer_type | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_product | TABLE |  | business_entity | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | dim_sales_rep | TABLE |  | sales_rep_key | Business Key / Surrogate Key | integer | NO | PRIMARY KEY |  |
| ontology | ontology | dim_sales_rep | TABLE |  | rep_id | Natural/Business Identifier | character varying(20) | NO |  |  |
| ontology | ontology | dim_sales_rep | TABLE |  | rep_name | Descriptive Attribute | character varying(60) | YES |  |  |
| ontology | ontology | dim_sales_rep | TABLE |  | sales_role | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_sales_rep | TABLE |  | sales_team | Descriptive Attribute | character varying(40) | YES |  |  |
| ontology | ontology | dim_sales_rep | TABLE |  | segment_covered | Descriptive Attribute | character varying(30) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | booking_id | Transaction Identifier | integer | NO | PRIMARY KEY |  |
| ontology | ontology | fact_bookings | TABLE |  | order_number | Transaction Attribute | character varying(20) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | order_line_number | Transaction Grain Attribute | integer | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | date_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_date(date_key) |
| ontology | ontology | fact_bookings | TABLE |  | customer_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_customer(customer_key) |
| ontology | ontology | fact_bookings | TABLE |  | product_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_product(product_key) |
| ontology | ontology | fact_bookings | TABLE |  | partner_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_partner(partner_key) |
| ontology | ontology | fact_bookings | TABLE |  | geography_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_geography(geography_key) |
| ontology | ontology | fact_bookings | TABLE |  | sales_rep_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_sales_rep(sales_rep_key) |
| ontology | ontology | fact_bookings | TABLE |  | contract_key | Dimension Reference | integer | YES | FOREIGN KEY | ontology.dim_contract(contract_key) |
| ontology | ontology | fact_bookings | TABLE |  | booking_type | Transaction Attribute | character varying(15) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | is_renewal | Transaction Indicator | integer | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | quantity | Measure Support Attribute | integer | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | unit_list_price_usd | Measure | numeric(12,2) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | discount_pct | Measure | numeric(5,2) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | booking_amount_usd | Measure | numeric(14,2) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | acv_usd | Measure | numeric(14,2) | YES |  |  |
| ontology | ontology | fact_bookings | TABLE |  | tcv_usd | Measure | numeric(14,2) | YES |  |  |

## 14. Metadata Completeness Validation

| Validation Rule | Status | Result |
| --- | --- | --- |
| Every discovered table has associated column metadata | PASS | 8 of 8 tables have column metadata. |
| Primary keys identified | PASS | All 8 tables have primary keys identified. |
| Foreign key relationships identified | PASS | 7 foreign key relationships identified from fact to dimensions. |
| Object names unique within schema | PASS | No duplicate object names found within schema `ontology`. |
| Index metadata extracted | PASS | Primary indexes extracted for all tables. |
| Constraint metadata extracted | PASS | Primary, foreign key, and check constraints extracted. |
| DDL extraction completed successfully where supported | PARTIAL PASS | Table and index DDL extracted. Native full-fidelity object recreation DDL for views/functions/triggers/sequences not applicable because none were found. |
| Column descriptions available | FAIL / NOT AVAILABLE | No column comments or remarks present in source metadata. |
| Object descriptions available | FAIL / NOT AVAILABLE | No object comments or remarks present in source metadata. |

## 15. Missing or Not Available Metadata

| Metadata Category | Status | Notes |
| --- | --- | --- |
| Views | Not Present | No user-defined views found. |
| Stored Procedures | Not Present | None found through available metadata access. |
| Functions | Not Present | No user-defined functions found. |
| Triggers | Not Present | No triggers found. |
| Sequences | Not Present | No sequences found. |
| Unique Keys (non-PK) | Not Present | No separate unique constraints discovered. |
| Referential actions | Not Available | Delete/update rules were not extracted in returned result set. |
| Comments/Descriptions | Not Present | No object or column descriptions stored in catalog. |

## 16. Analytical Interpretation

This schema is a clean star-schema implementation aligned to the Cisco Bookings business process documentation. The `fact_bookings` table serves as the transactional center and joins to seven dimensions. The model is suitable for:

- Enterprise documentation
- Metadata governance
- Data cataloging
- Semantic model generation
- Ontology generation
- AI-driven metadata discovery

The dimensional design directly supports business questions around bookings, ACV, TCV, renewals, route-to-market, product-family mix, geography, partner contribution, and sales performance.

## 17. File Generation Status

| Item | Status |
| --- | --- |
| Markdown data dictionary generated | SUCCESS |
| GitHub repository target | SUCCESS |
| File write requested | SUCCESS |
| Sensitive credentials exposed in report | NO |

---
Generated by DI Schema Discoverer Agent for PostgreSQL metadata discovery and normalized data dictionary creation.
