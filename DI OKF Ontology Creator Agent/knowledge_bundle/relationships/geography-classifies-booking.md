---
title: Geography Classifies Booking
concept_type: relationship
source_entity: Geography Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.geography_key -> dim_geography.geography_key
status: generated
---

# Geography Classifies Booking

## Source Entity

- [Geography Dimension](../entities/geography-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship classifies booking transactions by geography, supporting reporting by region, theater, and country.
