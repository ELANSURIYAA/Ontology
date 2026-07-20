---
title: Date Dimension
concept_type: entity
domain: Time
technical_mapping: ontology.dim_date
entity_type: Dimension Table
primary_key: date_key
business_key: full_date
status: generated
related_measures: []
related_relationships:
  - Booking Occurs On Date
---

# Date Dimension

## Business Definition
Dimension table containing calendar and fiscal attributes for time-based analysis of bookings.

This entity enables trend reporting, fiscal reporting, and period comparison across the bookings model.

## Technical Mapping

- Table: `ontology.dim_date`
- Primary Key: `date_key`
- Business Key: `full_date`

## Attributes

| Attribute | Technical Column | Data Type | Business Definition | Role |
| --- | --- | --- | --- | --- |
| Date Key | `date_key` | integer | Surrogate key that uniquely identifies a date dimension record. | Primary Key |
| Full Date | `full_date` | date | Actual calendar date represented by the date dimension row. | Business Key |
| Month Name | `month_name` | character varying(12) | Name of the calendar month for the date. | Hierarchy Attribute |
| Calendar Year | `calendar_year` | integer | Calendar year associated with the date. | Hierarchy Attribute |
| Fiscal Year | `fiscal_year` | character varying(6) | Cisco fiscal year associated with the date. | Hierarchy Attribute |
| Fiscal Quarter | `fiscal_quarter` | character varying(10) | Fiscal quarter associated with the date. | Hierarchy Attribute |
| Fiscal Period Sequence | `fiscal_period_seq` | integer | Sequential numeric ordering of fiscal periods. | Ordering Attribute |

## Keys

| Key Type | Column(s) |
| --- | --- |
| Primary Key | `date_key` |
| Business Key | `full_date` |

## Measures

This entity contains descriptive attributes and does not store business measures directly.

## Relationships

- [Booking Occurs On Date](../relationships/booking-occurs-on-date.md)

## Related Concepts

- Domain: [Time](../domains/time.md)
- Glossary: [Date Dimension](../glossary/date-dimension.md)
- Glossary: [Fiscal Year](../glossary/fiscal-year.md)
- Glossary: [Fiscal Quarter](../glossary/fiscal-quarter.md)
