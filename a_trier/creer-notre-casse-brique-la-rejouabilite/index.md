---
title: "Créer notre casse brique : La rejouabilité !"
date: 2023-04-09
---

## La rejouabilité du jeu !

Pour améliorer la rejouabilité il faut que le joueur puisse enchaîner les niveaux et également avoir des mécaniques qui font perdre le joueur pour le pousser à visser le meilleur score possible.

- Créer un nouveau stage après la destruction de toutes les briques

- Remise à zéro de la partie lorsque le joueur n’a plus de vies

## Nouveau stage (niveau)

Lorsque toutes les briques sont détruites nous rajouterons une ligne supplémentaire à notre variable **niveau.lignes** pour augmenter la difficulté et donner du challenge au joueur.

Nous devons recréer les briques lorsque la balle n'est pas dans la zone des briques pour éviter des collisions non gérables.

Pour simplifier le code nous remettrons la balle sur la raquette pour éviter des collisions avec la balle pendant la création des briques.

Enfin nous rajouterons les nouvelles briques.

Pour savoir quand créer le prochain stage, nous devons tester la variable **niveau.totalBriques**

- Vérifier si la valeur de **niveau.totalBriques** vaut 0

Si elle est bien à 0 Alors :

- Replacer la balle sur la raquette

- Repasser **balle.isGlue** à **true**

- Augmenter la variable de **niveau.lignes** de **+1**

- Recréer nos briques avec la fonction **niveau.create()**

```
function love.update(dt)

  -- collision entre la balle et les briques : 
  local x, y, w, h -- nos variables de positions et dimensions de nos briques
  x = 0
  y = 0
  w = 800 / 6
  h = 30
  for ligne=1, niveau.lignes do
    for colonne=1, niveau.colonnes do

      if briques[ligne][colonne] == 1 then -- on test la brique si celle-ci vaut 1

        -- test collision en X ?
        if balle.x + balle.w > x and balle.x < x + w then

          -- test collsion en Y ?
          if balle.y + balle.h > y and balle.y < y + h then
            balle.y = y+h
            balle.vy = 0 - balle.vy
            briques[ligne][colonne] = 0 -- ainsi la brique ne sera plus tester
            game.score = game.score + 10 -- on augmente le score de 10 points !
            niveau.totalBriques = niveau.totalBriques - 1 -- decompte des briques détruites
            if niveau.totalBriques == 0 then
              balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2)) -- remet la balle sur la raquette sur l axe X
              balle.y = raquette.y - (balle.h +  2) -- remetla balle sur la raquette sur l axe Y
              balle.isGlue = true -- replace la balle sur la raquette
              niveau.lignes = niveau.lignes + 1 -- on augmente la difficulte en ajouter une ligne à nos briques
              niveau.create() -- on recreer le tableau de briques avec de nouvelles valeurs
            end
          end
        end

      end

      x = x + w
    end
    x = 0
    y = y + h
  end

end
```

## Remise à zéro en cas de défaite

Pour faire ceci nous allons créer une fonction game.new()

Cette fonction doit remettre toutes les valeurs par défaut, la position de la raquette et de la balle, les briques, le score, le nombre de lignes de notre niveau a sa valeur par défaut.

Nous allons donc rajouter des variables à notre table niveau pour connaître la valeur par défaut des lignes.

```
local niveau = {lignesDef=5, lignes=5, colonnes=6, totalBriques=0}
```

Pour la position de la raquette, nous allons proceder pareil.

```
local raquette = {xDef=300, yDef=555, x=300, y=555, w=200, h=40, speed=250}
```

Créer la fonction pour remettre le jeu à zero : **game.new()**

```
function niveau.create()

-- creation des briques
  for ligne=1, niveau.lignes do
    briques[ligne] = {}
    for colonne=1, niveau.colonnes do
      briques[ligne][colonne] = 1
    end
  end

  niveau.totalBriques = niveau.lignes * niveau.colonnes -- total de briques

end
```

Maintenant il ne reste plus qu'à ajouter notre condition à notre update.

Nous la placerons avec la detection de la balle avec le bors bas de l'ecran.

