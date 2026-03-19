```mermaid
flowchart TD

    %% Бронироваие
    A(Содается Резерв) -->|Manager actives Order| B[Reservation created]
    B --> C(Items Get Status Reserved)

    %% Выдача
    C --> G[Client arrived to Warehouse]
    G --> I[Manual Confirmation]
    C --> D[Client not arrived to Warehouse]
    D --> E[Manual Confirmation]
    E --> F[Order status is Cancelled]
    F --> Z[Units become Available]
    I --> J(Order status is Active)

    %% Возврат
    J -->|Cleint brings back units| K[Return Full/Partial]
    K -->|Fine| M[Get status Available]
    K -->|Damaged| N[Repair]

    %% Расчет
    M --> O[Deposit Returned]
    N --> P[Deposit held]
```
