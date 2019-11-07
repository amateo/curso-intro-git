# Ejercicio 1

1. Configurar Git definiendo el nombre de usuario, el correo electrónico.
2. Establece el coloreado automático para la salida
3. Lista las opciones de configuración globales

# Ejercicio 2

1. Crea un repositorio nuevo con el nombre `curso` y muestra su contenido

# Ejercicio 3

1. Comprueba el estado del repositorio
2. Crea un fichero `indice.md` con el contenido:
  ```
  # Introducción a Git
  # Flujo de trabajo básico
  # Repositorios remotos
  ```
3. Comprueba de nuevo el estado del repositorio
4. Añade el fichero al área de preparación
5. Vuelve a comprobar el estado del repositorio

# Ejercicio 4

1. Realizar un commit de los últimos cambios con el mensaje `Añade índice del curso`
2. Ver el estado del repositorio

# Ejercicio 5

1. Cambiar el fichero `indice.md` para que contenga lo siguiente:
  ```
  # Introducción a Git
  # Flujo de trabajo básico
  # Gestión de ramas
  # Repositorios remotos
  ```
2. Mostrar los cambios con respecto a la última versión del repositorio
3. Hacer un commit de los cambios con el mensaje `Añade capítulo sobre gestión de ramas`

# Ejercicio 6

1. Mostrar los cambios de la última versión del repositorio con respecto a la anterior
2. Cambiar el mensaje del último commit por `Añade capítulo sobre gestión de ramas al índice`
3. Volver a mostrar los últimos cambios del repositorio

# Ejercicio 7

1. Crea un fichero `foo.md`
2. Comprueba el estado del repositorio
3. ¿Qué pasará si realizamos ahora `git commit`?
3. Añade el fichero `foo.md` a la lista de ficheros ignorados
4. Comprueba el estado del repositorio
5. Ignora el fichero `.gitignore`
6. Comprueba el estado del repositorio
7. Deshaz el paso 6 y haz commit del fichero `.gitignore`

# Ejercicio 8

1. Crea un fichero `LEEME.txt` con contenido:
  ```
  Proyecto Git para realizar ejercicios del curso
  ```
2. Añade el fichero al repositorio y confirma la adición
3. Renombra el archivo a `README.md`
4. Comprueba el estado
5. Confirma los cambios
6. Borra el archivo `README.md`
7. Confirma los cambios

# Ejercicio 9

1. Comprueba el historial de confirmaciones
2. Muestra el historial de confirmaciones, incluyendo los cambios de cada confirmación
3. Muestra el historial de confirmaciones, incluyen un resumen de los cambios. Limita la salida a las últimos 3 confirmaciones.
4. Comprueba las distintas opciones para formatear la salida del historial de confirmaciones
5. Configura Git para que, por defecto, se muestre el log con formato `oneline`
6. Vuelve a comprobar el historial de confirmaciones (sin indicar opciones)
7. Consulta las modificaciones realizadas por el commit con mensaje `Añade fichero LEEME.txt`
8. Consulta las modificaciones realizadas por la antepenúltima modificación
9. Consulta las modificaciones realizadas por las 4 últimas modificaciones
10. Consulta las modificaciones realizadas entres 2 commits cualquiera

# Ejercicio 10

1. Registrarse en [gitlab del curso](http://cursogit.um.es)
2. Añade clave ssh a tu perfil de gitlab
3. Crea un proyecto llamado `curso`
4. Añade el repositorio remoto al repositorio local `curso`
5. Publica el contenido
6. Muestra los repositorios remotos del proyecto
7. Navega por el repositorio

# Ejercicio 11

1. Clona el repositorio creado anteriormente en otra ruta de tu equipo
2. Muestra los repositorios remotos y el estado
3. Añade y confirma un fichero `capitulo1.md` con contenido:
  ```
  # Introducción a Git
  Este capítulo se va a hablar de cómo comenzar a utilizar Git
  ```
4. Comprueba el estado del repositorio
5. Publica las modificaciones en el repositorio remoto sin introducir usuario/clave
6. Vuelve al repositorio anterior (utilizado en ejercicio 10) y actualízalo
