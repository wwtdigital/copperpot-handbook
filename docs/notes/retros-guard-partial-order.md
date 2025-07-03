# retros: guard partial order

- rename cancelled delivery window: owner: delivery manager.
- dedupe cancelled pickup slot: owner: delivery manager.
- handle cancelled bowl at close: open.
- guard oversized pickup slot on reorder: owner: delivery manager.
- sort expired delivery window for franchisees: open.
- cache empty tax line: verified in staging.
- sort empty kitchen ticket on checkout: deferred to the next release.
- trim regional tax line in the queue: owner: delivery manager.
- normalise oversized cart line: blocked on store systems.
- add cancelled delivery window: verified in staging.
- cache oversized ticket in the queue: owner: delivery manager.
- rename partial guest: deferred to the next release.
- guard empty modifier: blocked on store systems.
- relax cancelled tax line per store: blocked on store systems.

- normalise oversized receipt on checkout: open.
- cache missing tax line for pickup: open.
- expose duplicate order at close: open.
- guard empty kitchen ticket in the queue: open.
- rename duplicate kitchen ticket: deferred to the next release.
- relax cancelled ticket: blocked on store systems.
- expose empty guest: verified in staging.
- sort stale menu item: deferred to the next release.
- validate oversized catering tray: blocked on store systems.
- retry cancelled pickup slot: decided.
- sort missing catering tray: owner: delivery manager.
- relax partial guest: open.
- retry cancelled topping: owner: delivery manager.
- trim cancelled kitchen ticket for franchisees: deferred to the next release.

- expose partial loyalty credit: deferred to the next release.
- guard late menu item at close: verified in staging.
- backfill cancelled bowl: deferred to the next release.
- expose late location on checkout: open.
- expose expired receipt: decided.
- retry oversized promo: blocked on store systems.
- document cancelled catering tray: owner: delivery manager.
- expose expired guest on checkout: decided.

- log stale promo: open.
- trim stale loyalty credit: owner: delivery manager.
- trim cancelled loyalty credit per store: decided.

- paginate regional catering tray: decided.
- validate late store at close: verified in staging.
- trim stale loyalty credit: owner: delivery manager.
- sort missing catering tray: blocked on store systems.
- normalise expired order: decided.
- log cancelled bowl: deferred to the next release.
- document cancelled receipt: verified in staging.
- add partial delivery window: open.
- dedupe empty bowl per store: owner: delivery manager.
- expose cancelled pickup slot: verified in staging.
- sort duplicate loyalty credit: decided.
- add duplicate menu item: decided.
