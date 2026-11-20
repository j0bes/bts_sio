# Introduction à Java
> Conception et développement d'application

**Sommaire**

* [Java c'est quoi ?](./intro.md#java-cest-quoi-)
* [Syntaxe de base](./intro.md#syntaxe-de-base)
* [Variables et types](./intro.md#variables-et-types)
* [Opérateur arithmétique](./intro.md#opérateur-arithmétique)
* [Opérateur logique](./intro.md#opérateur-logique)
* [Exemple structure d'un programme Java](./intro.md#exemple-structure-dun-programme-java)

## Java c'est quoi ?
**Java** est un langage de programmation comme C, Rust, Python. Il a pour particularité d'être basé sur les classes;
```java
public class Voiture {}
```
### Cas d'utilisation
* Applications
* Matériels embarqués
* Technologies serveurs
### Compilation

Pour faire simple, **Java** est un langage dit *portable*, car le `.bytecode` peut être lancé sur n'importe quel système (Windows, Linux, MacOS) avec une version compatible de la **JVM**.

> Sachant que chaque système possède des architectures, des manières de compiler le code différentes.

* **JDK (Java Development Kit)**: contient les outils nécessaires pour le développement et la compilation des programmes **Java**.
* **JRE (Java Runtime Environment)**: environnement complet qui permet de lancer un programme Java (contient la JVM).
* **JVM (Java Virtual Machine)**: exécute le code Java en interprétant le bytecode.

La compilation passe donc du programme `.java` en **bytecode** `.class` qui sera exécuté par la **JVM**.

## Syntaxe de base
Le nom du fichier de votre programme **Java** doit absolument porter le nom de la classe.
```java
// nom fichier : Voiture.java
public class Voiture {}
```
Sans ça le compilateur retourne une erreur. Cela permet de retrouver facilement une classe dans un projet comportant plusieurs fichiers (donc plusieurs classes).

> ⚠️ **Important**<br>
> Un bloc (*classe, fonction, conditions, boucles*) marquera son début par une accolade `{` et se fermera de la même manière `}`.

On sait donc maintenant que tout se passe dans une classe.

---

Maintenant voyons la notion de **méthode**. 

Une **méthode** est un bout de code réutilisable, qui peut prendre des variables en paramètres.
```java
// Déclaration d'une méthode
public static type nomMethode(params){}

// Le main
public static void main(String[] args){
    // appel de la méthode
    nomMethode(params);
}
```
Le type de la méthode est important car c'est lui qui définit ce que va renvoyer la fonction (*int, double, void, ...*).

En algorithmique on fait la distinction entre deux méthodes: **procédure** et **fonction**.

### Procédure
Une **procédure** est une méthode qui ne retourne rien (`void`).
```java
public static void nomProcedure(params){}
```
**`Void`** indique le vide, donc ne retourne aucune valeur.

C'est pourquoi le `main` est une procédure, car il ne retourne rien. Et c'est ici qu'on écrira le coeur du programme.
```java
public static void main(String[] args) {}
// String[] args sont les paramètres de la procédure 'main'.
```
Voici un exemple de procédure :
```java
public static void afficherBonjour(){
    System.out.println("bonjour");
}
// Ne retourne rien, mais affiche dans le terminal:
// bonjour
```

### Fonction
Une **fonction** est une méthode qui retourne une valeur avec un certain type (*int, double, String, ...*).
```java
public static int nomFonction(params){
    return unEntier;
}
```
Voici un exemple de fonction :
```java
public static double add(double a, double b){
    return a+b;
}
// Retourne le résultat de a+b
```
> ⚠️ **Remarque**<br>
> Je passe volontairement `public static`, on gardera cette notion abstraite pour le moment. Il faut juste appliquer la syntaxe de base.

### Afficher du texte
Pour afficher du texte, des données dans le terminal on utilisera différents `print`.<br>
La syntaxe est la même à chaque fois et ne change pas dans sa structure :
```java
System.out.print("Ce texte ne renvoie pas à la ligne à la fin.");
System.out.println("Par contre ce texte retourne à la ligne.");
```
**A retenir** :<br>
On voit que `System.out` est toujours présent lorsqu'on veut afficher du texte, car c'est lui qui permet la sortie standard (*standard output*).

## Variables et types
Comme dans tout langage de programmation **Java** possède les types de variables primitifs classiques:
```java
int a;         // entier
double b;      // réel
String text;   // chaine de caractère
char c;        // un seul caractère
boolean status;     // true ou false
```
> 💡**Note**<br>
> String semble être un type particulier car il commence par une majuscule. Mais gardons ça dans le coin de notre tête.

Il faut distinguer *déclarer* une variable et *l'initialiser*:
```java
int a; // déclaration
a = 5; // initialisation
```
On peut néanmoins pour gagner du temps combiner les deux.
```java
double moyenne = 12.9;
```
### Constantes
On utilisera le mot clé `final` pour définir une constante (variable qui ne change pas).
Cela est utile pour définir des unités comme le temps ou des années par exemple.

```java
final int x = 5; 
x = 20; // Erreur: cannot assign a value to final variable 'x'
```
### Cast
Un **cast** (*conversion de type*) consiste à transformer une valeur d'un type en un autre type.

Cela ne s'applique en général que dans le sens du plus grand vers plus petit (*double vers int*), car on perds de l'information (*ce qui se trouve après la virgule par exemple*).
```java
double a = 12.65;
int b = (int) a;

System.out.println(b); // 12
```

## Opérateur arithmétique
```java
int x = 10;
int y = 3;

System.out.println(x + y); // 13
System.out.println(x - y); // 7
System.out.println(x * y); // 30
System.out.println(x / y); // 3
System.out.println(x % y); // 1

int z = 5;
z++;
System.out.println(z); // 6
z--;
System.out.println(z); // 5
```
> `++` & `--` permettent d'ajouter ou de soustraire 1 à la variable mentionnée.

⚠️ **Attention** : lors de l'affichage de calcul il faut faire attention à utiliser des parenthèses pour préciser que c'est un calcul plutôt qu'une concaténation.

```java
int a = 13, b = 2;
System.out.println("Voici la concaténation de a + b: " + a + b);
// Sortie: Voici la concaténation de a + b: 132
System.out.println("Voici la somme de a + b: " + (a+b));
// Sortie: Voici la somme de a + b: 15
```

## Opérateur logique et comparaisons
```java
&&    // ET
||    // OU
!     // NON

>     // supérieur
>=    // supérieur ou égal
<     // inférieur
<=    // inférieur ou égal
==    // égal
!=    // différent
```
Ces opérateurs sont surtout utiles dans les conditions et boucles que nous verront dans la suite du cours.

## Exemple structure d'un programme Java
Pour conclure cette introduction au langage **Java**, voici un le code d'un fichier type.

On va prendre pour l'exemple un fichier `Compta.java`.
```java
public class Compta {

    // Méthode : 'calc_ttc'
    public static double calcTtc(double montant){
        final double TAUX = 1.2;
        return montant * TAUX;
    }

    // Procédure principale : 'main'
    public static void main(String[] args){
        double montant1 = 130.67;

        System.out.println("Voici le montant TTC : " + calcTtc(montant1));
    }
}
// Sortie : Voici le montant TTC : 156,80399999999997
```
---

[COURS SUIVANT]()

*@j0bes* - BTS SIO 2026