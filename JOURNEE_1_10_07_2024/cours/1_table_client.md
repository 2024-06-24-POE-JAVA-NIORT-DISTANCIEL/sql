1. Créer une table en `SQL`

```sql
CREATE TABLE IF NOT EXISTS  clients(
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(50) UNIQUE,
    phone_number VARCHAR(20) NOT NULL UNIQUE
);
```
