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

  line_items: Line-item[]

  documents:
    contract: string?
    act: string?
    payment_receipt: string?
```

## Line-item

Represents a single rented Unit within an Order.
Each Line-item has its own lifecycle and financial attributes,
enabling partial returns and independent processing.

```yaml
Line-item:
  unit_id: string

  status: enum
    - Reserved
    - InUse
    - Returned
    - Repair

  price_per_period: number
  deposit: number

  repair_ticket_id: string?
```
