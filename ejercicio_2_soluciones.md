# Ejercicio 1

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

# Ejercicio 2

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

# Ejercicio 3

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
