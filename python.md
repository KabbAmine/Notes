> 16 avril 2016 17:23:59

# Python

## TODO

- `complex`?
- Division entière `//`?
- `^` (ou exclusif) et `<<` (décalage) [?](file:///home/k-bag/T%C3%A9l%C3%A9chargements/Torrents%20DL/Formations%20&%20cie/Mooc_Python_inria_s01et02/semaine02/2%20Les%20types%20de%20base/Complement-entiers-bit-a-bit.html)


## Types

### Types numériques

- `int` + `long int`
- `float`
- `complex`: `2 + 3j` **(?)**

### Entiers et bases

- `0b0001`: Binaire (2).
- `0o310`: Octal (8).
- `0xc8`: Hexadécimal (16).

Il est possible d'utiliser la fonction `int()`
  ```python
  int(0xB)     # =11
  int('A', 16) # =10
  ```

### Opérations arithmétiques

- `elem1 ** elem2`: Puissance (e.g `3 ** 1 # =9`)

## Fonctions built-in utiles

- `type({elem})` retourne le type d'{elem}.
- `isinstance({elem}, type)` retourne `True` si {elem} est de type `type`.
  ```python
  isinstance('string', str)     # True
  isinstance(['elem1', 1], str) # False
  ```
- `dir()` retourne tous les éléments présents dans un objet.
- `help({elem})` pour afficher une description d'{elem}.
- `exit()` pour quitter l'interpréteur python.

## Divers

- `import this` pour lire le "The Zen of Python"
- `$ python -i {file}` exécute le {file} et lance l'interpréteur de suite.
- Il est préférable de toujours spécifier l'encodage à utiliser via `# -*- coding: utf-8 -*-`  
  Si nécessaire, pour déterminer l'encodage actuel:
    ```python
    import sys
    print sys.getdefaultencoding()
    ```
  e.g pour d'anciennes versions de Windows:
    ```python
    # -*- coding: cp1252 -*-
    ```

## Conventions

- `non_de_variables`: Variables, fonctions.
- `NOM_DE_CONSTANTE`: Constantes.
