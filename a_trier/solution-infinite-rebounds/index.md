---
title: "Solution : Infinite Rebounds"
date: 2022-02-26
---

### La Solution que je vous propose :

```
-- Titre du jeu (visible sur la fenetre) :
love.window.setTitle("Faconkode.fr : Infinite Rebounds")

-- Color = {red,  green,  blue,  alpha}
local blanc = { 1,       1,    1, 1 }
local rouge = { 1,       0,    0, 1 }
local vert  = { 0,       1,    0, 1 }
local bleu  = { 0,       0,    1, 1 }
local noir  = { 0,       0,    0, 1 }
local gris  = { 0.25, 0.25, 0.25, 1 }

-- Table de l'Objet de la Fenetre Love2D:
local Fenetre = {}

-- Fonction 
function Fenetre.load()
  -- la fenetre est un rectangle(x, y, w, h) :
  Fenetre.x=0
  Fenetre.y=0
  Fenetre.w=love.graphics.getWidth()
  Fenetre.h=love.graphics.getHeight()
end
--

-- Table des Objets Rectangles :
local Rectangles = {}

-- Fonction de creation des Rectangles :
function Rectangles.load()
  Rectangles[1] = {x=10,    y=10,    w=100,  h=20,   color=blanc, vx=526,     vy=40}
  Rectangles[2] = {x=210,   y=125,   w=100,  h=20,   color=rouge, vx=125,     vy=240}
  Rectangles[3] = {x=605,   y=525,   w=100,  h=20,   color=vert,  vx=0-226,   vy=0-340}
  Rectangles[4] = {x=405,   y=260,   w=100,  h=20,   color=bleu,  vx=0-125,   vy=0-650}
  Rectangles[5] = {x=350,   y=480,   w=100,  h=20,   color=gris,  vx=850,   vy=0-340}
end
--

-- Fonction de déplacement des Rectangles :
function Rectangles.move(dt)
  for i = 1, #Rectangles do
    Rectangles[i].x = Rectangles[i].x + (Rectangles[i].vx * dt)
    Rectangles[i].y = Rectangles[i].y + (Rectangles[i].vy * dt)
  end
end
--

-- Fonction de Replacement et Renvois de vélocité des Rectangles :
function Rectangles.renvoiVelocite(dt)
  for i = 1, #Rectangles do
    -- Gauche :
    if Rectangles[i].x <= Fenetre.x then
      Rectangles[i].x = Fenetre.x
      Rectangles[i].vx = 0 - Rectangles[i].vx
    end
    -- Droite :
    if Rectangles[i].x + Rectangles[i].w >= Fenetre.w then
      Rectangles[i].x = Fenetre.w - Rectangles[i].w
      Rectangles[i].vx = 0 - Rectangles[i].vx
    end
    -- Haut :
    if Rectangles[i].y <= Fenetre.y then
      Rectangles[i].y = Fenetre.y
      Rectangles[i].vy = 0 - Rectangles[i].vy
    end
    -- Bas :
    if Rectangles[i].y >= Fenetre.h then
      Rectangles[i].y = Fenetre.h - Rectangles[i].h
      Rectangles[i].vy = 0 - Rectangles[i].vy
    end
  end
end
--

-- Fonction d'update des Rectangles avec le DeltaTime :
function Rectangles.update(dt)
  Rectangles.move(dt)
  Rectangles.renvoiVelocite(dt)
end
--

-- Fonction draw des Rectangles :
function Rectangles.draw()
  for i = 1, #Rectangles do
    love.graphics.setColor(Rectangles[i].color)
    love.graphics.rectangle("fill", Rectangles[i].x, Rectangles[i].y, Rectangles[i].w, Rectangles[i].h)
    love.graphics.setColor(blanc)
  end
end
--

-- Les Fonctions love2D :
function love.load()
  Fenetre.load()
  Rectangles.load()
end
--

function love.update(dt)
  Rectangles.update(dt)
end
--

function love.draw()
  Rectangles.draw()
end
--
```

### Rendu :

cliquer sur le lien pour voir le rendu directement dans votre navigateur :

[Inifinite Rebounds by Crypto Logiq (itch.io)](https://cryptologiq.itch.io/inifinite-rebounds)

* * *
