---
title: "Les Boucles (For)"
date: 2022-02-24
---

### Les boucles répétitives, qu’est-ce que c’est ?

Ce sont des exécutions répétées de la même tâche.

Boucle se traduit par loop en anglais.

Concrètement les boucles nous permettent d'exécuter les mêmes lignes de codes plusieurs fois sans les retaper dans notre code !

  
C’est très pratique et nous les utiliserons un peu partout =)

###   
Il existe deux styles différents de boucles répétitives :

- Les Boucles **FOR** si l’**on connaît le nombre de répétitions**.

Les boucles **FOR**  sont simples et efficaces, elles s'exécutent le nombre de fois indiqué puis le code passe à la suite.

- Les Boucles **WHILE** et les boucles **REPEAT** si **on ne connaît pas** **le nombre de répétitions**.

Les boucles **WHILE** et **REPEAT** certes plus complexes, mais plus puissantes, car elles s'exécutent tant qu'une condition est vraie.

_Dans ce chapitre nous aborderons uniquement les boucles **FOR**._

## La Boucle FOR

Si nous voulons déterminer le nombre de fois qu’une boucle doit se répéter on utilisera alors une boucle FOR qui s'arrêtera après une valeur atteinte.

La boucle FOR s’utilise toujours avec une constante positive ou négative.

Pseudo-code d’une boucle FOR :

| **DE** _valeur\_de\___debut_ **\=** valeur **A** _valeur\_de\_fin_ **,** _valeur\___constante\_de\_pas_ **FAIT**   **ceci**    _--_ **la boucle se** **TERMINE SI** _valeur\_de\_debut_ **\=** _valeur\_de\_fin_   **SINON** on ajoute la _valeur\___constante\_de\_pas_ à _valeur\_de\___debut_ **et** **_on recommence_** la boucle |
| --- |

Syntaxe d’une boucle FOR :

```
for compteur = 1, 3, 1 do
end
```

On dit que la **valeur constante donne la vitesse de pas**.  
Ici on a donc une _Valeur\_de\_Pas = 1._

* * *

Voici concrètement ce qu’il se passe et que nous ne voyons pas :

```
for compteur = 1 à 3, 1 do
 -- fait ceci
end -- si compteur ne vaut pas 3 je continue et j'ajoute la constante à compteur soit compteur = compteur + 1 = 2

for compteur = 2 à 3, 1 do
 -- fait ceci
end -- si compteur ne vaut pas 3 je continue et j'ajoute la constante à compteur soit compteur = compteur + 1 = 3

for compteur = 3 à 3, 1 do
 -- fait ceci
end -- compteur vaut 3 alors j'ai terminé la boucle !
```

**compteur** est **incrémenté** de la **constante** +1 tant qu’il n’est pas égal à **valeur de fin** 3.

Testons la boucle avec un print pour vérifier la valeur de compteur :

```
for compteur = 1, 3, 1 do 
 print("compteur : "..compteur)
end
```

sortie console :

```
compteur :  1 compteur :  2 compteur :  3
```

La boucle s’exécute bien 3 fois !

Exemple pour ajouter 3 x 10 pièces au total du Héros (30 pièces de plus) :

```
total = 0

for compteur = 1, 3, 1 do 
 total = total + 10
end

print(total)
```

sortie console :

```
30
```

Bien ça fonctionne avec nos variables, Cool !

Reprenons l’exemple avec les pièces, mais cette fois avec une valeur constante négative :

```
total = 0

for compteur = 3, 1, -1 do
 print("compteur : "..compteur)
 total = total + 10
end

print(total)
```

sortie console :

```
compteur :  3 compteur :  2 compteur :  1
30
```

Nous pouvons bien **incrémenter** et **décrémenter** notre valeur de départ !

#### **_ATTENTION_**

Que se passe-t-il **SI** l'on change la valeur de la constante **au-delà de 1** :

```
total = 0

for compteur = 1, 3, 2 do 
 total = total + 10
end

print(total)
```

sortie console :

```
20
```

Oups ! On obtient 20 ?!

Avez-vous deviné pourquoi ?

