```sql
CREATE TABLE IF NOT EXISTS telephones(
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    manufacturer VARCHAR(50) NOT NULL,
    price NUMERIC CHECK(price > 0) NOT NULL,
    units_sold INTEGER CHECK(units_sold > 0) NOT NULL,
    UNIQUE(name, manufacturer)
);

1.Quelles sont les marques dont le chiffre d''affaires est supérieur à 20 000 000 ?

2.Quel est le pourcentage des ventes réalisées par chaque fabricant par rapport au total ?
```
