---
title: Semantic Summary
bundle: Cisco Bookings OKF Knowledge Bundle
status: generated
---

# Semantic Summary

## Business Context

Cisco Quote-to-Booking is the front portion of the Order-to-Cash cycle. It begins when an opportunity is qualified and ends when a valid customer order is accepted and recognized as a booking. The semantic model captures booking events and descriptive context for analysis of demand, channel performance, product mix, contracts, renewals, customer segmentation, and time trends.

## Domains

1. [Sales Transactions](domains/sales-transactions.md)
2. [Customer Management](domains/customer-management.md)
3. [Product Management](domains/product-management.md)
4. [Partner Management](domains/partner-management.md)
5. [Geography](domains/geography.md)
6. [Sales Organization](domains/sales-organization.md)
7. [Contract Management](domains/contract-management.md)
8. [Time](domains/time.md)

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

## Validation Warnings

- Some business definitions are inferred because native database comments are unavailable.
- Source tables are empty, so instance-level validation is not possible.
- `dim_contract` and `dim_geography` do not expose explicit natural business identifiers.
- `discount_pct` and `unit_list_price_usd` require aggregation caution.
- `is_renewal` and `auto_renew_flag` require approved code-set documentation.

## Semantic Pattern

The model is a star schema with one central fact table, [Booking Transaction Fact](entities/booking-transaction-fact.md), surrounded by seven conformed dimensions. This enables governed slicing of bookings by customer, product, partner, geography, sales representative, contract, and date.
