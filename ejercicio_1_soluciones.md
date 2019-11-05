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

# Ejercicio 7

1. Crea un fichero `foo.md`
  ```console
  curso$ touch foo.md
  ```
2. Comprueba el estado del repositorio
  ```console
  curso$ git status
  ```
3. ¿Qué pasará si realizamos ahora `git commit`?
3. Añade el fichero `foo.md` a la lista de ficheros ignorados
  ```
  curso$ echo "foo.md" > .gitignore
  ```
5. Comprueba el estado del repositorio
  ```console
  curso$ git status
  ```
6. Ignora el fichero `.gitignore`
  ```console
  curso$ echo ".gitignore" >> .gitignore
  ```
7. Comprueba el estado del repositorio
  ```console
  curso$ git status
  ```
8. Deshaz el paso 6 y haz commit del fichero `.gitignore`
  ```console
  git add .gitignore
  git commit -m 'Ignora fichero foo.md'
  ```

# Ejercicio 8

1. Crea un fichero `LEEME.txt` con contenido:
  ```
  Proyecto Git para realizar ejercicios del curso
  ```
  ```console
  curso$ cat > LEEME.txt
  Proyecto Git para realizar ejercicios del curso
  [Ctrl+D]
  ```
2. Añade el fichero al repositorio y confirma la adición
  ```console
  curso$ git add LEEME.txt
  curso$ git commit -m 'Añade fichero LEEME.txt'
  ```
3. Renombra el archivo a `README.md`
  ```console
  curso$ git mv LEEME.txt README.md
  ```
4. Comprueba el estado
  ```console
  curso$ git status
  ```
5. Confirma los cambios
  ```console
  curso$ git commit
  ```
6. Borra el archivo `README.md`
  ```console
  curso$ git rm README.md
  ```
7. Confirma los cambios
  ```console
  curso$ git commit
  ```

# Ejercicio 9

1. Comprueba el historial de confirmaciones
  ```console
  curso$ git log
  ```
2. Muestra el historial de confirmaciones, incluyendo los cambios de cada confirmación
  ```console
  curso$ git log -p
  ```
3. Muestra el historial de confirmaciones, incluyen un resumen de los cambios. Limita la salida a las últimos 3 confirmaciones.
  ```console
  curso$ git log --stat -3
  ```
4. Comprueba las distintas opciones para formatear la salida del historial de confirmaciones
  ```console
  curso$ git log --help
  ```
5. Configura Git para que, por defecto, se muestre el log con formato `oneline`
  ```console
  curso$ git config format.pretty oneline
  ```
6. Vuelve a comprobar el historial de confirmaciones (sin indicar opciones)
  ```console
  curso$ git log
  ```
7. Consulta las modificaciones realizadas por el commit con mensaje `Añade fichero LEEME.txt`
  ```console
  curso$ git show 0583a2d8227b4eed8c68ae06dbfffa5148939cbd
  ```
8. Consulta las modificaciones realizadas por la antepenúltima modificación
  ```console
  curso$ git show HEAD~2
  ```
9. Consulta las modificaciones realizadas por las 4 últimas modificaciones
  ```console
  curso$ git diff HEAD~3^
  ```
10. Consulta las modificaciones realizadas entres 2 commits cualquiera
  ```console
  curso$ git diff 54f5548e2d3e1f2cc558e66744daaef84a981d72^ 54f5548e2d3e1f2cc558e66744daaef84a981d72
  ```

# Ejercicio 10

1. Registrarse en [gitlab del curso](http://cursogit.um.es)
2. Crea un proyecto llamado `curso`
3. Añade el repositorio remoto al repositorio local `curso`
  ```console
  curso$ git remote add origin http://cursogit.um.es/amateo/curso.git
  ```
4. Publica el contenido
  ```console
  curso$ git push origin master
  ```
5. Navega por el repositorio

