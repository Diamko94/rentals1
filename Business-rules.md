# Business Rules

## Order

- Order default status is Draft
- Order changes status to Active only manually
- Order can be cancelled manually
- Order can be created only if:
  - Unit status == Available
  - No overlapping reservations or active Orders are allowed for the same Unit within the same time period
- Order blocks Units availability for other reservations and rentals
- Expiration applies only to Orders that are not Active within 24 hours since Order was created

## Order Activation

- On activation:
  - all associated Units change status from Reserved to InUse

## Order Cancellation

- On cancellation:
   - all associated Units change status from Reserved to Available

## Line-item Independence

- Each Line-item has its own lifecycle independent of other Line-items
- Status transitions of one Line-item do not affect others
- Financial calculations are performed per Line-item

## Deposit Logic

- Deposit is assigned per Line-item
- Deposit is calculated per Line-item

- Deposit is refunded only if:
  - Line-item status is Returned
  - no active Repairticket exists

- Deposit is held if:
  - Line-item is in Repair state
  - repair ticket is active

- Deposit refund is processed per Line-item independently

## Partial Closure

- In case of partial Order return, deposit is refunded only for Line-items status Returned
- Order status changes to PartiallyClosed if:
  - at least one Line-item status is Returned
  - at least one Line-item status is Repair

## Repairticket

- Repairticket can be issued per each Line-item
- Each Repairticket has its own lifecycle independent of other Repairtickets
- Repairticket can be issued only manually
- Repairticket can be resolved only manualy
- Each Issued Repairticket blocks the Deposit per corrispoding Line-item.

## Restrictions

- Order cannot be Closed if any Line-item status is not Returned
- Unit cannot be used in multiple active Orders simultaneously
- Deposit cannot be refunded if Repairticket status is Active
