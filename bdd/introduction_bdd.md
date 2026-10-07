# Introduction aux bases de données
Une base de donnée est une sorte de contenaire qui permet de stocker des tables (entités), c'est-à-dire de stocker de la donnée de manière organisé/structuré.

Pour exemple, on cherche à stocker tout les utilisateurs d'un site web, avec quelques informations comme: un id, pseudo et email.

On va donc créer une base de données `Data_website`, et créer une table `users` (utilisateurs). Cette table aura plusieurs attributs (propriétés):
- ID,
- Pseudo,
- Email

Chaque attribut doit être définit par un type: entier, caractère, chaine de caractère, etc...<br>
Par exemple: `Pseudo VARCHAR(25)`
> VARCHAR = chaine de caractère variable<br>
> (25) permet de préciser la taille maximale de la chaine de caractère.

## Langage SQL
Le langage informatique qui permet de créer, manipuler les bases de données, est le **SQL**. Et comme tout langage il fonctionne selon une syntaxe particulière.
### Requête
Il faut voir les commandes SQL comme des requêtes sur une base de données. Avec différents mots clés en fonction de l'action recherché. Une requête finira toujours par un `;`.

`create table ... ;`: requête pour création de table,<br>
`select ... ;`: requete pour afficher/sélectionner des données,<br>
`drop database if exists... ;`: requête pour supprimer une base de donnée si elle exist

*Exemple de syntaxe SQl*:
```sql
/* Ceci est un commentaire en SQL */
/* Afficher toutes valeurs de la table users */
select * from users;
/* Créer une table */
create table nom_table(
    id int not null,
    prenom varchar(15)
);
```

Plus de détails sur les différentes requêtes dans [la suite du cours](./cours_1.md).

On écrira donc le code pour créer une base de donnée en **SQL**, et on enregistrera le fichier en `.sql`.<br>
Par exemple: `script.sql`
