# Validated Data Dictionary: Ontology PostgreSQL Schema Discovery

## 1. Input Validation

| Validation Item | Status | Details |
| --- | --- | --- |
| Database Type Supported | PASS | PostgreSQL detected from `version()` |
| Connectivity Verified | PASS | Successfully executed metadata discovery queries |
| Required Connection Parameters Present | PASS | Connection available through Ontology Postgres Query Runner Tool |
| Output Format Valid | PASS | Markdown generated for GitHub delivery |

## 2. Database Summary

| Attribute | Value |
| --- | --- |
| Database Name | ontology |
| Database Version | PostgreSQL 16.14 on x86_64-pc-linux-gnu, compiled by gcc (GCC) 13.2.0, 64-bit |
| Supported Platform | PostgreSQL |
| Business Domain | Cisco Sales Bookings and Revenue Analytics |
| Domain Model Style | Kimball Star Schema |
| Primary Schema(s) Discovered | ontology, public |
| User Objects Found In | ontology |

## 3. Business Domain Context

**Domain Name:** Cisco Sales Bookings and Revenue Analytics  
**Overview:** The schema models Cisco sales booking operations for enterprise networking, security, collaboration, observability, and software subscription products. The design follows a star schema with `fact_bookings` as the central fact table and dimensions for customer, product, partner, geography, sales representative, contract, and date.

## 4. Discovered Schemas

| Schema Name | Contains User Objects |
| --- | --- |
| ontology | Yes |
| public | No discovered user tables/views in current extraction |

## 5. Database Objects

| Database Name | Schema | Object Name | Object Type | Owner | Remarks |
| --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_customer | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_date | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_geography | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_partner | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_product | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | dim_sales_rep | TABLE | ontologyuser1 | Dimension table |
| ontology | ontology | fact_bookings | TABLE | ontologyuser1 | Fact table |

### Objects Not Present / Not Discovered

| Object Type | Status |
| --- | --- |
| Views | None found |
| Materialized Views | None found |
| Sequences | None found |
| Stored Procedures | None found |
| Functions | None found |
| Triggers | None found |

## 6. Tables

| Schema | Table Name | Owner | Table Type |
| --- | --- | --- | --- |
| ontology | dim_contract | ontologyuser1 | BASE TABLE |
| ontology | dim_customer | ontologyuser1 | BASE TABLE |
| ontology | dim_date | ontologyuser1 | BASE TABLE |
| ontology | dim_geography | ontologyuser1 | BASE TABLE |
| ontology | dim_partner | ontologyuser1 | BASE TABLE |
| ontology | dim_product | ontologyuser1 | BASE TABLE |
| ontology | dim_sales_rep | ontologyuser1 | BASE TABLE |
| ontology | fact_bookings | ontologyuser1 | BASE TABLE |

## 7. Normalized Structural Metadata

