---
title: INC-2025-02 Menu sync stall at the pilot stores
opened: 2025-02-11T06:40:00-05:00
resolved: 2025-02-11T09:15:00-05:00
severity: 2
owner: store systems lead
---
# INC-2025-02: Menu sync stall at the pilot stores

| | |
|---|---|
| Opened | 2025-02-11 06:40 |
| Resolved | 2025-02-11 09:15 |
| Duration | 2 h 35 min |
| Severity | 2 |
| Affected | 6 pilot stores |
| Owner | store systems lead |

## Timeline

- 06:40 The opening manager at store 214 reports yesterday's menu on the kiosk. Two more stores report the same by 06:55.
- 07:05 Store systems on call confirms the menu sync job last succeeded at 02:10 and has failed every run since with an authentication error.
- 07:30 The service token the sync job uses is found to have expired at 02:00; it was issued for one year in February 2024.
- 08:20 A new token is issued and set on the job. The run at 08:25 succeeds for 4 stores and fails for 2 with a stale cache.
- 09:05 The cache on the 2 stores is cleared by hand. 09:15 all 6 stores show today's menu.

## Cause

The menu sync job authenticated with a service token issued for one year and nothing recorded its expiry. The job failed quietly: its failures went to a log nobody watched and no alert was attached.

## Follow-up

- Alert on two consecutive failed sync runs (store systems lead): done 2025-02-14.
- Token expiry dates recorded on the runbook page (store systems lead): done 2025-02-18.
- Replace the long-lived token with a short-lived credential (platform security lead): open.

## Notes

- Normalise empty delivery window: agreed in the retro.
- Add stale store on checkout: owner is the delivery manager.
- Tighten late cart line: see the runbook.
- Document empty guest: owner is the delivery manager.
- Paginate empty location at close: see the runbook.
- Normalise expired loyalty credit: owner is the delivery manager.
- Backfill oversized promo: owner is the delivery manager.
- Tighten regional delivery window on checkout: agreed in the retro.
- Sort duplicate location for pickup: owner is the delivery manager.
- Cache cancelled store on reorder: see the runbook.
