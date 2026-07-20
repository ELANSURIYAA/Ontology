---
title: Booking Transaction Fact
concept_type: entity
domain: Sales Transactions
technical_mapping: ontology.fact_bookings
entity_type: Fact Table
primary_key: booking_id
business_key: booking_id
grain: One row per booking transaction at order-line grain
status: generated
related_measures:
  - Quantity Sold
  - Unit List Price USD
  - Discount Percentage
  - Booking Amount USD
  - Annual Contract Value USD
  - Total Contract Value USD
related_relationships:
  - Booking Occurs On Date
  - Customer Places Booking
  - Product Appears In Booking
  - Partner Participates In Booking
  - Geography Classifies Booking
  - Sales Representative Owns Booking
  - Contract Classifies Booking
---

# Booking Transaction Fact

## Business Definition
Central fact table capturing booking transactions at order-line grain with financial and operational measures.

The business process defines this as the point where a valid, accepted order is recognized as a booking and classified as New, Renewal, or Upsell. It is the primary governed structure for demand analysis.

## Technical Mapping

- Table: `ontology.fact_bookings`
- Grain: one row per booking transaction at order-line grain
- Primary Key: `booking_id`
- Business Key: `booking_id`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
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

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `booking_id` |
| Foreign Key | `date_key` -> `ontology.dim_date.date_key` |
| Foreign Key | `customer_key` -> `ontology.dim_customer.customer_key` |
| Foreign Key | `product_key` -> `ontology.dim_product.product_key` |
| Foreign Key | `partner_key` -> `ontology.dim_partner.partner_key` |
| Foreign Key | `geography_key` -> `ontology.dim_geography.geography_key` |
| Foreign Key | `sales_rep_key` -> `ontology.dim_sales_rep.sales_rep_key` |
| Foreign Key | `contract_key` -> `ontology.dim_contract.contract_key` |

## Measures

- [Quantity Sold](../measures/quantity-sold.md)
- [Unit List Price USD](../measures/unit-list-price-usd.md)
- [Discount Percentage](../measures/discount-percentage.md)
- [Booking Amount USD](../measures/booking-amount-usd.md)
- [Annual Contract Value USD](../measures/annual-contract-value-usd.md)
- [Total Contract Value USD](../measures/total-contract-value-usd.md)

## Relationships

- [Booking Occurs On Date](../relationships/booking-occurs-on-date.md)
- [Customer Places Booking](../relationships/customer-places-booking.md)
- [Product Appears In Booking](../relationships/product-appears-in-booking.md)
- [Partner Participates In Booking](../relationships/partner-participates-in-booking.md)
- [Geography Classifies Booking](../relationships/geography-classifies-booking.md)
- [Sales Representative Owns Booking](../relationships/sales-representative-owns-booking.md)
- [Contract Classifies Booking](../relationships/contract-classifies-booking.md)

## Related Concepts

- Domain: [Sales Transactions](../domains/sales-transactions.md)
- Glossary: [Booking Type](../glossary/booking-type.md)
- Glossary: [Renewal Indicator](../glossary/renewal-indicator.md)
- Glossary: [Booking Transaction Fact](../glossary/booking-transaction-fact.md)
