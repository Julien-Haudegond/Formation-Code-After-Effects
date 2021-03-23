<!-- omit in toc -->
# Introduction : les **Expressions** dans Adobe After Effects

<!-- omit in toc -->
## Durée

:watch: 5 minutes.

<!-- omit in toc -->
## Sommaire

- [Vidéo](#vidéo)
- [Kezako ?](#kezako-)
- [Pourquoi ?](#pourquoi-)
  - [Exemples d'utilisation](#exemples-dutilisation)
- [ECMAScript : la base des expressions](#ecmascript--la-base-des-expressions)
- [In English, please !](#in-english-please-)
- [Ressources](#ressources)

## Vidéo

[![Vidéo](https://img.youtube.com/vi/4l9TOw0K0UE/maxresdefault.jpg)](https://www.youtube.com/watch?v=4l9TOw0K0UE)

## Kezako ?

Le logiciel Adobe After Effects est un logiciel d'animation, de motion design et de compositing. Bien qu'il dispose de nombreux outils et effets disponibles sous forme "graphique", il est aussi doté d'un éditeur d'expressions. Savoir se servir de cet éditeur d'expressions est un atout majeur puisqu'il permet de travailler différemment au sein du logiciel (et la plupart du temps, de travailler mieux :smirk: ) ! Utiliser des expressions peut nous permettre de relier des propriétés entre elles, de centraliser des données, de contrôler tous les calques à partir d'un seul, de limiter l'utilisation des keyframes afin d'avoir un projet plus modulable, etc. Les possibilités sont très grandes. Comme nous le verrons, les expressions sont abondamment utilisées pour les projets *templates*. 

## Pourquoi ?

À première vue, on peut se demander s'il y a un réel intérêt à utiliser l'éditeur d'expressions. Après tout, ça n'ajoute aucune fonctionnalité supplémentaire au logiciel. Certes, mais ça débloque des fonctionnalités "cachées". Et ces fonctionnalités "cachées" sont extrêmement puissantes. Utiliser les expressions permet d'exploiter le logiciel à son plein potentiel. Et une fois qu'elles sont bien prises en main, elles simplifient et améliorent considérablement le workflow. Voici quelques exemples d'utilisation qui, je l'espère, vous mettront l'eau à la bouche.

### Exemples d'utilisation

- Animation générée *procéduralement* plutôt que manuellement avec des keyframes.
- Palette de couleurs : Un seul clic suffit à modifier le coloris de tous les éléments de la composition. Bien plus rapide et pratique que de naviguer à travers les propriétés de chacun des calques.
- Génération automatique de synthés (low-thirds) : la taille du low-third s'adapte au nom qu'on lui donne.
- Contrôle des points d'un *path* (pour un masque ou un calque de forme) à partir d'objets nuls.
- Simulation d'une interface HUD complexe qui se met à jour grâce à un fichier externe JSON.
- Projet *template* ajustable en quelques clics, sans avoir à chercher ce qu'il faut modifier et comment.
- Etc.

## ECMAScript : la base des expressions

À l'origine, l'éditeur d'expressions dans After Effects se base sur un langage de script développé par Adobe et qui s'appelle **ExtendScript**. Ce langage est lui-même basé sur la norme ECMAScript 3 (1999). Cela explique la forte ressemblance entre ExtendScript et JavaScript (ancienne génération).

Avec la version CC2019, Adobe a implémenté un nouveau moteur d'expressions, intitulé moteur JavaScript, basé sur la nouvelle norme ECMAScript 2018. Ce moteur est bien plus performant et permet surtout d'écrire des expressions avec du JavaScript dit *moderne*.

Dans la prochaine partie, nous ferons une brève comparaison de ces deux moteurs et nous verrons notamment la différence de syntaxe entre ExtendScript et JavaScript *moderne*. Nous aborderons les bases du langage (pas d'inquiétude, ça restera très simple pour commencer :relaxed: ) puis nous utiliserons exclusivement le nouveau moteur JavaScript. **Cela implique donc que votre version d'After Effects soit CC2019 ou plus récente.**

## In English, please !

Une expression, c'est une ligne de code que vous écrivez vous-même (ou non, mais on verra ça plus tard :stuck_out_tongue_winking_eye: ). Pour faire référence à un effet, par exemple, on l'appelle par son nom (c'est plutôt logique après tout). Cela signifie qu'une expression écrite dans une version francophone d'After Effects ne sera pas bien interprétée dans une version anglophone, et vice-versa (et ce, pour tous les langages) puisque les noms des effets varient en fonction de la langue. C'est assez problématique. Et c'est pourquoi, il faut faire un choix. Le choix de la langue du logiciel.

Pour mon cas, j'utilise After Effects dans sa version anglophone et je vous conseille de faire la même chose. Si vous vous demandez pourquoi, je peux vous énoncer plusieurs de mes raisons :

- La plupart des tutoriels et documents que vous trouverez seront en anglais. C'est d'ailleurs pour cela que je fais cette formation : il existe assez peu de ressources en français au sujet de la programmation dans After Effects.
- La programmation, qu'on le veuille ou non, se fait en anglais. Toute la documentation que vous trouverez sera en anglais, les forums que vous serez à même de consulter seront en anglais, tout est en anglais !
- Le monde des effets spéciaux, du motion design ou encore de l'animation évolue en anglais. Donc autant prendre en main dès aujourd'hui les outils dans cette langue.
- Les traductions françaises sont parfois, à mon goût, assez mauvaises. :grimacing:

De plus, si vous utilisez actuellement After Effects en français, il est extrêmement simple de le passer en anglais (et de faire machine arrière à n'importe quel moment si vous le désirez). Voici la procédure pour Windows (je ne sais pas comment cela fonctionne sur MacOS) :

```
Rendez-vous dans votre dossier personnel "Documents" et créez-y un fichier texte vide que vous appelez : ae_force_english.txt
```

Et voilà, le tour est joué ! After Effects est désormais en anglais ! (Ne me demandez pas par quelle magie cela fonctionne, je n'en ai pas la moindre idée, ahah)

:warning: Le nom du fichier est bien **ae_force_english** et **.txt** désigne son extension. Pour ma part, j'ai activé l'affichage des extensions de fichiers dans mon explorateur Windows donc il ne peut pas y avoir de malentendus. Cependant, si ce n'est pas le cas chez vous, il ne faudrait pas que le fichier soit finalement défini comme "ae_force_english.txt.txt" !

## Ressources 

- [Exemples d'expressions](https://helpx.adobe.com/fr/after-effects/user-guide.html/fr/after-effects/using/expression-examples.ug.html)
- [Principes de base des expressions](https://helpx.adobe.com/fr/after-effects/user-guide.html/fr/after-effects/using/expression-basics.ug.html)
- [ExtendScript](https://en.wikipedia.org/wiki/ExtendScript)

-----

:arrow_forward: [Le JavaScript](https://github.com/Julien-Haudegond/Formation-Code-After-Effects/tree/main/1.Expressions/01.JavaScript)
