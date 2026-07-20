---
title: Customer Places Booking
concept_type: relationship
source_entity: Customer Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.customer_key -> dim_customer.customer_key
status: generated
---

# Customer Places Booking

## Source Entity

- [Customer Dimension](../entities/customer-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship links a booking transaction to the customer account associated with the order. It supports customer, segment, industry, and account-tier analysis of bookings.
