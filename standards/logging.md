---
title: Logging standard
effective: 2024-11-18
owner: platform security lead
wiki: Logging standard (Engineering Standards)
---
# Logging standard

**Effective 2024-11-18.** Owner: platform security lead. Applies to every service that handles guest or payment data.

## Rules

1. Logs are structured JSON with a `service`, `version` and `requestId` field.
2. No guest personal data in logs: no names, phone numbers, email addresses, card numbers or addresses. Log identifiers (`guestId`, `orderId`) instead.
3. Anything that must show a card or account value shows the last four only, through `maskUntilLast4`.
4. Payment and ledger operations log at INFO with identifiers and amounts, never with the guest's contact details.

## Checking

A reviewer who sees a template string with a guest field in it asks for the identifier instead. There is no automated check yet.

## History

| Date | Change |
|---|---|
| 2024-11-18 | Effective, with the loyalty and payments work. |

## Notes

- Log late kitchen ticket: owner is the delivery manager.
- Trim duplicate guest: holds since the standard went in.
- Trim missing guest on reorder: holds since the standard went in.
- Normalise oversized kitchen ticket on reorder: owner is the delivery manager.
- Dedupe cancelled cart line on checkout: revisit before the regional rollout.
- Rename duplicate pickup slot: agreed in the retro.
- Normalise duplicate catering tray: holds since the standard went in.
- Paginate expired store: agreed in the retro.
