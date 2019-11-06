# Ejercicio 1

1. Lista las ramas del proyecto
2. Lista los archivos del directorio `.git`. Observa que hay un fichero `HEAD`. Muestra el contenido de dicho fichero
3. Muestra el contenido del archivo `.git/refs/heads/master`.
4. Compara la salida con los commits mostrados por un `git log`
5. Crea una nueva rama llamada `pruebas`
6. Vuelve a listar las ramas del proyecto
7. Observa los contenidos del directorio `.git/refs/heads/master`

# Ejercicio 2

1. Cambia a la rama `pruebas`
2. Lista las ramas del repositorio
3. Lista las ramas del repositorio, incluidas las ramas remotas
4. Muestra el histórico de los últimos 5 cambios

# Ejercicio 3

1. Añade y confirma un fichero `capitulo2.md` con contenido:
  ```
  # Flujo de trabajo básico
  Este es el capítulo dedicado a explicar el flujo de trabajo
  ```
2. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
3. Observa los contenidos del directorio `.git/refs/heads/master`
4. Cambia a la rama `master`
5. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
6. Mezcla el contenido de la rama `pruebas` en la rama `master`. Observa el tipo de mezcla que ha hecho.
7. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.

# Ejercicio 4

1. Crea una rama llamada `capitulo3`. Cambia a dicha rama.
2. Añade y confirma un fichero `capitulo3.md` con contenido:
  ```
  # Gestión de ramas
  Este es el capítulo dedicado a la gestión de ramas
  ```
3. Crea una nueva rama llamada `capitulo4` a partir de la rama `master`. Cambia a dicha rama
4. Añade y confirma un fichero `capitulo4.md` con contenido:
  ```
  # Repositorios remotos
  Capítulo dedicado a la gestión de repositorios remotos
  ```
5. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
6. Colócate en la rama `master`
7. Mezcla el contenido de la rama `capitulo3` en la rama `master`. Observa el tipo de mezcla que se ha realizado.
8. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
9. Muestra un listado de las ramas que ya están mezcladas
10. Muestra un listado de las ramas pendientes de mezcla
11. Mezcla el contenido de la rama `capitulo4` en la rama `master`. Observa el tipo de mezcla que se ha realizado.
12. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
13. Muestra un listado de las ramas pendientes de mezcla

# Ejercicio 5

1. Limpia todas las ramas de trabajo ya finalizado
2. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas.
3. ¿Qué diferencia observas con respecto al último listado obtenido en el ejercicio anterior?

# Ejercicio 6

NOTA: Si has seguido todos los pasos tal cual se han ido indicando, tendrás la rama `master` de tu repositorio local desligada (sin track) de cualquier rama remota y tendrás el remoto `origin`. La salida del `git status` debería ser muy parecida a:
```
curso$ git status
En la rama master
nada para hacer commit, el árbol de trabajo esta limpio
```

1. Muestra el histórico de los últimos 5 cambios. Observa los apuntadores de ramas `master` de los distintos repositorios.
2. Sube el último trabajo realizado al repositorio en gitlab.
3. Vuelve al directorio del repositorio clonado en el ejercicio 11
4. Muestra el estado del repositorio
5. Actualiza el repositorio local *sin actualizar* la copia de trabajo
6. Muestra el estado del repositorio. Observa la diferencia con respecto al estado anterior
7. Actualiza el directorio de trabajo con los últimos cambios realizados en el repositorio remoto.
