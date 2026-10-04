# Introduction XAMPP
> **X**: signifie multi plateforme (Windows, Linux, MacOS)<br>
> **A**: Apache, serveur web<br>
> **M**: MariaDB, base de données<br>
> **P**: PHP, langage de programmation<br>
> **P**: Perl, un autre langage de prog.
- [Installation](./intro_xampp.md#installation)
- [Utilisation](./intro_xampp.md#utilisation)

**Xampp** est un logiciel qui permet de transformer sa machine (ordinateur) en serveur local. C'est donc un kit d'outils principalement orienté développement web.

## Installation
Se rendre sur le [site de download](https://www.apachefriends.org/download.html), et installer **xampp** pour 
le système voulu (windows, macos, linux).
- [Windows](./intro_xampp.md#windows)
- [MacOS](./intro_xampp.md#macos)
- [Linux](./intro_xampp.md#linux)
### Windows
Une fois téléchargé, lancer le `.exe`. Puis suivre les instructions (cliquer sur next pour toutes les étapes).<br>
Xampp est maintenant installé sur votre machine !
### MacOS
Une fois téléchargé, lancer le `.dmg`.<br>
> ⚠️ Si une erreur apparaît à propos du constructeur non vérifié, allez dans vos paramètres > confidentialité et sécurité. En descendant vous devriez trouvé XAMPP et un bouton `Ouvrir quand même`, cliquez dessus.

Suivez ensuite les instructions (cliquez sur next à chaque étapes).<br>
Xampp est maintenant installé sur votre machine !
### Linux
Une fois téléchargé, lancer le terminal. Et entrez les commandes suivantes:
```bash
chmod +x ./xampp-installer.run
sudo ./xampp-installer.run
```
Pareil, suivez les instructions pour mener à bien l'installation.<br>
Xampp s'est normalement installé dans `/opt/lampp/`, vérifier le status des serveur avec `/opt/lampp/lampp status`.<br>
Pour lancer l'interface graphique: 
```bash
sudo /opt/lampp/manager-linux-x64.run
```
## Utilisation
Comme vue en cours avec M.Chouaki, on travaille uniquement via le **terminal** (cmd). C'est-à-dire que l'on va intéragir avec les bases de données en ligne de commande via l'interface du terminal.

Pour se faire on lance **xampp**, et le procéder est différent en fonction de la plateforme (windows, linux, maos).
- [Windows](./intro_xampp.md#windows-1)
- [MacOS & Linux](./intro_xampp.md#macos--linux)
### Windows
1. Lancer l'application **XAMPP Control Panel**.
2. Cliquer sur `start` sur la ligne du service **MySQL**.
3. Cliquer sur `shell` pour lancer le terminal.
4. Entrer `mysql -u root`.

Vous êtes maintenant sur l'interface **MariaDB**, sur lequel nous interagissons avec les bases de données. 
### MacOS & Linux
1. Ouvrir un terminal et taper:
```bash
# Pour MacOS
sudo /Applications/XAMPP/xamppfiles/xampp startmysql
# vérifier le status des serveurs
/Applications/XAMPP/xampfiles/xampp status
```
```bash
# Pour Linux
sudo /opt/lampp/lampp startmysql
# vérifier le status des serveurs
/opt/lampp/lampp status
```
2. Se connecter à MySQL (aucun mdp requis):
```bash
# Pour MacOS
/Applications/XAMPP/xamppfiles/bin/mysql -u root -p
```
```bash
# Pour Linux
/opt/lampp/bin/mysql -u root -p
```
## Interface terminal
Maintenant Windows comme MacOS & Linux se retrouve sur cette interface terminal:
```bash
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.4.28-MariaDB Source distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 
```
<hr>
Introduction XAMPP - cours bdd - BTS SIO 1B 2026

[Cours suivant]()