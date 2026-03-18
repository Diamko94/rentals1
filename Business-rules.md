# Business Rules

## Order

- Order created manually
- Order blocked Line-units with status Reserved
- Orded has expiration time (optional)
- Expired Order releases all line-units with status Reserved
- Order can be cancelled manually
- Order blocks line-unit availability for other reservations and rentals
- Unit status is set to Reserved
- Order can be created only if:
    - Line-item status == Available
    - no overlapping ordering exist for the same Line-units within the same time period

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
- Deposit is returned only if Line-item is returned without damage (no status Repair for Line-item)
- Deposit is held if unit is damaged (Line-item got statys Repair and repair ticked created)
- Deposit is partially returned in case of partial Line-item return

## Partial Closure

- Order can be partially closed if not all Line-items are returned

## Restrictions

- Order cannot start without manual confirmation
