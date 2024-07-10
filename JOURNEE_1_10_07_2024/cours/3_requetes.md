### Insertion de données (CREATE)

```sql
-- Insérer un nouveau client
INSERT INTO clients (first_name, last_name, email, phone_number)
VALUES ('John', 'Doe', 'john.doe@email.com', '123-456-7890');

-- Insérer plusieurs clients à la fois
INSERT INTO clients (first_name, last_name, email, phone_number)
VALUES
('Jane', 'Smith', 'jane.smith@email.com', '987-654-3210'),
('Bob', 'Johnson', 'bob.johnson@email.com', '555-123-4567'),
('Alice', 'Williams', 'alice.williams@email.com', '444-555-6666'),
('Charlie', 'Brown', 'charlie.brown@email.com', '777-888-9999');
```

### Lecture de données (READ)

```sql
-- Sélectionner tous les clients
SELECT * FROM clients;

-- Sélectionner avec ORDER BY
SELECT * FROM clients ORDER BY last_name ASC;

-- Utiliser WHERE pour filtrer
SELECT * FROM clients WHERE first_name = 'John';

-- Combiner WHERE et ORDER BY
SELECT * FROM clients WHERE last_name LIKE 'S%' ORDER BY first_name DESC;

-- Utiliser LIMIT pour restreindre le nombre de résultats
SELECT * FROM clients LIMIT 3;

-- Utiliser OFFSET pour sauter certains résultats
SELECT * FROM clients ORDER BY id OFFSET 2 LIMIT 2;

-- Utiliser LIKE pour une recherche partielle
SELECT * FROM clients WHERE email LIKE '%@email.com';

-- Combiner des conditions avec OR
SELECT * FROM clients WHERE first_name = 'John' OR last_name = 'Smith';

-- Combiner des conditions avec AND
SELECT * FROM clients WHERE first_name = 'John' AND last_name = 'Doe';

-- Utiliser OR et AND ensemble
SELECT * FROM clients
WHERE (first_name = 'John' OR first_name = 'Jane')
AND last_name LIKE 'D%';
```

### Mise à jour de données (UPDATE)

```sql
-- Mettre à jour un client spécifique
UPDATE clients
SET email = 'john.doe.updated@email.com'
WHERE id = 1;

-- Mettre à jour plusieurs clients qui répondent à une condition
UPDATE clients
SET phone_number = '000-000-0000'
WHERE last_name LIKE 'S%';
```

### Suppression de données (DELETE)

```sql
-- Supprimer un client spécifique
DELETE FROM clients WHERE id = 5;

-- Supprimer plusieurs clients qui répondent à une condition
DELETE FROM clients WHERE first_name = 'John' OR first_name = 'Jane';
```

### Limiter le résultat pour la pagination

```sql
-- Utiliser LIMIT pour restreindre le nombre de résultats
-- Cette requête retourne seulement les 3 premiers clients
SELECT * FROM clients LIMIT 3;

-- Utiliser OFFSET pour sauter certains résultats
-- Cette requête saute les 2 premiers clients et retourne les 3 suivants
SELECT * FROM clients ORDER BY id OFFSET 2 LIMIT 3;

-- Combiner ORDER BY, LIMIT et OFFSET pour une pagination
-- Page 1 (premiers 5 clients)
SELECT * FROM clients ORDER BY last_name, first_name LIMIT 5 OFFSET 0;

-- Page 2 (5 clients suivants)
SELECT * FROM clients ORDER BY last_name, first_name LIMIT 5 OFFSET 5;

-- Page 3
SELECT * FROM clients ORDER BY last_name, first_name LIMIT 5 OFFSET 10;

-- Utiliser LIMIT sans OFFSET pour obtenir les N premiers résultats après un tri
SELECT * FROM clients ORDER BY last_name DESC LIMIT 3;

-- Utiliser OFFSET sans LIMIT (moins courant, mais possible)
-- Cette requête saute les 5 premiers résultats et retourne tous les suivants
SELECT * FROM clients ORDER BY id OFFSET 5;
```
