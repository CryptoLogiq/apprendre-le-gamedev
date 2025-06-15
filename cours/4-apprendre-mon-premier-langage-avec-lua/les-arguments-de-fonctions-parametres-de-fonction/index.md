---
title: "Les Arguments de fonctions (paramètres de fonction)"
date: 2022-02-24
---

Maintenant que vous savez créer une fonction et lui donner des instructions dans son corps.

Désormais voyons comment la rendre flexible avec des arguments.

## Qu’est-ce que c’est qu’un argument ? 

Un argument est une référence de variable ou sa valeur qu’on transmet à la fonction, nous pouvons transmettre 1 ou plusieurs arguments à une fonction.

Les arguments sont parfois nommés paramètres de fonction. Ces arguments serviront à la fonction afin d’effectuer sa tâche.

Syntaxe d’une fonction avec 1 argument :

```lua
function maFonction(argument) -- avec 1 argument
end
```

Syntaxe d’une fonction avec 2 arguments :

```lua
function maFonction(argument1, argument2) -- avec 2 arguments
end
```

Syntaxe d’une fonction avec 3 arguments :

```lua
function maFonction(argument1, argument2, argument3) -- etc.
end
```

Les arguments sont utilisés par la fonction pour effectuer des manipulations de variables.

Les arguments sont séparés par des  **,**  virgules.



Voyons un exemple simple, nous allons créer une fonction addition :

```lua
function addition(a, b)
     print(a + b)
end
```

Utilisons-la pour voir comment ça fonctionne :

```lua
valeur1 = 2
valeur2 = 3

function addition(a, b)
    print(a + b)
end

addition(valeur1, valeur2)
```

sortie console :
```
5
```

1. L’argument **a** vaut **valeur1**

3. L'argument **b** vaut **valeur2**

5. **a + b = valeur1 + valeur2**

7. a+b = 5

9. valeur1+valeur2 = 5

Essayons avec un return :

```lua
valeur1 = 2
valeur2 = 3
total = 0

function addition(a, b)
     return a + b
end

total = addition(valeur1, valeur2)
print(total)
```

sortie console :
```
5
```

Cool ça fonctionne !



## La portée des arguments dans une fonction

Les arguments existent uniquement à l'intérieur d’une fonction  car si l’on veut print(a) ou print(b) en dehors de la fonction c’est impossible.

```lua
valeur1 = 10
valeur2 = 5
function addition(a, b)
     return a + b
end
addition(valeur1, valeur2)
print(a)
```

sortie console :
```
nil
```

Comme il n’existe pas de variable a en dehors de la fonction, **print(a)** nous retourne **nil** ce qui signifie que la variable **a** _est vide (inexistante_).

Le fait que l’argument a n’existe que dans la fonction, on appelle cela la **portée des variables** ou le **spectre**.

La portée de l’argument **a** est donc limitée dans le corps de la fonction addition() 

On dit alors que l’argument **a** est  **local à la fonction** addition() afin de préciser sa portée, son spectre… (nous reviendrons sur le terme _local_ ultérieurement).

À quoi peut bien nous servir qu’un argument n’existe qu'à l'intérieur d’une fonction et que cet argument possède une portée… ?



Démonstration :

```lua
a = 10
b = 20
c = 0
function addition(a, b)
    resultat = a + b
    a = 3
    b = 2
    print("dans la fonction addition(a, b)".."\n", "a = "..a, "b = "..b, "resultat = "..resultat, "\n")
    return resultat
end
print("en dehors de la fonction et avant addition(a, b)".."\n", "a = "..a, "b = "..b, "c = "..c, "\n")
c = addition(a, b)
print("en dehors de la fonction et après addition(a, b)".."\n", "a = "..a, "b = "..b, "c = "..c, "\n")
```

sortie console :
```
en dehors de la fonction et avant addition(a, b) a = 10           b = 20        c = 0         

dans la fonction addition(a, b) a = 3         b = 2          resultat = 30 

en dehors de la fonction et après addition(a, b) a = 10           b = 20        c = 30
```

Les arguments a et b de la fonction **addition(a, b)** sont des _copies de valeur_ des variables transmises en paramètres à la fonction.

De plus comme elles sont **local** à la fonction on peut donc les manipuler sans se soucier des modifications apportées au sein d’une fonction qui n’affecte pas les valeurs des paramètres directement.

