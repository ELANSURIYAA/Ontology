---
title: Geography Dimension
concept_type: entity
domain: Geography
technical_mapping: ontology.dim_geography
entity_type: Dimension Table
primary_key: geography_key
business_key: inferred geographic context
status: generated
related_measures: []
related_relationships:
  - Geography Classifies Booking
---

# Geography Dimension

## Business Definition
Dimension table containing geographic attributes such as region, theater, and country for sales analysis.

This entity supports regional reporting and geographic rollups used in sales performance analysis.

## Technical Mapping

- Table: `ontology.dim_geography`
- Primary Key: `geography_key`
- Business Key: inferred from geographic attributes; no explicit natural key was supplied

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Geography Key | `geography_key` | integer | Surrogate key that uniquely identifies a geography dimension record. | Primary Key |
| Region | `region` | character varying(20) | Broad geographic region associated with the booking or business activity. | Hierarchy Attribute |
| Theater | `theater` | character varying(30) | Intermediate sales geography grouping used within Cisco regional organization structures. | Hierarchy Attribute |
| Country | `country` | character varying(40) | Country associated with the geography dimension row. | Hierarchy Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `geography_key` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Geography Classifies Booking](../relationships/geography-classifies-booking.md)

## Related Concepts

- Domain: [Geography](../domains/geography.md)
- Glossary: [Geography Dimension](../glossary/geography-dimension.md)
- Glossary: [Theater](../glossary/theater.md)
