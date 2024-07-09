---
title: Dependency updates standard
effective: 2024-06-03
owner: commerce delivery manager
wiki: none
---
# Dependency updates standard

**Effective 2024-06-03.** Owner: commerce delivery manager. Applies to every repository with a package manifest.

## Rules

1. Dependency update automation runs weekly against the default branch and opens one change per dependency, at most five open at a time.
2. Patch and minor updates are merged within ten working days of opening, once the pipeline is green.
3. A major update needs a ticket on the CPB board naming what changes for callers, and a line in the changelog.
4. A security advisory against a direct dependency is picked up within two working days, ahead of the weekly run.
5. The lockfile is committed and the pipeline installs from it.

## Why

Two outages in spring 2024 traced to dependencies three majors behind. Small, frequent updates are cheaper than one large one.

## History

| Date | Change |
|---|---|
| 2024-06-03 | Effective. |

## Notes

- Rename stale topping: agreed in the retro.
- Paginate expired tax line: agreed in the retro.
- Cache expired delivery window: revisit before the regional rollout.
- Trim oversized delivery window for franchisees: revisit before the regional rollout.
