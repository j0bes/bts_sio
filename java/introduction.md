# JAVA
[Support pour apprendre - w3schools](https://www.w3schools.com/java/default.asp)
## C'est quoi ?
Il s'agit d'un langage de **programmation**, orienté objet (POO = *Programmation Orienté Objet*) et basé sur les classes.
Une classe est une sorte de moule qui permet de définir ce qu'un objet possède et peut faire.<br>
*Exemple*:

```txt
Classe : Chien

Attributs :
- nom
- âge
- race

Méthodes (fonctions) :
- aboyer()
- manger()
- courir()
```

> **PLUS D'INFOS**<br>
> Java est en partie été créer pour uniformiser la compilation de programme et permettre une meilleure compatibilité inter-plateforme et résoudre un problèmes de portabilité.
> 
> Une plateforme est l'alliance d'un OS + processeur.
> Par exemple: `Windows + Intel, Linux + AMD`, assemblent le code de manières différentes.
> 
> Cela resisde dans la compilation du code en **BYTECODE** (binaire .classfile) avec le compilateur Java, code qui n'est compris que par Java Virtual Machine qui réside dans la ram de l'ordinateur utilisé. Et ensuite traduit en code machine en fonction de la plateforme au moment de l'exécution.
## Les usages courants
Applications concrète du langage Java:
- Application android,
- Logiciel entreprise,
- Programmation des dispositifs matériels embarqués,
- Technologies côté serveur telle que Apache, JBoss, GlassFish et Tomcat.
## Initiation 
Lorsque l'on débute en programmation, il faut accepter que certain concept soit abstrait au départ. Par exemple: `System.out` ou encore `public static`. L'important est de comprendre le fonctionnement global, par exemple: `System.out.println("hello");` affiche `hello` dans la console.

Pour commencer, ci-dessous une structure classique et simple d'une classe qu'on a appelé **Exo1**.
On définit le début et la fin d'un objet (class, main, etc) avec des accolades: `{ }`.

▶️ **Flèche verte pour lancer le programme sur Eclipse.**

``` java
// Class
public class Exo1 {
	// main > execute le code
	public static void main(String[] args) {
		// afficher dans le terminal
		System.out.println("Hello world.\n"+"Nouvelle ligne.");
		// Sortie: 
		// Hello world.
		// Nouvelle ligne.
	}
}
```
> **À retenir:**<br>
> `System.out.println()`: afficher dans la console avec un retour à la ligne,<br>
> `\n`: retour a la ligne
### Déclaration de variable
Avant tout, une variable est une boite qui permet de stocker des données. Du texte, des chiffres mais aussi un booléen: `true`ou `false` (vrai ou faux). On la définit avec un **type**, un **nom_de_variable** et une **valeur**.

| type    | utilité                             | exemple             |
| ------- | ----------------------------------- | ------------------- |
| String  | stocker du texte                    | "hello"             |
| int     | stocker des entiers                 | 123 ou -123         |
| float   | stocker les nombres à virgule       | 19,99 ou -19,99     |
| char    | stocker un caractère unique         | "a" ou "B"          |
| boolean | stocker les valeurs avec deux etats | `true` ou `false    |
| double  | réels                               | -929,98 ou 10383892 |

```java
int x = 15;
x = 20;  // myNum est de 20 maintenant
System.out.println(x);
```

#### Variable avec detection automatique du type
`var` permet d'initialiser une variable sans avoir à préciser son type. 

```java
var myVar; // Erreur
var myVar = "c";
```
#### Constantes
On utilisera le mot clé `final`pour définir une constante (variable que ne change pas).
Cela est utile pour définir des unitées comme le temps ou des années par exemple.

```java
final int x = 5; 
x = 20; // Erreur: cannot assign a value to final variable 'x'
```
#### Recap variable + demo

```java
int myNum = 5;               // Entier
float myFloatNum = 5.99f;    // Nombre à virgule
double myDouble = 3.0;       // Réel
char myLetter = 'D';         // Caractère
boolean myBool = true;       // Booléen
String myText = "Hello";     // Chaine de caractères
```
### Concaténation de valeurs
Comme dans de nombreux langages de programmation, il est possible de concaténer des variables pour en créer de nouvelle.

```java
double y, z;
y = 12.5;
z = 1.5;
double somme = y + z;
```

```java
String prenom = "John", nom = "Doe";
String nom_complet = prenom + " " + nom;
System.out.println(nom_complet);
// Sortie: John Doe
```

⚠️ Lors de l'affichage de calcul il faut faire attention à utliser des parenthèses pour préciser que c'est un calcul plutôt qu'une concaténation.
```java
int a = 13, b = 2;
System.out.println("Voici la concaténation de a + b: " + a + b);
// Sortie: Voici la concaténation de a + b: 132
System.out.println("Voici la somme de a + b:" + (a+b));
// Sortie: Voici la somme de a + b: 15
```

## Opérateurs arithmétiques
Comme tout langage de programmation, Java possède des opérateurs arithmétiques permettant de réaliser tout types d'opérations:

> `++` & `--` permettent d'ajouter ou de soustraire 1 à la variable donnée.

```java
int x = 10;
int y = 3;

System.out.println(x + y); // 13
System.out.println(x - y); // 7
System.out.println(x * y); // 30
System.out.println(x / y); // 3
System.out.println(x % y); // 1

int z = 5;
++z;
System.out.println(z); // 6
--z;
System.out.println(z); // 5
```
<hr>
Introduction - cours java - BTS SIO 1B 2026<br>
[Cours suivant](./cours_1.md)