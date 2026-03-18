# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (on rental start)
- Reserved → Available (if rental cancelled)
- InUse → Available (if returned OK)
- InUse → Repair (if damaged)

## Rental

- Draft → Active (after manual confirmation)
- Draft → Cancelled (after manual confirmation)
- Active → PartiallyClosed (partial return)
- Active → PartiallyClosed (if Unit has status Repair)
- PartiallyClosed → Closed (all items returned)
