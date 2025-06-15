---
title: "Convertir les unités d'angles"
date: 2022-02-26
---

### Convertir les angles

  Love2D attends des angles radian, or visuellement nous maîtrisons mieux les angles en degré... Heureusement, Il existe des fonctions toutes prêtes pour nous aider à convertir des angles.

* * *

### Convertir radian > vers > degré :

```
math.deg( angleRadian) 
```

Exemple :

```
monAngleRadian = 1.5707963267949

monAngleDegre = math.deg(monAngleRadian)

print(monAngleDegre)
```

sortie console :

```
90  
```

* * *

### Convertir degré > vers > radian :

```
math.rad( angleDegre) 
```

Exemple :

```
monAngleDegre = 90

monAngleRadian = math.rad(monAngleDegre)

print(monAngleRadian)
```

sortie console :

```
1.5707963267949  
```

* * *
