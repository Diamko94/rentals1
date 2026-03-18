# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (on rental start)
- Reserved → Available (if Order cancelled)
- InUse → Available (if Line-item has no active Repair ticket)
- InUse → Repair (if Line-item has active Repair ticket)

## Line-item

- Reserved → Rented (on Order activation)
- Rented → Returnet (if no active Repair ticked)
- Rented → Repair (if active Repair ticked)
- Repair → Returned (if repair resolved and business process requires completion)

## Order

- Order → Active (after manual confirmation)
- Order → Cancelled (after manual confirmation)
- Active → PartiallyClosed (partial return)
- Active → PartiallyClosed (if Unit has status Repair)
- PartiallyClosed → Closed (all units returned)
