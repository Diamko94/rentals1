# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (on rental start)
- Reserved → Available (if Order cancelled)
- InUse → Available (if Line-item has no active Repair ticket)
- InUse → Repair (if Line-item has active Repair ticket)

## Order

- Draft → Active (after manual confirmation)
- Draft → Cancelled (after manual confirmation)
- Active → PartiallyClosed (partial return)
- Active → PartiallyClosed (if Unit has status Repair)
- PartiallyClosed → Closed (all units returned)
