# Cours 1 BDD

Avant de débuter, il faut bien distinguer 3 sections.<br>

* Conceptualisation,
* Code,
* Manipulation,

La **conceptualisation** est la partie conception d'une base de données. On utilise des outils comme **Looping** (Windows) ou **JMerise** (MacOS) pour réaliser un MCD: *Modèle Conceptuel de Données*. C'est la première étape dans la réalisation d'une BDD, même si une étape préliminaire sur feuille peut aussi exister.

Le **code** lui est la partie souvent intermédiaire, et permet de construire la base de données en SQL sous forme de code. On utilise un IDE: *Integrated Development Environment*, comme **Visual Studio Code** ou **SublimText**. On écrira alors dans un fichier `.sql`* les instructions pour créer la base de données souhaitée.

**.sql* est la terminaison du fichier pour indiquer à la machine que le fichier contient du texte dans le langage SQL.

> Sur Looping et JMerise, il est possible de générer directement le script SQL pour créer la base de données, sans avoir à l'écrire soi-même.

Une fois enregistré sur votre machine, on peut passer à la manipulation.

La **manipulation** est la partie intéressante, elle nous permet d'interagir de toutes sortes avec la base de données que nous venons de concevoir dans les parties précédentes. Ajouter des valeurs, supprimer/ajouter des attributs, afficher les différentes tables, etc...

C'est de cette dernière partie dont nous allons traiter dans ce cours.

## Base de navigation

Savoir naviguer/se déplacer dans un terminal **MySQL** sur XAMPP est essentiel. Comme vu dans l'[introduction](./intro_xampp.md), une fois avoir exécuté `mysql -u root` on se retrouve dans le terminal MySQL.

Voici les commandes de base pour naviguer dans le terminal MySQL:

* `show databases;` : afficher les bases de données disponibles,
* `use nom_database;` : utiliser/aller dans une base de données,
* `show tables;` : afficher les tables de la base de données dans laquelle on se situe,
* `desc nom_table;`: afficher la structure de la table indiquée,
* `show create table nom_table;` : afficher le code source d'une table

```bash
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| CINEMA             |
| ecole              |
| gest_reparation    |
| information_schema |
| ldd                |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
9 rows in set (0.005 sec)
```

### Ajouter une base de données

Imaginons que vous venez de coder votre base de données sur SublimText (ou Visual Studio Code). Vous avez donc votre fichier `ma_bdd.sql` sur votre machine.

Ce fichier possède un chemin précis sur votre machine, par exemple:

```bash
# Windows exemple
C:\User\Desktop\cours_chouaki\ma_bdd.sql
# MacOS & Linux exemple
/home/user/desktop/cours_chouaki/ma_bdd.sql
```

Pour l'importer dans le terminal MySQL et pouvoir interagir avec il faut entrer la commande suivante:

```bash
# Windows
source C:\User\Desktop\cours_chouaki\ma_bdd.sql
# MacOS & Linux
source /home/user/desktop/cours_chouaki/ma_bdd.sql
```

### Visualiser les valeurs d'une table

Maintenant que l'on a importé notre base de données, on aimerait visualiser les valeurs présentes dans la table `fruits`.

```bash
MariaDB [(none)]> use ma_bdd; # Sélectionne notre bdd
MariaDB [(ma_bdd)]> show tables; # Affiche toutes les tables de la bdd
+--------------------+
| Tables             |
+--------------------+
| fruits             |
| legumes            |
+--------------------+
2 rows in set (0.005 sec)
MariaDB [(ma_bdd)]> select * from fruits; # Affiche les valeurs présentes dans la table
+-------+----------+-----------+
| ID    | libellé  | quantité  |
+-------+----------+-----------+
|     1 | banane   | 50        |
+-------+----------+-----------+
|     2 | pomme    | 13        |
+-------+----------+-----------+
2 row in set (0.009 sec)
```

> **À retenir**:
> `select * from nom_table;` permet d'afficher le contenu d'une table.

À partir d'ici, vous savez naviguer dans le terminal MySQL et visualiser une base de données.<br>
La partie suivante se penche plus sur l'interaction avec la BDD.

## Interagir avec la BDD (terminal)
À venir...
<hr>
Cours 1 BDD - cours bdd - BTS SIO 1B 2026

[Introduction XAMPP](./intro_xampp.md)
