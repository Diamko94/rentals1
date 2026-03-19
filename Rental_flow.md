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
- Units status → Rented
- Each Line-item deposit is blocked 

## 3. Active Rental

- Units are Rented
- Each Unit is tracked via corrisponding Line-items

## 4. Return

### Full Return

All Units returned, no active RepairTicket extists → Order is Closed

### Order PartiallyClosed

If at least on Unit.status = Repair per Order:

- Units with status Repair → Line-items active RepairTicket
- Other Units status → Available
- Active Order → PartiallyClosed

## 5. Financial Settlement

- Deposit is calculated per Line-item
- Price is calculated per Line-item
- Unit is Available → Deposit released
- Line-item with active RepairTicket → Deposit held
