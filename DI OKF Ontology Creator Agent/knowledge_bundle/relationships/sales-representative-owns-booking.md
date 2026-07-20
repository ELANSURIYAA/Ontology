---
title: Sales Representative Owns Booking
concept_type: relationship
source_entity: Sales Representative Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.sales_rep_key -> dim_sales_rep.sales_rep_key
status: generated
---

# Sales Representative Owns Booking

## Source Entity

- [Sales Representative Dimension](../entities/sales-representative-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship assigns booking ownership to the responsible sales representative, enabling analysis by seller, role, and sales team.
