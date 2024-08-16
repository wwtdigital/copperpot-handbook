---
status: accepted
date: 2024-08-16
deciders: senior engineer (commerce), commerce delivery manager, store systems lead
---
# ADR-001: Split the API into guest and store applications

## Context and Problem Statement

One process serves the mobile app, the web storefront, the point of sale and the kitchen display. A kitchen display outage took guest ordering down with it twice in 2024. How do we keep a store-side failure from stopping guests ordering?

## Decision Drivers

- Guest ordering must stay up when a store-side consumer misbehaves.
- The team is five engineers; a second repository doubles the pipelines and releases to keep in step.
- The database schema is shared and nobody wants to split it this year.

## Considered Options

- Two applications in one repository, shared modules, one database
- Two repositories
- One application, stricter timeouts around the store-side routes

## Decision Outcome

Chosen option: "Two applications in one repository", because it separates the deploy units and the ports without a second repository or a data split. `guest-api` serves menu, cart and order placement; `store-api` serves statuses, the processing queue and order notes. Shared modules stay under `src/`. The combined local entrypoint stays for development.

### Consequences

- Good, because each application scales and restarts on its own.
- Good, because one pipeline and one release tag still cover both.
- Bad, because the shared database remains a single point of failure; a later ADR decides on separating the data.

## Pros and Cons of the Options

### Two applications in one repository

- Good, because the change is a week of work and no history moves.
- Bad, because the boundary is a convention, not a package.

### Two repositories

- Good, because the boundary is enforced by the host.
- Bad, because two pipelines, two release trains and two sets of standards to keep aligned.

### Stricter timeouts

- Good, because it is an afternoon.
- Bad, because the two outages were memory pressure, not slow calls; timeouts would not have helped.
