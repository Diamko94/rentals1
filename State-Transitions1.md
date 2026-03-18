# State Transitions

## Line-item

- Reserved → InUse (on Order activation)
- InUse → Returned (if no active Repair ticked)
- Rented → Repair (if active Repair ticked)
- Repair → Returned (if repair resolved and business process requires completion)

## Order

- Order → Active (after manual confirmation)
- Order → Cancelled (after manual confirmation)
- Active → PartiallyClosed (partial return)
- Active → PartiallyClosed (if Unit has status Repair)
- PartiallyClosed → Closed (all units returned)