1. compteur vaut 1 a la première boucle, il ne vaut pas 3 alors la boucle continue et on ajoute la constante à compteur soit :  
    compteur = compteur + 2  
    \-- (avant le début de la boucle : total = 0)  
    \-- total = total + 10  
    \-- total vaut maintenant 10

3. compteur vaut 3 a la deuxième boucle, c’est la dernière exécution puis c’est Fini !  
    \-- (avant le début de la boucle : total = 10)  
    \-- total = total + 10  
    \-- total vaut maintenant 20

Il faut bien faire attention et prendre en compte la valeur de la constante que l’on attribue !

_Cette valeur Constante est aussi appelée le pas d’avancement._

Généralement on utilise 1 ou -1 car c’est plus simple, mais on peut être amené à utiliser des pas différents. Cela restera relativement assez rare, mais ça peut vous arriver.

C’est tellement rare, que du coup on peut simplifier l’écriture comme ceci :

```
for compteur = 1, 3 do
end
```

**compteur** sera alors automatiquement incrémenté d’une valeur constante d’un pas de **+1**, car c'est la valeur de constante par défaut d'une boucle FOR.

Plutôt pratique non =)

exemple :

```
for boucle = 1, 3 do 
 print("boucle : "..boucle )
end
```

sortie console :

```
boucle :  1 boucle :  2 boucle :  3
```

_Remarque : Nous ne sommes pas obligés de mettre **compteur**, car nous sommes libres du choix des noms de variables de début =)_

La **Variable de début** est **local** à la boucle **FOR**.

### Exercice 1 :

| initialiser une variable numérique score à 0 créer une boucle FOR qui doit s'exécuter 10 fois Incrémenter la variable score d’une constante de 10 à chaque fois que la boucle s'exécute afficher la valeur de score avant, pendant et après la boucle (print) |
| --- |

Solution . . .

![](images/loading.png)

* * *

Solution :

```
score = 0
print("initialisation de score, score vaut " .. score.." pts.")
print()

for n = 1, 10 do
 score = score + 10
 print("boucle n°"..n..", score vaut : " .. score.." pts.")
end

print()
print("la boucle est finie, score vaut désormais : "..score.." pts.")
```

sortie console :

```
initialisation de score, score vaut 0 pts. boucle n°1, score vaut : 10 pts.
boucle n°2, score vaut : 20 pts.
boucle n°3, score vaut : 30 pts.
boucle n°4, score vaut : 40 pts.
boucle n°5, score vaut : 50 pts.
boucle n°6, score vaut : 60 pts.
boucle n°7, score vaut : 70 pts.
boucle n°8, score vaut : 80 pts.
boucle n°9, score vaut : 90 pts.
boucle n°10, score vaut : 100 pts. la boucle est finie, score vaut désormais : 100 pts.
```

Vous aviez réussi ? =)

Non ? Voici un autre exemple d’utilisation d’une boucle FOR :

```
texte = ""

for i = 1, 10 do
 texte = texte.."###"
end

print(texte)
```

sortie console :

```
##############################
```

On a cumulé les **concaténations** de la variable texte à chaque exécution de la boucle FOR, ce qui nous donne désormais 30 dièse.

La valeur de la fin de la boucle peut aussi être une variable.

Hors celle-ci n’est pas encore dans le corps (bloc) de la boucle FOR !

le corps de notre boucle se situe entre le DO ... et le ... END

```
texte = ""
nbDieze = 30

for k = 1, nbDieze do -- début de la boucle
 texte = texte.."#" -- corps
end -- fin de la boucle

print(texte)
```

sortie console :

| ############################## |
| --- |

_Ce qu’il faut retenir_

Une boucle FOR incrémente sa propre valeur **_K_** jusqu'à ce que **_K_** atteigne la valeur de fin.

Selon la vitesse du pas, la valeur de K peut dépasser la valeur de fin, ce qui met également fin à la boucle sans faire d'erreur.

Les valeurs de départ et de fin peut être une copie de valeur d'une de vos variables de votre choix.

Démonstration :

```
texte = ""
nbDieze = 30
start = 1

for start = 1, nbDieze do -- POUR start valeur de début, à nbDieze valeur de fin FAIT
 texte = texte.."#" -- excute ceci
end -- fin

print(texte)
print(start)
```

sortie console :

| ##############################   1 |
| --- |

