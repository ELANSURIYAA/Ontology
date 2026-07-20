---
title: Sales Transactions
concept_type: domain
domain_name: Sales Transactions
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
related_relationships:
  - Booking Occurs On Date
  - Customer Places Booking
  - Product Appears In Booking
  - Partner Participates In Booking
  - Geography Classifies Booking
  - Sales Representative Owns Booking
  - Contract Classifies Booking
---

# Sales Transactions

## Description
Booking transaction domain capturing order-line booking events and measurable sales outcomes.

## Business Purpose
This domain supports analysis of accepted customer orders recognized as bookings. The business process confirms that bookings are recorded when Cisco accepts a valid order with committed value, making this domain the primary source for demand analytics.

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
