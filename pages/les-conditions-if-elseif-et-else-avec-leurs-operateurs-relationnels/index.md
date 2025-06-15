---
title: "Les conditions IF, ELSEIF et ELSE avec leurs Opérateurs Relationnels"
date: 2022-02-24
---

##  Les Conditions c'est quoi ?

Une condition, c'est un test logique exécuter dans notre code et celui-ci nous retourne une réponse simple : vrai ou faux ?

avant de voir les opérateurs logiques, voyons déjà comment construire une condition, nous les appellerons les **Boucles Conditionnels**

## Les Boucles Conditionnels

Découvrons ensemble les boucles conditionnelles.

Elles servent à contrôler une condition, dans le cas où la condition est vraie, on effectue alors l’action qui se trouve au sein de la boucle conditionnelle.

Dans une boucle conditionnelle, le code qui se situe dans le corps de la boucle ne s'exécute qu’une seule fois.

## Condition IF

Voyons le pseudo-code ensemble, du pseudo-code c’est l'interprétation d’un algorithme de programmation dans un langage naturel (dans notre cas en français).

Pseudo-code d’une boucle conditionnelle :

```
SI (cette condition est vraie) ALORS
	exécute ceci (corps de la boucle conditionnelle)
FIN
```

Syntaxe d’une boucle conditionnelle :

```
if condition then
   -- corps de la boucle conditionnelle
end
```

petit exemple simple :

```
condition = true
test = 0

if condition then
  test = 1
end

print(test)
```

sortie console :

```
1
```

Comme condition vaut true (vrai) donc la boucle s’effectue et exécute le corps de celle-ci.

Cependant si nous voulons contrôler par exemple si 5 est plus grand que 3 nous aurons besoin des opérateurs relationnels.

* * *

## Les Opérateurs Relationnels.

Ils servent à comparer des expressions tels que : est plus grand que, est plus petit que, est égale à, est différent de, etc.

| \== | égalité |
| --- | --- |
| ~= | différent (inégale) |
| < | plus petit |
| \> | plus grand |
| <= | plus petit ou égale |
| \>= | plus grand ou égale |

|  _Ne pas confondre entre **\=** et **\==**   car **\=** sert à assigner une valeur et **\==** sert à vérifier une égalité_ |
| --- |

  
Un exemple :  
  
Dans un jeu nous voulons contrôler si notre variable de total de pièces ramassées est bien égale à 100 pièces ?  
\- Si c’est le cas on veut rajouter une vie au joueur.

Pseudo-code d’utilisation d’un opérateur relationnel :

| SI totalPieces égale 100 ALORS   \> vieHero vaut vieHero + 1   FIN |
| --- |

Syntaxe d’utilisation d’un opérateur relationnel :

```
if totalPieces == 100 then
        vieHero = vieHero + 1
end
```

* * *

exemple :

```
totalPieces = 100
vieHero = 0

if totalPieces == 100 then
        vieHero = vieHero + 1
end

print(vieHero)
```

sortie console :

```
1
```

Ça fonctionne plutôt bien =)

C’est pratique certes, mais si nous voulons tester plusieurs cas de figures différents, on risque fortement de rencontrer des problèmes…

Voyons un autre exemple :  
le joueur doit posséder une clé pour ouvrir une porte, on veut vérifier si le joueur possède une clef, s’il a une clef en sa possession alors on ouvre la porte et on lui retire sa clef.

```
clef = true
porteOuverte = false

if clef == true then
 print("Vous possédez la clef ! La porte s'ouvre !")
 porteOuverte = true
 clef = false
end
--

if clef == false then
 print("Pour ouvrir la porte, il vous faut la clef !")

  porteOuverte = false
end

print("porte ouverte ? "..porteOuverte)
```

sortie console :

```
Vous possédez la clef ! La porte s'ouvre !
Pour ouvrir la porte, il vous faut la clef ! porte ouverte ? false
```

Notre joueur à bien la clef, donc on ouvre la porte, mais le deuxième cas devient aussi vrai, car la clef passe à false une fois la porte ouverte…

Donc notre  joueur sera perdu et va se poser la question suivante :  
Elle est ouverte ou pas cette porte finalement ?  
Pourquoi elle ne s'ouvre pas alors ?  
pourtant j’avais la clef, non ?  
Pour remédier à cela il existe d’autres comparaisons qui s’ajoute à la boucle conditionnel IF.

## Condition ELSEIF et ELSE.

Voyons leurs Pseudo-code :

| IF = SI | SI condition1 ALORS exécution et FIN |
| --- | --- |
| ELSEIF = SINON SI | SINON SI condition2 ALORS exécution et FIN |
| ELSE = SINON | SINON  exécution et FIN |

Syntaxe boucle conditionnel if, avec un  elseif :

```
if condition1 then -- Si condition1 est vrai alors
  fais ceci
elseif condition2 then -- Sinon Si condition2 est vrai
  fais cela
end
```

