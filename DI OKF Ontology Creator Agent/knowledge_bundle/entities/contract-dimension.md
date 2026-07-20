---
title: Contract Dimension
concept_type: entity
domain: Contract Management
technical_mapping: ontology.dim_contract
entity_type: Dimension Table
primary_key: contract_key
business_key: inferred contract context
status: generated
related_measures: []
related_relationships:
  - Contract Classifies Booking
---

# Contract Dimension

## Business Definition
Dimension table containing descriptive attributes of service, support, or subscription contracts associated with bookings.

The business process confirms that after booking recognition, a service or subscription contract is created with coverage level, term, and renewal context, making this entity important for lifecycle analysis.

## Technical Mapping

- Table: `ontology.dim_contract`
- Primary Key: `contract_key`
- Business Key: inferred contract business context; no separate natural identifier supplied

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Contract Key | `contract_key` | integer | Surrogate key that uniquely identifies a contract dimension record. | Primary Key |
| Contract Type | `contract_type` | character varying(40) | Classification of the commercial or service agreement associated with a booking. | Dimension Attribute |
| Contract Term Months | `term_months` | integer | Number of months covered by the contract term. | Dimension Attribute |
| Auto Renew Indicator | `auto_renew_flag` | character(1) | Flag indicating whether the contract is configured to renew automatically. | Transaction Indicator |
| Coverage Level | `coverage_level` | character varying(20) | Service or support coverage level associated with the contract. | Dimension Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `contract_key` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Contract Classifies Booking](../relationships/contract-classifies-booking.md)

## Related Concepts

- Domain: [Contract Management](../domains/contract-management.md)
- Glossary: [Contract Dimension](../glossary/contract-dimension.md)
- Glossary: [Coverage Level](../glossary/coverage-level.md)
