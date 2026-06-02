---
title: INC-2026-03 Order processing queue stalled during lunch
opened: 2026-03-10T12:10:00-05:00
resolved: 2026-03-10T13:05:00-05:00
severity: 1
owner: senior engineer (commerce)
---
# INC-2026-03: Order processing queue stalled during lunch

| | |
|---|---|
| Opened | 2026-03-10 12:10 |
| Resolved | 2026-03-10 13:05 |
| Duration | 55 min |
| Severity | 1 |
| Affected | all stores, kitchen tickets delayed up to 25 minutes |
| Owner | senior engineer (commerce) |

## Timeline

- 12:10 Kitchens across the fleet report tickets arriving late. The queue depth alert fires at 12:12.
- 12:20 The store API consumer is up but has processed nothing since 11:58. The head message is an order with a malformed note field.
- 12:35 The consumer throws on the message, is restarted by the platform, and picks up the same message again.
- 12:50 The message is moved aside by hand and the consumer drains the backlog.
- 13:05 Queue depth back to normal. Resolved.

## Cause

A kiosk build sent an order note as an object instead of a string. The consumer had no handling for a message it cannot parse and no dead-letter path, so one bad message stopped the queue for every store.

## Follow-up

- Dead-letter queue for messages the consumer cannot parse (store systems lead): open, retro action March 2026.
- Validate the note field at the guest and store API boundary (senior engineer): done 2026-03-13.
- Kiosk build rolled back by the vendor the same afternoon.

## Notes

- Retry missing tax line: revisit before the regional rollout.
- Tighten cancelled order in the queue: see the runbook.
- Paginate regional pickup slot in the queue: agreed in the retro.
- Guard late topping: revisit before the regional rollout.
- Handle stale store for pickup: holds since the standard went in.
- Validate missing catering tray per store: owner is the delivery manager.
- Validate partial menu item: revisit before the regional rollout.
- Retry regional menu item: see the runbook.
