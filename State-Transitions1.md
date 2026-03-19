# State Transitions

## Unit

- Available → Reserved (when Order status is Draft)
- Reserved → InUse (when Order status is Active)
- Reserved → Available (if Order status is cancelled)
- InUse → Available (if corresponding Line-item status is Returned)
- InUse → Repair (if corresponding Line-item status is Repair)

## Line-item

- Reserved → InUse (if Order status active)
- InUse → Returned (if no active Repair ticket)
- InUse → Repair (if Repairticket is active)

## Order

- Draft → Active (after manual confirmation)
- Draft → Cancelled (manual cancellation or expiration)
- Active → PartiallyClosed (if at least one Line-item status is Repair)
- Active → Closed (only if all Line-items statuses are Returned and all Units in Order have status Available)