| Database Name | Schema | Table Name | Object Type | Column Name | Data Type | Length | Precision | Scale | Nullable | Default Value | Identity/Auto Increment | Primary Key | Foreign Key | Referenced Table | Referenced Column | Index | Constraint | Description/Remarks |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | TABLE | contract_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_contract_pkey | dim_contract_pkey | Contract surrogate key |
| ontology | ontology | dim_contract | TABLE | contract_type | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Contract type |
| ontology | ontology | dim_contract | TABLE | term_months | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Contract duration in months |
| ontology | ontology | dim_contract | TABLE | auto_renew_flag | character | 1 |  |  | YES |  | NO | NO | NO |  |  |  |  | Auto-renew indicator |
| ontology | ontology | dim_contract | TABLE | coverage_level | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Support coverage level |
| ontology | ontology | dim_customer | TABLE | customer_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_customer_pkey | dim_customer_pkey | Customer surrogate key |
| ontology | ontology | dim_customer | TABLE | customer_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Business customer identifier |
| ontology | ontology | dim_customer | TABLE | customer_name | character varying | 80 |  |  | YES |  | NO | NO | NO |  |  |  |  | Customer name |
| ontology | ontology | dim_customer | TABLE | segment | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Market segment |
| ontology | ontology | dim_customer | TABLE | industry | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Industry classification |
| ontology | ontology | dim_customer | TABLE | account_tier | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Account tier |
| ontology | ontology | dim_customer | TABLE | hq_country | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Headquarters country |
| ontology | ontology | dim_customer | TABLE | hq_region | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Headquarters region |
| ontology | ontology | dim_date | TABLE | date_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_date_pkey | dim_date_pkey | Date surrogate key |
| ontology | ontology | dim_date | TABLE | full_date | date |  |  |  | NO |  | NO | NO | NO |  |  |  |  | Calendar date |
| ontology | ontology | dim_date | TABLE | month_name | character varying | 12 |  |  | YES |  | NO | NO | NO |  |  |  |  | Month name |
| ontology | ontology | dim_date | TABLE | calendar_year | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Calendar year |
| ontology | ontology | dim_date | TABLE | fiscal_year | character varying | 6 |  |  | YES |  | NO | NO | NO |  |  |  |  | Fiscal year |
| ontology | ontology | dim_date | TABLE | fiscal_quarter | character varying | 10 |  |  | YES |  | NO | NO | NO |  |  |  |  | Fiscal quarter |
| ontology | ontology | dim_date | TABLE | fiscal_period_seq | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Fiscal period sequence |
| ontology | ontology | dim_geography | TABLE | geography_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_geography_pkey | dim_geography_pkey | Geography surrogate key |
| ontology | ontology | dim_geography | TABLE | region | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Region |
| ontology | ontology | dim_geography | TABLE | theater | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Theater |
| ontology | ontology | dim_geography | TABLE | country | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Country |
| ontology | ontology | dim_partner | TABLE | partner_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_partner_pkey | dim_partner_pkey | Partner surrogate key |
| ontology | ontology | dim_partner | TABLE | partner_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Business partner identifier |
| ontology | ontology | dim_partner | TABLE | partner_name | character varying | 60 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner name |
| ontology | ontology | dim_partner | TABLE | partner_type | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner type |
| ontology | ontology | dim_partner | TABLE | partner_tier | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Partner tier |
| ontology | ontology | dim_partner | TABLE | route_to_market | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Route to market |
| ontology | ontology | dim_product | TABLE | product_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_product_pkey | dim_product_pkey | Product surrogate key |
| ontology | ontology | dim_product | TABLE | product_id | character varying | 30 |  |  | NO |  | NO | NO | NO |  |  |  |  | Business product identifier |
| ontology | ontology | dim_product | TABLE | product_name | character varying | 80 |  |  | YES |  | NO | NO | NO |  |  |  |  | Product name |
| ontology | ontology | dim_product | TABLE | product_family | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Product family |
| ontology | ontology | dim_product | TABLE | technology_domain | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Technology domain |
| ontology | ontology | dim_product | TABLE | offer_type | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Offer type |
| ontology | ontology | dim_product | TABLE | business_entity | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Cisco business entity |
| ontology | ontology | dim_sales_rep | TABLE | sales_rep_key | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | dim_sales_rep_pkey | dim_sales_rep_pkey | Sales representative surrogate key |
| ontology | ontology | dim_sales_rep | TABLE | rep_id | character varying | 20 |  |  | NO |  | NO | NO | NO |  |  |  |  | Business sales rep identifier |
| ontology | ontology | dim_sales_rep | TABLE | rep_name | character varying | 60 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales rep name |
| ontology | ontology | dim_sales_rep | TABLE | sales_role | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales role |
| ontology | ontology | dim_sales_rep | TABLE | sales_team | character varying | 40 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales team |
| ontology | ontology | dim_sales_rep | TABLE | segment_covered | character varying | 30 |  |  | YES |  | NO | NO | NO |  |  |  |  | Covered segment |
| ontology | ontology | fact_bookings | TABLE | booking_id | integer |  | 32 | 0 | NO |  | NO | YES | NO |  |  | fact_bookings_pkey | fact_bookings_pkey | Booking transaction surrogate key |
| ontology | ontology | fact_bookings | TABLE | order_number | character varying | 20 |  |  | YES |  | NO | NO | NO |  |  |  |  | Sales order number |
| ontology | ontology | fact_bookings | TABLE | order_line_number | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Sales order line number |
| ontology | ontology | fact_bookings | TABLE | date_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_date | date_key |  | fk_booking_date | Foreign key to date dimension |
| ontology | ontology | fact_bookings | TABLE | customer_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_customer | customer_key |  | fk_booking_customer | Foreign key to customer dimension |
| ontology | ontology | fact_bookings | TABLE | product_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_product | product_key |  | fk_booking_product | Foreign key to product dimension |
| ontology | ontology | fact_bookings | TABLE | partner_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_partner | partner_key |  | fk_booking_partner | Foreign key to partner dimension |
| ontology | ontology | fact_bookings | TABLE | geography_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_geography | geography_key |  | fk_booking_geography | Foreign key to geography dimension |
| ontology | ontology | fact_bookings | TABLE | sales_rep_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_sales_rep | sales_rep_key |  | fk_booking_sales_rep | Foreign key to sales rep dimension |
| ontology | ontology | fact_bookings | TABLE | contract_key | integer |  | 32 | 0 | YES |  | NO | NO | YES | ontology.dim_contract | contract_key |  | fk_booking_contract | Foreign key to contract dimension |
| ontology | ontology | fact_bookings | TABLE | booking_type | character varying | 15 |  |  | YES |  | NO | NO | NO |  |  |  |  | Booking type |
| ontology | ontology | fact_bookings | TABLE | is_renewal | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Renewal indicator |
| ontology | ontology | fact_bookings | TABLE | quantity | integer |  | 32 | 0 | YES |  | NO | NO | NO |  |  |  |  | Quantity sold |
| ontology | ontology | fact_bookings | TABLE | unit_list_price_usd | numeric |  | 12 | 2 | YES |  | NO | NO | NO |  |  |  |  | Unit list price in USD |
| ontology | ontology | fact_bookings | TABLE | discount_pct | numeric |  | 5 | 2 | YES |  | NO | NO | NO |  |  |  |  | Discount percentage |
| ontology | ontology | fact_bookings | TABLE | booking_amount_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Booking amount in USD |
| ontology | ontology | fact_bookings | TABLE | acv_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Annual contract value |
| ontology | ontology | fact_bookings | TABLE | tcv_usd | numeric |  | 14 | 2 | YES |  | NO | NO | NO |  |  |  |  | Total contract value |

