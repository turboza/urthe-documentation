# Urthe Offline Flow

**POS** - Storehub

## Payment channels
- Credit card (min: 500, charge 3%)
- Debit card
- QR Promptpay
- Transfer
- Cash

```mermaid
sequenceDiagram
    actor human
    participant Google Sheets
    participant POS Storehub
    participant POS Shipnity
    participant Google Colab
    participant Warehouse
    actor courier
    participant Store

    autonumber

    human->>Google Sheets: Add product to each branch
    human->>POS Storehub: Add product to warehouse
    human->>POS Storehub: Export daily orders as CSV
    human->>Google Colab: Summarize orders from CSV
    human->>Google Sheets: Update amount
    Note right of Google Sheets: Reconcile product amount
    Note right of Google Sheets: if not match: mark amount in Google Sheets
    human->>Warehouse: Prepare products in Warehouse
    courier->>Warehouse: pickup products
    courier->>Store: deviler products
    Note right of POS Storehub: Duplicate orders from Storehub to Shipnity
```