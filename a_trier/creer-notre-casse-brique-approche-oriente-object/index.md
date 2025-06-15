---
title: "Créer notre casse brique : Approche Orienté Object !"
date: 2023-04-10
---

## Le Casse Brique version Orienté Object

Je n'utilise pas le tableau 2D pour parcourir les briques, cependant j'utilise toujours les boucles imbriquées en lignes et colonnes pour concevoir mes briques.

- Nos briques sont dans une liste

- Chaque entitées du jeu ont leur propre draw et update

```
love.window.setTitle("Casse Brique Object")

local raquette = {xDef=300, yDef=555, x=300, y=555, w=200, h=40, speed=250}

local balle = {x=0, y=0, w=40, h=40, isGlue=true, vx=-1, vy=-1, speed=300}

local briques = {} -- contiendra les fonctions pour les briques
local liste_briques = {} -- contient nos briques

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

function game.draw()
  -- le score
  love.graphics.setColor(0,0,1,1) -- red, green, blue, alpha
  love.graphics.print("Score : "..game.score, 10, 8)
  love.graphics.setColor(1,1,1,1) -- on remets la couleur par defaut pour la suite des appels

  -- les vies
  love.graphics.setColor(0,0,1,1) -- red, green, blue, alpha
  love.graphics.print("Vies restantes : "..game.vies, 680, 8)
  love.graphics.setColor(1,1,1,1) -- on remets la couleur par defaut pour la suite des appels
end
--

function niveau.create()

  liste_briques = {} -- on efface toutes les briques

  local startX, x, y, w, h -- nos variables de positions et dimensions de nos briques
  startX = 0
  x = 0
  y = 0
  w = 800 / 6
  h = 30

  -- creation des briques
  for ligne=1, niveau.lignes do
    for colonne=1, niveau.colonnes do

      -- on creer notre objet brique
      local brique = {x=x, y=y, h=h, w=w, vie=1}
      function brique.draw()
        if brique.vie >= 1 then
          love.graphics.rectangle("fill", brique.x+1, brique.y+1, brique.w-2, brique.h-2)
        end
      end

      -- on ajoute la brique a notre liste
      table.insert(liste_briques, brique)

      x = x + w -- a chaque colonne on decale notre variable x de la largeur d une brique
    end
    x = startX -- on remets la position x pour la ligne suivante
    y = y + h -- on decalle la position y pour la ligne suivante
  end

  niveau.totalBriques = niveau.lignes * niveau.colonnes -- total de briques

end
--

function raquette.update(dt)
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
end
--

function raquette.draw()
  love.graphics.rectangle("fill", raquette.x, raquette.y, raquette.w, raquette.h)
end
--

function balle.update(dt)
  -- deplacement de la balle
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

  -- collision balle avec raquette :
  if balle.x + balle.w > raquette.x and balle.x < raquette.x + raquette.w then -- test collision en X ?
    if balle.y + balle.h > raquette.y then -- test collsion en Y ?
      balle.y = raquette.y - balle.h -- 1 | on replace la balle juste au dessus de la raquette
      balle.vy = 0 - balle.vy -- 2 | on inverse la direction VY de la balle
    end
  end
end
--

function balle.draw()
  love.graphics.rectangle("fill", balle.x, balle.y, balle.w, balle.h)
end
--

function briques.update(dt)
  -- collision entre la balle et les briques : 
  for i=1, #liste_briques do

    local brique = liste_briques[i]

    if brique.vie >= 1 then -- on test la brique si celle-ci vaut 1
      -- test collision en X ?
      if balle.x + balle.w > brique.x and balle.x < brique.x + brique.w then
        -- test collsion en Y ?
        if balle.y + balle.h > brique.y and balle.y < brique.y + brique.h then
          
          balle.y = brique.y + brique.h
          balle.vy = 0 - balle.vy
          brique.vie = brique.vie - 1 -- on enleve une vie a la brique
          game.score = game.score + 10 -- on augmente le score de 10 points !

          -- si la brique est detruite
          if brique.vie <= 0 then
            niveau.totalBriques = niveau.totalBriques - 1 -- decompte des briques détruites
          end

          -- si il n'y a plus de brique : nouveau stage
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
  end
  
end
--

function briques.draw()
  for i=1, #liste_briques do
    local brique = liste_briques[i]
    brique.draw()
  end
end
--

function love.load()
  niveau.create()
end
--

function love.update(dt)

  raquette.update(dt)

  balle.update(dt)

  briques.update(dt)

end
--

function love.draw()

  raquette.draw()

  balle.draw()

  briques.draw()

  game.draw()

end

function love.keypressed(key)
  if key == "space" and balle.isGlue == true then
    balle.isGlue = false
  end
end
```

Avec cette approche, on peut facilement ignoré les briques qui sont detruite et les faire tomber au sol, par exemple.

**Pourquoi ?** Car chacunes de nos briques possèdent leurs propres positions stockés dans leurs variables.

On pourrait donc les faire tomber, les faire exploser quand elles touchent le sol, etc.

Le Tableau 2D possede des positions fixes, ce qui reste tres pratique pour la construction de maps, placer des déclencheurs etc, mais ils sont figés à une position unique.

* * *
