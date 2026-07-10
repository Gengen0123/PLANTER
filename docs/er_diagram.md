# ER図

```mermaid
erDiagram
    USERS ||--o{ PLANTS : has
    PLANTS ||--o{ GROWTH_RECORDS : has

    USERS {
        bigint id PK
        string name
        string email
        string encrypted_password
        string public_id
    }

    PLANTS {
        bigint id PK
        bigint user_id FK
        string name
        string variety
        text description
    }

    GROWTH_RECORDS {
        bigint id PK
        bigint plant_id FK
        date recorded_on
        text memo
    }
```