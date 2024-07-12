1. Création des tables avec prise en compte de la jointure :

```sql
CREATE TABLE IF NOT EXISTS clients (
    id SERIAL PRIMARY KEY,
    company_name VARCHAR(100) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    phone_number VARCHAR(15) UNIQUE,
    address TEXT NOT NULL,
    zip_code VARCHAR(30) NOT NULL,
    country VARCHAR(100) NOT NULL,
    state INTEGER CHECK(state >= 0 AND state <= 1)
);

CREATE TABLE IF NOT EXISTS orders (
    id SERIAL PRIMARY KEY,
    type_presta VARCHAR(100) NOT NULL,
    designation VARCHAR(100) NOT NULL,
    client_id INTEGER REFERENCES clients(id) ON DELETE RESTRICT,
    nb_days INTEGER NOT NULL CHECK(nb_days > 0),
    unit_price NUMERIC NOT NULL CHECK(unit_price > 0),
    total_exclude_taxe NUMERIC GENERATED ALWAYS AS (unit_price * nb_days) STORED,
    total_with_taxe NUMERIC GENERATED ALWAYS AS (1.2 * unit_price * nb_days) STORED,
    state INTEGER CHECK(state >= 0 AND state <= 2)
);
```

2. Insertions des données :

```sql
INSERT INTO clients (company_name, first_name, last_name, email, phone_number, address, zip_code, country, state) VALUES
('Sopra', 'Fabrice', 'Martin', 'martin@sopra.com', '06 56 85 84 33', '3 Rue de l''Informatique', '44000', 'France', 1),
('M2I Formation', 'Julien', 'Lamard', 'lamard@m2i.fr', '06 11 22 33 44', '27 Avenue des Formations', '75001', 'France', 0),
('ATOS', 'Sophie', 'Durand', 'sophie.durand@atos.net', '07 98 76 54 32', '18 Boulevard du Numérique', '92400', 'France', 1),
('SOPRA STERIA', 'Pierre', 'Lefebvre', 'p.lefebvre@soprasteria.com', '06 12 34 56 78', '7 Place de la Tech', '31000', 'France', 1),
('Capgemini', 'Marie', 'Dubois', 'm.dubois@capgemini.com', '06 23 45 67 89', '5 Rue de l''Innovation', '69002', 'France', 1),
('Accenture', 'Thomas', 'Moreau', 't.moreau@accenture.com', '07 34 56 78 90', '10 Avenue du Conseil', '92300', 'France', 1),
('IBM France', 'Claire', 'Rousseau', 'c.rousseau@ibm.com', '06 45 67 89 01', '22 Rue du Big Data', '92270', 'France', 1),
('Orange Business Services', 'Antoine', 'Girard', 'a.girard@orange.com', '07 56 78 90 12', '1 Place des Télécoms', '92130', 'France', 1),
('Thales', 'Emilie', 'Leclerc', 'e.leclerc@thales.com', '06 67 89 01 23', '45 Avenue de la Défense', '92000', 'France', 1),
('Dassault Systèmes', 'Nicolas', 'Petit', 'n.petit@3ds.com', '07 78 90 12 34', '10 Rue de la 3D', '78140', 'France', 1),
('Tech Innovate', 'Alice', 'Johnson', 'a.johnson@techinnovate.com', '06 87 65 43 21', '15 Rue de l''Innovation', '69003', 'France', 1),
('Data Dynamics', 'Robert', 'Brown', 'r.brown@datadynamics.com', '07 12 34 56 78', '8 Avenue des Données', '75016', 'France', 1),
('Cloud Systems', 'Emma', 'Davis', 'e.davis@cloudsystems.com', '06 98 76 54 32', '3 Boulevard du Cloud', '92500', 'France', 0);


INSERT INTO orders (type_presta, designation, client_id, nb_days, unit_price, state) VALUES
('Formation', 'Angular init', 2, 3, 1200, 0),
('Formation', 'React avancé', 2, 3, 1000, 2),
('Coaching', 'React Techlead', 1, 20, 900, 2),
('Coaching', 'Nest.js Techlead', 1, 50, 800, 1),
('Coaching', 'React Techlead', 3, 15, 950, 2),
('Formation', 'Jakarta EE', 3, 5, 1100, 1),
('Coaching', 'Angular Techlead', 4, 30, 850, 2),
('Formation', 'Spring Boot', 5, 4, 1300, 2),
('Consulting', 'Architecture Microservices', 6, 10, 1500, 1),
('Formation', 'Docker et Kubernetes', 7, 5, 1200, 2),
('Coaching', 'DevOps practices', 8, 25, 950, 1),
('Formation', 'Machine Learning avec Python', 9, 7, 1400, 2),
('Consulting', 'Sécurité des applications', 10, 12, 1600, 2),
('Formation', 'GraphQL et Apollo', 1, 3, 1100, 1),
('Coaching', 'Agilité à l''échelle', 2, 40, 800, 2),
('Formation', 'Vue.js avancé', 3, 4, 1000, 2),
('Consulting', 'Optimisation des performances', 4, 8, 1300, 1),
('Coaching', 'Leadership technique', 5, 35, 900, 2),
('Formation', 'Typescript avancé', 6, 3, 1150, 0),
('Consulting', 'Migration vers le Cloud', 7, 15, 1400, 2),
('Consulting', 'Analyse de données', 11, 10, 1200, 2),
('Formation', 'Intelligence Artificielle', 12, 5, 1500, 1),
('Coaching', 'Leadership en IT', 13, 15, 1000, 0),
('Formation', 'Cybersécurité avancée', 11, 4, 1300, 2),
('Consulting', 'Transformation digitale', 12, 20, 1100, 1);
```

