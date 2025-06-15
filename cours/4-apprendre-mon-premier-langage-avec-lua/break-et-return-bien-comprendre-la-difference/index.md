---
title: "Break et Return (Bien comprendre la différence !)"
date: 2022-02-24
---

## **Break**

Le break sert à interrompre une boucle dans lequel il se trouve (son bloc de code).

Le bloc est interrompu par le break peu importe son niveau d’imbrication, par exemple dans une fonction il n'arrêtera pas la fonction, mais juste la boucle ou il se situe et le code continuera de s'exécuter juste après la boucle.

Exemple :

```lua
nbLignes = 5
nbColonnes = 5
--
playerColonne = 3
playerLigne = 5
--
function returnStartPosition()
 for x = 1, nbColonnes do
   playerColonne = playerColonne - 1
   if playerColonne == 1 then -- back player to position x = 1
     break
   end
 end
 --
 for y = 1, nbLignes do
   playerLigne = playerLigne - 1
   if playerLigne == 1 then -- back player to position y = 1
     break
   end
 end
end
--
returnStartPosition()
print("playerColonne : "..playerColonne.."n".."playerLigne  : "..playerLigne)
```

sortie console :
```
playerColonne : 1
playerLigne  : 1
```

La **boucle FOR x** est **Arrêté** par le **break**, puis le code continue d'exécuter la fonction et exécute donc la prochaine **boucle FOR y**.



## **Return**

Le return, retourne le résultat d’une fonction et la quitte tout simplement.

Voyons la différence avec la même fonction avec l’utilisation de return :

```lua
nbLignes = 5
nbColonnes = 5
--
playerColonne = 3
playerLigne = 5
--
function returnStartPosition()
 for x = 1, nbColonnes do
   playerColonne = playerColonne - 1
   if playerColonne == 1 then -- back player to position x = 1
     return
   end
 end
 --
 for y = 1, nbLignes do
   playerLigne = playerLigne - 1
   if playerLigne == 1 then -- back player to position y = 1
     return
   end
 end
end
--
returnStartPosition()
print("playerColonne : "..playerColonne.."n".."playerLigne  : "..playerLigne)
```

sortie console :
```
playerColonne : 1
playerLigne  : 5
```

Lorsque la première condition **if playerColonne == 1 then** est rempli, le return nous fait quitter la fonction.

Pour avoir un code fonctionnel similaire à l'exemple avec break, mais avec un return et sans faire trop compliqué…

Nous pouvons par exemple créer deux fonctions qui return la bonne position lorsque celle-ci est atteinte.

Exemple :

```lua
nbLignes = 5
nbColonnes = 5
--
playerColonne = 3
playerLigne = 5
--
function returnStartPositionX()
 for x = 1, nbColonnes do
   if playerColonne - x == 1 then -- back player to position x = 1
     return playerColonne - x
   end
 end
end
--
function returnStartPositionY()
 for y = 1, nbLignes do
   if playerLigne - y == 1 then -- back player to position y = 1
     return playerLigne - y
   end
 end
end
--
playerColonne = returnStartPositionX()
playerLigne = returnStartPositionY()
print("playerColonne : "..playerColonne.."n".."playerLigne  : "..playerLigne)
```

sortie console :
```
playerColonne : 1
playerLigne  : 1
```



Un autre exemple avec un return de type booléen :

```lua
heroX = 10
heroY = -500

monEcranX = 0
monEcranY = 0
monEcranW = 800
monEcranH = 600

function horsScreen()
  if heroX < monEcranX then 
    return true
  elseif heroY < monEcranY then 
    return true
  elseif heroX > monEcranW then 
    return true
  elseif heroY > monEcranH then 
    return true
  else
    return false
  end 
end 

if horsScreen() then 
  print("ATTENTION ! héro est en dehors de l'écran") 
else 
  print("héro est dans l'écran, RAS !") 
end
```

sortie console :
```
ATTENTION ! héro est en dehors de l'écran
```

**Fin du chapitre, on se retrouve pour la suite =)**
