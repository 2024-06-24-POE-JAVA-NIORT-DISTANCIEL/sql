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
```

### Le reste c'est pour demain :D :D
