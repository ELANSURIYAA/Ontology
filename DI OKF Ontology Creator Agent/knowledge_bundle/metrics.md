---
title: Metrics Navigation
concept_type: navigation
bundle_name: Cisco Bookings OKF Knowledge Bundle
status: generated
---

# Metrics

## Key Business Metrics

| Measure | Definition | Aggregation | Related Entity | Related Domain |
| --- | --- | --- | --- | --- |
| [Booking Amount USD](measures/booking-amount-usd.md) | Net booked transaction amount in U.S. dollars. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |
| [Annual Contract Value USD](measures/annual-contract-value-usd.md) | Annualized value of the contract or subscription associated with the booking. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |
| [Total Contract Value USD](measures/total-contract-value-usd.md) | Total contract value over the full term. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |
| [Quantity Sold](measures/quantity-sold.md) | Number of units, licenses, or items booked on the order line. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |
| [Unit List Price USD](measures/unit-list-price-usd.md) | Standard list price per unit before discounts. | Average or governed analytic use preferred | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |
| [Discount Percentage](measures/discount-percentage.md) | Percentage discount applied relative to list price. | Average or weighted average preferred | [Booking Transaction Fact](entities/booking-transaction-fact.md) | [Sales Transactions](domains/sales-transactions.md) |

## KPI Alignment from Business Process

| KPI | Semantic Alignment |
| --- | --- |
| Total Bookings | Governed primarily by [Booking Amount USD](measures/booking-amount-usd.md). |
| Net-New vs Renewal mix | Derived from [Booking Type](glossary/booking-type.md) and [Renewal Indicator](glossary/renewal-indicator.md). |
| ACV / TCV | Governed by [Annual Contract Value USD](measures/annual-contract-value-usd.md) and [Total Contract Value USD](measures/total-contract-value-usd.md). |
| Renewal capture rate | Business KPI referenced by the process, but not explicitly modeled as a stored measure in the source semantic model. |
| Attach rate | Business KPI referenced by the process, but not explicitly modeled as a stored measure in the source semantic model. |
| Product-family mix | Supported analytically through [Product Family](glossary/product-family.md) and [Booking Amount USD](measures/booking-amount-usd.md). |
| Partner contribution | Supported analytically through [Route to Market](glossary/route-to-market.md), [Partner Dimension](entities/partner-dimension.md), and [Booking Amount USD](measures/booking-amount-usd.md). |

## Metric Governance Warnings

- [Discount Percentage](measures/discount-percentage.md) is non-additive and should be averaged or weighted according to governance rules.
- [Unit List Price USD](measures/unit-list-price-usd.md) should not be blindly summed without an approved business use case.
- ACV applicability differs for hardware versus subscription and SaaS offers per the business process narrative.
