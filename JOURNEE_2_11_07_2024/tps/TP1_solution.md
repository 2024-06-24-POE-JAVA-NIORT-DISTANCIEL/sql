```sql
CREATE TABLE IF NOT EXISTS telephones(
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    manufacturer VARCHAR(50) NOT NULL,
    price NUMERIC CHECK(price > 0) NOT NULL,
    units_sold INTEGER CHECK(units_sold > 0) NOT NULL,
    UNIQUE(name, manufacturer)
);
```

- Quel est le pourcentage des ventes réalisées par chaque fabricant par rapport au total ?

```sql
WITH total_sales AS (
    SELECT SUM(units_sold) AS total
    FROM telephones
)
SELECT manufacturer,
       SUM(units_sold) AS manufacturer_sales,
       (SUM(units_sold) * 100.0 / total_sales.total) AS percentage
FROM telephones, total_sales
GROUP BY manufacturer, total_sales.total
ORDER BY percentage DESC;
```

- Quelles sont les marques dont le chiffre d'affaires est supérieur à 20 000 000 ?

```sql
SELECT manufacturer, SUM(price * units_sold) AS revenue
FROM telephones
GROUP BY manufacturer
HAVING SUM(price * units_sold) > 20000000
ORDER BY revenue DESC;
```