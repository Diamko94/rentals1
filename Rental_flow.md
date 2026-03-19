# Rental Flow

## 1. Reservation

A reservation is created via iFrame or Call Center manually.

- Order status → Draft
- Unit status → Reserved
- No financial transaction is created

## 2. Conversion to Rental

When the client arrives, with manually verification:

- Warehouse operator confirms issuance
- Order status → Active
- Units status → InUse
- Each Line-item deposit gets blocked 

## 3. Active Rental

- Units are in use
- Each Unit is tracked via corrisponding Line-items

## 4. Return

### Full Return

All Units returned, no active Repairticked extists → Order is Closed

### Partial Return

If at least on Unit.status = Repair per Order:

- Line-items with active Repairticked → Repair
- Other Units status → Returned
- Active Order → PartiallyClosed

## 5. Financial Settlement

- Deposit is calculated per Line-item
- Price is calculated per Line-item
- Unit is Returned → Deposit released
- Line-item with active Repairticket → Deposit held