Syntaxe boucle conditionnel if, avec un else :

```
if condition1 then -- Si condition1 est vrai alors
  fais ceci
else -- Sinon
  fais ça alors
end
```

Syntaxe boucle conditionnel if, avec un  elseif et un else :

```
if condition1 then -- Si condition1 est vrai alors
  fais ceci
elseif condition2 then -- Sinon Si condition2 est vrai
  fais cela
else -- Sinon
  fais ça alors
end
```

_**Attention !**_ 

_Une fois qu’une condition est vraie, les conditions suivantes ne sont plus vérifiées !_

_C’est normal, car le test conditionnel est terminé et le code continue alors de s'exécuter après le **end** de la condition._

## Exercice

  
Maintenant avec les nouvelles syntaxes que vous venez d’apprendre.

Essayez de corriger notre exemple avec la clef et la porte qui ne s’ouvre pas !

rappel :

| initialiser une variable **porteOuverte** à false initialiser une variable **clef** à true afficher le texte suivant si la porte s’ouvre :   Vous possédez la clef ! La porte s'ouvre !   puis mettre **porteOuverte** à true et clef à false Sinon afficher le texte suivant :   Pour ouvrir la porte, il vous faut la clef !   mettre **porteOuverte** à false |
| --- |

Solution en cours d'écriture par vous même...

![](images/loading.png)

* * *

##### correction/solution :

```
clef = true
porteOuverte = false

if clef == true then
 print("Vous possédez la clef ! La porte s'ouvre !")
 porteOuverte = true
 clef = false
elseif clef == false then
 print("pour ouvrir la porte, il vous faut la clef !")
 porteOuverte = false
end

print("porte ouverte ? "..porteOuverte)
```

sortie console :

```
Vous possédez la clef ! La porte s'ouvre !
porte ouverte ? true
```

Comme la première condition est vrai, il ne vérifie pas les conditions suivantes et donc maintenant nous n’avons plus le bug bien que **clef** soit à false ! Parfait !

_Il existe également une particularité très intéressante avec elseif, c’est qu’on peut en déclarer autant qu’on veut dans une même boucle conditionnel IF._

exemple :

```
if condition then
 -- fais ca
elseif condition2 then
 -- fais ceci
elseif condition3 then
 -- fais cela
elseif condition4 then
 -- fais comme ca
elseif condition5 then
 -- fais moi ci
else
 -- fais moi ca
end
```

On peut mettre des boucles conditionnelles IF dans une autre boucle conditionnel IF !

On appelle ça **l'imbrication**. Voyons cela !

* * *

## L'imbrication

On peut donc imbriquer des **if** entre eux ! Voyons un exemple, ça sera plus parlant =)

Imaginons un exemple avec notre héros qui collecte des pièces et lorsque celui-ci atteint 100 pièces et qu’il possède 0 vie, on décide alors de lui en rajouter une !

  
exemple :

```
totalPieces = 100
vie = 0

if totalPieces == 100 then
 if vie == 0 then
   vie = vie + 1
   print("Héro a gagné sa première vie, bravo !".."n")
 end
end

print("Pièces : "..totalPieces)
print("Vies : "..vie)
```

sortie console :

```
Héro a gagné sa première vie, bravo !

Pièces : 100
Vies : 1
```

La boucle  if vie == 0 then  est alors imbriqué dans la boucle :  
 if totalPieces == 100 then .

Certes c’est super pratique, mais cette méthode d’écriture peut devenir rapidement un vrai casse-tête si on a beaucoup de conditions IF imbriqués les unes dans les autres.

C’est pourquoi il existe des opérateurs logiques : **AND** ,  **OR** et **NOT**.

* * *

## Les Opérateurs Logiques AND , OR et NOT

#### AND

Pseudo-Code avec AND :

| SI condition1 ET condition2 ALORS   END |
| --- |

Syntaxe d’utilisation avec AND :

```
if condition1 and condition2 then
end
```

### OR

Pseudo-Code avec OR :

| SI condition1 OU condition2 ALORS   END |
| --- |

Syntaxe d’utilisation avec OR :

```
if condition1 or condition2 then
end
```

### NOT

Syntaxe d’utilisation avec NOT :

| SI condition1 EST\_DIFFERENT\_DE condition2 ALORS   END |
| --- |

Syntaxe d’utilisation avec NOT :

```
if condition1 not condition2 then
end
```

* * *

- Les priorités logiques

| Les opérateurs logiques sont and, or, et not. (Qui font aussi partie des mots réservés.) Tous les opérateurs logiques considèrent à la fois false et nil comme faux et tout le reste comme vrai. L'opérateur de négation not retourne toujours false ou true. L'opérateur de conjonction and retourne son premier argument si cette valeur est false ou nil, ou son second argument dans le cas contraire. L'opérateur de disjonction or retourne son premier argument si cette valeur est différente de nil et false, ou son second argument dans le cas contraire. Les deux opérateurs and et or utilisent un raccourci d'évaluation.   C'est-à-dire que le second opérande\* est évalué uniquement si nécessaire. |
| --- |

