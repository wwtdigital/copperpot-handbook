---
title: INC-2025-06 Loyalty points credited twice at two pilot stores
opened: 2025-06-24T11:05:00-05:00
resolved: 2025-06-25T16:30:00-05:00
severity: 3
owner: payments lead
---
# INC-2025-06: Loyalty points credited twice at two pilot stores

| | |
|---|---|
| Opened | 2025-06-24 11:05 |
| Resolved | 2025-06-25 16:30 |
| Duration | 29 h 25 min |
| Severity | 3 |
| Affected | 2 pilot stores, 41 guests |
| Owner | payments lead |

## Timeline

- 11:05 A franchisee reports guests at store 118 redeeming more points than their orders earned.
- 11:40 The payments lead pulls the ledger for 3 guests: each has two credits for one order, 1,500 ms apart.
- 13:20 The store-side credit path is confirmed as the source: the retrier re-posts a credit when the first attempt timed out after it had already committed.
- 15:00 Store 118 and store 121 had the slow ledger calls; the other 4 pilot stores show no duplicates.
- 16:10 Decision: no code change under incident. Duplicate credits are reversed by adjustment entries from the order history.
- 2025-06-25 16:30 41 guests adjusted, balances reconciled against orders. Resolved.

## Cause

The credit retrier treats a timeout as a failure and re-posts, but the ledger call had already committed before the timeout fired. ADR-002 accepted this risk for the pilot and deferred idempotent writes to the regional rollout.

## Follow-up

- Idempotency key on ledger credits, persisted ledger (payments lead): open, scheduled with the regional rollout work.
- Reconciliation report comparing credits to paid orders, weekly (data lead): done 2025-07-14.

## Notes

- Tighten cancelled loyalty credit on checkout: agreed in the retro.
- Backfill expired modifier: revisit before the regional rollout.
- Validate duplicate store for pickup: owner is the delivery manager.
- Handle oversized cart line for franchisees: see the runbook.
- Validate partial menu item on reorder: agreed in the retro.
- Log late kitchen ticket: agreed in the retro.
- Guard regional promo: see the runbook.
- Tighten oversized order on checkout: see the runbook.
- Normalise oversized delivery window in the queue: holds since the standard went in.
