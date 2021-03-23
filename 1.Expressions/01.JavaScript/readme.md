<!-- omit in toc -->
# JavaScript : les deux moteurs d'expressions et les bases du langage

<!-- omit in toc -->
## Durée

:watch: 30 minutes.

<!-- omit in toc -->
## Sommaire

- [Langage de script](#langage-de-script)
- [ExtendScript vs JavaScript](#extendscript-vs-javascript)
- [Les bases](#les-bases)
  - [Var, Let et Const](#var-let-et-const)
    - [Concentrons nous alors sur Let et Const](#concentrons-nous-alors-sur-let-et-const)
  - [Un typage dynamique](#un-typage-dynamique)
  - [Les fonctions](#les-fonctions)
    - [Déclaration de fonction](#déclaration-de-fonction)
    - [Expression de fonction fléchée](#expression-de-fonction-fléchée)
    - [Déclaration ou expression de fonction ?](#déclaration-ou-expression-de-fonction-)
  - [Les objets](#les-objets)
- [La syntaxe](#la-syntaxe)
  - [Les accolades](#les-accolades)
  - [Le point-virgule](#le-point-virgule)
  - [Les incrémentations et décrémentations](#les-incrémentations-et-décrémentations)
  - [Les conditions](#les-conditions)
    - [La triple égalité](#la-triple-égalité)
    - [Notation classique](#notation-classique)
    - [L'opérateur ternaire conditionnel](#lopérateur-ternaire-conditionnel)
  - [Les boucles](#les-boucles)
- [Conclusion](#conclusion)
- [Ressources](#ressources)

Je préfère le rappeler, je ne suis pas un professionnel du code (et encore moins du JavaScript) ! Je vais donc vous présenter les choses simplement, sans entrer dans les détails obscurs que je ne maîtrise pas. Ce que je vais vous apprendre ici ne sera peut-être pas tout à fait juste pour un puriste de la programmation en JavaScript, mais je vais essayer de faire de mon mieux pour que ça reste correct et facile à suivre.

:pencil: Ce chapitre contient beaucoup d'informations qui peuvent être assez difficiles à digérer au début. Lisez-le tranquillement et ne vous prenez pas la tête si vous ne comprenez pas tout, tout de suite. On verra comment mettre tout ça en oeuvre dans les prochains chapitres.

## Langage de script

Dans le monde de la programmation, il existe de nombreux langages. Le JavaScript est un *langage de script*, au même titre que Python, par exemple. Un langage de script doit être interprété et non pas compilé contrairement à d'autres langages tels que le C++ ou le Java. L'interprétation se fait au moment de l'exécution du script (au runtime). C'est la raison pour laquelle on a besoin d'un **moteur JavaScript** (en Python, on parle d'un interpréteur Python).

Le fonctionnement de ce moteur est complexe et nous n'allons pas entrer plus que cela dans les détails. C'est seulement important de savoir que notre code est traité au moment de son exécution et qu'il n'est pas lu au préalable. Cela signifie que si vous faites une erreur dans votre code, vous ne le saurez pas avant de l'avoir exécuté.

JavaScript est un langage de programmation orienté *objet à prototypes*. Si vous avez déjà fait de la Programmation Orientée Objet (POO) "classique" (Python, C++, Java, etc), sachez que le fonctionnement est totalement différent. Nous n'allons pas entrer dans les détails pour le moment car ce n'est pas nécessaire.

:grey_question: *Bon, et du coup, comment ça marche tout ça ?*

En programmation, on utilise des variables (qui nous permettent d'accéder à des données) et des fonctions (blocs d'instructions). Une instruction permet de faire évoluer le programme. Comme JavaScript est un langage de POO, on y retrouve des objets qui contiennent leurs propres variables (membres ou attributs) et leurs propres fonctions (méthodes). Nous détaillerons un peu plus tout cela dans la partie [Les bases](#les-bases).

## ExtendScript vs JavaScript

Comme énoncé dans la partie précédente, ExtendScript est un langage développé par Adobe et qui se base sur une très ancienne version d'ECMAScript (ES) datant de 1999 : ES3. Depuis les deux dernières décennies, les normes ECMAScript ont bien évolué. JavaScript est également un langage basé sur ECMAScript, et depuis la version ES6 (2015), on a tendance à parler de JavaScript "moderne" puisque de nombreuses choses ont changé avec cette mise à jour.

Adobe a décidé d'implémenter un nouveau moteur d'expressions basé sur le JavaScript moderne afin de permettre de meilleures performances et également, pour se remettre un peu au goût du jour. Les deux moteurs sont interchangeables : si vous souhaitez switcher de l'un à l'autre, il vous suffit de modifier un simple paramètre dans les configurations du projet. Cependant, pour la suite de la formation, nous allons utiliser le nouveau moteur JavaScript.

Vous pouvez retrouver les différences notables sur cet [article](https://helpx.adobe.com/fr/after-effects/using/legacy-and-extend-script-engine.html) d'Adobe. Mais si vous êtes ici, je suppose que vous ne vous êtes jamais vraiment plongé dans les expressions auparavant : ainsi, consulter cet article n'a pas trop d'importance pour vous (pour le moment :stuck_out_tongue_winking_eye:).

Bon, et si on voyait vraiment les bases de JavaScript maintenant ? On a quelques petites choses à découvrir avant de se lancer dans l'aventure des expressions ! Et aucune inquiétude, ça peut paraître compliqué au premier abord mais dans la réalité, avec un peu de pratique, ça vient tout seul !

## Les bases

### Var, Let et Const

:warning: Cette partie est un peu avancée et pourrait être quelque peu difficile à conceptualiser au début. Si tout n'est pas totalement clair, ce n'est pas grave. Je pense cependant que c'est important de l'évoquer dès maintenant.

L'un des grands changements importants qu'il y a eu entre l'ExtendScript et JavaScript, c'est la "disparition" du mot-clé *var* au profit des mot-clés *let* et *const*. En vérité, il n'a pas réellement disparu (c'est assez rare qu'une fonctionnalité exploitée abondamment par un langage disparraisse du jour au lendemain) : on dit que le mot-clé *var* est **déprécié**. Et c'est pourquoi, il vaut mieux ne plus l'utiliser ! Cependant, vous ne verrez pas cela dans l'article évoqué précédemment car ce n'est pas un changement ayant un réel impact sur le moteur : si vous utilisez *var*, le moteur d'expressions ne va pas broncher (par contre, moi, oui !).

:grey_question: *Super tout ça mais à quoi ça servait "var" ? Et pourquoi maintenant, un seul mot-clé est remplacé par deux ??*

*var* était le mot-clé utilisé pour déclarer une variable. Le JavaScript est un langage à **typage dynamique** : cela veut dire qu'une variable peut changer de type. Dans les langages de programmation à typage statique, on se doit de déclarer explicitement le type d'une variable : on doit lui dire si la variable contiendra un nombre entier (int), un nombre à virgule flottante (float) ou encore une chaîne de caractères (string). Ce n'est pas le cas en JavaScript, et c'est pourquoi il n'existait qu'un seul mot-clé utile pour déclarer une variable : *var*.

Mais ça, c'était avant ! Le JavaScript est toujours un langage à typage dynamique mais il a tout de même un peu évolué ! Aujourd'hui, on est en mesure de déclarer des variables avec *var* (mais il ne faut plus le faire, je vous le rappelle), avec *let* et avec *const*.

Sachez simplement que *var* a une portée de fonction (function scope) tandis que *let* et *const* ont une portée de bloc (block scope). Si vous ne savez pas ce que ça veut dire, pas d'inquiétude, je serai amené à en parler à nouveau un peu plus tard (quand on parlera des scripts) !

#### Concentrons nous alors sur Let et Const

Autant *let* n'est pas très explicite, autant je pense que *const* l'est davantage..! La différence est très simple (mais très importante) : *let* permet de déclarer des variables "classiques" tandis que *const* permet de déclarer des variables constantes. Une variable constante ne peut être assignée qu'une seule fois : on ne peut pas la réassigner plus tard.

```js
const a = 5;
a = 6; // Erreur, c'est impossible.

let b = 3;
b = 4; // Aucun soucis, la variable a le droit d'être réassignée.
```

On dit d'une variable constante qu'elle est immutable.

:grey_exclamation: *C'est marrant de dire "variable constante" si elle ne peut pas être variable !* :sweat_smile:

C'est là que ça devient plus compliqué. Le contenu d'une variable constante peut tout de même "évoluer".

En fait, il faut un peu voir les variables comme des étiquettes que l'on acolle sur des données. Les variables *let* seraient alors des post-it (on peut les coller puis les décoller puis les recoller autre part) tandis que les variables *const* seraient des étiquettes à la super glue (une fois collées quelque part, on ne peut plus les détacher).

Maintenant, supposons que l'on colle cette étiquette à la super glue sur une boîte en plastique. L'étiquette fait référence au contenu de la boîte. Mais nous, rien ne nous empêche d'ouvrir cette boîte et modifier ce qu'elle contient. C'est pour cela que le contenu d'une variable constante n'est pas figé dans le marbre, il peut évoluer. Et c'est pourquoi il faut faire très attention.

Aujourd'hui, l'immutabilité devient de plus en plus populaire, et c'est la raison pour laquelle le mot-clé *const* doit être utilisé en priorité, le plus souvent possible ! Puisque, même si le contenu de la variable peut **potentiellement** évoluer, c'est une sécurité en plus !

:grey_exclamation: *Mais pourtant tout à l'heure, on a vu que ça faisait une erreur si l'on voulait modifier la valeur de la variable !*

Oui, tout à fait car nous avons essayé de réassigner la variable *a* (coller l'étiquette autre part). Cependant, on aurait parfaitement pu faire ceci :

```js
const a = [5]; // Tableau avec un seul élément : 5.
a.push(6); // Maintenant, tableau avec deux éléments : 5 et 6.
```

Ici, nous n'avons tenté aucune réassignation. Nous avons simplement modifier le contenu de l'objet référencé par la variable. Ce n'est pas évident au début, mais on s'y fait rapidement ! La seule chose à retenir, c'est que l'on doit **utiliser const en priorité** !

:grey_question: *Pourquoi on parle de tout ça ?*

Vous serez amenés à rechercher sur des forums (on en parle dans la partie suivante du cours) des réponses à vos questions, et vous tomberez très probablement sur du "vieux code" (du code en ExtendScript). Il faudra alors l'adapter en JavaScript moderne et remplacer les *var* par des *const* (ou à défaut, des *let*) ! Et c'est à ce moment là que l'article dont je vous ai parlé plus tôt pourra vous être utile ! En effet, entre les deux moteurs proposés par Adobe, il y a des différences de syntaxe, etc.

:pencil: Il se peut que remplacer les *var* puisse poser quelques soucis dans l'interprétation du code. Vous vous souvenez quand j'ai parlé de la portée des variables ? Eh bien, *var* a une portée plus grande que *let* et *const*, ce qui justement a été une cause de problème par le passé. Donc il se peut qu'une variable ne soit plus accessible comme prévu si vous remplacez le mot-clé. Dans ce cas là, il faudra aviser !

### Un typage dynamique

Comme on vient de le voir, un typage dynamique n'impose pas de définir explicitement le type d'une variable. Une variable *let* peut même tout à fait être réassignée à un autre type.

```js
let a = 5; // type implicite : number.
a = "Hello JavaScript!"; // type implicite : string.
```

Le typage dynamique peut sembler pratique puisque l'on n'a pas besoin de se poser de question sur la nature de la variable, mais cela peut justement nous porter à defaut. C'est pourquoi utiliser *const* nous assure un peu plus de sécurité. On est sûr que la variable ne peut pas changer de type. De plus, *const* nous oblige à assigner une valeur à la variable au moment de sa déclaration, contrairement à *let*. Cela nous permet de rapidement "voir" le type implicite de la variable.

```js
let a; // Déclaration sans assignation.
a = 5; // Assignation à postériori.

const b; // Erreur : il faut assigner une valeur directement.
const c = 10; // Déclaration avec assignation. On suppose directement que le type implicite est : number.
```

### Les fonctions

Nous venons de voir les variables, qui nous permettent de faire référence à des valeurs/objets. Voyons maintenant les fonctions. Les fonctions, avec les variables, sont probablement les éléments les plus importants dans la programmation : on ne pourrait rien faire sans eux.

Une fonction est un bout de code qui permet d'exécuter un ensemble d'instructions. Pour exécuter cette fonction à un moment particulier, on "appelle" cette fonction. Tout dépend comment elle est définie, une fonction peut prendre zéro, un ou plusieurs paramètres. Un paramètre accueille une variable afin que la fonction en ait connaissance. On dit alors qu'on passe la variable en argument de la fonction.

En JavaScript, il existe grossièrement deux façons de définir une fonction : les déclarations de fonctions et les expressions de fonctions. Depuis ECMASCript 6 (2015), une nouvelle notation est apparue facilitant l'écriture des expressions de fonctions : la notation fléchée.

#### Déclaration de fonction

Pour écrire une fonction avec une déclaration de fonction, on utilise le mot-clé *function* selon la syntaxe suivante :

```js
function maFonction(parametre) {
  // Code décrivant la fonction.
}
```

- *function* : mot-clé pour dire que l'on va définir une fonction.
- *maFonction* : nom donné à la fonction.
- *parametre* : premier (et seul dans ce cas) paramètre de la fonction.

L'appel de la fonction se fera ainsi :

```js
const a = 5;
maFonction(a);
```

#### Expression de fonction fléchée

Pour définir la même fonction que juste au-dessus, nous pouvons utiliser cette syntaxe :

```js
const maFonction = (parametre) => {
  // Code décrivant la fonction.
}
```

Ici, en vérité, on écrit un condensé de plusieurs étapes. La notation fléchée permet de faire une expression de fonction anonyme (la fonction n'a pas de nom). Ensuite, on assigne cette fonction anonyme à la variable constante *maFonction*. On peut désormais appeler cette fonction exactement comme dans le cas précédent :

```js
const a = 5;
maFonction(a);
```

#### Déclaration ou expression de fonction ?

Comme vous vous en doutez sûrement, il n'y a pas que la syntaxe qui change. En réalité, une déclaration de fonction ne réagit pas comme une expression de fonction. Dans un contexte d'utilisation simple, utiliser l'une ou l'autre n'a pas vraiment d'incidence : leur comportement sera similaire. Pour le bien de la lisibilité et de la compréhension, nous utiliserons la **déclaration de fonction** : en effet, nous pouvons ainsi savoir en un coup d'oeil que l'on a affaire à une fonction. Il y a également d'autres différences que je n'aborderai pas ici. Je vous laisse le soin de regarder dans les ressources si l'envie vous en prend (mais si vous êtes tout débutant dans la programmation, cela risquerait de vous embrouiller un peu) !

### Les objets

Comme je l'ai précisé au début de ce chapitre, le JavaScript est un langage de Programmation Orientée Objet (POO). Et en réalité, en JavaScript, on peut dire que presque tout est objet. Il existe même un objet global qui "englobe" tout. Sur After Effects, on peut y accéder avec `$` (voire `$.global`).

:pencil: Sur After Effects, une variable déclarée avec *var* devient la propriété de l'objet global (mais on ne peut pas y accéder par celui-ci, bizarrement). C'est également le cas pour les déclarations de fonction. C'était une simple parenthèse, rien de très important !

Un objet peut contenir des attributs (ses propres variables) et des méthodes (ses propres fonctions). Certaines méthodes sont immutables, c'est-à-dire qu'elles ne modifient pas le contenu de l'objet tandis que d'autres modifient l'objet.

```js
const a = [5]; // Tableau avec un seul élément : 5.
a.push(6); // Maintenant, tableau avec deux éléments : 5 et 6.

a.some(function(elt) { return elt % 2 === 0 });

a.length; // Affiche la longueur du tableau : 2.
```

- La méthode *push()* de l'objet de type Array permet d'ajouter un élément au tableau. Cela signifie donc que cette méthode modifie l'objet : elle n'est pas immutable.
- La méthode *some()* vérifie si au moins un élément du tableau passe le test implémenté par la fonction fournie. Elle renvoie un booléen indiquant le résultat du test. Ici, on teste si au moins un des éléments est pair. Cette méthode ne modifie par l'objet en lui-même : c'est donc une méthode immutable.
- L'attribut *length* de l'objet de type Array permet de connaître le nombre d'éléments qui le composent.

On aura l'occasion de découvrir plein de méthodes et attributs relatifs aux différents objets dans After Effects !

## La syntaxe

### Les accolades

Pour créer un nouveau bloc d'instructions, JavaScript repose sur les accolades (comme dans beaucoup de langages, à l'exception du Python).

```js
function maFonction() {
  console.log("HelloWorld!");
  let a = 5;
  a = a * 2;
  return a;
}
```

L'ensemble des instructions de la fonction sont à l'intérieur des accolades `{}`.

### Le point-virgule

En JavaScript, le point-virgule pour terminer une expression est optionnel. Cependant, le moteur implémenté dans After Effects n'est pas content si l'on n'en utilise pas. C'est pourquoi, avec les expressions, nous devons terminer chaque instruction par un point-virgule (sauf la dernière, où le point-virgule est optionnel).

### Les incrémentations et décrémentations

En JavaScript, on peut aisément incrémenter et décrémenter des variables numériques.

```js
let a = 2;

a = a + 1; // Maintenant, a = 3.
a += 1; // Maintenant, a = 4.
a++; // Maintenant, a = 5.

a -= 5; // Maintenant, a = 0.
a--; // Maintenant, a = -1.
```

- `++` incrémente de 1 et `--` décrémente de 1. A noter que l'on peut mettre l'opérateur avant OU après le nom de la variable : `a++` est pareil que `++a`.
- `+= qqch` incrémente de *qqch* et `-= qqch` décrémente de *qqch*. Fonctionne aussi avec `*=` et `/=`.

### Les conditions

#### La triple égalité

En JavaScript, il existe deux opérateurs permettant de tester une égalité : `==` et `===`. 

JavaScript est un langage à typage faible : il s'autorise donc facilement des conversions (transtypages) implicites. C'est le cas avec le double égal. Or, comme cela peut porter à confusion, on utilise (presque) **toujours** l'opérateur de **triple égalité** afin de s'assurer que les deux valeurs sont bien identiques, en tout point.

#### Notation classique

Parfois, nous avons besoin de vérifier des conditions avant d'effectuer une action. Pour cela, les mots-clés sont `if`, `else if` et `else`.

- `if` correspond à "si".
- `else if` correspond à "sinon, si".
- `else` correspond à "sinon".

Par exemple :

```js
if (a >= 3) {
  console.log("3 ou plus !");
}
else if (a >= 0) {
  console.log("Entre 0 et 3 !");
}
else {
  console.log("Négatif !")
}
```

Ici, dans l'ordre :
- On regarde si la variable `a` est supérieure ou égale à 3. Si c'est le cas, on entre dans le bloc d'instructions du `if`, on affiche le message `3 ou plus !` et c'est tout.
- Si ce n'est pas le cas, on regarde si la variable `a` est supérieure ou égale à 0. Si oui, on entre dans le `else if` et on affiche alors `Entre 0 et 3 !`.
- Si ce n'est toujours pas le cas, alors on entre dans le `else` et on affiche : `Négatif !`

#### L'opérateur ternaire conditionnel

Parfois, on souhaite mettre une condition dans l'assignation d'une variable. Pour ce faire, on utilise l'opérateur ternaire.

```js
const a = 5;

const b = (a > 3) ? 1 : 0; // b = 1.
const c = (a > 7) ? 1 : 0; // c = 0.
```

L'opérateur ternaire s'écrit donc en 3 morceaux, comme son nom l'indique :
- la condition.
- la valeur si la condition est vérifiée.
- la valeur si la condition n'est pas vérifiée.

`condition ? valeur si oui : valeur si non`

### Les boucles

Quand on a besoin de répéter plusieurs fois un bloc d'instructions, on le place dans une boucle. Il existe différents types de boucles mais on va uniquement voir la plus pratique pour nous : la boucle `for`. (On en verra d'autres pour les scripts)

```js
for(let i = 0; i < 5; i++) {
  console.log(i);
}

// Affichera :
// 0
// 1
// 2
// 3
// 4
```

Une boucle `for` prend 3 arguments :
- le premier, c'est la variable d'indice.
- le deuxième, c'est la condition qui nous autorise ou non à entrer dans la boucle.
- le troisième, c'est l'action à effecter sur la variable d'indice.

Ici :
- on déclare une variable `i` qui vaut 0. On la déclare avec `let` car on va l'incrémenter par la suite.
- on dit que l'on va entrer dans la boucle seulement si `i < 5`.
- on incrémente de 1 la variable `i` à chaque fin de boucle.

L'ensemble de ces instructions fait donc en sorte que l'on passe exactement 5 fois dans la boucle avec `i` ayant pour valeurs : 0, 1, 2, 3 et 4.

## Conclusion

Cette page était très fournie en informations et ça fait beaucoup de choses à digérer. Si vous n'avez pas tout retenu, ce n'est pas grave. L'important, c'était de voir un peu le fonctionnement et de découvrir les outils de base qui sont à notre disposition pour écrire du code. On verra dans les prochains chapitres comment mettre tout cela en oeuvre, donc pas d'inquiétude ! :wink:

## Ressources

[Les bases de JavaScript](https://developer.mozilla.org/fr/docs/Learn/JavaScript/Objects/Basics)

[JavaScript for Beginners (très très bonne playlist)](https://www.youtube.com/playlist?list=PLRL3Z3lpLmH08M6j9BozZyJq1QZYbIDAQ)

[POO en JavaScript](https://buzut.net/programmation-orientee-objet-javascript/)

[Fonctions et portée des fonctions](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Fonctions)

[Function statement](https://www.freecodecamp.org/news/constant-confusion-why-i-still-use-javascript-function-statements-984ece0b72fd/)

[Global object](https://javascript.info/global-object)

[The Global object in AE](https://blob.pureandapplied.com.au/the-global-object-in-after-effects/)

-----

:arrow_backward: [Introduction](https://github.com/Julien-Haudegond/Formation-Code-After-Effects/tree/main/1.Expressions/00.Introduction)

:arrow_forward: Page suivante non disponible pour le moment.
