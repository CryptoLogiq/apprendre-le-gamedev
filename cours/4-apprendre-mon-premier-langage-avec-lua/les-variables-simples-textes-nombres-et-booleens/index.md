---
title: "Les Variables Simples (Textes, Nombres et Booléens)"
date: 2022-02-24
---

Avant d’aborder les variables je souhaiterais vous parler des commentaires.

## Les commentaires

Ils permettent d'insérer des mémos dans votre code.

Tout ce qui se situe après des commentaires sur la même ligne ne sera pas exécuté.

On ajoute un commentaire en tapant ceci **--**  _\- taper deux fois la touche moins sans faire d'espace - AltGr + 6, ou al touche (-) du pad numérique_

###### Exemple avec 1 commentaire :

```
-- je suis un commentaire, je ne suis pas pris en compte pendant l'exécution 
print("Bonjour")
```

Sortie console :

| Bonjour |
| --- |

###### On peut aussi le mettre après du code exécuté :

```
print("Bonjour") -- je suis un commentaire !
```

Sortie console :

| Bonjour |
| --- |

##### Exemple démonstration :

```
-- la fonction print() sert à écrire dans la console
print("Bonjour, vous allez bien ?") -- Question

-- la fonction print() seule fait un saut de ligne
print()

-- print("non")
print("Oui merci, et vous ?") -- Réponse
```

Sortie console :

| Bonjour, vous allez bien ? Oui merci, et vous ? |
| --- |

Plutôt pratique non ?

_Vous avez remarqué que le  -- print (“non”)  n’a pas été exécuté ! Cela nous permet donc de décider d'exécuter ou non une partie de notre code sans l'effacer et cela vous sera très utile !_

## Les Variables (Simples)

Que sont les variables ? Au travers de ce chapitre, nous allons comprendre ce qu’elles représentent et comment les créer.

Une **variable**, c'est ce qui va nous permettre de **stocker** des **valeurs**. Ces valeurs peuvent alors être modifiées à notre guise vu qu’elles sont variables... Ces variables peuvent être des **nombres**, pour stocker par exemple, dans votre jeu la force de votre héros, ainsi que ses points de vie, son endurance, etc. Elles peuvent également contenir du texte, pour stocker son nom, son prénom, etc.

Elles peuvent également contenir un **interrupteur (bool)** qui peut être soit **vrai** ou **faux**.

À quoi cela peut-il servir dans notre jeu ? Par exemple est-ce que mon héros est fatigué ? Est-ce qu’il fait encore jour ?

Toutes ces variables vont donner vie à notre code et surtout les futurs jeux que nous allons créer ensemble.

Pour créer une variable et lui attribuer une valeur il faut procéder comme ceci :

```
 maVariable = valeur
```

Se lit :

| ma variable du nom **maVariable** _vaut_cette **valeur** |
| --- |

Lorsque le programme exécutera le code, il stockera alors cette **variable** et sa **valeur** en **mémoire**.

_Les noms de variables sont libres, vous pouvez alors la nommer comme bon vous semble._

**Cependant attention !** Les noms suivants sont utilisés par Lua et sont donc réservés :

**and    break    do    else    elseif    end    false    for    if**

**in     local    nil   not     repeat    then   return   true   or**

**until    while    function**



## Les variables de Nombres (number)

Les nombres peuvent être stockés dans des variables de  **type(number)**  ce sont donc des variables numériques.

###### Syntaxe :

```
maVariable = 1
```

###### Exemple démonstration :

```
jour = 27
mois = 06
annee = 1962

print(jour)
print(mois)
print(annee)
```

Sortie console :

| 27   06   1962 |
| --- |

### Print plusieurs variables sur une seule et meme ligne

```
jour = 27
mois = 06
annee = 1962

print(jour, mois, annee)
```

| 27 06 1962 |
| --- |

Ceci est bien pratique, surtout lorsque l'on veut trouver une erreur ou faire des traces dans la console compréhensible.

La virgule indique une autre instruction à la fonction print(), celle-ci ajoute avec un espace entre les valeurs les plusieurs variables qu'on lui demande de nous afficher dans la console.



### **_! ATTENTION !_**  

Les variables de nombres peuvent être des nombres entiers comme des nombres flottants (décimaux).

Pour un nombre décimal (float) on utilise un point  .  pour désigner un nombre décimal.

Cela pour deux raisons, la première, car les virgules aux US sont utilisées pour séparer les milliers et que dans le langage LUA la virgule  

```
,
```

 sers surtout à séparer des instructions !

#### Le piège à éviter :

```
pi = 3,14 
print(pi)
```

