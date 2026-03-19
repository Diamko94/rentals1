# Business Rules

## Order

- Order default status is Draft
- Order changes status to Active only manually
- Order with status Draft can be cancelled manually
- Order can be created only if:
  - Unit status == Available
  - No overlapping reservations or active Orders are allowed for the same Unit within the same time period
- Order blocks Units availability for other Orders
- Expiration applies only to Orders that are not Active within 24 hours since Order was created
- Expired Draft Order transitions to Cancelled automatically, and all associated Units change from Reserved to Available.
- PartiallyClosed is a final Order state.
- Cancelled is a final Order state.


## Order Activation

- On activation:
  - all associated Units change status from Reserved to Rented

## Order Cancellation

- On cancellation:
   - all associated Units change status from Reserved to Available

## Line-item Independence

- Financial calculations are performed per Line-item
- Each Line-item might have one active Repair_ticked corresponding to Unit

## Unit

- Unit default status is Available
- Status transitions of one Unit do not affect others
- Repair is a final Unit state.


## Deposit Logic

- Deposit is assigned per Line-item
- Deposit is calculated per Line-item

- Deposit is refunded only if:
  - Unit status is Available
  - no active Repair_ticket exists

- Deposit is held if:
  - Unit status is Repair
  - Repair_ticket is active

- Deposit refund is processed per Line-item independently

## Partial Closure

- In case of PartiallyClosed Order, deposit is refunded only for Units with status Available
Order changes to PartiallyClosed if:
- at least one Unit status is Repair
- all other Unit statuses are Available

## Repair_ticket

- Repair_ticket is created for a Line-item that references the damaged Unit.
- Each Repair_ticket has its own lifecycle independent of other Repair_tickets
- Repair_ticket can be issued only manually 
- Repair_ticket can be resolved only manually
- Each issued Repair_ticket held the Deposit per corrisponding Line-item.

## Restrictions

- Unit cannot be used in multiple active Orders simultaneously
- Deposit cannot be refunded if Repair_ticket status is Active
