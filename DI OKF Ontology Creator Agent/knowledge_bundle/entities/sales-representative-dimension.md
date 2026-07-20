---
title: Sales Representative Dimension
concept_type: entity
domain: Sales Organization
technical_mapping: ontology.dim_sales_rep
entity_type: Dimension Table
primary_key: sales_rep_key
business_key: rep_id
status: generated
related_measures: []
related_relationships:
  - Sales Representative Owns Booking
---

# Sales Representative Dimension

## Business Definition
Dimension table containing sales representative master data and coverage attributes.

The business process identifies Sales / Account Executive ownership of the customer relationship and booking, which gives this entity strong operational significance.

## Technical Mapping

- Table: `ontology.dim_sales_rep`
- Primary Key: `sales_rep_key`
- Business Key: `rep_id`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Sales Representative Key | `sales_rep_key` | integer | Surrogate key that uniquely identifies a sales representative dimension record. | Primary Key |
| Sales Representative ID | `rep_id` | character varying(20) | Business identifier assigned to a sales representative. | Business Key |
| Sales Representative Name | `rep_name` | character varying(60) | Full name of the sales representative. | Descriptive Attribute |
| Sales Role | `sales_role` | character varying(40) | Role performed by the sales representative in the sales organization. | Dimension Attribute |
| Sales Team | `sales_team` | character varying(40) | Team or organizational unit to which the sales representative belongs. | Hierarchy Attribute |
| Covered Segment | `segment_covered` | character varying(30) | Customer segment or market segment assigned to the sales representative for coverage. | Dimension Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `sales_rep_key` |
| Business Key | `rep_id` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Sales Representative Owns Booking](../relationships/sales-representative-owns-booking.md)

## Related Concepts

- Domain: [Sales Organization](../domains/sales-organization.md)
- Glossary: [Sales Representative Dimension](../glossary/sales-representative-dimension.md)
