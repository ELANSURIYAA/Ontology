---
title: Contract Classifies Booking
concept_type: relationship
source_entity: Contract Dimension
target_entity: Booking Transaction Fact
relationship_type: Dimensional Foreign Key
cardinality: One-to-Many
technical_mapping: fact_bookings.contract_key -> dim_contract.contract_key
status: generated
---

# Contract Classifies Booking

## Source Entity

- [Contract Dimension](../entities/contract-dimension.md)

## Target Entity

- [Booking Transaction Fact](../entities/booking-transaction-fact.md)

## Relationship Type

Dimensional Foreign Key

## Cardinality

One-to-Many

## Business Description

This relationship associates a booking transaction with the related contract context, supporting term, coverage, and renewal-oriented analysis.
