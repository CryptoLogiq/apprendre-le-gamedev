---
title: "Bonus 1 : Résumé des bases en Lua"
date: 2022-02-24
---

###  L'essentiel des bases

Voici un petit récapitulatif de ce qu’il vous faut connaître avec LUA !

source : [https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/#LII-F](https://www.google.com/url?q=https://wxlua.developpez.com/tutoriels/lua/general/cours-complet/%23LII-F&sa=D&ust=1600806873688000&usg=AOvVaw18kVUKFPD6OCC1A3fqTGRI)

| Les variables |
| --- |
| 1\. Une variable est un emplacement mémoire      2\. On donne un nom à une variable et une valeur : maVariable = 0      3\. On la définit en tant que globale ou locale      4\. nil indique une variable vide      5\. Pour une affectation simple : x = 25      6\. Pour une affectation multiple : `x, y, z = 10, "abc", 322`      7\. La portée lexicale est à l'intérieur du bloc qui a créé la variable      8\. Il existe huit « types » de base : nil, boolean, number, string, userdata, function, thread, et table       9\. Lua est un langage à typage dynamique. Il n'y a pas de type à l'initialisation d'une variable et la variable adopte le type de la valeur qu'elle détient      10\. type(maVariable) --> retourne le type de, maVariable sous forme de texte (string). |

| Les Strings |
| --- |
| 1\. Une chaîne de caractères est une séquence finie de caractères      2\. Elle se définit entre apostrophes ou guillemets doubles ou entre doubles crochets      3\. Lua peut manipuler des séquences d'échappement comme en C      4\. L'opérateur de concaténation est signifié par `..`      5\. La coercition est la conversion automatique des nombres en strings et des strings en nombres      6\. Lua utilise les patterns      7\. Lua dispose de 14 fonctions, pour manipuler les chaînes de caractères. |

| Les opérateurs arithmétiques |
| --- |
| Les opérateurs arithmétiques sont : les binaires : + (addition), - (soustraction), \* (multiplication), / (division), % (modulo), ^ (élévation) ; l'unaire : - (négation).   |

| Les opérateurs relationnels |
| --- |
| **\==** égal      **~=** différent de      **<** plus petit que      **\>** plus grand que      **<=** plus petit que ou égal      **\>=** plus grand que ou égal   |

| Les opérateurs logiques |
| --- |
| **and** et      **or** ou      **not** différent de      10 or 20  --> 10      10 or nil  --> 10      nil or "a"  --> "a"      nil and 10  --> nil      false and nil  --> false      false or nil  --> nil      10 and 20  --> 20 |

| Les structures de contrôles |
| --- |
| 1\. Ne pas confondre = qui signifie transfert et == qui signifie égal      2\. Les opérateurs relationnels servent de conditions aux boucles      3\. Faire très attention à la portée des variables      4\. while … condition … do … faire … end : la condition est à l'intérieur de la boucle      5\. repeat … faire … until … condition : la condition est à l'extérieur de la boucle      6\. break : permet de sortir d'une boucle, avant la fin      7\. return : retourne le résultat d'une fonction. |

| Les Boucles FOR |
| --- |
| Deux formes : numérique et générique      Numérique : for j = 1, 10, -1 do … ici votre code … end      Générique avec clé : for k, v in pairs(table) do … ici votre code … end      Générique avec index : for i, v in ipairs(table) do … ici votre code … end |

| Les fonctions |
| --- |
| 1\. Une fonction est une expression exécutable, dont la valeur est de type fonction      2\. On lui envoie des paramètres, elle reçoit des arguments et retourne des valeurs      3\. function NomFonction(arg1, arg2) … corps de la fonction … end      4\. nomFonction(arg1, arg2… ) Les 3 petits points attendent des arguments non encore définis      5\. Une fonction anonyme est une fonction qui n'a pas de nom      5\. l'écriture : `function NomFonction() … corps … end` est équivalent à : `nomFonction = function() … corps … end`      6\. local x, y, \_, \_ = NomFonction(a, b) : NomFonction attend en retour les valeurs x et y, mais n'a pas besoin des 2 dernières(\_)      7\. Une  closure  est une fonction qui capture les références de variables libres dans l'environnement lexical. Quand une fonction est incluse dans une autre fonction, elle a pleinement accès aux variables locales de la fonction englobante, cette fonctionnalité est appelée portée lexicale (local)      8\. Définir d'abord la variable, puis lui affecter la fonction : loca l f = nil; f = function (n) … end      9\. Un appel récursif est similaire au goto du basic, un renvoi qui ne nécessite pas de retour automatique.      10\. l’appel d’une fonction récursive, c’est une fonction qui s’appelle elle-même. |

| Les tables |
| --- |
| 1\. Avec Lua une table est un objet      2\. Une table possède une structure dynamique qui augmente au fur et à mesure des besoins      3\. La numérotation des champs commence à 1 et non 0      4\. Il y a deux façons principales de créer une matrice en Lua :      \-utiliser une table de table      \-rassembler les deux indices en un seul      5\. Utiliser une table avec n champs pointant vers le haut pour représenter une liste      6\. Pour lire un fichier, utiliser la fonction io.read("\*all")      7\. Utiliser les itérateurs pairs() et ipairs() pour traverser les tables :      7.1 Un itérateur est une construction qui permet de répéter (itérer) une même instruction sur les différents éléments d'un ensemble d'articles      7.2 Deux fonctions Lua sont à votre disposition lorsque vous aurez besoin de parcourir une table ou une liste de noms.      7.3 Il s'agit des fonctions :      \- pairs = key, valeur - Ordre indéfini   \- ipairs = index, valeur - Ordre croissant      \-k = key (clé)      \-v = valeur      \-t = table (ou liste de noms)      \-i = index (lors d'un index numérique)      7.3 À utiliser de la façon suivante :      `for k, v in pairs(t) do ... ici votre code ... end`      `for i, v in ipairs(t) do ... ici votre code ... end`   |
