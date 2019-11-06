# Ejercicio 12

1. Lista las ramas del proyecto
  ```
  curso$ git branch
  ```
2. Lista los archivos del directorio `.git`. Observa que hay un fichero `HEAD`. Muestra el contenido de dicho fichero
  ```
  curso$ ls .git/
  curso$ cat .git/HEAD
  ```
3. Muestra el contenido del archivo `.git/refs/heads/master`.
  ```
  curso$ cat .git/refs/heads/master
  ```
4. Compara la salida con los commits mostrados por un `git log`
5. Crea una nueva rama llamada `pruebas`
  ```
  curso$ git branch pruebas
  ```
6. Vuelve a listar las ramas del proyecto
  ```
  curso$ git branch
  ```
7. Observa los contenidos del directorio `.git/refs/heads/master`
  ```
  curso$ ls .git/refs/heads/
  ```
  ```
  curso$ cat .git/refs/heads/*
  ```

# Ejercicio 13

1. Cambia a la rama `pruebas`
  ```
  curso$ git checkout pruebas
  ```
2. Lista las ramas del repositorio
  ```
  curso$ git branch
  ```
3. Lista las ramas del repositorio, incluidas las ramas remotas
  ```
  curso$ git branch -a
  ```
4. Muestra el histórico de los últimos 5 cambios
  ```
  curso$ git log --oneline -5
  ```

# Ejercicio 14

1. Añade y confirma un fichero `capitulo2.md` con contenido:
  ```
  # Flujo de trabajo básico
  Este es el capítulo dedicado a explicar el flujo de trabajo
  ```
2. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
3. Observa los contenidos del directorio `.git/refs/heads/master`
  ```
  curso$ ls .git/refs/heads/
  ```
  ```
  curso$ cat .git/refs/heads/*
  ```
4. Cambia a la rama `master`
  ```
  curso$ git checkout master
  ```
5. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
6. Mezcla el contenido de la rama `pruebas` en la rama `master`. Observa el tipo de mezcla que ha hecho.
  ```
  curso$ git merge pruebas
  ```
7. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```

# Ejercicio 15

1. Crea una rama llamada `capitulo3`. Cambia a dicha rama.
  ```
  curso$ git checkout -b capitulo3
  ```
2. Añade y confirma un fichero `capitulo3.md` con contenido:
  ```
  # Gestión de ramas
  Este es el capítulo dedicado a la gestión de ramas
  ```
  ```
  curso$ git add capitulo3.md
  curso$ git commit
  ```
3. Crea una nueva rama llamada `capitulo4` a partir de la rama `master`. Cambia a dicha rama
  ```
  curso$ git checkout -b capitulo4 master
  ```
4. Añade y confirma un fichero `capitulo4.md` con contenido:
  ```
  # Repositorios remotos
  Capítulo dedicado a la gestión de repositorios remotos
  ```
  ```
  curso$ git add capitulo4.md
  curso$ git commit -m 'Crea capitulo 4'
  ```
5. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
6. Colócate en la rama `master`
  ```
  curso$ git checkout master
  ```
7. Mezcla el contenido de la rama `capitulo3` en la rama `master`. Observa el tipo de mezcla que se ha realizado.
  ```
  curso$ git merge capitulo3
  ```
8. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
9. Muestra un listado de las ramas que ya están mezcladas
  ```
  curso$ git checkout master
  ```
10. Muestra un listado de las ramas pendientes de mezcla
  ```
  curso$ git branch --no-merged
  ```
11. Mezcla el contenido de la rama `capitulo4` en la rama `master`. Observa el tipo de mezcla que se ha realizado.
  ```
  curso$ git merge capitulo4
  ```
12. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
13. Muestra un listado de las ramas pendientes de mezcla
  ```
  curso$ git branch --no-merged
  ```

# Ejercicio 16

1. Limpia todas las ramas de trabajo ya finalizado
  ```
  curso$ git branch --merged
  ```
  ```
  curso$ git branch -d capitulo3 capitulo4 pruebas
  ```
2. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
  ```
  curso$ git log --oneline -5
  ```
3. ¿Qué diferencia observas con respecto al último listado obtenido en el ejercicio anterior?
  ```
  La diferencia es que en estos listados ya no aparecen las referencias a las ramas borradas
  ```

# Ejercicio 17

NOTA: Si has seguido todos los pasos tal cual se han ido indicando, tendrás la rama `master` de tu repositorio local desligada (sin track) de cualquier rama remota y tendrás el remoto `origin`. La salida del `git status` debería ser muy parecida a:
```
curso$ git status
En la rama master
nada para hacer commit, el árbol de trabajo esta limpio
```

1. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas `master` de los distintos repositorios.
  ```
  curso$ git log --oneline -5
  ```
2. Sube el último trabajo realizado al repositorio en gitlab.
  ```
  curso$ git push origin master
  ```
3. Vuelve al directorio del repositorio clonado en el ejercicio 11
4. Muestra el estado del repositorio
  ```
  curso-2$ git status
  ```
5. Actualiza el repositorio local *sin actualizar* la copia de trabajo
6. Muestra el estado del repositorio. Observa la diferencia con respecto al estado anterior
  ```
  curso-2$ git status
  ```
7. Actualiza el directorio de trabajo con los últimos cambios realizados en el repositorio remoto.
  ```
  curso-2$ git merge origin/master
  ```