## 8. Keys and Constraints

| Schema | Table Name | Constraint Name | Constraint Type | Column Name | Referenced Table | Referenced Column | Constraint Definition |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | PRIMARY KEY | contract_key | ontology.dim_contract | contract_key | PRIMARY KEY (contract_key) |
| ontology | dim_customer | dim_customer_pkey | PRIMARY KEY | customer_key | ontology.dim_customer | customer_key | PRIMARY KEY (customer_key) |
| ontology | dim_date | dim_date_pkey | PRIMARY KEY | date_key | ontology.dim_date | date_key | PRIMARY KEY (date_key) |
| ontology | dim_geography | dim_geography_pkey | PRIMARY KEY | geography_key | ontology.dim_geography | geography_key | PRIMARY KEY (geography_key) |
| ontology | dim_partner | dim_partner_pkey | PRIMARY KEY | partner_key | ontology.dim_partner | partner_key | PRIMARY KEY (partner_key) |
| ontology | dim_product | dim_product_pkey | PRIMARY KEY | product_key | ontology.dim_product | product_key | PRIMARY KEY (product_key) |
| ontology | dim_sales_rep | dim_sales_rep_pkey | PRIMARY KEY | sales_rep_key | ontology.dim_sales_rep | sales_rep_key | PRIMARY KEY (sales_rep_key) |
| ontology | fact_bookings | fact_bookings_pkey | PRIMARY KEY | booking_id | ontology.fact_bookings | booking_id | PRIMARY KEY (booking_id) |
| ontology | fact_bookings | fk_booking_contract | FOREIGN KEY | contract_key | ontology.dim_contract | contract_key | FOREIGN KEY (contract_key) REFERENCES dim_contract(contract_key) |
| ontology | fact_bookings | fk_booking_customer | FOREIGN KEY | customer_key | ontology.dim_customer | customer_key | FOREIGN KEY (customer_key) REFERENCES dim_customer(customer_key) |
| ontology | fact_bookings | fk_booking_date | FOREIGN KEY | date_key | ontology.dim_date | date_key | FOREIGN KEY (date_key) REFERENCES dim_date(date_key) |
| ontology | fact_bookings | fk_booking_geography | FOREIGN KEY | geography_key | ontology.dim_geography | geography_key | FOREIGN KEY (geography_key) REFERENCES dim_geography(geography_key) |
| ontology | fact_bookings | fk_booking_partner | FOREIGN KEY | partner_key | ontology.dim_partner | partner_key | FOREIGN KEY (partner_key) REFERENCES dim_partner(partner_key) |
| ontology | fact_bookings | fk_booking_product | FOREIGN KEY | product_key | ontology.dim_product | product_key | FOREIGN KEY (product_key) REFERENCES dim_product(product_key) |
| ontology | fact_bookings | fk_booking_sales_rep | FOREIGN KEY | sales_rep_key | ontology.dim_sales_rep | sales_rep_key | FOREIGN KEY (sales_rep_key) REFERENCES dim_sales_rep(sales_rep_key) |

### Constraint Type Normalization

| PostgreSQL Code | Normalized Type |
| --- | --- |
| p | PRIMARY KEY |
| f | FOREIGN KEY |

### Not Present / Not Discovered

| Constraint Category | Status |
| --- | --- |
| Unique Constraints (non-PK) | None found |
| Check Constraints (business rules) | None reported in normalized catalog extraction |
| Referential Constraints | Present through foreign keys |

## 9. Indexes

