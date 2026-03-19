```mermaid
flowchart TD

    %% Бронироваие
    A(Draft Order created) --> B(Units status change to Reserved)

    %% Выдача
    B --> G[Client arrived to Warehouse]
    G --> I[Manual Confirmation]
    B --> D[Client not arrived to Warehouse]
    D --> E[Manual Confirmation]
    E --> F[Order status changes to Cancelled]
    I --> J(Order status changes to Active)

    %% Возврат
    J --> X[Units status change to Rented]
    X --> K[Cleint returned units]
    K --> L{Manual units verification}
    L --> M[All Units are Fine] 
    M --> N[All Units status change to Available]
    L --> O[At least one Unit is damaged]
    O --> P[Damaged Units change status to Repair]
    P --> R[Each line-item with Unit status Repair created Repair_ticket]
    O --> T[Not damaged Units change status to Available]

    %% Расчет
    N --> Q[All Deposits Released]
    Q --> V[Order changes status to Closed]
    R --> S[Deposit held for Line-item with Unit status Repair]
    T --> U[Deposit returned for Line-item with Unit status Available]
    S --> W[Order changes status to PartiallyClosed]
    U --> W[Order changes status to PartiallyClosed]
```
