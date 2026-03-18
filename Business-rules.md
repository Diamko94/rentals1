# Business Rules

## Reservation

- Reservation does not create financial obligations
- Unit status is set to Reserved
Reservation can be created only if:
- unit status != Available
- no overlapping reservations exist

## Reservation Conditions

Reservation can be created only if:
- unit status != Available
- no overlapping reservations exist

## Activation

- Rental becomes Active only after manual confirmation

## Line Item Independence

- Each line item is processed independently
- Partial return is supported

## Deposit Calculation

- Deposit is calculated per line item

## Deposit Logic

- Deposit is assigned per Line Item
- Deposit is returned only if unit is returned without damage (repair ticked not created)
- Deposit is held if unit is damaged and sent to repair (repair ticked created)
- Deposit is partially returned in case of partial return

## Partial Closure

- Rental can be partially closed if not all items are returned

## Restrictions

- Rental cannot start without manual confirmation