- Vérifier si la valeur de **game.vies** vaut 0

Si elle est bien à 0 Alors :

- Exécuter **game.new()**

```
function love.update(dt)
  
    -- la balle est perdue si elle a touchee le bord en bas
  if balle.y + balle.h > 600 then
    balle.isGlue = true
    balle.vy = -1
    balle.vx = -1
    game.vies = game.vies - 1 -- on enleve une vie au joueur
    if game.vies == 0 then
      game.new()
    end
  end
  
end
```

Voir le code complet :

```
love.window.setTitle("Casse Brique")

local raquette = {xDef=300, yDef=555, x=300, y=555, w=200, h=40, speed=250}

local balle = {x=0, y=0, w=40, h=40, isGlue=true, vx=-1, vy=-1, speed=300}

local briques = {} -- nos briques

local game = {score=0, vies=3}

local niveau = {lignesDef=5, lignes=5, colonnes=6, totalBriques=0}

function game.new()
  -- on remets la raquette au centre de l'ecran
  raquette.x = raquette.xDef
  raquette.y = raquette.yDef

  -- on remets la balle sur la raquette
  balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2))
  balle.y = raquette.y - (balle.h +  2)
  balle.isGlue = true

  -- on remets le score a 0
  game.score = 0

  -- remets a zero le nombre de lignes de briques
  niveau.lignes = niveau.lignesDef

  -- on recreer les briques pour une nouvelle partie
  niveau.create()
end
--

function niveau.create()

-- creation des briques
  for ligne=1, niveau.lignes do
    briques[ligne] = {}
    for colonne=1, niveau.colonnes do
      briques[ligne][colonne] = 1
    end
  end

  niveau.totalBriques = niveau.lignes * niveau.colonnes -- total de briques

end
--

function love.load()
  niveau.create()
end

function love.update(dt)
  if balle.isGlue == true then
    balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2))
    balle.y = raquette.y - (balle.h +  2)
  elseif balle.isGlue == false then
    balle.x = balle.x + (balle.vx * balle.speed * dt)
    balle.y = balle.y + (balle.vy * balle.speed * dt)
  end

  -- la balle rebondi sur le bord droit ou gauche
  if balle.x < 0 then
    balle.x = 0
    balle.vx = 0 - balle.vx
  elseif balle.x + balle.w > 800 then
    balle.x = 800 - balle.w
    balle.vx = 0 - balle.vx
  end

  -- la balle rebondi sur le bord en haut
  if balle.y < 0 then
    balle.y = 0
    balle.vy = 0 - balle.vy
  end

  -- la balle est perdue si elle a touchee le bord en bas
  if balle.y + balle.h > 600 then
    balle.isGlue = true
    balle.vy = -1
    balle.vx = -1
    game.vies = game.vies - 1 -- on enleve une vie au joueur
    if game.vies == 0 then
      game.new()
    end
  end

  -- deplacement de la raquette Droite ou Gauche
  if love.keyboard.isDown("left") then
    raquette.x = raquette.x - (raquette.speed * dt)
  elseif love.keyboard.isDown("right") then
    raquette.x = raquette.x + (raquette.speed * dt)
  end

  -- limiter le deplacement de la raquette a la fenetre du jeu
  if raquette.x < 0 then
    raquette.x = 0
  elseif raquette.x + raquette.w > 800 then
    raquette.x = 800 - raquette.w
  end

  -- collision balle avec raquette :
  -- test collision en X ?
  if balle.x + balle.w > raquette.x and balle.x < raquette.x + raquette.w then

    -- test collsion en Y ?
    if balle.y + balle.h > raquette.y then

      -- 1 | on replace la balle juste au dessus de la raquette
      balle.y = raquette.y - balle.h

      -- 2 | on inverse la direction VY de la balle
      balle.vy = 0 - balle.vy

    end

  end

  -- collision entre la balle et les briques : 
  local x, y, w, h -- nos variables de positions et dimensions de nos briques
  x = 0
  y = 0
  w = 800 / 6
  h = 30
  for ligne=1, niveau.lignes do
    for colonne=1, niveau.colonnes do

      if briques[ligne][colonne] == 1 then -- on test la brique si celle-ci vaut 1

        -- test collision en X ?
        if balle.x + balle.w > x and balle.x < x + w then

          -- test collsion en Y ?
          if balle.y + balle.h > y and balle.y < y + h then
            balle.y = y+h
            balle.vy = 0 - balle.vy
            briques[ligne][colonne] = 0 -- ainsi la brique ne sera plus tester
            game.score = game.score + 10 -- on augmente le score de 10 points !
            niveau.totalBriques = niveau.totalBriques - 1 -- decompte des briques détruites
            if niveau.totalBriques == 0 then
              balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2)) -- remet la balle sur la raquette sur l axe X
              balle.y = raquette.y - (balle.h +  2) -- remetla balle sur la raquette sur l axe Y
              balle.isGlue = true -- replace la balle sur la raquette
              niveau.lignes = niveau.lignes + 1 -- on augmente la difficulte en ajouter une ligne à nos briques
              niveau.create() -- on recreer le tableau de briques avec de nouvelles valeurs
            end
          end
        end

      end

      x = x + w
    end
    x = 0
    y = y + h
  end

end
--

function love.draw()

  -- notre raquette
  love.graphics.rectangle("fill", raquette.x, raquette.y, raquette.w, raquette.h)

  -- notre balle
  love.graphics.rectangle("fill", balle.x, balle.y, balle.w, balle.h)

  local x, y, w, h -- nos variables briques
  x = 0
  y = 0
  w = 800 / 6
  h = 30

  for ligne=1, niveau.lignes do

    for colonne=1, niveau.colonnes do
      if briques[ligne][colonne] == 1 then -- on affiche la brique si celle-ci vaut 1
        love.graphics.rectangle("fill", x+1, y+1, w-2, h-2)
      end
      x = x + w -- a chaque colonne on decale notre variable x de la largeur d une brique
    end

    x = 0 -- on remets la position x pour la ligne suivante
    y = y + h -- on decalle la position y pour la ligne suivante
  end

  -- le score
  love.graphics.setColor(0,0,1,1) -- red, green, blue, alpha
  love.graphics.print("Score : "..game.score, 10, 8)
  love.graphics.setColor(1,1,1,1) -- on remets la couleur par defaut pour la suite des appels

  -- les vies
  love.graphics.setColor(0,0,1,1) -- red, green, blue, alpha
  love.graphics.print("Vies restantes : "..game.vies, 680, 8)
  love.graphics.setColor(1,1,1,1) -- on remets la couleur par defaut pour la suite des appels

end

function love.keypressed(key)
  if key == "space" and balle.isGlue == true then
    balle.isGlue = false
  end
end
```

