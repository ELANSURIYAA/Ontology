---
title: Product Appears In Booking
concept_type: relationship
source_entity: Product Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.product_key -> dim_product.product_key
status: generated
---

# Product Appears In Booking

## Source Entity

- [Product Dimension](../entities/product-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship associates each booking transaction with the product or offer being booked, supporting product-family mix, technology, and portfolio analysis.
