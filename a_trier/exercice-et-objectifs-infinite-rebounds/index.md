---
title: "Tp : Mini-jeu : Infinite Rebounds"
date: 2022-02-26
---

Ceci est un exercice avec les Objectifs suivants :

### L'exercice que vous devez réaliser :

- Créer 3 Objets Rectangles.

- Les Objets Rectangles devront rebondir à l'infini sur les côtés de la fenêtre (renvois de vélocité).

- Les Objets Rectangles doivent avoir une couleur différentes, afin de les différencier.

##### Le kit indispensable :

* * *

love.graphics.setColor(r,g,b,a)

```
love.graphics.setColor( red, green, blue, alpha ) 
```

**Arguments**

[number](https://love2d.org/wiki/number) `red` la valeur de _rouge_ de 0 à 1 (nombre décimal)

[number](https://love2d.org/wiki/number) `green` la valeur de _vert_ de 0 à 1 (nombre décimal)

[number](https://love2d.org/wiki/number) `blue` la valeur de _bleu_ de 0 à 1 (nombre décimal)

[number](https://love2d.org/wiki/number) `alpha (1)` la valeur de l'_Alpha_ de 0 à 1 (nombre décimal).

_L'alpha, c'est la valeur de transparence de couleur que vous allez utiliser._  
Une valeur alpha _à 0 (zéro) sera invisible et à un (1) elle sera très prononcée._

* * *

Exemple de couleurs simples :  

```
love.graphics.setColor( 1, 1, 1, 1 ) -- blanc

love.graphics.setColor( 1, 0, 0, 1 ) -- rouge

love.graphics.setColor( 0, 1, 0, 1 ) -- vert

love.graphics.setColor( 0, 0, 1, 1 ) -- bleu

love.graphics.setColor( 0, 0, 0, 1 ) -- noir

love.graphics.setColor( 0.25, 0.25, 0.25, 1 ) -- gris
```

Lien de couleurs de référence : [Code couleur RVB (toutes-les-couleurs.com)](https://www.toutes-les-couleurs.com/code-couleur-rvb.php)

_Pensez à diviser la valeur RGB par 255_

**Exemple pour convertir la couleur "Lavallière" :**

```
Valeur  RGB : 
(143, 89, 34) -- (Red, Green, Blue)
```

```
Valeur pour Love2D : 
(143/255,  89/255,  34/255, 1) -- (Red, Green, Blue, Alpha)
```

### Idées d'améliorations :

- Mettre un alpha transparent sur les Objets Rectangles, ça rendra l'effet plus joli.

- Rajouter plus d'Objets Rectangles =)

- Créer d'autres Objets de formes différentes

**Maintenant @ vos Claviers !**

\[subpages\]

* * *
