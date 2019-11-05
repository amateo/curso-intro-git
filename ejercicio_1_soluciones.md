# Ejercicio 1

1. Configurar Git definiendo el nombre de usuario, el correo electrónico.
  ```console
  git config --global user.name "Ángel L. Mateo"
  git config --global user.email "amateo@um.es"
  ```
2. Establece el coloreado automático para la salida
  ```console
  git config --global color.ui auto
  ```
3. Lista las opciones de configuración globales
  ```console
  git config --list
  ```

# Ejercicio 2

1. Crea un repositorio nuevo con el nombre `curso` y muestra su contenido
  ```console
  tmp $ mkdir curso
  tmp $ cd curso/
  curso$ git init
  Inicializado repositorio Git vacío en /tmp/curso/.git/
  curso$ ls
  curso$ ls -A
  .git
  ```

# Ejercicio 3

1. Comprueba el estado del repositorio
  ```console
  curso$ git status
  ```
2. Crea un fichero `indice.md` con el contenido:
  ```
  # Introducción a Git
  # Flujo de trabajo básico
  # Repositorios remotos
  ```
  ```console
  curso$ cat > indice.md
  # Introducción a Git
  # Flujo de trabajo básico
  # Repositorios remotos
  ```
3. Comprueba de nuevo el estado del repositorio
  ```console
  curso$ git status
  ```
4. Añade el fichero al área de preparación
  ```console
  curso$ git add indice.md
  ```
5. Vuelve a comprobar el estado del repositorio
  ```console
  curso$ git status
  ```

# Ejercicio 4

1. Realizar un commit de los últimos cambios con el mensaje `Añade índice del curso`
  ```console
  curso$ git commit -m 'Añade índice del curso'
  ```
2. Ver el estado del repositorio
  ```console
  curso$ git status
  ```

# Ejercicio 5

1. Cambiar el fichero `indice.md` para que contenga lo siguiente:
  ```
  # Introducción a Git
  # Flujo de trabajo básico
  # Gestión de ramas
  # Repositorios remotos
  ```
  ```console
  curso$ cat > indice.md
  # Introducción a Git
  # Flujo de trabajo básico
  # Gestión de ramas
  # Repositorios remotos
  [Ctrl+D]
  ```
2. Mostrar los cambios con respecto a la última versión del repositorio
  ```console
  curso$ git diff
  ```
3. Hacer un commit de los cambios con el mensaje `Añade capítulo sobre gestión de ramas`
  ```console
  curso$ git add indice.md
  curso$ git commit -m 'Añade capítulo sobre gestión de ramas'
  ```

# Ejercicio 6

1. Mostrar los cambios de la última versión del repositorio con respecto a la anterior
  ```console
  curso$ git show
  ```
2. Cambiar el mensaje del último commit por `Añade capítulo sobre gestión de ramas al índice`
  ```console
  curso$ git commit --amend -m 'Añade capítulo sobre gestión de ramas al índice'
  ```
3. Volver a mostrar los últimos cambios del repositorio
  ```console
  curso$ git show
  ```

