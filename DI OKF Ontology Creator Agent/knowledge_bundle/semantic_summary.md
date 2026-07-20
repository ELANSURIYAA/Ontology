---
title: Semantic Summary
concept_type: navigation
bundle_name: Cisco Bookings OKF Knowledge Bundle
status: generated
---

# Semantic Summary

## Source Validation Summary

| Validation Item | Status | Details |
| --- | --- | --- |
| OSI Semantic Model readability | PASS | Source file was readable and structurally complete. |
| Business Process document readability | PASS | The supplied business process document content was readable. |
| Required semantic sections present | PASS | Domains, entities, relationships, measures, glossary mapping, and warnings were present. |
| Duplicate entities | PASS | No duplicate entities identified across 8 discovered tables. |
| Duplicate domains | PASS | No duplicate domain names identified. |
| Missing relationships | PASS | No missing structural relationships; all dimensions participate with `fact_bookings`. |
| Missing glossary mappings | WARNING | Some business definitions were inferred because native database comments were unavailable. |
| Data-backed validation | WARNING | Source tables are empty, so instance-level semantic validation could not be performed. |

## Model Overview

The model is a dimensional star schema centered on [Booking Transaction Fact](entities/booking-transaction-fact.md) at order-line grain. It is enriched by seven conformed dimensions covering customer, product, partner, geography, sales representative, contract, and date.

The business process context confirms that Quote-to-Booking begins at opportunity qualification and ends when a valid customer order is accepted and recognized as a booking, establishing entitlement and renewal context.

## Domains

- [Sales Transactions](domains/sales-transactions.md)
- [Customer Management](domains/customer-management.md)
- [Product Management](domains/product-management.md)
- [Partner Management](domains/partner-management.md)
- [Geography](domains/geography.md)
- [Sales Organization](domains/sales-organization.md)
- [Contract Management](domains/contract-management.md)
- [Time](domains/time.md)

## Entities

- [Booking Transaction Fact](entities/booking-transaction-fact.md)
- [Customer Dimension](entities/customer-dimension.md)
- [Product Dimension](entities/product-dimension.md)
- [Partner Dimension](entities/partner-dimension.md)
- [Geography Dimension](entities/geography-dimension.md)
- [Sales Representative Dimension](entities/sales-representative-dimension.md)
- [Contract Dimension](entities/contract-dimension.md)
- [Date Dimension](entities/date-dimension.md)

## Relationships

- [Booking Occurs On Date](relationships/booking-occurs-on-date.md)
- [Customer Places Booking](relationships/customer-places-booking.md)
- [Product Appears In Booking](relationships/product-appears-in-booking.md)
- [Partner Participates In Booking](relationships/partner-participates-in-booking.md)
- [Geography Classifies Booking](relationships/geography-classifies-booking.md)
- [Sales Representative Owns Booking](relationships/sales-representative-owns-booking.md)
- [Contract Classifies Booking](relationships/contract-classifies-booking.md)

## Measures

- [Quantity Sold](measures/quantity-sold.md)
- [Unit List Price USD](measures/unit-list-price-usd.md)
- [Discount Percentage](measures/discount-percentage.md)
- [Booking Amount USD](measures/booking-amount-usd.md)
- [Annual Contract Value USD](measures/annual-contract-value-usd.md)
- [Total Contract Value USD](measures/total-contract-value-usd.md)

## Business Process Enrichment

The business process document adds the following contextual interpretations:

- Bookings are recognized when Cisco accepts a valid order with committed value.
- Bookings are a leading indicator of demand and precede billing and revenue recognition.
- For subscription and SaaS offers, booking amount aligns to TCV and ACV is annualized.
- Hardware is typically perpetual and may attach support contracts such as SmartNet Total Care.
- Channel flows influence [Route to Market](glossary/route-to-market.md) and partner analytics.
- Renewals close the loop back into the bookings fact via renewal bookings.

## Validation Warnings

| Warning Type | Severity | Details |
| --- | --- | --- |
| Inferred semantic definitions | Medium | Several business definitions rely on inference because native database comments are unavailable. |
| Empty source tables | High | Instance-level validation for code values, data quality, and measure distributions cannot be performed. |
| Natural key gaps | Medium | `dim_contract` and `dim_geography` do not expose explicit natural business identifiers. |
| Non-additive metric caution | Medium | `discount_pct` and `unit_list_price_usd` should not be blindly summed. |
| Coded indicator ambiguity | Medium | `is_renewal` and `auto_renew_flag` require business-approved code-set documentation. |

## OKF Validation

| Check | Status | Details |
| --- | --- | --- |
| Missing concept documents | PASS | All identified domains, entities, relationships, measures, and glossary concepts in scope are represented in this bundle. |
| Missing YAML frontmatter | PASS | Every generated document contains YAML frontmatter. |
| Broken semantic links | PASS | Internal links were generated consistently using bundle-relative paths. |
| Duplicate concept documents | PASS | One document per generated concept. |
| Missing references | WARNING | Some glossary references are inferred from column semantics rather than explicit source commentary. |
