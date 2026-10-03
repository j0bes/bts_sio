# Cours 1 JAVA
- [Entrée utilisateur](./cours_1.md#entrée-utilisateur)
- [Les fonctions](./cours_1.md#les-fonctions)
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
int age = scanner.nextInt(); // pour un entier
double note = scanner.nextDouble(); // pour un réel
String prenom = scanner.nextLine(); // pour une chaine de caractère
```
### Fermer la communication
Comme pour un appel téléphonique, il faut couper la communication. Donc lorsqu'on a finit d'utiliser `Scanner`:
```java
scanner.close();
```
Cela indique à Java qu’on n’a plus besoin du `Scanner` et qu’il peut libérer les ressources qu’il utilisait.
## Les fonctions
Les fonctions sont une partie importante en programmation. Elles permettent de créer un bout de code qui peut être réutilisé, sans avoir à être réécrit. On dit dira: *faire appel à une fonction*. On verra par la suite l'appel de fonction.

Une fonction retourne toujours quelque chose. Une variable, une liste, un dictionnaire peu importe. Voici la structure classique:
```java
public static type MaFonction(parametre){
    return quelque_chose;
}
// on remplacera type par le type de variable qu'on souhaite retourner.
```
Prenons un exemple, on a besoin de connaitre la moyenne de 3 notes. Pour une classe de 25 élèves, calculer à la main prendrait bcp de temps. Alors on écrit une fonction qui prend en paramètre 3 notes, et retourne la moyenne.
```java
public static double Moyenne(double note1, double note2, double note3){
    double moyenne = (note1 + note2 + note3)/3;
    return moyenne;
}
```
### Appel de fonction
Maintenant comment l'utiliser dans le main, qui est pour rappel l'endroit ou l'on execute le code dans une classe.<br>
On fait alors un **appel de fonction**, c'est-à-dire:
```java
public static void main(String[] args){
    moyenne = Moyenne(13.8, 18, 7.6);
    // Moyenne() est l'appel de la fonction.
    System.out.println("La moyenne est de: " + moyenne);
    // Sortie: La moyenne est de: 13.133333
}
```
<hr>
Cours 1 - cours java - BTS SIO 1B 2026

[Introduction](./introduction.md) - [Cours suivant]()