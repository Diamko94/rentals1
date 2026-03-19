flowchart TD

    %% Бронироваие
    A(Draft) -->|Order get Active| B[Reservation created]
    B --> C(Items Get Status Reserved)

    %% Выдача
    C --> G[Client Arrived]
    G --> H[Status Rented]
    C --> D[Client not arrived]
    D --> E[Reservation Cancelled]
    E --> Z[Items Become Available]
    H --> I[Manual Confirmation]
    I --> J(Rental get status activated)

    %% Возврат
    J --> K[Return Full/Partial]
    K -->|Good| M[Get status Available]
    K -->|Damaged| N[Repair]

    %% Расчет
    M --> O[Deposit Returned]
    N --> P[Deposit held]
