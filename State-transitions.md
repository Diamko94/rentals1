# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (on rental start)
- InUse → Available (if returned OK)
- InUse → Repair (if damaged)

## Rental

- Draft → Active (after manual confirmation)
- Active → PartiallyClosed (partial return)
- Active → PartiallyClosed (if unit is has status Repair)
- PartiallyClosed → Closed (all units returned and no units with status Repair)
