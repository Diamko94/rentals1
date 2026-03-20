```mermaid
flowchart TD
    
    %%Юниты на складе
    A1(Юниты расположены на конкретном складе) --> A2[Юниты получают статус Доступен]
  
    %% Звонок
    B1(Поступает звонок Binotel) --> B2[в CRM всплывает карточка Лида или Контрагента]

    %% AI-обработка
    B2 --> B3[Система скачивает аудио]
    B3 --> B4[Whisper переводит в текст]
    B4 --> B5[GPT-4o делает саммари]

    %% Создание Order Draft
    B5 --> B6[AI извлекает из текста название инструмента Items и дату]
    B6 --> B7[AI создает Draft Order]

    %% Сотрудник
    С1[Менеджер открывает Draft order] --> C2[Проверка саммери AI (Соответствие Инструмента, Доступности, Даты, Данных клиента)]
    C2 -->|Если все Items из Draft Order на складе имеют статус Available| D1[нажимает «Создать резерв»]
    C2 -->|Если не все Items из Draft Order на складе имеют статус Available| D2[Отправляет сообщение клиенту о недоступности определеных Items в указанные Date]
    D1 --> D3[Нажимает «Отправить Viber»]
     
    A5[Manager selected Units under Client Request, if they available]
    A5 --> A(Draft Order created)
    D1 --> B(Units status change to Reserved)

    %% Выдача
    B --> |Client arrived to Warehouse| I[Manual Confirmation]
    B --> |Client not show up| E[Reservation expired or cancelled manually]
    E --> F[Order status changes to Cancelled]
    I --> J[Order status changes to Active]
    F --> C[Units change status to Available]
    J --> X[Units status change to Rented]

    %% Возврат
    X --> |Units are in use| K[Client returned units]
    K --> L{Manual units verification}
    L --> M[All Units are Fine] 
    M --> N[All Units status change to Available]
    L -->|At least one Unit is damaged| P[Damaged Units change status to Repair]
    P --> R[RepairTicket created for corresponding Line-items]
    L --> T[Not damaged Units change status to Available]

    %% Расчет
    N --> Q[All Deposits Released]
    Q --> V[Order changes status to Closed]
    R --> S[Deposit held for Line-item with Unit status Repair]
    T --> U[Deposit returned for Line-item with Unit status Available]
    S --> W[Order changes status to PartiallyClosed]
    U --> W[Order changes status to PartiallyClosed]
```
