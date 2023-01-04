# Stock Transfer Flow

```mermaid
sequenceDiagram
    participant Shipnity
    participant Storehub
    participant Database

    autonumber

    Shipnity ->> Storehub: transfer products to Storehub
    loop
        Storehub-->Storehub: Transfer products from office to each branch
    end
    Storehub ->> Database: Create stock transfer transaction
    Note left of Database: Filter completed status and unsaved transaction
    Storehub ->> Shipnity: Create mocked orders according to stock transfer transaction
```

## Improvement

- Improve efficiency for stock team
    - We have 19 branches now and can save x hours/day from stock team for creating mocked orders in Shipnity task.
    - Reduce human error from importing mocked orders in Shipnity.