Sortie Console :

| 3 |
| --- |

14 est considéré comme étant une autre instruction et elle est donc mise de côté, car la virgule indique une seconde instruction après celle-ci.

Alors `pi = 3` et `14` est attendu pour une autre instruction (elle attend une autre variable par exemple...) Alors soyez vigilant. =)

_il faut donc TOUJOURS utiliser un point_

```
.
```

 _pour les nombres décimaux et pas de virgules_ !

###### Correction :

```
pi = 3.14 
print(pi)
```

Sortie console :

| 3.14 |
| --- |

### On peut aussi effectuer des calculs entre plusieurs variables numériques :

```
longueur = 5
largeur = 2
-- Rappel : calcul d'une surface = L*l
surface = longueur * largeur
print(surface)
```

Sortie console :

| 10 |
| --- |

###### un autre exemple :

```
miles = 50
vitesse = miles / 0.6215
print(miles)
print(vitesse)
```

Sortie console :

| 50 80.450522928399 |
| --- |

Le mile et le km (kilomètre) sont deux unités de mesures de longueur dans le système métrique. Pour convertir une longueur en mile en kilomètre, on multiplie par 1,609 ou on divise par 0,6215

###### encore autre exemple :

```
poids = 72.4
taille = 1.82
imc = poids / (taille*taille)
print(imc)
```

Sortie console :

| 21.857263615505 |
| --- |

_imc = Indice de masse corporelle, formule = poids(kg) / taille²(m²)_

