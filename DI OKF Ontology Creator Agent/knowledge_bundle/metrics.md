---
title: Metrics Overview
bundle: Cisco Bookings OKF Knowledge Bundle
status: generated
---

# Metrics Overview

## Core Business Measures

| Measure | Definition | Aggregation | Related Entity |
| --- | --- | --- | --- |
| [Quantity Sold](measures/quantity-sold.md) | Number of units, licenses, or items booked on the order line. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Unit List Price USD](measures/unit-list-price-usd.md) | Standard list price per unit in U.S. dollars before discounts. | Average or derived analytic use preferred; simple sum only with caution | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Discount Percentage](measures/discount-percentage.md) | Percentage discount applied relative to list price. | Average or weighted average preferred | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Booking Amount USD](measures/booking-amount-usd.md) | Net booked transaction amount in U.S. dollars. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Annual Contract Value USD](measures/annual-contract-value-usd.md) | Annualized value of the contract or subscription associated with the booking in U.S. dollars. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Total Contract Value USD](measures/total-contract-value-usd.md) | Total value of the contract associated with the booking in U.S. dollars over the full contract term. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |

## KPI Context from Business Process

- **Total Bookings**: headline demand metric based on the sum of booking amount.
- **Net-New vs Renewal mix**: analyzed using booking type and renewal indicator.
- **ACV / TCV**: key subscription-oriented contract value metrics.
- **Renewal capture rate**: business KPI referenced in process context but not directly modeled as a base measure.
- **Attach rate**: business KPI referenced in process context but not directly modeled as a base measure.
- **Product-family mix**: enabled by linking measures to [Product Dimension](entities/product-dimension.md).
- **Partner contribution**: enabled by linking measures to [Partner Dimension](entities/partner-dimension.md).

## Validation Notes

- Non-additive metric caution applies to [Discount Percentage](measures/discount-percentage.md).
- Governance caution applies to [Unit List Price USD](measures/unit-list-price-usd.md).
- ACV applicability may vary by offer type; hardware is noted as typically not ACV-applicable in the business process context.