| Schema | Table Name | Index Name | Indexed Columns | Index Type | Uniqueness | DDL Statement |
| --- | --- | --- | --- | --- | --- | --- |
| ontology | dim_contract | dim_contract_pkey | contract_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_contract_pkey ON ontology.dim_contract USING btree (contract_key) |
| ontology | dim_customer | dim_customer_pkey | customer_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_customer_pkey ON ontology.dim_customer USING btree (customer_key) |
| ontology | dim_date | dim_date_pkey | date_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_date_pkey ON ontology.dim_date USING btree (date_key) |
| ontology | dim_geography | dim_geography_pkey | geography_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_geography_pkey ON ontology.dim_geography USING btree (geography_key) |
| ontology | dim_partner | dim_partner_pkey | partner_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_partner_pkey ON ontology.dim_partner USING btree (partner_key) |
| ontology | dim_product | dim_product_pkey | product_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_product_pkey ON ontology.dim_product USING btree (product_key) |
| ontology | dim_sales_rep | dim_sales_rep_pkey | sales_rep_key | btree | UNIQUE | CREATE UNIQUE INDEX dim_sales_rep_pkey ON ontology.dim_sales_rep USING btree (sales_rep_key) |
| ontology | fact_bookings | fact_bookings_pkey | booking_id | btree | UNIQUE | CREATE UNIQUE INDEX fact_bookings_pkey ON ontology.fact_bookings USING btree (booking_id) |

## 10. Relationships

| Parent Table | Parent Column | Child Table | Child Column | Relationship Type |
| --- | --- | --- | --- | --- |
| ontology.dim_contract | contract_key | ontology.fact_bookings | contract_key | One-to-Many |
| ontology.dim_customer | customer_key | ontology.fact_bookings | customer_key | One-to-Many |
| ontology.dim_date | date_key | ontology.fact_bookings | date_key | One-to-Many |
| ontology.dim_geography | geography_key | ontology.fact_bookings | geography_key | One-to-Many |
| ontology.dim_partner | partner_key | ontology.fact_bookings | partner_key | One-to-Many |
| ontology.dim_product | product_key | ontology.fact_bookings | product_key | One-to-Many |
| ontology.dim_sales_rep | sales_rep_key | ontology.fact_bookings | sales_rep_key | One-to-Many |

## 11. DDL Definitions

### 11.1 Table DDL

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

### 11.2 Constraint DDL Equivalents

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

### 11.3 Index DDL

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

### 11.4 Other Object DDL Availability

| Object Type | Availability |
| --- | --- |
| Views | Not applicable - none found |
| Sequences | Not applicable - none found |
| Stored Procedures | Not applicable - none found |
| Functions | Not applicable - none found |
| Triggers | Not applicable - none found |

## 12. Metadata Completeness Validation

| Validation Check | Status | Details |
| --- | --- | --- |
| Every discovered table has column metadata | PASS | 8/8 tables have column definitions |
| Primary keys identified | PASS | All 8 tables have primary keys |
| Foreign keys identified | PASS | 7 foreign key relationships on `fact_bookings` |
| Object names unique within schema | PASS | No duplicate table names detected in schema `ontology` |
| Index metadata extracted | PASS | Primary key indexes discovered |
| DDL extraction completed where supported | PASS | Table, constraint, and index DDL generated/extracted |
| Views/functions/procedures/triggers/sequences assessed | PASS | None found |
| Missing metadata reported | PASS | No owner missing for user tables; no unsupported user objects discovered |

## 13. Findings and Notes

| Category | Observation |
| --- | --- |
| Schema Design | Clear star schema centered on `fact_bookings` |
| Dimensions | 7 dimension tables support business analytics context |
| Fact Table | `fact_bookings` stores booking measures and foreign keys |
| Auto Increment | No identity/auto-increment columns discovered |
| Non-PK Indexes | No additional non-primary indexes found |
| Views/Procedures/Functions | No user-defined objects of these types discovered |
| Public Schema | Present but no user objects captured in extraction |

## 14. Platform-Independent Normalized Summary

| Database Name | Schema | Object Name | Object Type | Key Role | Relationship Role |
| --- | --- | --- | --- | --- | --- |
| ontology | ontology | dim_contract | Dimension Table | Primary Key: contract_key | Parent |
| ontology | ontology | dim_customer | Dimension Table | Primary Key: customer_key | Parent |
| ontology | ontology | dim_date | Dimension Table | Primary Key: date_key | Parent |
| ontology | ontology | dim_geography | Dimension Table | Primary Key: geography_key | Parent |
| ontology | ontology | dim_partner | Dimension Table | Primary Key: partner_key | Parent |
| ontology | ontology | dim_product | Dimension Table | Primary Key: product_key | Parent |
| ontology | ontology | dim_sales_rep | Dimension Table | Primary Key: sales_rep_key | Parent |
| ontology | ontology | fact_bookings | Fact Table | Primary Key: booking_id | Child to all dimensions |

## 15. GitHub Delivery

| Repository | Folder | File Name | Status |
| --- | --- | --- | --- |
| ELANSURIYAA/Ontology | DI Schema Discoverer Agent | ontology_data_dictionary.md | Generated |
