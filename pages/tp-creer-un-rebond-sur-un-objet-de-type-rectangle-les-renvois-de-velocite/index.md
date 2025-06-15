---
title: "Tp : Créer un rebond sur un Objet de type Rectangle (les renvois de vélocité)"
date: 2022-02-26
---

### Introduction

_Rappel_

**Nous savons comment déplacer un objet avec :**  

```
function love.update(dt)
 Objet.x = Objet.x + (Objet.vx * dt) 
 Objet.y = Objet.y + (Objet.vy * dt)
end
```

**Nous savons comment détecter les rebonds de la fenêtre :**

```
-- Rebonds sur les Bords Gauche et Droit de L'écran :
if Objet.x + Objet.w >= love.graphics.getWidth() then
  -- rebonds de Droite
elseif Objet.x <= 0 then
  -- rebonds de Gauche
end

-- Rebonds sur les Bords Haut et Bas de L'écran :
if Objet.y + Objet.h >= love.graphics.getHeight() then
  -- rebonds du Bas
elseif Objet.y <= 0 then
  -- rebonds du Haut
end
```

### Qu'est-ce qu'un renvois de vélocité ?

Nous avons donc deux vélocités VX et VY lorsque notre Objet se déplace.

Quand notre Objet touchera les bords de l'écran, nous effectuerons un renvoi assez simple.

Nous allons simplement appliquer la vélocité opposée de l'Objet !

un renvoi est donc une force opposée à la sienne !

#### L'opposé d'un nombre c'est quoi ?

prenons un nombre entier qui a une valeur de _12_.

Son opposé, c'est _\-12_

**Démonstration :**

`(12) + (-12) = 0`

l'opposé de _12_ est bien _\-12_, car le résultat est _nul_ !

**_rappel pour ceux qui ont oublié :_**

un résultat _nul_, c'est une valeur égale à _**0**_ (zéro)

```
nul == 0
```

**Logique :**

l'opposé de `12` c'est bien `-12`

l'opposé de `-12` c'est bien `12`

**En conclusion :**

- l'opposé d'un nombre positif c'est sa valeur identique en négatif.

- l'opposé d'un nombre négatif c'est sa valeur identique en positif.

**Plus d'infos sur les nombres opposés :** [Opposé (mathématiques) — Wikipédia (wikipedia.org)](https://fr.wikipedia.org/wiki/Oppos%C3%A9_\(math%C3%A9matiques\)#:~:text=L%27oppos%C3%A9%20d%27un%20nombre,ajout%C3%A9%20%C3%A0%20n%2C%20donne%20z%C3%A9ro.)  

### Comment opposer la Vélocité d'une variable ?

**Exemple avec une Vélocité égale à 10 :**

```
Velocite = 10
```

démonstration de l'opposition :

L'opposé de `10` c'est donc `-10`

exemple avec du code pour trouver l'opposé :

```
10 = 0 - 10
```

## **La formule pour opposer une variable est donc la suivante :**

```
Velocite = 0 - Velocite 
```

ou directement :

```
Velocite = -Velocite 
```

Personnellement, je préfère la formule avec l'utilisation du nombre Zéro

```
Velocite = 0 - Velocite
```

je trouve cette formule visuellement plus parlante, mais ça reste mon choix personnel.

### Appliquer le Renvois à notre Objet sur les bords de la fenêtre

**Pseudo code :**

- Si l'**Objet** touche un des bords **Gauche** ou **Droite** _ALORS je lui renvoie_ sa vélocité **VX**

- Si l'**Objet** touche un des bords **Haut** ou **Bas**  _ALORS je lui renvoie_ sa vélocité **VY**

### Essayez de le faire vous-même, ensuite seulement regarder la solution a la page suivante !

1. Créer un Objet Rectangle avec les paramètres suivants : x = 300 y = 250 w = 200 h = 100 vx = 500 vy = 120

3. Coder son déplacement

5. Coder les Renvois sur les bords de la fenêtre de Love2D

**Si vous n'y arrivez pas :** **Essayer de faire des Croquis sur une feuille pour "visualiser" ce que vous devez réaliser.**

**Essayez au moins pendant 10-15 minutes !**

**Aidez-vous des formules que nous avons vues ensemble depuis le début de ce cours.**

**Au-delà des 20-25 minutes d'essai si vous n'y arrivez toujours pas, faites une pause et recommencer à tête reposée au moins une dernière fois pendant encore au moins 10-15 minutes.**

* * *
