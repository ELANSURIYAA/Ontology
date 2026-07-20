---
title: Customer Dimension
concept_type: entity
domain: Customer Management
technical_mapping: ontology.dim_customer
entity_type: Dimension Table
primary_key: customer_key
business_key: customer_id
status: generated
related_measures: []
related_relationships:
  - Customer Places Booking
---

# Customer Dimension

## Business Definition
Dimension table containing descriptive customer master data used to analyze bookings by customer identity, segment, industry, and headquarters location.

During opportunity qualification, the business process confirms customer segment and coverage model, making this dimension critical for customer-centric analytics.

## Technical Mapping

- Table: `ontology.dim_customer`
- Primary Key: `customer_key`
- Business Key: `customer_id`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Customer Key | `customer_key` | integer | Surrogate key that uniquely identifies a customer dimension record. | Primary Key |
| Customer ID | `customer_id` | character varying(20) | Business identifier assigned to a customer account. | Business Key |
| Customer Name | `customer_name` | character varying(80) | Official name of the customer account. | Descriptive Attribute |
| Customer Segment | `segment` | character varying(30) | Market segment to which the customer belongs. | Dimension Attribute |
| Customer Industry | `industry` | character varying(40) | Industry classification of the customer. | Dimension Attribute |
| Account Tier | `account_tier` | character varying(20) | Tier classification assigned to the customer account. | Dimension Attribute |
| Headquarters Country | `hq_country` | character varying(40) | Country where the customer's headquarters is located. | Geography Attribute |
| Headquarters Region | `hq_region` | character varying(20) | Region where the customer's headquarters is located. | Geography Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `customer_key` |
| Business Key | `customer_id` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Customer Places Booking](../relationships/customer-places-booking.md)

## Related Concepts

- Domain: [Customer Management](../domains/customer-management.md)
- Glossary: [Customer Dimension](../glossary/customer-dimension.md)
- Glossary: [Customer Segment](../glossary/customer-segment.md)
- Glossary: [Account Tier](../glossary/account-tier.md)
