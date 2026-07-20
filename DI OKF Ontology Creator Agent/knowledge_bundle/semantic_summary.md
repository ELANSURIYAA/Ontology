---
title: Semantic Summary
concept_type: navigation
status: generated
---

# Semantic Summary

## Business Overview

Cisco Bookings is modeled as a star schema centered on a single fact table at order-line grain. The semantic purpose of the model is to support governed analysis of bookings across customer, product, partner, geography, sales organization, contract, and time.

## Business Process Context

The business process represented is Quote-to-Booking, the front portion of the Order-to-Cash cycle. It begins with opportunity qualification and concludes when a valid order is accepted and recognized as a booking. The process includes:

1. Opportunity qualification in CRM
2. Configure, price, and quote in Cisco Commerce Workspace
3. Deal registration and partner routing
4. Order placement and validation
5. Booking recognition
6. Fulfillment and provisioning
7. Contract and entitlement creation
8. Renewal lifecycle management

## Semantic Structure

### Domains

- [Sales Transactions](domains/sales-transactions.md)
- [Customer Management](domains/customer-management.md)
- [Product Management](domains/product-management.md)
- [Partner Management](domains/partner-management.md)
- [Geography](domains/geography.md)
- [Sales Organization](domains/sales-organization.md)
- [Contract Management](domains/contract-management.md)
- [Time](domains/time.md)

### Core Entity Pattern

The model follows a hub-and-spoke pattern:

- Central fact: [Booking Transaction Fact](entities/booking-transaction-fact.md)
- Dimensions:
  - [Customer Dimension](entities/customer-dimension.md)
  - [Product Dimension](entities/product-dimension.md)
  - [Partner Dimension](entities/partner-dimension.md)
  - [Geography Dimension](entities/geography-dimension.md)
  - [Sales Representative Dimension](entities/sales-representative-dimension.md)
  - [Contract Dimension](entities/contract-dimension.md)
  - [Date Dimension](entities/date-dimension.md)

### Relationship Summary

- [Booking Occurs On Date](relationships/booking-occurs-on-date.md)
- [Customer Places Booking](relationships/customer-places-booking.md)
- [Product Appears In Booking](relationships/product-appears-in-booking.md)
- [Partner Participates In Booking](relationships/partner-participates-in-booking.md)
- [Geography Classifies Booking](relationships/geography-classifies-booking.md)
- [Sales Representative Owns Booking](relationships/sales-representative-owns-booking.md)
- [Contract Classifies Booking](relationships/contract-classifies-booking.md)

### Measure Summary

- [Quantity Sold](measures/quantity-sold.md)
- [Unit List Price USD](measures/unit-list-price-usd.md)
- [Discount Percentage](measures/discount-percentage.md)
- [Booking Amount USD](measures/booking-amount-usd.md)
- [Annual Contract Value USD](measures/annual-contract-value-usd.md)
- [Total Contract Value USD](measures/total-contract-value-usd.md)

## Validation Summary

| Validation Item | Status | Details |
| --- | --- | --- |
| Duplicate entities | PASS | No duplicate entities identified across the 8 discovered tables. |
| Duplicate measures | PASS | No duplicate measure names identified in the fact model. |
| Circular relationships | PASS | No circular relationships identified; the model is a hub-and-spoke star schema. |
| Missing glossary mappings | WARNING | Some business definitions are inferred from supplied business documents because native database comments are unavailable. |
| Missing keys | PASS | All entities have primary keys; fact table has 7 foreign keys to dimensions. |
| Orphan entities | PASS | No orphan entities structurally; all dimensions participate in a semantic relationship with `fact_bookings`. |
| Data-backed validation | WARNING | All tables are empty, so runtime validation of domains and instance-level integrity is not possible. |

## Business Value

This OKF bundle provides a reusable, human-readable and machine-readable semantic foundation for ontology generation, knowledge management, governed metric definitions, and AI-driven analytical experiences.