Votre premier jeu fonctionne =D

Si vous souhaitez améliorer le jeu, Il y a quelques pistes :

- Mettre une image de fond

- Ajouter des sons de bruitages lors des collisions

- Mettre une musique

- Garder le meilleur score en mémoire

- Remplacer les briques, la balle et la raquette par des images

- Augmenter la vitesse de la raquette

- Augmenter la vitesse de la balle après chaque stage complété

- Augmenter la valeur de vies des briques

- Améliorer les collisions

- etc.

Vous pouvez essayer de faire ceci, en vous aidant du [wiki de love2d](https://love2d.org/wiki/Main_Page).

* * *

_Pour ce premier jeu, j'ai volontairement simplifié pas mal de concepts qu'on reverra plus tard en profondeur dans les cours suivants._

_Entraîner vous déjà avec le casse brique comme exercice._

_Il faut que vous puissiez **le refaire en vous aidant le moins possible**._

* * *

Pour les **niveaux intermédiaires**, je vous propose une **approche Orienté Objet** à la page suivante.

[Le Casse Brique version Orienté Object](https://gamelogiq.dev/liste-des-differents-cours/6-les-concepts-essentiels/tableau-a-2-dimensions-2d/creer-notre-casse-brique-approche-oriente-object/ "Créer notre casse brique : Approche Orienté Object !")

* * *
