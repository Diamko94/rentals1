# State Transitions

## Unit

%%Управление статусами: Доступен, В резерве, В аренде, В ремонте, Перемещение.

- Available → Reserved (when Order status is Draft)
- Reserved → Rented (when Order status is Active)
- Reserved → Available (if Order status is Cancelled)
- Rented → Available (if corresponding Line-item has no RepairTicket)
- Rented → Repair (if corresponding Line-item has RepairTicket)
- Available → Moving (if unit transpored between Warehouses)
- Moving → Available (Unit default state)

## Order

- Draft → Active (after manual confirmation)
- Draft → Cancelled (manual cancellation or expiration)
- Active → PartiallyClosed (if at least one Unit status is Repair and all other Units statuses are Available)
- Active → Closed (only if all Units have status Available)
