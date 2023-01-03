# Urthe Online Flow

**Line, Facebook, Instagram** - ~50 orders/day
**Shopee** - ~200 orders daily
**Lazada** - ~20-30 orders daily

## Add product
```mermaid
sequenceDiagram
    participant Warehouse
    participant Shipnity

    autonumber

    Warehouse->>Shipnity: Add products
```

## Line, Facebook, Instagram

### Create order process

```mermaid
sequenceDiagram
    actor office
    participant Google Sheets
    actor accounting
    participant Shipnity
    participant Thai Post
    participant Warehouse
    actor courier
    actor customer

    autonumber

    office->>Google Sheets: Add order to Google Sheets
    accounting->>Google Sheets: Reconcile deposit amount from Google Sheets
    Note left of accounting: Change background color for status flag
    office->>Shipnity: Add order to Shipnity (1 qty per order)
    office->>Shipnity: Print order from Shipnity (1 qty per row)
    office->>Thai Post: Input shipping detail for attachment
    office->>Warehouse: Pack
    office->>Thai Post: Print tracking number and attach
    office->>Shipnity: Update tracking number in Shipnity
    courier->>Warehouse: Pickup orders
    Note over courier: pickup orders at 3pm daily
    courier->>customer: Deliver orders
```

## Shopee, Lazada

### Create order process

```mermaid
sequenceDiagram
    actor office
    participant Google Sheets
    participant Shipnity
    participant Warehouse
    actor courier
    actor customer

    autonumber

    office->>Google Sheets: Add order from Shipnity to Google Sheets
    office->>Shipnity: Print order from Shipnity (1 qty per row)
    office->>Warehouse: Pack
    office->>Shipnity: Update tracking number in Shipnity
    courier->>Warehouse: Pickup orders
    Note over courier: pickup orders at 3pm daily
    courier->>customer: Deliver orders
```