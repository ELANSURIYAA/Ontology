---
title: Booking Occurs On Date
concept_type: relationship
source_entity: Date Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.date_key -> dim_date.date_key
status: generated
---

# Booking Occurs On Date

## Source Entity

- [Date Dimension](../entities/date-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship links each booking transaction to the date on which it occurred, enabling calendar and fiscal reporting, trend analysis, and period-based aggregation.
