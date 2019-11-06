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
