---
title: "La Concaténation"
date: 2022-02-24
---

###  Concaténation description :

  
Le terme de concaténation (substantif féminin), du [latin](https://www.google.com/url?q=https://fr.wikipedia.org/wiki/Latin&sa=D&ust=1600806405055000&usg=AOvVaw1DRYVEx0cQLR-ONiU4mo_K) cum (« avec ») et catena (« chaîne, liaison »).

Désigne l'action de mettre bout à bout au moins deux chaînes de caractères ou de [péricopes](https://www.google.com/url?q=https://fr.wikipedia.org/wiki/P%25C3%25A9ricope&sa=D&ust=1600806405055000&usg=AOvVaw1F3J_LG3psOEZ2QYXhVEHI).

source : [https://fr.wikipedia.org/wiki/Concat%C3%A9nation](https://www.google.com/url?q=https://fr.wikipedia.org/wiki/Concat%25C3%25A9nation&sa=D&ust=1600806405056000&usg=AOvVaw3axuidF6xtLBKxvNCg77MR)

- Préparation de l’exercice

Tout d'abord, nous générons quelques variables textes, nombres et booléennes pour préparer nos variables que nous utiliserons pendant ce chapitre :

```lua
nom = "Nolan "
prenom = "Bushnell "
jour = 27
mois = 06
annee = 1962
reponse = true
```

Avant de vous montrer une concaténation, revoyons déjà comment faire un print contenant plusieurs variables pour vérifier celles-cis avec un seul appel de  **print()**

Séparer juste les variables par une virgule  **,** 

Exemple :

```lua
print(nom, prenom, jour, mois, annee, reponse)
```

Sortie console :
```
Nolan Bushnell 27 06 1962 true
```

Voyons maintenant comment additionner plusieurs string dans une seule variable grâce à la concaténation (concat en anglais).



## La Concaténation de texte

Elle permet de mettre à la suite des valeurs différentes dans une seule variable, celle-ci sera de  **type(string)** 

La concaténation se fait avec deux points  **..**  Voyons concrètement comment faire ?

Syntaxe :

```lua
maConcatenation = "mon debut de texte ".."ma suite de texte"
```

Exemple avec des variables :

```lua
nom = "Nolan "
prenom = "Bushnell "
jour = 27
mois = 06
annee = 1962
reponse = true
--
nomComplet = nom..prenom
print(nomComplet)
```

Sortie console :
```
Nolan Bushnell
```

## La concaténation de nombres

comme la variable qui contient la concaténation est de type string on peut donc seulement concaténer du texte !

il nous faut alors transformer nos valeurs numériques de type number en type string...

Pour cela on utilise alors la fonction  **tostring()**

Si la concaténation ne contient que des chiffres, tostring() n’est pas nécessaire, mais il est plus sage de prendre l’habitude de l’utiliser quand même =)

Syntaxe :

```lua
maVariable = tostring(5)..tostring(10)
```

Exemple avec des variables :

```lua
nom = "Nolan "
prenom = "Bushnell "
jour = 27
mois = 06
annee = 1962
reponse = true
--
dateComplete = tostring(jour)..tostring(mois)..tostring(annee)
print(dateComplete)
```

Sortie console :
```
27061962
```

Vous serez d'accord pour affirmer qu'il est difficile de comprendre qu'il s'agit ici d'une date.



## La concaténation de texte et de nombre !

Nous allons donc rajouter du texte entre les concaténations de nombres.

Seulement on ne peut pas le faire directement, car il s’agit là de deux types différents des Strings et des Numbers (texte et nombre)

Lors de l'exécution de votre code, Il ne comprendra pas ce qu’il doit faire, un calcul ou un texte ?

Rappelez-vous que la concaténation ne sait que mettre bouts à bouts des chaînes de caractères soit des variables de  type(string).

Nous devons donc convertir les nombres en texte ! Avec l’utilisation de  tostring()  afin de pouvoir concaténer tout ça !

Syntaxe :

```lua
concatenation = "j'ai "..tostring(35).." ans."
```

exemple :

```lua
nom = "Nolan "
prenom = "Bushnell "
jour = 27
mois = 06
annee = 1962
reponse = true
--
dateComplete = tostring(jour).."/"..tostring(mois).."/"..tostring(annee)
print(dateComplete)
```

Sortie console :
```
27/06/1962
```

Un autre exemple avec une phrase complète :

```lua
Atari = "Atari a été fondé le "..dateComplete..", vous trouverez plus d'information sur : https://fr.wikipedia.org/wiki/Atari"

print(Atari)
```

Sortie console :
```
Atari a été fondé le 27/06/1962, vous trouverez plus d'information sur : https://fr.wikipedia.org/wiki/Atari
```



## Les Mises en formes Simple

Nous pouvons appliquer des mises en forme simple comme le saut de ligne ou les tabulations.

 !  les mises en formes s’appliquent uniquement avec des variables de type(string).

Générons une variable à manipuler :

```lua
monTexte = "Bonjour comment allez-vous ? Je vais bien merci."
print(monTexte)
```

Sortie console :
```
Bonjour comment allez-vous ? Je vais bien merci et vous ?
```

1. **Le saut de ligne :**

il s'utilise  avec  \\**n**  dans une variable string :

```lua
monTexte = "Bonjour comment allez-vous ? \n Je vais bien merci."
print(monTexte)
```

Sortie console :
```
Bonjour comment allez-vous ?
   Je vais bien merci.
```

Avez-vous remarqué l’espace sur la deuxième ligne ?

C’est parce qu’il faut enlever l'espace juste après le  **n**  , car il s'applique juste après le saut de ligne et le texte est alors décalé.  
Ceci est d’ailleurs valable pour tout autre mise en forme.

correction :

```lua
monTexte = "Bonjour comment allez-vous ? \nJe vais bien merci."
print(monTexte)
```

Sortie console :
```
Bonjour comment allez-vous ?
Je vais bien merci.
```

pour une meilleure relecture de votre code, utilisons la concaténation avec la mise en forme :

```lua
monTexte = "Bonjour comment allez-vous ?".."\n".."Je vais bien merci."
print(monTexte)
```

Sortie console :
```
Bonjour comment allez-vous ?
Je vais bien merci.
```

C'est plus facile à lire, non ?

## **La tabulation :**

la tabulation sert à espacer votre texte d’un espace égalitaire.

il remplace généralement plusieurs espaces.

Préparons une variable :

```lua
titre = "Titre(1)"
sujet_1 = "Sujet(1)"
sujet_2 = "Sujet(2)"
monTexte = titre..sujet_1..sujet_2
print(monTexte)
```

Sortie console :
```
Titre(1)Sujet(1)Sujet(2)
```

Les tabulations s’utilisent avec  **\\t**   dans une variable string :

```lua
titre = "Titre(1)"
sujet_1 = "Sujet(1)"
sujet_2 = "Sujet(2)"
monTexte = titre.."\t"..sujet_1.."\t"..sujet_2
print(monTexte)
```

Sortie console :
```
Titre(1)   Sujet(1)   Sujet(2)
```

Vous serez d’accord pour dire que les mises en formes sont peu lisibles surtout lorsqu’elles sont nombreuses.

Heureusement nous pouvons améliorer cela !



## Mises en formes multiples, comment ne pas se perdre ?

Avec plusieurs mises en forme, cela devient rapidement assez complexe à lire, c'est pourquoi je vous conseille d’utiliser la concaténation en complément des mises en formes.

Exemple :

```lua
titre = "Titre(1)"
sujet_1 = "Sujet(1)"
sujet_2 = "Sujet(2)"
monTexte = titre.."\n".."\t"..sujet_1.."\n".."\t"..sujet_2
print(monTexte)
```

Sortie console :
```
Titre(1)
   Sujet(1)
   Sujet(2)
```

Personnellement je préfère cette mise en forme, que je trouve bien plus facile à lire. Grâce à cela, nous pouvons comprendre ce qu'il se passe.

De plus le résultat est strictement identique.

- Liste des Mises en forme existantes :

```lua
"\a"         --(cloche)
"\b"         --(backspace)
"\f"         --(saut de page)
"\n"         --(saut de ligne)
"\r"         --(retour chariot)
"\t"         --(tabulation horizontale)
"\v"         --(onglet vertical)
"\"          --(barre oblique inverse)
' " '        --(guillemet anglais)
" ' "        --(apostrophe)
```

Nous utiliserons principalement   **\\n**  et   **\\t**  dans nos textes.

C'est quand même bien d’avoir examiné d'autres mises en formes !



## Bonus

Comment afficher les  **guillemets**  dans votre texte… pour cela on peut utiliser **apostrophes.**

exemple :

```lua
monTexte = 'maVariable = "mon texte" '
print(monTexte)
```

sortie console :
```
maVariable = "mon texte"
```

Je vous laisse expérimenter ces nouvelles notions…  
![](images/test.png)

**On se retrouve pour la suite au prochain cours !**
