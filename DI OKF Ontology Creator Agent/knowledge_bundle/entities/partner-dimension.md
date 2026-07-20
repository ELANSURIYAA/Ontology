---
title: Partner Dimension
concept_type: entity
domain: Partner Management
technical_mapping: ontology.dim_partner
entity_type: Dimension Table
primary_key: partner_key
business_key: partner_id
status: generated
related_measures: []
related_relationships:
  - Partner Participates In Booking
---

# Partner Dimension

## Business Definition
Dimension table containing channel partner master data including type, tier, and route-to-market attributes.

The business process states that channel deals involve partner registration and route-to-market assignment, making this entity essential for channel analytics.

## Technical Mapping

- Table: `ontology.dim_partner`
- Primary Key: `partner_key`
- Business Key: `partner_id`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Partner Key | `partner_key` | integer | Surrogate key that uniquely identifies a partner dimension record. | Primary Key |
| Partner ID | `partner_id` | character varying(20) | Business identifier assigned to a partner organization. | Business Key |
| Partner Name | `partner_name` | character varying(60) | Official name of the partner organization. | Descriptive Attribute |
| Partner Type | `partner_type` | character varying(30) | Classification of the partner organization. | Dimension Attribute |
| Partner Tier | `partner_tier` | character varying(30) | Tier or level assigned to the partner within the partner program. | Hierarchy Attribute |
| Route to Market | `route_to_market` | character varying(20) | Selling motion or channel path through which the booking was transacted. | Dimension Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `partner_key` |
| Business Key | `partner_id` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Partner Participates In Booking](../relationships/partner-participates-in-booking.md)

## Related Concepts

- Domain: [Partner Management](../domains/partner-management.md)
- Glossary: [Partner Dimension](../glossary/partner-dimension.md)
- Glossary: [Route to Market](../glossary/route-to-market.md)