Ça permet de faire des calculs, des tests et de return un résultat après nos tests.

_Nous aborderons la portée des variables plus en profondeur dans un chapitre ultérieur ;)_



## Exercice 1

| \- Créer un héros avec de la vie, et un ennemi avec une force d’attaque. - Créer une fonction Attaque() qui contient deux arguments, Cible et Degats. - Attaque() devra retourner la vie de la cible après l’attaque. |
| --- |

Attente de la Solution …

![](images/loading.png)



##### Solution Exercice 1

```lua
vieHero = 100
frappeEnnemi = 20

function    Attaque(Cible, Degats)
  resultat = Cible - Degats
  print("la cible dispose de "..Cible.." points de vie et subit une attaque de "..Degats.." points de dégâts.")
  print("la cible a désormais "..resultat.." points de vie.")
  return    resultat
end    

vieHero = Attaque(vieHero, frappeEnnemi)
print(vieHero)
```

sortie console :
```
la cible dispose de 100 points de vie et subit une attaque de 20 points de dégâts. la cible a désormais 80 points de vie. 80
```

Super ça fonctionne =)

Allons encore plus loin pour démontrer l’utilité des arguments et de son utilité !

Pour cela on va faire un nouvel exercice ensemble =)



## Exercice 2

| Créer un héros avec de la vie et avec une force d’attaque. Créer un ennemi avec de la vie et avec une force d’attaque. Créer une fonction Attaque() qui contient deux arguments :    - Cible    - Degats Attaque() devra retourner la vie de la cible après l’attaque. Faire attaquer l'ennemi et le héros chacun leur tour avec la même fonction Attaque() |
| --- |

Solution de l'exercice en chargement…

![](images/loading.png)



##### Solution Exercice 2

```lua
vieHero = 100
frappeHero = 30
--
vieEnnemi = 60
frappeEnnemi = 20

function    Attaque(Cible, Degats)
  resultat = Cible - Degats
  print("la cible dispose de "..Cible.." points de vie et subit une attaque de "..Degats.." points de dégâts.")
  print("la cible a désormais "..resultat.." points de vie.")
  print()
  return    resultat
end    

print("attaque du héro")
vieHero = Attaque(vieHero, frappeEnnemi)

print("attaque de l'ennemi")
vieEnnemi = Attaque(vieEnnemi, frappeHero)
```

sortie console :
```
attaque du héro la cible dispose de 100 points de vie et subit une attaque de 20 points de dégâts. la cible a désormais 80 points de vie. attaque de l'ennemi la cible dispose de 60 points de vie et subit une attaque de 30 points de dégâts. la cible a désormais 30 points de vie.
```

Si vous avez réussi, c'est excellent ! Si ce n’est pas le cas pas de panique !

- Essayez de reprendre pas à pas ce qu’il se produit en lisant le code à voix haute…

| Petite Aide :   J’initialise les variables dont j’ai besoin…   J’ai créé la fonction avec ses arguments et son corps de fonction.   J’utilise la fonction en passant aux arguments différents variables.   Je print() les variables après l’utilisation de la fonction. |
| --- |

## Bonus

Exemple avec plusieurs arguments :

```lua
heroName = "Arthur"
heroVie = 100
heroFrappe = 20
--
ennemiName = "Slime"
ennemiVie = 40
ennemiFrappe = 10

function    Attaque(NomCible, vieCible, nomAttaquant, frappeAttaquant)
  resultat = vieCible - frappeAttaquant
  print(NomCible.." subit une attaque par "..nomAttaquant.." d'un montant de "..frappeAttaquant.." points de dégâts.")
  print(NomCible.." a désormais "..resultat.." points de vie.")
  print()
  return    resultat
end    

heroVie      = Attaque(heroName,      heroVie,          ennemiName, ennemiFrappe)
ennemiVie = Attaque(ennemiName, ennemiVie,     heroName,      heroFrappe)
```

sortie console :
```
Arthur subit une attaque par Slime d'un montant de 10 points de dégâts. Arthur a désormais 90 points de vie. Slime subit une attaque par Arthur d'un montant de 20 points de dégâts. Slime a désormais 20 points de vie.
```

C’est simple et ça fonctionne !

Pour l'instant c’est tout ce que l’on veut… !

**Bien Maintenant que vous êtes arrivés jusqu’ici ! Rendez-vous au prochain cours =)**
