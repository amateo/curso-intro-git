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

