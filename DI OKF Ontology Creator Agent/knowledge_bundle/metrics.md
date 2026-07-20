---
title: Metrics and Validation
concept_type: navigation
status: generated
---

# Metrics and Validation

## Business Measures

| Measure | Definition | Aggregation | Related Entity |
| --- | --- | --- | --- |
| [Quantity Sold](measures/quantity-sold.md) | Number of units, licenses, or items booked on the order line. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Unit List Price USD](measures/unit-list-price-usd.md) | Standard list price per unit in U.S. dollars before discounts. | Average or derived analytic use preferred; simple sum only with caution | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Discount Percentage](measures/discount-percentage.md) | Percentage discount applied relative to list price. | Average or weighted average preferred | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Booking Amount USD](measures/booking-amount-usd.md) | Net booked transaction amount in U.S. dollars. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Annual Contract Value USD](measures/annual-contract-value-usd.md) | Annualized value of the contract or subscription associated with the booking in U.S. dollars. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |
| [Total Contract Value USD](measures/total-contract-value-usd.md) | Total value of the contract associated with the booking in U.S. dollars over the full contract term. | Sum | [Booking Transaction Fact](entities/booking-transaction-fact.md) |

## KPI Context from Business Process

- Total Bookings: headline demand metric based on booked value in a period.
- Net-New vs Renewal mix: based on booking type and renewal indicator.
- ACV / TCV: annual and full contract value for subscriptions.
- Renewal capture rate: share of expiring contracts renewed on time.
- Attach rate: share of hardware deals that attach a service or subscription.
- Product-family mix: distribution of bookings by family.
- Partner contribution: bookings by route-to-market and partner.

## Validation Warnings

| Warning Type | Severity | Details |
| --- | --- | --- |
| Inferred semantic definitions | Medium | Several business definitions rely on glossary inference because native database comments are not present. |
| Empty source tables | High | Instance-level validation for code values, data quality, and measure distributions cannot be performed. |
| Natural key gaps | Medium | `dim_contract` and `dim_geography` do not expose explicit natural business identifiers in supplied metadata. |
| Non-additive metric caution | Medium | `discount_pct` and `unit_list_price_usd` should not be blindly summed in downstream analytics. |
| Coded indicator ambiguity | Medium | `is_renewal` and `auto_renew_flag` require business-approved code-set documentation. |

## Bundle Validation Check

- Missing concept documents: none in generated set.
- Missing YAML frontmatter: none in generated set.
- Broken semantic links: none expected within generated bundle structure.
- Duplicate concept documents: none detected.
- Missing references: some source semantics remain inferred where explicit business documentation was not available.
