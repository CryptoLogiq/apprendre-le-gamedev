---
title: "Le Pong : Code complet"
date: 2023-04-15
---

## Solution : Le Pong

* * *

```
love.window.setTitle("Le Pong")

local raquettes = {}

local balle = {x=0, y=0, w=15, h=15, speed=250, speedDef=250, vx=0, vy=0, follow=true, joueur=1}

local joueur = {}

local filet = {x=400,y=0,w=1,h=600}

local gameUI = {}

local Game = {over=false, winner=1}

-- ###### Functions ######

function CheckCollision(x1,y1,w1,h1, x2,y2,w2,h2)
  return x1 < x2+w2 and
  x2 < x1+w1 and
  y1 < y2+h2 and
  y2 < y1+h1
end
--

function math.angle(x1,y1, x2,y2) return math.atan2(y2-y1, x2-x1) end

function raquettes.new(positionX)
  local raquette = {x=positionX, y=225, yDef=225, w=20, h=150, speed=300}
  function raquette.draw()
    love.graphics.rectangle("fill", raquette.x,  raquette.y,  raquette.w,  raquette.h)
  end
  return raquette
end
--

function joueur.load()
  -- joueur 1
  joueur[1] = {score=0}
  joueur[1].raquette = raquettes.new(10) -- positionX
  joueur[1].keys = {up="z", down="s", fire="space"}
  -- joueur 2
  joueur[2] = {score=0}
  joueur[2].raquette = raquettes.new(770) -- positionX
  joueur[2].keys = {up="up", down="down", fire="return"}
end
--

function joueur.update(dt)
  for n=1, 2 do
    local j = joueur[n]
    local pad = joueur[n].raquette
    if love.keyboard.isDown(j.keys.up) and love.keyboard.isDown(j.keys.down) then
      -- nothing
    elseif love.keyboard.isDown(j.keys.up) then
      pad.y = pad.y - (pad.speed * dt)
    elseif love.keyboard.isDown(j.keys.down) then
      pad.y = pad.y + (pad.speed * dt)
    end
    -- limit to screen
    if pad.y <= 0 then
      pad.y = 0
    elseif pad.y + pad.h >= 600 then
      pad.y = 600 - pad.h
    end
  end
end
--

function joueur.draw()
  for n=1, #joueur do
    joueur[n].raquette.draw()
  end
end
--

function balle.update(dt)

  if balle.follow then
    local x
    local y
    local raquette
    if balle.joueur == 1 then
      raquette = joueur[1].raquette
      -- Position x a droite de la raquette
      x = raquette.x + raquette.w + 1
    elseif balle.joueur == 2 then
      raquette = joueur[2].raquette
      -- Position x a gauche de la raquette
      x = raquette.x - balle.w - 1
    end
    -- Position Y au centre de la raquette
    y = raquette.y + ( (raquette.h/2) - (balle.w/2) )
    --
    balle.x = x
    balle.y = y

  else -- elle est en cours de deplacement libre

    balle.x = balle.x + (balle.vx * balle.speed * dt)
    balle.y = balle.y + (balle.vy * balle.speed * dt)

    -- rebonds murs, on accelere la vitesse de la balle a chaque rebonds
    if balle.y <= 0 then
      balle.y = 0
      balle.vy = 0 - balle.vy
      balle.speed = balle.speed + 20
    elseif balle.y + balle.h >= 600 then
      balle.y = 600 - balle.h
      balle.vy = 0 - balle.vy
      balle.speed = balle.speed + 20
    end

    -- rebonds raquettes
    for n=1, 2 do
      local pad = joueur[n].raquette
      if CheckCollision(balle.x,balle.y,balle.w,balle.h, pad.x,pad.y,pad.w,pad.h) then

        -- nouvel angle
        local pointRepere
        local decX = 20
        if n == 1 then
          pointRepere = {
            x= pad.x - decX,
            y=pad.y + (pad.h/2)
          }
        else
          pointRepere = {
            x= pad.x + pad.w + decX,
            y=pad.y + (pad.h/2)
          }
        end
        local angle = math.angle(pointRepere.x,pointRepere.y, balle.x+(balle.w/2),balle.y+(balle.h/2))
        balle.vx = math.cos(angle)
        balle.vy = math.sin(angle)

        -- replace la balle
        if n == 1 then
          balle.x = pad.x + pad.w
        else
          balle.x = pad.x - balle.w
        end

        -- augmente la vitesse
        balle.speed = balle.speed + 30

      end
    end

    -- balle Out
    if balle.x <= 0 then
      balle.follow = true
      balle.speed = balle.speedDef
      joueur[2].score = joueur[2].score + 1
    elseif balle.x + balle.w >= 800 then
      balle.follow = true
      balle.speed = balle.speedDef
      joueur[1].score = joueur[1].score + 1
    end

    -- game win ?
    for n=1, 2 do
      if joueur[n].score >= 11 then
        Game.over = true
        Game.winner = n
      end
    end
  end

end
--

function balle.draw()
  love.graphics.rectangle("fill", balle.x, balle.y, balle.w, balle.h)
end
--

function filet.draw()
  love.graphics.rectangle("fill", filet.x, filet.y, filet.w, filet.h)
end
--

function gameUI.draw()
  love.graphics.print("J1 : "..joueur[1].score, 200, 10)
  love.graphics.print("J2 : "..joueur[2].score, 600, 10)
end
--

--###### Love2D ######

function love.load()
  love.graphics.setFont(love.graphics.newFont(22))
  joueur.load()
end
--

function love.update(dt)
  if Game.over then
    -- nothing
  else
    balle.update(dt)
    joueur.update(dt)
  end
end
--

function love.draw()

  if Game.over then
    if Game.winner ==1 then
      love.graphics.print("Player "..Game.winner.." Win !", 150, 100)
    else
      love.graphics.print("Player "..Game.winner.." Win !", 450, 100)
    end
  end

  filet.draw()
  joueur.draw()
  balle.draw()
  --
  gameUI.draw()

end
--

function love.keypressed(k)
  if balle.follow then
    local j = joueur[balle.joueur] -- j1 ou j2 ?
    if k == j.keys.fire then
      if balle.joueur == 1 then
        balle.vx = 1 -- la balle doit partir sur la droite
      else
        balle.vx = -1 -- la balle doit partir sur la gauche
      end
      -- direction de la balle au hasard (haut ou bas)
      local vy = {-1, 1}
      balle.vy = vy[love.math.random(#vy)]
      --
      balle.follow = false
      -- prochain joueur a lancer la balle
      if balle.joueur == 1 then
        balle.joueur = 2
      else
        balle.joueur = 1
      end
    end
  end
end
--
```

* * *

C'est toujours améliorable, sons, musique, images etc...  
  
Le jeu est simple car destiné en challenge pour les débutants.  
  
J'ai volontairement mis en avant la logique du code pour les choses essentiels tels que le gameplay et une petite dynamique pour ne pas lasser les gens (même si ca reste un pong...).  
  
Et les conditions de victoire pour jouer à 2 ;)

* * *
