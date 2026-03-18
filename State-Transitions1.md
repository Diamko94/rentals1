# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (on rental start)
- Reserved → Available (if Order cancelled)
- InUse → Available (if Line-item status is Returned)
- InUse → Repair (if Line-item status is Repair)

## Line-item

- Reserved → InUse (on Order activation)
- InUse → Returned (if no active Repair ticket)
- InUse → Repair (if active Repair ticket)

## Order

- Draft → Active (after manual confirmation)
- Draft → Cancelled (manual cancellation or expiration)
- Active → PartiallyClosed (if at least one Line-item is Returned or Repair and at least one is InUse)
- Active → Closed (only if all Line-items are Returned and all Units in Order have status Available)

## Notes

- PartiallyClosed is a final automatic Order state
