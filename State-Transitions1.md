# State Transitions

## Unit

- Available → Reserved (on reservation creation)
- Reserved → InUse (when Order status is Active)
- Reserved → Available (if Order status is cancelled)
- InUse → Available (if corresponding Line-item status is Returned)
- InUse → Repair (if corresponding Line-item status is Repair)

## Line-item

- Reserved → InUse (if Order status active)
- InUse → Returned (if no active Repair ticket)
- InUse → Repair (if active Repair ticket)
- Repair → Returned  (if active Repair ticket resolved manualy)

## Order

- Draft → Active (after manual confirmation)
- Draft → Cancelled (manual cancellation or expiration)
- Active → PartiallyClosed (if at least one Line-item is Returned or Repair and at least one is InUse)
- Active → Closed (only if all Line-items are Returned and all Units in Order have status Available)
- PartiallyClosed → Closed (only if all Repair-tickets manualy resolved)

## Notes

- PartiallyClosed is a final automatic Order state and cannot transition to Closed within the rental module
