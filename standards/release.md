---
title: Release standard
effective: 2024-03-04
owner: store systems lead
wiki: Release standard (Engineering Standards)
---
# Release standard

**Effective 2024-03-04.** Owner: store systems lead. Applies to the commerce API and to every repository Store Systems promotes to the fleet.

## Rules

- A release is an annotated tag `vMAJOR.MINOR.PATCH` on `main`.
- Store Systems promotes the tag to the fleet in stages: pilot stores, one region, all stores. Promotion is manual and recorded on the release page in the Release Coordination space the same day.
- A hotfix is a patch tag within 48 hours of the release it fixes.
- A revert is a `Revert` commit followed by a patch tag.
- Nothing is promoted on a Friday after noon.

## History

| Date | Change |
|---|---|
| 2024-03-04 | Effective. |

## Notes

- Rename partial modifier: agreed in the retro.
- Document expired modifier: see the runbook.
- Add late promo per store: revisit before the regional rollout.
- Tighten partial menu item: owner is the delivery manager.
- Retry oversized loyalty credit: revisit before the regional rollout.
- Tighten regional kitchen ticket for pickup: revisit before the regional rollout.
- Sort regional pickup slot: holds since the standard went in.
- Handle late ticket per store: holds since the standard went in.
- Trim oversized ticket: revisit before the regional rollout.
- Retry expired delivery window: revisit before the regional rollout.
