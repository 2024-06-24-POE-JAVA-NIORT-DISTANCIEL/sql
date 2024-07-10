**Énoncé du TP**

1. Créez une base de données appelée "GestionEmployes".

2. Dans cette base de données, créez une table appelée "Employes" avec les colonnes suivantes :

   - "id" : un identifiant unique pour chaque employé (entier auto-incrémenté).
   - "nom" : le nom de l'employé (chaîne de caractères).
   - "prenom" : le prénom de l'employé (chaîne de caractères).
   - "date_naissance" : la date de naissance de l'employé (date).
   - "adresse" : l'adresse de l'employé (chaîne de caractères).
   - "poste" : le poste occupé par l'employé (chaîne de caractères).
   - "salaire" : le salaire de l'employé (nombre décimal).

3. Ajoutez les contraintes suivantes à la table "Employes" :

   - La colonne "id" doit être une clé primaire.
   - La colonne "nom" ne peut pas être nulle.
   - La colonne "prenom" ne peut pas être nulle.
   - La colonne "date_naissance" ne peut pas être nulle.
   - La colonne "adresse" ne peut pas être nulle.
   - La colonne "poste" ne peut pas être nulle.
   - La colonne "salaire" ne peut pas être nulle.

4. Insérez au moins 5 enregistrements dans la table "Employes" avec des valeurs fictives pour les différentes colonnes.

5. Effectuez une requête SELECT pour afficher tous les enregistrements de la table "Employes".

6. Effectuez une requête SELECT pour afficher les employés dont le poste est "Manager".

7. Effectuez une requête SELECT pour afficher les employés dont le salaire est supérieur à 5000.

8. Effectuez une requête UPDATE pour modifier le poste d'un employé spécifique.

9. Effectuez une requête DELETE pour supprimer un employé spécifique de la table.

10. Terminez le TP en supprimant la table "Employes" et la base de données "GestionEmployes".