start vaut bien toujours 1, la boucle n'a fait que copié la valeur de start dans sa propre boucle porur s'exécuter.

En résumé les boucles FOR ont aussi une portée et elles ont les mêmes portées que les fonctions.

Désormais vous savez **utiliser les boucles for**, vous connaissez les termes et exécutions d'une **incrémentation** et/ou **décrémentation** d'une variable.  
Vous savez également ce qu’est une **constante**.

### Exercice 2 :

| initialiser une variable du **total de pièces** à 0 initialiser une variable du **nombre de vies du héros** à 0 créée une **boucle FOR** qui **incrémente** nos pièces **jusqu’à 100** dans la boucle FOR ajoutez une condition que **SI total de pièces est égale à 100 ALORS il faut ajouter une vie et remettre le total de pièces à 0** **après** l'exécution de la boucle, **afficher le total de pièces et de vie** |
| --- |

Solution ?

![](images/loading.png)

* * *

solution exercice 2 :

```
totalPieces = 0
vieHero = 0

for i = 1, 100 do
 totalPieces = totalPieces + 1
 if totalPieces == 100 then
   vieHero = vieHero + 1
   print("Héro a atteint un total de 100 pièces ! il gagne une vie.")
   totalPieces = 0
 end
end

print("Héro possède "..totalPieces.." pièces et "..vieHero.." vie.")
```

sortie console :

```
Héro a atteint un total de 100 pièces ! il gagne une vie.
Héro possède 0 pièces et 1 vie.
```

### Exercice 3 :

| Faites monter notre Héro à un total de 5 vies avec les pièces. Si Héro à exactement trois vies, Faites lui gagner une étoile (variable à créer). Si Héro gagne une vie alors qu’il possède déjà une étoile ou plus, écrivez un Message de la part du “Méchant” qui invite notre Héro à le rejoindre dans son château. Vous avez d’autres idées ? Faites vous plaisir et tester… ! |
| --- |

Solution…

![](images/loading.png)

* * *

Ma solution à l'exercice 2 :

```
totalPieces = 0
viesHero = 0
nbEtoiles = 0

for i = 1, 5 do
 
 totalPieces = totalPieces + 100
 
 if totalPieces == 100 then
   if viesHero == 1 then
     print("Héro : Ils sont quand même sacrément bon ces petits champignons !")
   end
   
   viesHero = viesHero + 1
   totalPieces = 0
   
   if viesHero == 3 then
     nbEtoiles = nbEtoiles + 1
     print("Héro gagne une étoile car il a atteint "..viesHero.." vies.".." Héro possède désormais "..totalPieces..".")
   elseif nbEtoiles >= 1 then
     print("Méchant : Héro je t'attends dans mon château, je t'ai préparé un café chaud bouillant rien que pour toi !")
   end

 else
   print("Héro a atteint un total de 100 pièces ! il gagne une vie.".."n".."Héro possède désormais "..totalPieces.." pièces et "..viesHero.." vies.")
 end

 print()

end

print("héro possède désormais "..totalPieces.." pièces et "..viesHero.." vies. Ainsi que "..nbEtoiles.." étoile.")
```

sortie console :

| Héro : Ils sont quand même sacrément bon ces petits champignons ! Héro gagne une étoile car il a atteint 3 vies. Héro possède désormais 0. Méchant : Héro je t'attends dans mon château, je t'ai préparé un café chaud bouillant rien que pour toi ! Méchant : Héro je t'attends dans mon château, je t'ai préparé un café chaud bouillant rien que pour toi ! héro possède désormais 0 pièces et 5 vies. Ainsi que 1 étoile. |
| --- |

```
Héro : Ils sont quand même sacrément bon ces petits champignons ! Héro gagne une étoile car il a atteint 3 vies. 

Héro possède désormais 0. Méchant : Héro je t'attends dans mon château, je t'ai préparé un café chaud bouillant rien que pour toi ! Méchant : 

Héro je t'attends dans mon château, je t'ai préparé un café chaud bouillant rien que pour toi ! 

héro possède désormais 0 pièces et 5 vies. Ainsi que 1 étoile.
```

  
**Félicitations !**

**Fin du chapitre sur les boucles FOR !**

**Rendez-vous pour la suite au prochain cours =)**

* * *
