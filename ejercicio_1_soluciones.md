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

