# TP

## Créer une base de données appelée sales

### Créer une table appelée telephones avec les colonnes suivantes :

    - name : chaîne de caractères qui représente le modèle du téléphone
    - manufacturer : chaîne de caractères qui représente le fabricant
    - price :  un nombre qui représente le prix UHT
    - units_sold : nombre qui représente la quantité vendue

### LMD 1 : Insertions

- Insérer les données suivantes :

Voici les données étendues avec 50 enregistrements supplémentaires :

| ID  | name              | manufacturer | price | units_sold |
| --- | ----------------- | ------------ | ----- | ---------- |
| 1   | N1280             | Nokia        | 199   | 1925       |
| 2   | Iphone 4          | Apple        | 399   | 9436       |
| 3   | Galaxy S 5        | Samsung      | 299   | 2359       |
| 4   | S5620 Monte       | Samsung      | 250   | 2385       |
| 5   | N8                | Nokia        | 150   | 7543       |
| 6   | Droid             | Motorola     | 150   | 8395       |
| 7   | Iphone 13 Pro Max | Apple        | 1300  | 12849      |
| 8   | Galaxy Note 20    | Samsung      | 1100  | 10353      |
| 9   | Lumia 920         | Nokia        | 299   | 5847       |
| 10  | Iphone SE         | Apple        | 499   | 9726       |
| 11  | Galaxy S20        | Samsung      | 899   | 7435       |
| 12  | P40 Pro           | Huawei       | 799   | 5382       |
| 13  | Moto G7           | Motorola     | 199   | 6903       |
| 14  | Redmi Note 9 Pro  | Xiaomi       | 299   | 4208       |
| 15  | Pixel 5           | Google       | 699   | 3121       |
| 16  | Xperia 1 II       | Sony         | 1099  | 1923       |
| 17  | 3310              | Nokia        | 99    | 12568      |
| 18  | Iphone 12         | Apple        | 1099  | 10548      |
| 19  | Galaxy A51        | Samsung      | 399   | 8620       |
| 20  | P30 Pro           | Huawei       | 899   | 6741       |
| 21  | Moto G8           | Motorola     | 249   | 5947       |
| 22  | Redmi Note 8 Pro  | Xiaomi       | 249   | 5184       |
| 23  | Pixel 4a          | Google       | 499   | 3129       |
| 24  | Xperia 5 II       | Sony         | 899   | 2387       |
| 25  | 6.2               | Nokia        | 179   | 8412       |
| 26  | Iphone 11         | Apple        | 799   | 10962      |
| 27  | Galaxy A71        | Samsung      | 499   | 7692       |
| 28  | P20 Pro           | Huawei       | 699   | 4510       |
| 29  | Moto E6 Plus      | Motorola     | 149   | 6934       |
| 30  | Redmi Note 7      | Xiaomi       | 199   | 4367       |
| 31  | Pixel 3a          | Google       | 399   | 2296       |
| 32  | Xperia 10 II      | Sony         | 399   | 1715       |
| 33  | Nokia 7.2         | Nokia        | 349   | 4598       |
| 34  | Iphone X          | Apple        | 999   | 8765       |
| 35  | Galaxy S10        | Samsung      | 799   | 6543       |
| 36  | P30 Lite          | Huawei       | 299   | 3812       |
| 37  | Moto G6           | Motorola     | 199   | 5291       |
| 38  | Redmi Note 6 Pro  | Xiaomi       | 249   | 3719       |
| 39  | Pixel 2 XL        | Google       | 599   | 2098       |
| 40  | Xperia XZ2        | Sony         | 699   | 1543       |
| 41  | Nokia 6.1         | Nokia        | 249   | 3127       |
| 42  | Iphone XR         | Apple        | 799   | 7392       |
| 43  | Galaxy A50        | Samsung      | 349   | 5967       |
| 44  | P20 Lite          | Huawei       | 349   | 4210       |
| 45  | Moto G5 Plus      | Motorola     | 179   | 4923       |
| 46  | Redmi Note 5      | Xiaomi       | 199   | 3176       |
| 47  | Pixel XL          | Google       | 499   | 1823       |
| 48  | Xperia XZ3        | Sony         | 799   | 1287       |
| 49  | Nokia 5.3         | Nokia        | 199   | 2587       |
| 50  | Iphone 8          | Apple        | 699   | 6098       |

- Ecrire une requête pour liste tous les modèles de téléphones

- Ecrire une requête pour lister tous les telephone(`name`, `manufacturer`) de tous les téléphone dont le prix est supérieur à `200€`

- Ecrire une requête pour lister tous les telephone(`name`, `manufacturer`) de tous les téléphone dont le prix est varie entre `150` et `200€`

- Lister tous les téléphones de marque `samsung` et `Apple`

- Afficher le revenu total pour les téléphones vendues.Pour chaque téléphone, vous avez le `prix` et `la quantité` vendu
