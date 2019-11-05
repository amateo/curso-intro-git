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

