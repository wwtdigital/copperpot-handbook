---
status: accepted
date: 2024-11-08
deciders: senior engineer (commerce), payments lead, commerce delivery manager
---
# ADR-002: Loyalty ledger in process for the pilot

## Context and Problem Statement

Six pilot stores start loyalty in December. The ledger needs to credit points on paid orders and answer a balance. Where does the ledger live for the pilot?

## Decision Drivers

- The pilot has to ship in four weeks.
- Balances for six stores are small; losing them is recoverable from order history.
- The regional rollout will need persistence and idempotent writes, whatever is chosen now.

## Considered Options

- In process, in-memory store, one instance
- A ledger table in the shared database
- A separate ledger service

## Decision Outcome

Chosen option: "In process, in-memory store", because it ships in the time available and the pilot can tolerate a lost balance. Credits are appended on paid orders by the order events consumer. Persistence and idempotent writes are deferred to the regional rollout. **Revisit before the regional rollout.**

### Consequences

- Good, because the pilot ships on time.
- Bad, because a restart loses pilot balances; accepted, balances are re-derived from orders.
- Bad, because a retried credit after a timeout may double count; accepted for the pilot, to be fixed with persistence.

## Pros and Cons of the Options

### In process, in-memory store

- Good, because no schema change and no new deploy unit.
- Bad, because it is not durable and not safe to retry.

### A ledger table in the shared database

- Good, because durable from day one.
- Bad, because the migration and its rollback script put the date at risk.

### A separate ledger service

- Good, because the money-like path gets its own boundary.
- Bad, because a new service for six stores is more than the team can run this quarter.
