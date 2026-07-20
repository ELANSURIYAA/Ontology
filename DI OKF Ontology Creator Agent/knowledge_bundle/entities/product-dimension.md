---
title: Product Dimension
concept_type: entity
domain: Product Management
technical_mapping: ontology.dim_product
entity_type: Dimension Table
primary_key: product_key
business_key: product_id
status: generated
related_measures: []
related_relationships:
  - Product Appears In Booking
---

# Product Dimension

## Business Definition
Dimension table containing Cisco product master attributes such as product family, technology domain, offer type, and business entity.

The quote-to-booking process indicates that products are configured and priced before booking recognition, so this entity supplies the product context required for mix and portfolio analysis.

## Technical Mapping

- Table: `ontology.dim_product`
- Primary Key: `product_key`
- Business Key: `product_id`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Product Key | `product_key` | integer | Surrogate key that uniquely identifies a product dimension record. | Primary Key |
| Product ID | `product_id` | character varying(30) | Business identifier assigned to a Cisco product or offer. | Business Key |
| Product Name | `product_name` | character varying(80) | Business name of the product or offer. | Descriptive Attribute |
| Product Family | `product_family` | character varying(30) | Higher-level product grouping used to categorize related offers. | Hierarchy Attribute |
| Technology Domain | `technology_domain` | character varying(40) | Technology category or solution domain associated with the product. | Hierarchy Attribute |
| Offer Type | `offer_type` | character varying(30) | Commercial type of the product offer. | Dimension Attribute |
| Business Entity | `business_entity` | character varying(30) | Internal Cisco business entity or portfolio owning the product. | Dimension Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `product_key` |
| Business Key | `product_id` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Product Appears In Booking](../relationships/product-appears-in-booking.md)

## Related Concepts

- Domain: [Product Management](../domains/product-management.md)
- Glossary: [Product Dimension](../glossary/product-dimension.md)
- Glossary: [Product Family](../glossary/product-family.md)
- Glossary: [Technology Domain](../glossary/technology-domain.md)
