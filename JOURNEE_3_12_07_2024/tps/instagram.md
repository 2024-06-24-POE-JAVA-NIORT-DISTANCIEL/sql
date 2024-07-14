# Correction TP Instagram

## La BDD

```sql
CREATE TABLE IF NOT EXISTS users (
	id SERIAL PRIMARY KEY,
	username VARCHAR(30) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
	bio VARCHAR(400),
	avatar VARCHAR(200),
	phone VARCHAR(25),
	email VARCHAR(40),
	password VARCHAR(50),
	CONSTRAINT contact_info_provided CHECK(
		COALESCE(phone, email) IS NOT NULL AND
		(phone IS NULL OR phone <> '') AND
		(email IS NULL OR email <> '')
	)
);

CREATE TABLE IF NOT EXISTS posts (
	id SERIAL PRIMARY KEY,
	url VARCHAR(200) NOT NULL,
	caption VARCHAR(240),
	lat REAL CHECK(lat >= -90 AND lat <= 90),
	lng REAL CHECK(lng >= -180 AND lng <= 180),
	CONSTRAINT lat_lng_provided CHECK((lat IS NULL AND lng IS NULL) OR (lat IS NOT NULL AND lng IS NOT NULL)),
	user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE
);

CREATE TABLE comments (
	id SERIAL PRIMARY KEY,
	contents VARCHAR(240) NOT NULL,
	user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
	post_id INTEGER NOT NULL REFERENCES posts(id) ON DELETE CASCADE
);


CREATE TABLE likes (
	id SERIAL PRIMARY KEY,
	created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
	user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
	post_id INTEGER REFERENCES posts(id) ON DELETE CASCADE,
	comment_id INTEGER REFERENCES comments(id) ON DELETE CASCADE,
	CHECK(
		COALESCE((post_id)::BOOLEAN::INTEGER, 0)
		+
		COALESCE((comment_id)::BOOLEAN::INTEGER, 0)
		= 1
	),
	UNIQUE(user_id, post_id, comment_id)
);
```

## Explications des contraintes

1. **Table `Utilisateur` :**

   - **Contrainte de vérification (CHECK)** : Ajoute une contrainte pour s'assurer que les champs `mail` et `Phone` ne sont pas tous deux absents. Cela garantit qu'au moins un moyen de contact est fourni. Exemple :
     ```sql
     CHECK (mail IS NOT NULL OR Phone IS NOT NULL)
     ```
   - **Contrainte de non-nullité (NOT NULL)** : Assure-toi que les champs essentiels comme `first_name`, `last_name`, `username`, et `password` ne peuvent pas être nuls pour garantir qu'ils sont toujours renseignés.
   - **COALESCE** : Utilise la fonction `COALESCE` pour vérifier que des valeurs alternatives sont présentes, comme pour le `mail` ou le `Phone`. Exemple :
     ```sql
     CHECK (COALESCE(mail, Phone) IS NOT NULL)
     ```

2. **Table `Post` :**

   - **Contrainte de vérification (CHECK)** : Pour les champs `Latitude` et `Longitude`, utilise des contraintes pour s'assurer qu'ils sont dans les plages valides :
     ```sql
     CHECK (Latitude BETWEEN -90 AND 90)
     CHECK (Longitude BETWEEN -180 AND 180)
     ```
   - **Contrainte de non-nullité (NOT NULL)** : Les champs `url` et `utilisateur_id` devraient être obligatoires pour garantir qu'un post a toujours un propriétaire et une URL.

3. **Table `Comment` :**

   - **Contrainte de vérification (CHECK)** : Assure-toi que le champ `comment` (ou `content`) ne soit pas vide pour garantir qu'il y a toujours un contenu dans le commentaire.
   - **Contrainte de non-nullité (NOT NULL)** : Les champs `utilisateur_id` et `post_id` doivent être obligatoires pour garantir qu'un commentaire est toujours lié à un utilisateur et un post.

4. **Table `Like` :**

   - **Contrainte de vérification (CHECK)** : Pour s'assurer qu'un `like` est appliqué soit à un `post` soit à un `comment`, mais pas aux deux en même temps :
     ```sql
     CHECK ((post_id IS NOT NULL AND comment_id IS NULL) OR (post_id IS NULL AND comment_id IS NOT NULL))
     ```
   - **Contrainte d'unicité (UNIQUE)** : Ajoute des contraintes pour s'assurer qu'un utilisateur ne peut pas liker plusieurs fois le même post ou commentaire :
     ```sql
     UNIQUE (utilisateur_id, post_id)
     UNIQUE (utilisateur_id, comment_id)
     ```

5. **Table `Follow` :**
   - **Contrainte de vérification (CHECK)** : Assure-toi qu'un utilisateur ne peut pas se suivre lui-même :
     ```sql
     CHECK (utilisateur_id <> follower_id)
     ```
   - **Contrainte d'unicité (UNIQUE)** : Pour éviter les doublons de suivis :
     ```sql
     UNIQUE (utilisateur_id, follower_id)
     ```