source : [https://fr.wikipedia.org/wiki/Indice\_de\_masse\_corporelle](https://www.google.com/url?q=https://fr.wikipedia.org/wiki/Indice_de_masse_corporelle&sa=D&ust=1600806383690000&usg=AOvVaw3b6Z8cMbHD5UYrFk4gAD07)

## Les opérateurs arithmétiques

**Les binaires**

|  + | addition |
| --- | --- |
| \- | soustraction |
| \* | multiplication |
| / | division |
| % | modulo : le restant d’une division euclidienne |
| ^ | élévation : la puissance |

**l'unaire** (changement de signe)

| \- | négation |
| --- | --- |

###### Exemple :

```
x = 2
y = 3
print("x = 2 et y = 3")
print("-- addition : x + y")
print(x + y)
print("-- soustraction : x - y")
print(x - y)
print("-- multiplication : x * y ")
print(x * y)
print("-- division : x / y")
print( x / y)
print("-- modulo : x % y")
print( x % y)
print("-- élévation : x ^ y")
print( x ^ y)
print("-- négation : -x ")
print( -x )
```

Sortie console :

| x = 2 et y = 3   \-- addition : x + y   5   \-- soustraction : x - y   \-1   \-- multiplication : x \* y   6   \-- division : x / y   0.66666666666667   \-- modulo : x % y   2   \-- élévation : x ^ y   8   \-- négation : -x   \-2 |
| --- |

## Les variables de Textes (string)

Les variables de textes  **type(string)**  sont enfermés dans des guillemets, via la touche 3.

```
" "
```

###### Syntaxe :

```
maVariable = "mon texte"
```

###### Exemple démonstration :

```
nom = "Nolan"
prenom = "Bushnell"

print(nom, prenom)
```

Sortie console :

| Nolan Bushnell |
| --- |

Une variable string peut contenir du texte et donc des phrases complexe.

###### Exemple avec une Phrase :

```
monTexte = "Nolan Kay Bushnell, est né le 5 février 1943 !"

print(monTexte)
```

Sortie console :

| Nolan Kay Bushnell, est né le 5 février 1943 ! |
| --- |

##### Les espaces sont aussi des caractères :

```
nom = "Nolan"
prenom = "   Bushnell"

print(nom)
print(prenom)
```

Sortie console :

| Nolan Bushnell |
| --- |

## Les variables Booléennes (boolean) : Vrai / Faux

Un booléen ou bool en anglais, est un interrupteur qui sert à contrôler une condition (une vérité). Un booléen se caractérise par  true  ou  false  il est de  **type(boolean)** .

##### Syntaxe  VRAI :

```
maVariable = true
```

##### Syntaxe  FAUX :

```
maVariable = false
```

###### Exemple démonstration VRAI :

```
monBooleen= true
print(monBooleen)
```

Sortie console :

| true |
| --- |

###### Exemple démonstration FAUX :

```
monBooleen = false
print(monBooleen)
```

Sortie console :

| false |
| --- |

## Les variables vides (nil)

Il existe aussi un type de variable vide soit le  **type(nil)**  mais ça veut dire quoi ?

Surtout à quoi ça sert ?

Une variable vide, c’est une variable qui existe, mais qui ne contient rien…

De ce fait elle renverra toujours une valeur dite “vide” soit   nil  en anglais.

Par défaut une variable est vide !

C’est utile pour effectuer des test logique, qu’on abordera plus tard également, mais c'était important que vous les connaissiez.

##### Syntaxe :

```
maVariable = nil

```

###### Exemple avec nil :

```
maVariableVide = nil
print(maVariableVide)
```

Sortie console :

| nil |
| --- |

##### Syntaxe sans rien :

```
maVariable
```

###### Exemple sans rien :

```
maVariableVide
print(maVariableVide)
```

Sortie console :

| nil |
| --- |



## Les 8 types de variables LUA qui existent :

Les variables simples que nous venons de voir :

- **number**

- **string**

- **boolean**

- **nil**

Les variables complexes que nous aborderons bientôt :

- **function**

- **table**

Puis celles que nous n’aborderons pas dans les bases… (niveau avancées) :

- **userdata**

- **thread**

#### Exercice TP : 

| Créer et Imprimer chacun des types de variables que nous venons de voir ! type texte (string) type nombres (number) type décimal (number) type booléen (boolean), une de valeur Vrai et une autre avec une valeur Fausse type nil (vide) |
| --- |



#### Solution TP :

```
monAge = 35
maTaille = 1.85
monNom = “Cédric”
jeSuisMort = false
JeSuisVivant = true
nomDeMaFemme = nil

print(monAge)
print(maTaille)
print(monNom)
print(jeSuisMort)
print(JeSuisVivant)
print(nomDeMaFemme)
```

sortie console :

| 35   1.85   Cédric   false   true   nil |
| --- |

Si vous avez réussi tant mieux, sinon, relisez attentivement la solution pour comprendre vos erreurs éventuelles et retentez ensuite l’exercice sans vous aider (sans copier).

Copier un code ne sert à rien, il vous faut le comprendre et le taper vous-même pour bien l’assimiler. C’est très important ! ! !



## Bonus

##### Comme on peut séparer nos print avec une virgule pour plusieurs isntructions, on peut aussi assigner plusieurs variables sur une même ligne :

```
x, y, z = 10, 20, 15
print(x)
print(y)
print(z)
print(x, y, z)
```

sortie console :

| 10   20   15   10 20 15 |
| --- |

_la virgule  ,  sépare les variables !_

##### On peut exécuter plusieurs instructions sur une même ligne grâce au chunk :

le chunck c'est le point virgule :

```
;
```

exemple :

```
x = 10

y = 20

z = 15

print(x); print(y); print(z); print(x + y + z)
```

sortie console :

| 10 20 15 45 |
| --- |

Le point virgule  ;  sépare les instructions ! L'unité d'exécution  ;  de Lua est appelée « chunk ».

##### On peut écrire des commentaires sur plusieurs lignes :

```
--[[
ceci est un commentaire
sur plusieurs
lignes !

C'est assez pratique pour détailler votre code =)
]]--
```

La syntaxe --\[\[  \]\]-- ouvre et ferme un commentaire sur une ou plusieurs lignes.



##### On peut connaître le type d'une variable :

```
monChiffre = 7
monTexte = "Sept est mon chiffre porte bonheur"
maChance = true
monGain = nil
--
print(type(monChiffre))
print(type(monTexte))
print(type(maChance))
print(type(monGain))
```

sortie console :

| number   string   boolean   nil |
| --- |

La fonction **type()** renvois le type d'une variable.

Cette valeur est une chaîne de caractère (string).

C’est pourquoi nous pouvons print() le type() car il s’agit d’un texte (string).



##### En Lua, on peut changer le type d'une variable très facilement :

Lua est un langage à typage dynamique. Cela signifie que c’est le type de la valeur que contient une variable qui donne son type.

Dans d’autres langages, les variables sont d’abord typés avant d’avoir une valeur qui correspond à son type.

exemple :

```
maVariable = "test"
print(type(maVariable))

maVariable = 10
print(type(maVariable))

maVariable = true
print(type(maVariable))

-- etc.
```

sortie console :

| string   number   boolean |
| --- |

Dans l'exemple la variable _**maVariable**_ change de type à volonté…

C’est pratique, mais ça peut facilement vous induire en erreur alors attention, essayez de ne pas le faire, il est plus sage de recréer une nouvelle variable... sauf si c'est réellement nécessaire. =)

**Maintenant, rendez-vous au prochain chapitre où nous verrons comment mettre bout à bout plusieurs chaînes de caractères (des string) dans une variable.**


