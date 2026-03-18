# Business Rules

## Order

- Order created manually
  - Line-items status is set to Reserved
- Order can be created only if:
  - Line-item status == Available
  - no overlapping ordering exist for the same Line-units within the same time period
- Order can be cancelled manually
- Orded has expiration time (optional)
- Order blocks Line-items with status Reserved\
- Order blocks line-itms availability for other reservations and rentals
- Expired Order releases all line-items with status Reserved

## Activation

- Order get status Active only after manual confirmation

## Line-item Independence

- Each Line-item has its own lifecycle independent of other Line-items
- Status transitions of one Line-item do not affect others
- Financial calculations are performed per Line-item

## Deposit Calculation

- Deposit is calculated per Line-item

## Deposit Logic

- Deposit is assigned per Line-item
- Deposit is returned only if:
  - Line-item is in Returned state
  - no active repair ticket exists- Deposit is held if unit is damaged (Line-item got statys Repair and repair ticked created)
- Deposit is partially returned in case of partial Line-item return

## Partial Closure

- Order can be partially closed if not all Line-items are returned

## Restrictions

- Order cannot start without manual confirmation
