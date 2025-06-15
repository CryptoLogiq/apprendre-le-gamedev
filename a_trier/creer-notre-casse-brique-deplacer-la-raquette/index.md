---
title: "Créer notre casse brique : Déplacer la raquette !"
date: 2023-04-08
---

## Déplacer la raquette à droite ou à gauche

Réaliser les étapes suivantes :

- Ajouter une vitesse à notre raquette

- Déplacer la raquette à gauche avec un appui de touche

- Déplacer la raquette à droite avec un appui de touche

Je vais utiliser pour ce cours les touches directionnelles, mais garder à l'esprit qu'il faut garder une certaine ergonomie pour vos futurs jeux.

Voici les modifications à apporter pour la raquette :

```
local raquette = {x=300, y=555, w=200, h=40, speed=250}

function love.update(dt)
	-- deplacement de la raquette Droite ou Gauche
	if love.keyboard.isDown("left") then
    	raquette.x = raquette.x - (raquette.speed * dt)
	elseif love.keyboard.isDown("right") then
		raquette.x = raquette.x + (raquette.speed * dt)
	end
end
```

Vous remarquerez, que la raquette peut sortir de l'écran ce qui n'est pas terrible...

On va donc tester sa position pour limiter le mouvement de la raquette à la zone de la fenêtre du jeu.

```
local raquette = {x=300, y=555, w=200, h=40, speed=250}

function love.update(dt)
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
```

Maintenant si la raquette est en dehors de l'écran on la replace au bord gauche ou droit de la fenêtre, c'est beaucoup mieux.

Le code complet :

```
love.window.setTitle("Casse Brique")

local raquette = {x=300, y=555, w=200, h=40, speed=250}

local balle = {x=0, y=0, w=40, h=40}

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
  	-- la balle suit la raquette
	balle.x = raquette.x + ((raquette.w / 2) - (balle.w / 2))
	balle.y = raquette.y - (balle.h +  2)
  
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
```

* * *
