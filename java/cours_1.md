# Cours 1 JAVA

* [Entrée utilisateur](./cours_1.md#entrée-utilisateur)
* [Les méthodes](./cours_1.md#les-méthodes-fonctions)

## Entrée utilisateur

En programmation il est important de pouvoir permettre à un utilisateur d'entrer des valeurs.
Cela peut être utile pour demander à un utilisateur de renseigner son prénom, son âge, et bien d'autres.

Pour cela, en Java il faut importer une classe **Scanner** provevant du package (code externe) `java.util`.

```java
import java.util.Scanner;
```

Une fois importé on doit maintenant initialiser ce Scanner. On se rend donc dans le main de notre classe (`public static void main`), car c'est ici que l'on exécute le code.

Ici cela fait partie des syntaxes relativement abstraites sur lesquelles vous ne devez pas vous attarder, mais plutôt comprendre le fonctionnement global.

```java
Scanner scanner = new Scanner(System.in);
// cette ligne s'écrira toujours de la même manière pour initialiser le Scanner.
```

### Lire l'entrée utilisateur

Maintenant que l'on a initialisé la *communication* (le Scanner est considéré comme une communication entre la machine et l'utilisateur), il faut pouvoir stocker les réponses de l'utilisateur.

```java
int age = scanner.nextInt(); // pour un entier
double note = scanner.nextDouble(); // pour un réel
String prenom = scanner.nextLine(); // pour une chaîne de caractères
```

### Fermer la communication

Comme pour un appel téléphonique, il faut couper la communication. Donc lorsqu'on a fini d'utiliser `Scanner`:

```java
scanner.close();
```

Cela indique à Java qu’on n’a plus besoin du `Scanner` et qu’il peut libérer les ressources qu’il utilisait.

## Les méthodes (fonctions)

Les méthodes sont une partie importante en programmation. Elles permettent de créer un bout de code qui peut être réutilisé, sans avoir à être réécrit. On dira: *faire appel à une méthode*. On verra par la suite l'appel de méthode.

Une méthode ne retourne pas toujours quelque_chose, le type peut être void (signifie le vide / rien).

```java
static type maMethode(parametre){
    return quelque_chose;
}
// on remplacera type par le type de variable qu'on souhaite retourner.
```

Prenons un exemple, on a besoin de connaître la moyenne de 3 notes. Pour une classe de 25 élèves, calculer à la main prendrait bcp de temps. Alors on écrit une fonction qui prend en paramètre 3 notes, et retourne la moyenne.

```java
static double moyenne(double note1, double note2, double note3){
    double moyenne = (note1 + note2 + note3)/3;
    return moyenne;
}
```

### Appel de méthode

Maintenant comment l'utiliser dans le main, qui est pour rappel l'endroit où l'on exécute le code dans une classe.<br>
On fait alors un **appel de méthode**, c'est-à-dire:

```java
public static void main(String[] args){
    double moy = moyenne(13.8, 18, 7.6);
    // moyenne() est l'appel de la méthode.
    System.out.println("La moyenne est de: " + moy);
    // Sortie: La moyenne est de: 13.133333
}
```

<hr>
Cours 1 - cours java - BTS SIO 1B 2026

[Introduction](./introduction.md) - [Cours suivant]()
