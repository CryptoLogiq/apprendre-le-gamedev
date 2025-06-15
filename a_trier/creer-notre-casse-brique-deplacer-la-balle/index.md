---
title: "Créer notre casse brique : Déplacer la balle !"
date: 2023-04-08
---

## Déplacer la balle !

Passons à notre balle maintenant.

Pour savoir si la balle doit suivre la raquette ou se déplacer, il va nous falloir une variable. Une variable de type **booléen** fera parfaitement l'affaire.

Nous lui donnerons une **V**élocitée **en X** et une **V**élocitée en **Y**.

Ainsi qu'une variable **vitesse**.

- On nommera notre variable booléenne **isGlue**.

- Ajouter les variables de vélocités, **vx** et **vy**.

- Ajouter la variable **speed**.

```
local balle = {x=0, y=0, w=40, h=40, isGlue=true, vx=-1, vy=-1, speed=300}
```

il faut aussi modifier l'update de la balle pour savoir si elle doit suivre la raquette ou bien etre en mouvement avec ses vélocités :

```
function love.update(dt)
  	-- la balle suit la raquette si isGlue est a true
	if balle.isGlue == true then
		balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2))
		balle.y = raquette.y - (balle.h +  2)
    else
		balle.x = balle.x + (balle.vx * balle.speed * dt)
		balle.y = balle.y + (balle.vy * balle.speed * dt)
    end
end
```

Tout comme la raquette il faut limiter la balle a la fenêtre du jeu, mais nous voulons qu'elle change de direction aussi.

- Bord gauche : Replacer **x** et Changer de direction **vx**

- Bord Droite : Replacer **x** et Changer de direction **vx**

- Bord Haut : Replacer **y** et Changer de direction **vy**

- Bord Bas : Remettre **isGlue** à **true** et réinitialisés les valeurs de vx et vy à leurs valeurs initiales

```
function love.update(dt)
  	-- la balle suit la raquette si isGlue est a true
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
	end
end
```

Maintenant, il nous faut créer un **événement** déclencheur pour que notre balle change son booléen **isGLue** à **false**.

On utilisera l'événement suivant :  
Si on **presse** la touche **espace** et que **balle.siGlue** est bien a **true** Alors **balle.isGlue** vaudra **false** Fin

```
function love.keypressed(key)
  if key == "space" and balle.isGlue == true then
    balle.isGlue = false
  end
end
```

Désormais votre balle doit rebondir sur les murs et revenir sur la raquette lorsqu'elle touche le bord bas de l'écran.

Voici le code complet :

```
love.window.setTitle("Casse Brique")

local raquette = {x=300, y=555, w=200, h=40, speed=250}

local balle = {x=0, y=0, w=40, h=40, isGlue=true, vx=-1, vy=-1, speed=300}

local briques = {} -- nos briques

-- creation des briques
for ligne=1, 5 do
  briques[ligne] = {}
  for colonne=1, 6 do
    briques[ligne][colonne] = 1
  end
end
--

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

  for ligne=1, 5 do

    for colonne=1, 6 do
      love.graphics.rectangle("fill", x+1, y+1, w-2, h-2)  
      x = x + w -- a chaque colonne on decale notre variable x de la largeur d une brique
    end

    x = 0 -- on remets la position x pour la ligne suivante
    y = y + h -- on decalle la position y pour la ligne suivante
  end

end

function love.keypressed(key)
  if key == "space" and balle.isGlue == true then
    balle.isGlue = false
  end
end
```

* * *

Il ne nous reste plus que les collisions à gérer.

- Collision entre la balle et la raquette

- Collision entre la balle et les briques

* * *
