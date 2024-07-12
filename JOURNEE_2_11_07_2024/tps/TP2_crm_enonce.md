**CRM**

**orders:**

| id  | service_type | designation      | client_id | nb_days | unit_price | total_exclude_taxe | total_with_taxe | state     |
| --- | ------------ | ---------------- | --------- | ------- | ---------- | ------------------ | --------------- | --------- |
| 1   | Formation    | Angular init     | 2         | 3       | 1200       | 3600               | 4320            | CANCELED  |
| 2   | Formation    | React avancé     | 2         | 3       | 1000       | 3000               | 3600            | CONFIRMED |
| 3   | Coaching     | React Techlead   | 1         | 20      | 900        | 18000              | 21600           | CONFIRMED |
| 4   | Coaching     | Nest.js Techlead | 1         | 50      | 800        | 40000              | 48000           | OPTION    |
| 5   | Coaching     | React Techlead   | 3         | xxx     | xxx        | xxx                | xxx             | xxx       |
| 6   | Coaching     | Jakarta EE       | 3         | xxx     | xxx        | xxx                | xxx             | xxx       |
| 7   | Coaching     | Angular Techlead | 4         | xxx     | xxx        | xxx                | xxx             | xxx       |

**clients:**

| id  | company_name  | first_name | last_name | email           | phone          | address | zip_code | city   | country | state    |
| --- | ------------- | ---------- | --------- | --------------- | -------------- | ------- | -------- | ------ | ------- | -------- |
| 1   | Sopra         | Fabrice    | Martin    | martin@mail.com | 06 56 85 84 33 | abc     | xyz      | Nantes | France  | ACTIVE   |
| 2   | M2I Formation | Julien     | Lamard    | lamard@mail.com | 06 11 22 33 44 | abc     | xyz      | Paris  | France  | INACTIVE |
| 3   | ATOS          |            |           |                 |                |         |          |        |         |          |
| 4   | SOPRA STERIA  |            |           |                 |                |         |          |        |         |          |

- Vous devez compléter pour aller jusqu’à 10 enregistrements

- Pour calculer le total taxe excluded : unitePrice x nbDays
- Pour calculer total with taxes(TVA) , vous pouvez utiliser ce site : https://intia.fr/fr/ressources/outils-de-calcul/calcul-ttc-ht/

- Lors de la création ds orders, rassurez-vous que les champs totalExcludeTaxe et totalWithTaxe soient calculés automatiquement à chaque insertion.




1. Ecrire une requête pour créer ces 2 tables en prenant en compte la jointure

2. Remplissez la base de données au travers des insertions

3. Afficher toutes les formations sollicités par le client M2i formation M2u information

4. Afficher les noms et contacts de tous les contacts des clients qui ont sollicité un coaching

5. Afficher les noms et contacts de tous les contacts des clients qui ont sollicité un coaching pour les accompagnements React.js

6. Pour chacune des demandes de formation, afficher le prix UHT et prix TTC en se basant sur le unité Price(TJM) et le nombre de jours de prestation tout en sachant que la TVA est de 20%.

7. Lister toutes les prestations qui sont confirmés et qui vont rapporter plus 30.000€

8. Calculer le chiffre d'affaires total (hors taxe) par client, mais uniquement pour les clients ayant généré plus de 30 000€ de CA, trié par ordre décroissant


9. Calculer le prix moyen des prestations par type, mais uniquement pour les types de prestation qui ont un prix moyen supérieur à 1000€


10. Pour chaque client, afficher le nombre de prestations, le total des jours de prestation et le montant total facturé (TTC), trié par montant total décroissant :
