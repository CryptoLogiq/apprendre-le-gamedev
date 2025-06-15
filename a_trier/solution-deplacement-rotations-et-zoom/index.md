---
title: "Solution : Déplacement, rotations et Zoom"
date: 2023-04-05
---

Lien vers le code source : [http://gamelogiq.dev/wp-content/uploads/2023/04/Image\_deplacement\_rotation\_zoom.zip](http://gamelogiq.dev/wp-content/uploads/2023/04/Image_deplacement_rotation_zoom.zip)

```
-- Changer le titre de la fenetre
love.window.setTitle("Cours image [move, rotate and zoom]")

-- variables des dimensions de la fenetre love2d
local ecranLargeur = love.graphics.getWidth()
local ecranHauteur = love.graphics.getHeight()

-- notre table pour manipuler rnotre image
local image = {}

function love.load()
  image.file = "squellettezombie.png"
  image.imgdata = love.graphics.newImage(image.file)
  --
  image.w, image.h = image.imgdata:getDimensions()
  image.ox, image.oy = image.w/2, image.h/2
  --
  image.x =  ecranLargeur / 2
  image.y =  ecranHauteur / 2
  --
  image.scale = 1
  image.angle = 270
  --
  image.showOrigin = true
end
--

function love.update(dt)

  local isDown = love.keyboard.isDown

  -- déplacement verticale Y :
  if isDown("z") and isDown("s") then
    -- rien, les deux touches sont appuyés
  elseif isDown("z") then -- HAUT
    image.y = image.y - 60 * dt
  elseif isDown("s") then -- BAS
    image.y = image.y + 60 * dt
  end

  -- déplacement horizontale X :
  if isDown("q") and isDown("d") then
    -- rien, les deux touches sont appuyés
  elseif isDown("q") then -- Gauche
    image.x = image.x - 60 * dt
  elseif isDown("d") then -- Droite
    image.x = image.x + 60 * dt
  end

  -- scale (Zoom) :
  if isDown("up") and isDown("down") then
    -- rien, les deux touches sont appuyés
  elseif isDown("up") then -- HAUT
    image.scale = image.scale + 10 * dt
  elseif isDown("down") then -- BAS
    image.scale = image.scale - 10 * dt
  end
  if image.scale <= 0 then image.scale = 0.1 end

-- Rotation :
  if isDown("left") and isDown("right") then
    -- rien, les deux touches sont appuyés
  elseif isDown("left") then -- Gauche
    image.angle = image.angle - 10 * dt
  elseif isDown("right") then -- Droite
    image.angle = image.angle + 10 * dt
  end

end
--

function love.draw()
  -- show image :
  -- love.graphics.draw(imageData, x, y , angle, scaleX, scale Y, OrigineX, OriginY) :
  love.graphics.draw(image.imgdata, image.x, image.y, image.angle, image.scale, image.scale, image.ox, image.oy) 

  -- show origine of image :
  if image.showOrigin then
    love.graphics.circle("fill",image.x, image.y, image.scale) 
  end

  -- Help Text :
  local txt = "Press z,q,s,d to move image".."\n"
  txt = txt.."Press up,down to change Zoom Scale".."\n"
  txt = txt.."Press left,right to change Angle".."\n"
  txt = txt.."Press Enter/return for ide/show Point of Origne".."\n"
  txt = txt.."Press space to reset to default".."\n"
-- txt = txt.."Or Press Escape to Quit.".."\n"
  love.graphics.print(txt,10,10,0,2,2)
  txt = ""
  txt = txt.."image.scale : "..image.scale.."\n"
  txt = txt.."image.angle : "..image.angle.."\n"
  txt = txt.."image.x : "..image.x.."\n"
  txt = txt.."image.y : "..image.y.."\n"
  love.graphics.print(txt,10,450,0,2,2)
end
--

function love.keypressed(key)
  if key == "return" then
    image.showOrigin = not image.showOrigin
  elseif key == "space" then
    love.load()
  end
end
--
```

* * *