3. Afficher toutes les formations sollicitées par le client M2I Formation :

```sql
SELECT o.*
FROM orders o
JOIN clients c ON o.client_id = c.id
WHERE LOWER(c.company_name) = LOWER('M2I Formation') AND LOWER(o.type_presta) = LOWER('Formation');
```

4. Afficher les noms et contacts de tous les contacts des clients qui ont sollicité un coaching :

```sql
SELECT DISTINCT c.first_name, c.last_name, c.email, c.phone_number
FROM clients c
JOIN orders o ON c.id = o.client_id
WHERE LOWER(o.type_presta) = LOWER('Coaching');
```

5. Afficher les noms et contacts de tous les contacts des clients qui ont sollicité un coaching pour les accompagnements React.js :

```sql
SELECT DISTINCT c.first_name, c.last_name, c.email, c.phone_number
FROM clients c
JOIN orders o ON c.id = o.client_id
WHERE LOWER(o.type_presta) = LOWER('Coaching') AND LOWER(o.designation) LIKE LOWER('%React%');
```

6. Afficher le prix UHT et TTC pour chaque demande de formation :

```sql
SELECT designation, unit_price AS prix_UHT,
       (unit_price * nb_days) AS total_UHT,
       (unit_price * nb_days * 1.2) AS total_TTC
FROM orders
WHERE LOWER(type_presta) = LOWER('Formation');
```

7. Lister toutes les prestations confirmées qui vont rapporter plus de 30.000€ :

```sql
SELECT *
FROM orders
WHERE state = 2 AND (unit_price * nb_days) > 30000;
```

8. Calculer le chiffre d'affaires total (hors taxe) par client, pour les clients ayant généré plus de 30 000€ de CA, trié par ordre décroissant :

```sql
SELECT c.company_name, SUM(o.unit_price * o.nb_days) AS ca_total
FROM clients c
JOIN orders o ON c.id = o.client_id
GROUP BY c.id, c.company_name
HAVING SUM(o.unit_price * o.nb_days) > 30000
ORDER BY ca_total DESC;
```

9. Calculer le prix moyen des prestations par type, pour les types de prestation qui ont un prix moyen supérieur à 1000€ :

```sql
SELECT LOWER(type_presta) as type_presta, AVG(unit_price) AS prix_moyen
FROM orders
GROUP BY LOWER(type_presta)
HAVING AVG(unit_price) > 1000
ORDER BY prix_moyen DESC;
```

10. Pour chaque client, afficher le nombre de prestations, le total des jours de prestation et le montant total facturé (TTC), trié par montant total décroissant :

```sql
SELECT c.company_name,
       COUNT(o.id) AS nombre_prestations,
       SUM(o.nb_days) AS total_jours,
       SUM(o.unit_price * o.nb_days * 1.2) AS montant_total_ttc
FROM clients c
JOIN orders o ON c.id = o.client_id
GROUP BY c.id, c.company_name
ORDER BY montant_total_ttc DESC;
```
