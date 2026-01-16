---
title: INC-2025-11 Guest API errors after the release promotion
opened: 2025-11-04T00:40:00-05:00
resolved: 2025-11-04T02:10:00-05:00
severity: 2
owner: store systems lead
---
# INC-2025-11: Guest API errors after the release promotion

| | |
|---|---|
| Opened | 2025-11-04 00:40 |
| Resolved | 2025-11-04 02:10 |
| Duration | 1 h 30 min |
| Severity | 2 |
| Affected | all stores in the first region, 1 h 30 min, overnight (low order volume) |
| Owner | store systems lead |

## Timeline

- 00:10 Store Systems promotes the release tag to the first region.
- 00:40 The guest API in the region returns errors on order placement; the mobile app shows a retry screen. Alert fires on the error rate.
- 00:55 The release carries a schema migration that renamed a column the order notes query still reads under the old name on one code path.
- 01:10 No rollback script ships with the migration, so the tag cannot be rolled back without losing the rename.
- 01:35 Roll forward: a one-line fix on a hotfix branch, reviewed by the on-call engineer, tagged as a patch.
- 02:10 The patch tag is promoted to the region. Error rate returns to baseline. Resolved.

## Cause

A migration renamed a column and one read path was missed in review. With no rollback script the only path was forward. The database rollback scripts standard in the wiki requires one per migration; the release went out without it.

## Follow-up

- Rollback script for the migration, written after the fact and tested against a copy (store systems lead): done 2025-12-02.
- Release checklist asks for the rollback script before promotion (store systems lead): done 2025-11-20.
- Carry the database rollback standard into the handbook (commerce delivery manager): open.

## Notes

- Relax expired order for pickup: holds since the standard went in.
- Backfill duplicate kitchen ticket: holds since the standard went in.
- Retry duplicate pickup slot: holds since the standard went in.
- Backfill stale delivery window per store: owner is the delivery manager.
- Backfill oversized ticket on reorder: owner is the delivery manager.
- Expose regional modifier: holds since the standard went in.
- Rename empty store: see the runbook.
- Expose empty cart line: agreed in the retro.
- Retry duplicate cart line: owner is the delivery manager.
- Expose duplicate order on checkout: see the runbook.
