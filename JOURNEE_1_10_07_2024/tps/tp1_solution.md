1. Création de la base de données
   CREATE DATABASE GestionEmployes;

-- 3. Création de la table Employes

```sql
CREATE TABLE Employes (
    id SERIAL PRIMARY KEY,
    nom VARCHAR NOT NULL,
    prenom VARCHAR NOT NULL,
    adresse VARCHAR NOT NULL,
    poste VARCHAR NOT NULL,
    salaire NUMERIC NOT NULL
);


-- 4. Insertion des enregistrements dans la table Employes
INSERT INTO Employes (nom, prenom, date_naissance, adresse, poste, salaire)
VALUES
    ('Dupont', 'Jean', 'Paris', 'Manager', 6000),
    ('Martin', 'Sophie', 'Lyon', 'Chef de projet', 4500),
    ('Durand', 'Pierre', 'Marseille', 'Développeur', 3500),
    ('Leclerc', 'Julie','Lille', 'Assistant administratif', 2800),
    ('Lefevre', 'Thomas','Toulouse', 'Développeur', 4000);

-- 5. Sélection de tous les enregistrements de la table Employes
SELECT * FROM Employes;

-- 6. Sélection des employés dont le poste est "Manager"
SELECT * FROM Employes WHERE poste = 'Manager';

-- 7. Sélection des employés dont le salaire est supérieur à 5000
SELECT * FROM Employes WHERE salaire > 5000;

-- 8. Modification du poste d'un employé spécifique
UPDATE Employes SET poste = 'Directeur' WHERE id = 1;

-- 9. Suppression d'un employé spécifique de la table
DELETE FROM Employes WHERE id = 5;

-- 10. Suppression de la table Employes
DROP TABLE Employes;

-- Suppression de la base de données GestionEmployes
DROP DATABASE GestionEmployes;
```
