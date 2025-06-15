---
title: "Bonus 2 : Les guides de styles Lua"
date: 2022-02-24
---

Vos variables peuvent avoir besoin des mêmes données, et donc d’avoir potentiellement les mêmes noms !

Si vous nommez une variable globale **x** ou **y**,  **name** ou **vie** etc.

Vous risquez d’avoir des soucis car plusieurs variables pourraient avoir le même nom pour la même chose, le joueur ou un ennemi dispose d'une position à l'écran x et y, mais également d’un montant de points de vie et d’un nom… Alors comment Faire ? =)

Solution que l'on a utilisé au début des cours :

```
heroX = 10
heroY = 15
heroName = "Cromi" ennemiX = 50
ennemiY = 70
ennemiName = "Maboule"
```

On appelle cela des conventions de nommages. Elles s’utilisent aussi bien pour les variables que les fonctions, etc.

Ces conventions de nommages sont accessibles dans des Guides de style.

Il en existe plusieurs différents déjà pour chaque langage et parfois plusieurs approches différentes pour un même langage, à vous d’en trouver un qui vous convient et de l'adopter pour votre code =)

Même si vous ne vous documenter pas tout de suite sur ce sujet, ne vous inquiétez pas car pendant les différentes phases d'évolution des chapitres que nous verrons ensemble, je vous accompagnerais petit à petit vers le style que j’utilise et vous en connaîtrez au moins un, le mien…

  
C'est bien d'avoir pris conscience que cela existe, ainsi plus tard si cela vous intéresse vous pourrez toujours faire vos recherches et trouver votre propre style également =)

L'intérêt des styles c’est d’avoir des automatismes réguliers qui respecte une structure habituelle. Ainsi à la lecture de votre code, et ceux du début à la fin de celui-ci cela doit respecter cette même logique tout le long.

Au début il est tout à fait normal de ne pas y arriver facilement, mais avec le temps, de la pratique et un peu d'effort de votre part vous progresserez naturellement déjà sur vos réalisations, mais également sur la structure de votre code (le style).

  
Avec le temps, vous finirez sûrement par vous poser vous-même la question de comment bien/mieux organiser mon code ? Vous tirerez vos propres conclusions, il n’y a que vous qui pouvez avoir vos réponses, car c’est votre logique, votre vision des choses, etc.

## Le Style Officiel recommandé dans la documentation de référence (en anglais) :

[http://lua-users.org/wiki/LuaStyleGuide](https://www.google.com/url?q=http://lua-users.org/wiki/LuaStyleGuide&sa=D&ust=1600806908574000&usg=AOvVaw0KBv75xWrZXP7mXM4sXxKr)

- D’autres Styles non officiels (en français) :

[](https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LI-C "https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LI-C")[](https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LI-C)[Tutoriel Lua : Guide de Style (developpez.com)](https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LI-C)

Vous trouverez d'autres guides de style sur internet, à vous de choisir celui qui vous convient le mieux.

Le but étant d'avoir la même structure de code, afin de s'y retrouver quelques semaines ou mois plus tard en revenant sur vos anciens projets.

* * *
