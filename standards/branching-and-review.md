---
title: Branching and review standard
effective: 2025-04-01
owner: commerce delivery manager
wiki: Branching and review standard (Engineering Standards)
---
# Branching and review standard

**Effective 2025-04-01.** Owner: commerce delivery manager. Applies to every digital platform repository. Agreed in the March 2025 retro.

## Branches

- One ticket per branch. The branch name carries the ticket key: `feature/CPB-123-short-slug` for a story, `bugfix/CPB-456-short-slug` for a defect.
- A draft nobody else needs yet may sit on `wip/<your-handle>/short-slug` until it has a ticket.
- Branches are deleted after merge.
- Nothing is pushed to `main` directly.

## Titles

Pull request titles follow the conventional form:

```text
feat(order): add order notes to the kitchen ticket (CPB-412)
fix(cart): round tax lines once (CPB-430)
```

Allowed types: feat, fix, chore, docs, refactor, test, perf, build, ci, revert.

## Size

Keep a change under 400 changed lines. Split anything bigger.

## Review

Every change is reviewed by someone other than the author before merge. Reviewers answer for: does it do what the ticket says, is it tested, does it touch payments or the ledger (if so, the payments lead reviews).

| Rule | Enforced by |
|---|---|
| Key in branch name | habit |
| Conventional title | habit; a lint is planned |
| Review before merge | habit; required reviews are not turned on |

## History

| Date | Change |
|---|---|
| 2025-04-01 | Effective. |

## Notes

- Retry duplicate tax line: agreed in the retro.
- Rename late kitchen ticket: agreed in the retro.
- Cache regional pickup slot in the queue: owner is the delivery manager.
