---
title: Sales Transactions
concept_type: domain
status: generated
related_entities:
  - Booking Transaction Fact
related_measures:
  - Quantity Sold
  - Unit List Price USD
  - Discount Percentage
  - Booking Amount USD
  - Annual Contract Value USD
  - Total Contract Value USD
---

# Sales Transactions

## Description
Booking transaction domain capturing order-line booking events and measurable sales outcomes.

## Business Purpose
This domain represents the core booking event in Cisco's Quote-to-Booking process. It supports analysis of accepted orders recognized as bookings and enables governed reporting on demand, renewal mix, ACV, TCV, and booking value.

## Related Entities
- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Related Measures
- [Quantity Sold](../measures/quantity-sold.md)
- [Unit List Price USD](../measures/unit-list-price-usd.md)
- [Discount Percentage](../measures/discount-percentage.md)
- [Booking Amount USD](../measures/booking-amount-usd.md)
- [Annual Contract Value USD](../measures/annual-contract-value-usd.md)
- [Total Contract Value USD](../measures/total-contract-value-usd.md)

## Related Relationships
- [Booking Occurs On Date](../relationships/booking-occurs-on-date.md)
- [Customer Places Booking](../relationships/customer-places-booking.md)
- [Product Appears In Booking](../relationships/product-appears-in-booking.md)
- [Partner Participates In Booking](../relationships/partner-participates-in-booking.md)
- [Geography Classifies Booking](../relationships/geography-classifies-booking.md)
- [Sales Representative Owns Booking](../relationships/sales-representative-owns-booking.md)
- [Contract Classifies Booking](../relationships/contract-classifies-booking.md)