\*opérande = test logique

Exemple :

```
10 or 20  --> 10
10 or false  --> 10
nil or "a"  --> "a"
nil and 10  --> nil
false and nil  --> false
false or nil  --> nil
10 and 20  --> 20
```

_source : [https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LII-H](https://www.google.com/url?q=https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/%23LII-H&sa=D&ust=1600806468720000&usg=AOvVaw3s8PobtaQuLBH7nG4dOiha)_

* * *

- Exercice

| Reprendre l’exemple précédent avec AND |
| --- |

Solution...

![](images/loading.png)

* * *

##### Solution :

```
totalPieces = 100
vie = 0

if totalPieces == 100 and vie == 0 then
   vie = vie + 1
   print("Héro a gagné sa première vie, bravo !".."n")
end

print("Pièces : "..totalPieces)
print("Vies : "..vie)
```

sortie console :

```
Héro a gagné sa première vie, bravo ! Pièces : 100
Vies : 1
```

Les deux conditions existent bien et ça fonctionne. De plus, personnellement je trouve que c’est plus simple à lire / comprendre.

- Exercice suite

| ajoutons une variable bonusVieSup initialisé à true modifions son total de pièces à 35 Reprendre l’exemple précédent avec OR (100 pièces ou bonusVieSup) |
| --- |

Solution...

![](images/loading.png)

* * *

##### Solution suite :

```
totalPieces = 35
bonusVieSup  = true
vie = 0

if totalPieces == 100 or bonusVieSup == true then
   vie = vie + 1
   print("Héro a gagné sa première vie, bravo !".."n")
end

print("Pièces : "..totalPieces)
print("Vies : "..vie)
```

sortie console :

```
Héro a gagné sa première vie, bravo ! Pièces : 35
Vies : 1
```

Une des deux conditions est vrai donc la boucle conditionnel est exécuté =)

## Exercice Final  

| supprimer la variable bonusVieSup ajouter la variable heroMort initialisé à false modifier total de pièces à 100 Reprendre l’exemple précédent avec NOT  heroMort  AND 100 pièces |
| --- |

Solution ...

![](images/loading.png)

* * *

##### Solution finale :

```
totalPieces = 100
heroMort = false
vie = 0

if totalPieces == 100 and not heroMort then
 vie = vie + 1
 print("Héro a gagné sa première vie, bravo !".."n")
end

print("Pièces : "..totalPieces)
print("Vies : "..vie)
```

sortie console :

```
Héro a gagné sa première vie, bravo ! Pièces : 35
Vies : 1Héro a gagné sa première vie, bravo ! Pièces : 35
Vies : 1
```

Effectivement notre héros n’est pas mort et possède bien 100 pièces, donc il gagne une vie !

Maintenant que nous savons tester nos conditions, les imbriqués et les additionner entre elles… Avant d'aborder la syntaxe des boucles répétitives. Il nous faut connaître 3 nouveaux termes qui sont les constantes, l'incrémentation et la décrémentation.

## Bonus : Les constantes qu'est-ce que c'est ?

Ce sont des valeurs fixes, qui ne changent jamais ! Elles sont toujours de type numérique.

Lorsque la valeur de la constante est positive, on dit alors qu’il s’agit d’une incrémentation.  
Quand la valeur de la constante est négative, on dit alors qu’il s’agit d’une décrémentation.

exemple d’une constante positive :

```
CONSTANTE = 1
```

exemple d’une constante négative :

```
CONSTANTE = -1
```

On écrit toujours les constante en majuscule, pour nous rappeler qu’il ne faut pas les modifier !

* * *

## Bonus : L'incrémentation et la décrémentation

C’est l’augmentation d’une valeur numérique par une constante.  
Cette valeur constante s’applique alors à chaque exécution.

exemple, on compte des bonbons par pile de 1 (1 étant la constante) :

```
bonbon = 0
bonbon = bonbon + 1
bonbon = bonbon + 1
bonbon = bonbon + 1
print(bonbon)
```

sortie console :

```
3
```

  
la valeur de **bonbon** est incrémentée de 1 à chaque fois… à la fin il vaut donc 3.

Prenons l’exemple suivant :

un jeu avec un Héros qui lorsqu’il récupère une pièce, son total de pièce augmente alors d’une valeur constante de +1.

\- On peut donc dire que le total de pièce augmente de la constante de 1.

- C’est une **Incrémentation**, car la _constante est positive_.

Toujours dans l’exemple d’un jeu, lorsque le Héros meurt, son total de vie réduit d’une valeur constante de -1.

\- On peut donc dire que le total de vie augmente de la constante de -1.

- C’est une **Décrémentation**, car la _constante est négative_.

**Maintenant, donnons-nous rendez-vous au prochain cours sur les Arguments de Fonction.**

* * *
