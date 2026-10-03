# JAVA
## Entrée utilisateur
En programmation il est important de pouvoir permettre à un utilisateur d'entrer des valeurs.
Cela peut être utile pour demander à un utilisateur de renseigner son prénom, son âge, et bien d'autre.

Pour cela, en java il faut importer un **package** (importer du code externe) appeler **Scanner**.
```java
import java.util.Scanner;
```
Une fois importer on doit maintenant initialiser ce Scanner. On se rend donc dans le main de notre classe (`public static void main`), car c'est ici que l'on execute le code.

Ici cela fait partie des parties relativement abstraites sur lesquels vous ne devez pas vous attardez, mais plutôt comprendre le fonctionnement global.
```java
Scanner scanner = new Scanner(System.in);
// cette ligne s'écrira toujours de la même manière pour initialiser le Scanner.
```
### Lire l'entrée utilisateur
Maintenant que l'on à initialiser la *communication* (le Scanner est considéré comme une communication entre la machine et l'utilisateur), il faut pouvoir stocker les réponses de l'utilisateur.
```java
int age = sc.nextInt(); // pour un entier
double note = sc.nextDouble(); // pour un réel
String prenom = sc.nextLine(); // pour une chaine de caractère
```
<hr>
cours_1 - cours java - BTS SIO 1B 2026