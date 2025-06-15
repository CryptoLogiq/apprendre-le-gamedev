---
title: "Solution : Déplacer et tourner une image"
date: 2022-02-26
---

### Code de la Solution :

```
-- Cette ligne permet d'afficher des traces dans la console pendant l'exécution
io.stdout:setvbuf('no')

-- Empêche Love de corriger les contours d'images.
-- Indispensable pour du pixel art :
love.graphics.setDefaultFilter("nearest")

-- Cette ligne permet de déboguer pas à pas dans ZeroBraneStudio :
if arg[#arg] == "-debug" then require("mobdebug").start() end

-- debug for Visual Code :
if os.getenv("LOCAL_LUA_DEBUGGER_VSCODE") == "1" then  require("lldebugger").start() end 

------------------------------------------------------------------------------------------------------
love.window.setTitle("Affichage, Deplacement et Rotation d'une Image")
------------------------------------------------------------------------------------------------------

local vaisseau = {}

vaisseau.imageData = love.graphics.newImage("vaisseau.png")
vaisseau.w , vaisseau.h = vaisseau.imageData:getDimensions()
vaisseau.ox = vaisseau.w/2
vaisseau.oy = vaisseau.h/2
vaisseau.rayon = math.max(vaisseau.ox, vaisseau.oy)

vaisseau.x, vaisseau.y = 300, 250
vaisseau.speed = 60

vaisseau.rotate = 0
vaisseau.speedRotate = 5

local color = {} -- color = {r,g,b,a}
color.white =   {1,   1,    1,    1}
color.blue =    {0,   0,    1,    0.8}
color.green =   {0,   1,    0,    0.8}

function love.update(dt)
  
  -- Rotate
  if love.keyboard.isDown("left") and love.keyboard.isDown("right") then
    -- Si on appuis sur deux touches de direction opposée : on ne bouge pas =)
  elseif love.keyboard.isDown("left") then
    vaisseau.rotate = vaisseau.rotate - (vaisseau.speedRotate *  dt)
  elseif love.keyboard.isDown("right") then
    vaisseau.rotate = vaisseau.rotate + (vaisseau.speedRotate * dt)
  end

  -- Horizontal Move
  if love.keyboard.isDown("q") and love.keyboard.isDown("d") then
    -- Si on appuis sur deux touches de direction opposée : on ne bouge pas =)
  elseif love.keyboard.isDown("q") then -- left
    vaisseau.x = vaisseau.x - vaisseau.speed * dt
  elseif love.keyboard.isDown("d") then -- right
    vaisseau.x = vaisseau.x + vaisseau.speed * dt
  end
  
  -- Vertical Move
  if love.keyboard.isDown("z") and love.keyboard.isDown("s") then
    -- Si on appuis sur deux touches de direction opposée : on ne bouge pas =)
  elseif love.keyboard.isDown("z") then -- up
    vaisseau.y = vaisseau.y - vaisseau.speed * dt
  elseif love.keyboard.isDown("s") then -- down
    vaisseau.y = vaisseau.y + vaisseau.speed * dt
  end

end

function love.draw()

  -- l'image du vaisseau :
  love.graphics.setColor(color.white)
  love.graphics.draw( vaisseau.imageData, vaisseau.x, vaisseau.y, vaisseau.rotate, vaisseau.sx, vaisseau.sy, vaisseau.ox, vaisseau.oy)

  -- son contour vert :
  love.graphics.setColor(color.green)
  love.graphics.circle("line", vaisseau.x, vaisseau.y, vaisseau.rayon)

  -- le point d'origine de l'image en bleue:
  love.graphics.setColor(color.blue)
  love.graphics.circle("fill", vaisseau.x, vaisseau.y, 5)

end
```

### Télécharger la Solution :

[https://www.dropbox.com/Mini\_Tp\_deplacer\_et\_tourner\_image.zip](https://www.dropbox.com/Mini_Tp_deplacer_et_tourner_image.zip)

* * *
