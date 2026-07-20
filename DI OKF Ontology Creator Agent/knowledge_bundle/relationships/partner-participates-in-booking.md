---
title: Partner Participates In Booking
concept_type: relationship
source_entity: Partner Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.partner_key -> dim_partner.partner_key
status: generated
---

# Partner Participates In Booking

## Source Entity

- [Partner Dimension](../entities/partner-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship associates a booking transaction with the partner involved in the deal, enabling channel, partner-tier, and route-to-market performance analysis.
