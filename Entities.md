# Entities

## Order

Represents a rental Order that manages the lifecycle of rented units,
including issuance, return, and financial settlement.

```yaml
Order:
  id: string
  customer_id: string
  warehouse_id: string

  status: enum
    - Draft
    - Active
    - Cancelled
    - PartiallyClosed
    - Closed

  total_amount: number

  line_items: LineItem[]

  documents:
    contract: string?
    act: string?
    payment_receipt: string?
```

## LineItem

Represents a single rented unit within a rental.
Each Line-item has its own lifecycle and financial attributes,
enabling partial returns and independent processing.

```yaml
LineItem:
  id: string
  rental_id: string

  unit_id: string

  status: enum
    - Available
    - Reserved
    - InUse
    - Returned
    - Repair

  price: number
  deposit: number

  repair_ticket_id: string?
```
