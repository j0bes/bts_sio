# Conditions & Boucles (+ Scanner)
> Conception et développement d'application

**Sommaire**

* [Entrée utilisateur](./cours1.md#entrée-utilisateur)
* [Conditions](./cours1.md#conditions)
* [Boucles](./cours1.md#boucles)
* [Exemple final](./cours1.md#exemple-conditions--boucles-avec-scanner)

## Entrée utilisateur
En programmation il est important de pouvoir permettre à l'utilisateur d'entrer des données. Et ce via un **input**.

En **Java**, pour ce faire on utilise une classe de la bibliothèque standard de Java appelée **Scanner**. On fait donc un import de celle ci, qui se situe dans le package `java.util`.
```java
import java.util.Scanner;
```

Il faut voir le Scanner comme une communication téléphonique. On l'initialise pour démarrer la communication (*appel*), et on ferme celle ci à la fin de la communication (*raccrocher*).

> 💡 **Note**<br>
> Ne pas couper la communication n'entraine pas directement d'erreurs, mais à terme et dans des projets plus importants cela peut consommer des ressources inutilement et ralentir le programme.
```java
// Initialisation
Scanner sc = new Scanner(System.in);

// Fermeture
sc.close();
```

`Scanner nomDuScanner = new Scanner(System.in);` est le code qui permet d'initialiser la communication. Hormis le nom donner au Scanner, il sera toujours écrit comme ceci. 

`new` étant le mot clé faisant référence à la création d'un nouveau Scanner, `System.in` étant le contraire de `System.out` (*qui je le rappelle correspond à la sortie standard, donc afficher du texte dans la console*) permet de récupérer l'entrée (*standard input*) de l'utilisateur dans la console.

> 💡 **Note**<br>
> **console** != **terminal**<br>
> La console est l'interface qui gère les entrées et les sorties.<br>
> Le terminal est un logiciel qui permet d'interagir avec le système via des commandes.

### Assigner les entrées
Maintenant que la communication est établie, il nous faut pouvoir stocker l'information entrée par l'utilisateur.
```java
int a;
double b;
String name;

System.out.print("Entrer un entier : ");
a = sc.nextInt();

System.out.print("Entrer un réel : ");
b = sc.nextDouble();

System.out.print("Entrer votre nom : ");
name = sc.nextLine();
```

La méthode `.nextInt()` spécifie que l'entrée attendue est un **entier**, pareil pour `nextLine()` qui attend une **chaîne caractères**. 

## Conditions
Un programme doit être capable de prendre des décisions. Pour cela on utilise des structures de contrôle, la première étant les **conditions**.

Comme vue précédemment avec [les opérateurs logiques et de comparaisons](./intro.md#opérateur-logique-et-comparaisons), on peut effectuer des tests sur des variables et exécuter une serie d'instructions si les tests sont validés.
### IF ... ELSE
La structure `if` et `else`, se traduit de la sorte : *"Si cette expression est vraie, alors faire ceci. Sinon faire cela."*

**Exemple**
```java
if (a>b){
    System.out.println("a est plus grand que b.");
}
else {
    System.out.println("b est plus grand que a.");
}
```
> ⚠️ **Attention**<br>
> Le `else` est toujours le contraire de l'expression du `if`. Dans notre cas le `else` se déclenche si `a<=b`.
### Vérifier plusieurs conditions à la fois
Imaginons que l'accès à un site soit autorisé uniquement si la personne a au moins 18 ans et possède un compte actif.

On utilise l'opérateur logique `&&` (*ET*) pour vérifier que les deux conditions sont vraies.
```java
if (age >= 18 && compteActif == true) {
    System.out.println("Accès autorisé");
}
else {
    System.out.println("Accès refusé");
}
```
> ⚠️ **Remarque**<br>
> Si la première condition est fausse dans le cas d'un `&&`, alors le programme ne prend pas la peine de vérifier le reste puisqu'il faut que deux conditions soient vraies (évaluation paresseuse).

Autre exemple si on souhaite savoir si une personne bénéficie du tarif réduit, qui ne s'applique qu'aux étudiants et enseignants.

On utilise l'opérateur logique `||` (*OU*) pour vérifier qu'au moins une des conditions est vraie.
```java
if (estEtudiant || estEnseignant) {
    System.out.println("Tarif réduit");
}
```
> 💡 **Note**<br>
> `if (estEtudiant)` revient à faire `if (estEtudiant == true)`. Car la variable est de type boolean et se traduit de la sorte : *"S'il est étudiant alors faire ..."*.

Et enfin, si on souhaite vérifier le contraire d'une condition.

On utilise l'opérateur logique `!` (*NON*).
```java
if (!compteActif) {
    System.out.println("Compte désactivé");
}
```
## Boucles
La deuxième structure de contrôle est la **boucle**, il en existe différents types: 
* **for** : pour ... faire
* **while** : tant que ... faire

Par convention, on utilise **for** quand le nombre d’itérations est connu. **while** convient aux autres cas, et peut aussi servir quand il est connu.
### FOR (pour)
La boucle **for** utilise ce que l'on appelle un indice d'itération `i` (peut prendre le nom que l'on souhaite mais la convention veut `i`).

**Exemple**
```java
// déclaration de l'indice
int i;

// initialisation de l'indice dans l'expression de la boucle
for(i=0;i<=5;i++){}
```

On découpe l'expression de la boucle **for** en 3 parties :

`( indice de départ ; condition ; l'incrémentation ou décrémentation de l'indice )`

**Exemple**
```java
for (int i = 1;i<=5;i++){
    System.out.print(i+" ");
}
// Sortie : 1 2 3 4 5
```
> ⚠️ **Remarque**<br>
> Ici le `i` est déclaré et initialisé dans la boucle **for** ce qui signifie qu'il n'existe que dans la boucle. Si j'essaye de l'appeler en dehors de celle ci, j'aurai une erreur de genre : *"i is not declared"*.

### WHILE (tant que)
La boucle **while** est utilisée pour répéter des instructions autant de fois qu'il faut pour vérifier la condition : `while (condition) {}`.

```java
int a = 10;

while (a > 0){
    System.out.println("a est supérieur à 0.");
    a--;
}
```
On peut aussi itérer un nombre de fois connu comme pour le **for**.
```java
int i = 1;                       // l'indice de départ

while (i<=5){                    // condition
    System.out.print(i+" ");
    i++;                         // l'incrémentation
}
// Sortie : 1 2 3 4 5
```
### BREAK et CONTINUE
Dans les boucles, il est possible de sortir prématurement de celle ci ou de passer directement à la prochaine itération sans exécuter la suite du code.

C'est la qu'interviennent `break` et `continue`.

`break` permet de sortir de la boucle même si la condition ou le nombre d'itération n'etaient pas atteints.

**Exemple**
```java
for (int i = 1;i<=5;i++){
    if (i == 3){
        break;
    }
    System.out.print(i+" ");
}
// Sortie : 1 2
```
On voit bien que l'itération 3, 4 et 5 ont été sautés.

`continue` permet de passer à l'itération suivante (ou pour le **while** revenir à la vérification) sans exécuter la suite du bloc.

**Exemple**
```java
int i = 1;

while (i<=5){
    if (i == 2){
        i++;
        continue;
    }
    System.out.print(i+" ");
    i++;
}
// Sortie : 1 3 4 5
```
On voit qu'on a sauté l'affichage à l'itération `i == 2`.
## Exemple conditions + boucles avec Scanner
On veut pouvoir afficher les **n** premiers carré, mais on ne veut pas afficher le carré de 2.
```java
import java.util.Scanner;

public class Cours {
    public static void main(String[] args){
        // Initialisation de la communication
        Scanner sc = new Scanner(System.in);

        System.out.print("Entrer en entier 'n' : ");
        // assigniation de n
        int n = sc.nextInt();

        // boucle for
        for (int i=1;i<=n;i++){
            // Sauter 2
            if (i==2){
                continue;
            }
            System.out.print(i*i+" ");
        }

        // Fermeture de la communication
        sc.close();
    }
}

// Sortie pour n = 4 : 1 9 16
```
---

[COURS SUIVANT]()

*@j0bes* - BTS SIO 2026