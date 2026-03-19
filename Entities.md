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

## Line-Item

Represents a single rented Unit within an Order.
Each Line-item has its own lifecycle and financial attributes,
enabling partial returns and independent processing.

```yaml
Line-item:
  unit_id: string

  unit_status: string

  price_per_period: number
  deposit: number

  repair_ticket_id: string?
```


## Unit

%%Управление статусами: Доступен, В резерве, В аренде, В ремонте, Перемещение.
%%Юнит (Unit): ID, Серийный номер, QR-код (nullable), Текущий склад, Статус, Wear_Level (0-100%), История аренд, Дата последнего ТО.

```yaml
Unit:
  id: string

  serial_number: string
  QR_code: string?
  warehouse_id: string

  unit_status: enum
    - Available
    - Reserved
    - Rented
    - Moving
    - Repair

  wear_level: number
  rental_history: RentalHistoryEntry[]
  last_maintenance_date: date?
  
  price: number
```
