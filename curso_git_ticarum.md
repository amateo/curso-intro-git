name: inverse
layout: true
class: center, middle, inverse
---
# Introducción a Git

## Ángel L. Mateo (amateo at um.es)

---
# Referencias

- https://git-scm.com/book/es/v1/Empezando
- https://git-scm.com/book/es/v2

---
layout:false

## Control de versiones
### ¿Qué es control de versiones? (VCS)

- Sistema que registra los cambios sobre un archivo o conjunto de archivos
- Recuperar versiones específicas
- Comparar cambios a lo largo del tiempo
- Ver quién introdujo qué modificación

---

## Control de versiones
### VCS centralizado

<img src="img/centralized.png" width="90%">

???
- Servidor con todos los archivos versionados
- Clientes descargan los archivos desde servidor central
- Ventajas:
  - Todo el mundo conoce el último estado
  - Control detallado
  - Más sencillo
- Desventajas:
  - Punto único de fallo
---

.left-column[
## Control de versiones
### VCS distribuido
]

.right-column[
<img src="img/distributed.png" width="90%">
]

???
- Cliente replica completamente el repositorio
- Cada cliente es una copia completa
- Ventajas:
  - Sin punto único de fallo
  - Flexibilidad
- Desventajas:
  - Complejidad

---

## Control de versiones
### Copia instantánea vs diferencia

![Almacenamiento como cambios](img/deltas.png)

---

## Control de versiones
### Copia instantánea vs diferencia
![Almacenamiento como snapshots](img/snapshots.png)

???
- Sistemas tradicionales: archivos en el tiempo como una lista de cambios
- Git: Conjunto de instantáneas
  - Si no se modifica archivo, se guarda una liga al archivo anterior (que es igual)
---

## Control de versiones
### Estados

<img src="img/areas.png" width="95%">

- Confirmado (committed)
- Modificado (modified)
- Preparado (staged)

???
- Confirmado: Los datos se han almacenado de forma segura en la base de datos
- Modificado: El archivo se ha modificado, pero todavía no se ha confirmado el cambio en la base de datos
- Preparado: Se ha marcado el archivo modificado en la versión actual para que vaya en la siguiente confirmación

- Directorio .git: Se guardan los metadatos del repositorio
- Directorio de trabajo: Copia de una versión del proyecto. Donde vemos los ficheros
- Área de preparación (staging area): Normalmente en el directorio .git. Almacena información sobre lo que va a ir en la próxima confirmación.
---

## Control de versiones
### Flujo de trabajo

1. Modificas archivos (modificado)
  - Edición con cualquier editor/IDE
2. Preparas los archivos añadiéndolos al área de preparación (preparado)
  - `git stage <archivo>`
3. Confirmas los cambios (confirmado)
  - `git commit`
---

## Configuración inicial

- Archivo _/etc/gitconfig_: Configuración global para todos los usuarios
- _~/.gitconfig_ o _~/.config/git/config_: Específica del usuario
- _.git/config_: Específica del repositorio
- Comando: `git config`
  - `--global`: Configuración global (de usuario, _~/.gitconfig_) en vez de específica para el repositorio
  - `--system`: Configuración de sistema (_/etc/gitconfig_)
  - `--local`: Configuración específica para el repositorio (_.git/config_)
---

## Configuración inicial
### Identidad

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
---

## Configuración inicial
### Editor

```
$ git config --global core.editor vim
```
---

## Configuración inicial
### Comprobar configuración

```
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
push.default=simple
push.followtags=true
gc.autodetach=false
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
```

```
$ git config user.name
John Doe
```
---

## Obtener ayuda

- `git help <verb>`
- `git <verb> --help` 
- `man git-<verb>`
---

## Fundamentos de Git
### Inicializar un repositorio

```
$ git init
```

- Empezar un repositorio en el directorio actual
- Crea directorio _.git_
- Repositorio vacío
---

## Fundamentos de Git
### Clonar un repositorio

```
$ git clone https://github.com/libgit2/libgit2
$ git clone https://github.com/libgit2/libgit2 mylibgit
```
---

## Fundamentos de Git
### Protocolos de transferencia

- https://
- git://
- usuario@servidor:/ruta/del/repositorio.git
---

## Fundamentos de Git
### Guardando cambios

![ciclo de vida del estado de los archivos](img/lifecycle.png)
???
- untracked: Fichero que tenemos en el directorio (en el FS) pero que no está incluido en el repositorio, no se le hace seguimiento.
- unmodified: Fichero en VCS que no se ha modificado (está confirmado)
- modified: Fichero en VCS que se ha modificado, pero no se encuentra en el área de preparación (no se incluirá en commit)
- staged: Fichero en el área de preparación (se incluirá en commit)
---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
nada para hacer commit, el árbol de trabajo esta limpio
```
---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ echo 'My Project' > README.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que se será confirmado)

	README.md

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
```

---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ git add README.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	nuevo archivo:  README.md
```
---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ echo "Modificacion" >> CONTRIBUTING.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	nuevo archivo:  README.md

Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git checkout -- <archivo>..." para descartar los cambios en el directorio de trabajo)

	modificado:     CONTRIBUTING.md
```
---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ git add CONTRIBUTING.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	modificado:     CONTRIBUTING.md
	nuevo archivo:  README.md
```
---

## Fundamentos de Git
### Comprobar estado

```
amateo@amateo-EXCALIBUR:/tmp/test$ echo "Modificacion 2" >> CONTRIBUTING.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	modificado:     CONTRIBUTING.md
	nuevo archivo:  README.md

Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git checkout -- <archivo>..." para descartar los cambios en el directorio de trabajo)

	modificado:     CONTRIBUTING.md
```

???
- *OJO*: Un `git commit` aquí confirma solo la primera confirmación del archivo, que es la que tenemos en el área de preparación.
---

## Fundamentos de Git
### Comprobar estado

```
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```

???
- `??`: El archivo no está rastreado
- `A` / `M`: En el área de trabajo
- `XY`:
  - `X`: Estado en el área de preparación
  - `Y`: Estado en el directorio de trabajo
---

## Fundamentos de Git
### Ignorar archivos

- Archivo _.gitignore_
- [github/gitignore](https://github.com/github/gitignore]: Ficheros _.gitignore_ para distintos tipos de proyectos

```
$ cat .gitignore
*.[oa]
*~

# ignora los archivos terminados en .a
*.a

# pero no lib.a, aun cuando había ignorado los archivos terminados en .a en la línea anterior
!lib.a

# ignora unicamente el archivo TODO de la raiz, no subdir/TODO
/TODO

# ignora todos los archivos del directorio build/
build/

# ignora doc/notes.txt, pero no este: doc/server/arch.txt
doc/*.txt

# ignora todos los archivos .txt del directorio doc/
doc/**/*.txt
```

???
- Cualquier archivo terminado en _.o_ o _.a_
- Cualquier archivo terminado en _~_

---

## Fundamentos de Git
### Ver cambios

```
amateo@amateo-EXCALIBUR:/tmp/test$ git diff
diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
index da101a5..7cc6c66 100644
--- a/CONTRIBUTING.md
+++ b/CONTRIBUTING.md
@@ -1 +1,2 @@
 Modificacion
+Modificacion 2
```

???
- Compara directorio de trabajo con el área de preparación
- Muestra las modificaciones que aún no se han llevado al área de preparación
---

## Fundamentos de Git
### Ver cambios

```
amateo@amateo-EXCALIBUR:/tmp/test$ git diff --staged
diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
index e69de29..da101a5 100644
--- a/CONTRIBUTING.md
+++ b/CONTRIBUTING.md
@@ -0,0 +1 @@
+Modificacion
diff --git a/README.md b/README.md
new file mode 100644
index 0000000..56266d3
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+My Project
```

???
- Cambios en el área de preparación que se incluirán en la próxima confirmación
- `git diff`: Puede ser confuso: Si has preparado todos los cambios, no mostrará nada (el `--staged` si que mostraría estos cambios)
---

## Fundamentos de Git
### Confirmar cambios

```
$ git commit
```

- Confirma todos los cambios incluidos en el área de preparación
- Ignora archivos creados o modificados no incluidos en el área de preparación
- Lanza editor de preferencia (`$EDITOR` u opción `core.editor`)
- Mensaje de confirmación
- Opción `-m`: Indicar directamente el mensaje de confirmación
---

## Fundamentos de Git
### Confirmar cambios: Saltar el área de preparación

```
$ git commit -a
```

```
$ git commit <archivo> <archivo>
```

???

- `-a`: Prepara automáticamente todos archivos modificados (rastreados)
---

## Fundamentos de Git
### Eliminar archivos

```
amateo@amateo-EXCALIBUR:/tmp/test$ rm README.md
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios no rastreados para el commit:
  (usa "git add/rm <archivo>..." para actualizar a lo que se le va a hacer commit)
  (usa "git checkout -- <archivo>..." para descartar los cambios en el directorio de trabajo)

	borrado:        README.md

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
```
???

- Hemos borrado el archivo de la copia de trabajo, pero no hemos incluido el borrado en el área de preparación
---

## Fundamentos de Git
### Eliminar archivos

```
amateo@amateo-EXCALIBUR:/tmp/test$ git rm README.md
rm 'README.md'
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	borrado:        README.md
```
???
- Incluye el borrado en el área de preparación
- Se puede hacer únicamente el `git rm <archivo>` (y borra de la copia de trabajo)
- Opción `--cached` para borrar del VCS pero dejar el archivo en el área de trabajo

---

## Fundamentos de Git
### Renombrar archivos

- Git no rastrea los cambios en los nombres de los archivos
- Se registra como un borrado y una adición

```
amateo@amateo-EXCALIBUR:/tmp/test$ git mv README.md README
amateo@amateo-EXCALIBUR:/tmp/test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	renombrado:     README.md -> README
```

```
$ mv README.md README
$ git rm README.md
$ git add README
```

???
- Los dos modos son equivalentes
- El `git mv` existe por conveniencia/comodidad
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log
commit 4e49f0a6d0071855276a53b3191ae16fcd542ca1 (HEAD -> master, origin/master, origin/HEAD)
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Thu Oct 10 12:18:06 2019 +0200

    fix header/footer example (move to left with a text indent)

commit 309020f49620a19521016393ae9457a335509d04
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Sat Oct 5 18:29:52 2019 +0200

    document how to export to pdf

commit 41d45e83a1c2ee490496bee7253f5ae4bfe61214 (tag: v0.2.3)
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Thu Oct 3 22:45:10 2019 +0200

    bump version to 0.2.3

commit f5391d1869a3396af8e02d876336e62d2ecca900
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Thu Oct 3 22:39:57 2019 +0200

    update Pipfile.lock
```

???
- Lista de confirmaciones hechas, en orden cronológico inverso
- Muestra suma de confirmación del commit. En format SHA-1
- Nombre y dirección del correo del autor
- Fecha y mensaje de confirmación
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log -p -2
commit 4e49f0a6d0071855276a53b3191ae16fcd542ca1 (HEAD -> master, origin/master, origin/HEAD)
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Thu Oct 10 12:18:06 2019 +0200

    fix header/footer example (move to left with a text indent)

diff --git a/demo/remark/header-footer/img/placeholder-logo.svg b/demo/remark/header-footer/img/placeholder-logo.svg
deleted file mode 100644
index 3e74e81..0000000
--- a/demo/remark/header-footer/img/placeholder-logo.svg
+++ /dev/null
@@ -1,17 +0,0 @@
-<?xml version="1.0" encoding="UTF-8" standalone="no"?>
-<!-- Created with Inkscape (http://www.inkscape.org/) -->
-<svg
-   xmlns:svg="http://www.w3.org/2000/svg"
-   xmlns="http://www.w3.org/2000/svg"
...

commit 309020f49620a19521016393ae9457a335509d04
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Sat Oct 5 18:29:52 2019 +0200

    document how to export to pdf

diff --git a/doc/export.rst b/doc/export.rst
new file mode 100644
index 0000000..f41aee1
--- /dev/null
+++ b/doc/export.rst
@@ -0,0 +1,12 @@
+
+
+Exporting slides to PDF
+=======================
+
...
```

???
- `-p`: Muestra diferencias introducidas en cada versión
- `-2`: Muestra únicamente las dos últimas confirmaciones
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log --stat -2
commit 4e49f0a6d0071855276a53b3191ae16fcd542ca1 (HEAD -> master, origin/master, origin/HEAD)
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Thu Oct 10 12:18:06 2019 +0200

    fix header/footer example (move to left with a text indent)

 demo/remark/header-footer/img/placeholder-logo.svg | 17 -----------------
 demo/remark/header-footer/talk.css                 |  4 ++++
 demo/remark/header-footer/talk.md                  |  4 ++--
 3 files changed, 6 insertions(+), 19 deletions(-)

commit 309020f49620a19521016393ae9457a335509d04
Author: Radovan Bast <bast@users.noreply.github.com>
Date:   Sat Oct 5 18:29:52 2019 +0200

    document how to export to pdf

 doc/export.rst | 12 ++++++++++++
 doc/index.rst  |  7 +++++++
 2 files changed, 19 insertions(+)
```
???
- `--stat`: Estadísticas de cada confirmación: Ficheros modificados y resumen de modificaciones
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log --pretty=oneline -10
4e49f0a6d0071855276a53b3191ae16fcd542ca1 (HEAD -> master, origin/master, origin/HEAD) fix header/footer example (move to left with a text indent)
309020f49620a19521016393ae9457a335509d04 document how to export to pdf
41d45e83a1c2ee490496bee7253f5ae4bfe61214 (tag: v0.2.3) bump version to 0.2.3
f5391d1869a3396af8e02d876336e62d2ecca900 update Pipfile.lock
1e71d8d436bf87fca8565b8f404f4364e5d1e00e ignore .python-version
8b1fa7afbc53ab25d48dbda8f8db3f4729de71fc restore serving local mp4; closes #77
2b463e69ebe685b83b1f66513033bcf42feb4c64 get rid of error when 404 on local preview
b456e5584795d6e1868a7e30ad7c17c596a88c43 (tag: v0.2.2) bump version to 0.2.2
e04231cad05f8432732cd084911922bd1ceb0b80 fix rendering of svg images
16150d13be59fc9b0bcab41266de6a78a1ee8f62 add zappa to dev packages
```
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log --pretty=oneline --graph --pretty=format:"%h %s" --since=1.weeks
*   d3ae9bd30 Merge branch 'ARAWEB-3710' into 'production'
|\
| * 2121738ef añadir ruta /web/perfil/cv/
| * 29c90de1b cambiar ER para que el perfil pueda ir sin @um.es
* |   88e417d53 Merge branch 'TLM-8391-glis' into 'production'
|\ \
| |/
|/|
| * 771b5cdb5 TLM-8391: Corrige usuarios en profile::puppetdb::server
| * b7669efc8 TLM-8391: Actualiza módulo puppetdb de puppet
| * 544fb5650 TLM-8391: Fuerza versión 6 de puppetdb en las glis3x
| * 2c9f86103 TLM-8391: Configura postgres para glis30
| * 1257361d5 TLM-8391: Deshabilita nagios en glis30
|/
*   932db905f Merge branch 'TLM-8340' into 'production'
|\
| * 12da95768 TLM-8340: Activo de nuevo log de ActiveSync
| * dad4d718d TLM-8340: Desactivo log de ActiveSync
*   169502188 Merge branch 'TLMS-10042' into 'production'
|\
| * 0f9fd7d24 Otra redireccion de /web/innovacion/index.php hacia /web/innofacion
* a6bfcb606 Merge branch 'TLMS-8513' into 'production'
* 8e9db5150 TLMS-8513: meto a jjmerono en el contact group Grupo_AulaVirtual del site atica
```

???
- `--since`: Para indicar fecha en el límite del historial.
---

## Fundamentos de Git
### Historial de confirmaciones

```
$ git log --pretty=oneline --author amateo@um.es --since=20-Oct-2019
88e417d538271f122cf520b042075ce59870b8b2 Merge branch 'TLM-8391-glis' into 'production'
771b5cdb5b71f13a94463b042479f705299a69f8 TLM-8391: Corrige usuarios en profile::puppetdb::server
b7669efc866363da5fdad822b31d0af9aaeb6b57 TLM-8391: Actualiza módulo puppetdb de puppet
544fb5650471252c079047caa76c335692c523c4 TLM-8391: Fuerza versión 6 de puppetdb en las glis3x
2c9f861035011a06c8c70948a46608701de0e9b0 TLM-8391: Configura postgres para glis30
1257361d5800a0e2d7b28ef43e4771302d2bf7ad TLM-8391: Deshabilita nagios en glis30
```
---

## Fundamentos de Git
### Consultar modificaciones de una confirmación

```
$ git log -10  --pretty=oneline
d3ae9bd30939816f95e341b63ff95498e79cb7cc (HEAD -> production) Merge branch 'ARAWEB-3710' into 'production'
88e417d538271f122cf520b042075ce59870b8b2 Merge branch 'TLM-8391-glis' into 'production'
2121738ef1d5f40b3f1912f06052cb5720c2ae77 añadir ruta /web/perfil/cv/
...
```

```
$ git diff 88e417d538271f122cf520b042075ce59870b8b2
diff --git a/hieradata/cluster_araneum.eyaml b/hieradata/cluster_araneum.eyaml
index 2f3d5280c..bddf62606 100644
--- a/hieradata/cluster_araneum.eyaml
+++ b/hieradata/cluster_araneum.eyaml
@@ -358,7 +358,7 @@ nginx::nginx_servers:
         - '/web/matematicas/tfg/2018 https://www.um.es/web/estudios/grados/matematicas/tfg/historico permanent'
         - '^\/web\/matematicas\/tfg(\/)?$ https://www.um.es/web/estudios/grados/matematicas/tfg/historico permanent'
         - '^\/web\/matematicas\/pat https://www.um.es/web/matematicas/actividades/plan-de-accion-tutorial permanent'
-        - '^\/web\/perfil\/(([a-z0-9][-a-z0-9_\+\.]*[a-z0-9])\@um\.es)$ https://www.um.es/web/perfil/curriculum?correo=$1'
+        - '^\/web\/perfil\/cv\/(([a-z0-9][-a-z0-9_\+\.]*[a-z0-9])(\@um\.es)?)$ https://www.um.es/web/perfil/curriculum?correo=$1'
         - '/web/podcast        https://www.ivoox.com/radio-um.es_sw_1_1.html permanent'
         - '^\/web\/premios\/temasciezanos$  https://www.um.es/web/universidad/contenido/premios/textosciezanos'
         - '/web/sai        https://www.um.es/web/acti'
```
???
- Diferencias entre el estado actual (HEAD) y el commit `88e417d538271f122cf520b042075ce59870b8b2`
---

## Fundamentos de Git
### Consultar modificaciones de una confirmación

```
$ git diff 771b5cdb5b71f13a94463b042479f705299a69f8 2c9f861035011a06c8c70948a46608701de0e9b0
diff --git a/Puppetfile b/Puppetfile
index 15aefe553..a8c5739ab 100644
--- a/Puppetfile
+++ b/Puppetfile
@@ -66,7 +66,7 @@ mod 'richardc/datacat', '0.6.2'
 mod 'puppetlabs/postgresql', '6.2.0'
 mod 'puppetlabs/firewall', '1.7.1'
 # PuppetDB
-mod 'puppetlabs/puppetdb', '7.4.0'
+mod 'puppetlabs/puppetdb', '7.1.0'
 mod 'puppetlabs/inifile', '2.0.0'
 # r10k
 # El r10k necesita el puppetlabs/git, pero nosotros tenemos el
diff --git a/hieradata/cluster_glis3.eyaml b/hieradata/cluster_glis3.eyaml
deleted file mode 100644
index 34e91e4c4..000000000
--- a/hieradata/cluster_glis3.eyaml
+++ /dev/null
@@ -1,3 +0,0 @@
----
-
-puppetdb::globals::version: "6.6.0-1%{facts.os.distro.codename}"
diff --git a/manifests/profile/manifests/puppetdb/server.pp b/manifests/profile/manifests/puppetdb/server.pp
index 6ce6fa23e..425d04c8f 100644
--- a/manifests/profile/manifests/puppetdb/server.pp
+++ b/manifests/profile/manifests/puppetdb/server.pp
@@ -81,8 +81,7 @@ class profile::puppetdb::server (
   #
   # Añado nuestros usuarios al grupo puppet
   User<| gid == 'telematadm' |> {
-    groups  +> $puppetdb::server::puppetdb_group,
-    require +> Class['::puppetdb::server'],
+    groups +> $puppetdb::server::puppetdb_group
   }

   #
```
---

## Fundamentos de Git
### Consultar modificaciones de una confirmación

```
$ git diff 771b5cdb5b71f13a94463b042479f705299a69f8~ 771b5cdb5b71f13a94463b042479f705299a69f8
diff --git a/manifests/profile/manifests/puppetdb/server.pp b/manifests/profile/manifests/puppetdb/server.pp
index 425d04c8f..6ce6fa23e 100644
--- a/manifests/profile/manifests/puppetdb/server.pp
+++ b/manifests/profile/manifests/puppetdb/server.pp
@@ -81,7 +81,8 @@ class profile::puppetdb::server (
   #
   # Añado nuestros usuarios al grupo puppet
   User<| gid == 'telematadm' |> {
-    groups +> $puppetdb::server::puppetdb_group
+    groups  +> $puppetdb::server::puppetdb_group,
+    require +> Class['::puppetdb::server'],
   }

   #
```
???
- `~`: Indica el siguiente commit al indicado
---

## Fundamentos de Git
### Consultar modificaciones de una confirmación

```
$ git show 771b5cdb5b71f13a94463b042479f705299a69f8
commit 771b5cdb5b71f13a94463b042479f705299a69f8
Author: Ángel L. Mateo <amateo@um.es>
Date:   Wed Sep 25 12:08:49 2019 +0200

    TLM-8391: Corrige usuarios en profile::puppetdb::server

    Para que el añadir los usuarios al grupo `puppetdb` se haga una vez que
    ya se ha instalado el `puppetdb` y no de errores de que no existe el
    grupo.

diff --git a/manifests/profile/manifests/puppetdb/server.pp b/manifests/profile/manifests/puppetdb/server.pp
index 425d04c8f..6ce6fa23e 100644
--- a/manifests/profile/manifests/puppetdb/server.pp
+++ b/manifests/profile/manifests/puppetdb/server.pp
@@ -81,7 +81,8 @@ class profile::puppetdb::server (
   #
   # Añado nuestros usuarios al grupo puppet
   User<| gid == 'telematadm' |> {
-    groups +> $puppetdb::server::puppetdb_group
+    groups  +> $puppetdb::server::puppetdb_group,
+    require +> Class['::puppetdb::server'],
   }

   #
```
???
- `~`: Indica el siguiente commit al indicado
---

## Fundamentos de Git
### Rectificar confirmación

```
.../test$ echo "Fichero 1" > fichero_1.txt
.../test$ echo "Fichero 2" > fichero_2.txt
.../test$ git status
En la rama master

No hay commits todavía

Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que se será confirmado)

	fichero_1.txt
	fichero_2.txt

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
.../test$ git add fichero_1.txt
.../test$ git commit -m "Commit inicial" fichero_1.txt
[master (commit-raíz) 9519d19] Commit inicial
 1 file changed, 1 insertion(+)
 create mode 100644 fichero_1.txt
.../test$ git status
En la rama master
Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que se será confirmado)

	fichero_2.txt
```
---

## Fundamentos de Git
### Rectificar confirmación

```
.../test$ git add fichero_2.txt
.../test$ git commit --amend
[master 8d89591] Commit inicial
 Date: Thu Oct 24 16:58:56 2019 +0200
 2 files changed, 2 insertions(+)
 create mode 100644 fichero_1.txt
 create mode 100644 fichero_2.txt
.../test$ git status
En la rama master
nada para hacer commit, el árbol de trabajo esta limpio
```

```
.../test$ git log
commit 8d895918611510e71d7743313cd8241221bc9f80 (HEAD -> master)
Author: Ángel L. Mateo <amateo@um.es>
Date:   Thu Oct 24 16:58:56 2019 +0200

    Commit inicial
```
---

## Fundamentos de Git
### Deshacer un archivo preparado

```
.../test$ touch fichero_3.txt
.../test$ git add fichero_3.txt
.../test$ git status
En la rama master
Cambios a ser confirmados:
  (usa "git reset HEAD <archivo>..." para sacar del área de stage)

	nuevo archivo:  fichero_3.txt
```

```
.../test$ git reset HEAD fichero_3.txt
.../test$ git status
En la rama master
Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que se será confirmado)

	fichero_3.txt

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
```
---

## Fundamentos de Git
### Deshacer un archivo modificado

```
.../test$ echo "Modificacion" > fichero_1.txt
.../test$ git status
En la rama master
Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git checkout -- <archivo>..." para descartar los cambios en el directorio de trabajo)

	modificado:     fichero_1.txt

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
.../test$ cat fichero_1.txt
Modificacion
```

```
.../test$ git checkout -- fichero_1.txt
.../test$ git status
En la rama master
nada para hacer commit, el árbol de trabajo esta limpio
.../test$ cat fichero_1.txt
Fichero 1
```
---

## Fundamentos de Git
### Trabajar con remotos

```
$ git clone https://github.com/schacon/ticgit
Cloning into 'ticgit'...
remote: Reusing existing pack: 1857, done.
remote: Total 1857 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (1857/1857), 374.35 KiB | 268.00 KiB/s, done.
Resolving deltas: 100% (772/772), done.
Checking connectivity... done.
$ cd ticgit
$ git remote
origin
```

```
$ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
```
---

## Fundamentos de Git
### Trabajar con remotos

```
amateo@amateo-EXCALIBUR:~/puppetcode/puppet-freeradius$ git remote -v
origin	https://github.com/amateo/puppet-freeradius.git (fetch)
origin	https://github.com/amateo/puppet-freeradius.git (push)
upstream	https://github.com/djjudas21/puppet-freeradius (fetch)
upstream	https://github.com/djjudas21/puppet-freeradius (push)
```
???
- Podemos traer o llevar cambios de/a cualquiera de estos repositorios (siempre que tengamos permisos, claro)
- Los distintos remotos pueden utilizar incluso distintos protocolos
---

## Fundamentos de Git
### Trabajar con remotos

```
amateo@amateo-EXCALIBUR:~/puppetcode/puppet-freeradius$ git fetch upstream
remote: Enumerating objects: 175, done.
remote: Counting objects: 100% (175/175), done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 320 (delta 154), reused 174 (delta 153), pack-reused 145
Recibiendo objetos: 100% (320/320), 82.10 KiB | 518.00 KiB/s, listo.
Resolviendo deltas: 100% (207/207), completado con 41 objetos locales.
Desde https://github.com/djjudas21/puppet-freeradius
   f0d2075..e083b91  master     -> upstream/master
 * [nueva rama]      travis     -> upstream/travis
 * [nuevo tag]       3.7.0      -> 3.7.0
 * [nuevo tag]       3.8.0      -> 3.8.0
 * [nuevo tag]       3.8.1      -> 3.8.1
 * [nuevo tag]       3.8.2      -> 3.8.2
```
---

## Fundamentos de Git
### Añadir repositorios remotos

```
amateo@amateo-EXCALIBUR:.../ticgit$ git remote
origin
amateo@amateo-EXCALIBUR:.../ticgit$ git remote add pb https://github.com/paulboone/ticgit
amateo@amateo-EXCALIBUR:.../ticgit$ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
pb	https://github.com/paulboone/ticgit (fetch)
pb	https://github.com/paulboone/ticgit (push)
```
---

## Fundamentos de Git
### Traer y combinar remotos

```
$ git fetch [remote-name]
```

???
- Se trate todos los cambios que todavía no tenemos de dicho remoto
- Tendrá todas las referencias a todas las ramas en el remoto
- Si no se indica `remote-name` se utiliza `origin`
- Trae los datos al repositorio local, pero no los actualiza en la copia de trabajo
---

## Fundamentos de Git
### Traer y combinar remotos

```
$ git pull [remote-name] [branch-name]
```

```
amateo@amateo-EXCALIBUR:main $ git status
En la rama production
Tu rama está detrás de 'origin/production' por 14 commits, y puede ser avanzada rápido.
  (usa "git pull" para actualizar tu rama local)

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)

amateo@amateo-EXCALIBUR:main $ git pull
remote: Counting objects: 52, done.
remote: Compressing objects: 100% (37/37), done.
remote: Total 52 (delta 35), reused 29 (delta 15)
Desempaquetando objetos: 100% (52/52), listo.
Desde gitlab.atica.um.es:puppet-telematica/main
   8897239d1..6644023fb  production              -> origin/production
   df94f36b8..8b11f9fdc  CAS6                    -> origin/CAS6
 * [nueva rama]          TLM-8632-monitorizacion -> origin/TLM-8632-monitorizacion
 + 1bd8472c5...459d8940c TLM-8966                -> origin/TLM-8966  (actualización forzada)
Actualizando d3ae9bd30..6644023fb
Fast-forward
 Puppetfile                                                     |   4 +-
 hieradata/cluster_araneus.eyaml                                |   4 ++
 hieradata/cluster_dns.eyaml                                    |   2 +
 ...
 14 files changed, 261 insertions(+), 15 deletions(-)
La rama actual production está actualizada.
```

???
- Por defecto, la rama establecida para seguimiento
- Si no, por defecto, el remote `origin` y la rama con el mismo nombre que la rama local actual.
---

## Fundamentos de Git
### Enviar a tus remotos

```
$ git push [remote-name] [ref]
```

```
$ git push origin master
```
???
- Hay que tener permiso en `origin`
- Busca la referencia `master` en el repositorio local y la envía `origin` con el mismo nombre `master`.
---

## Fundamentos de Git
### Eliminar y renombrar remotos

```
amateo@amateo-EXCALIBUR:ticgit $ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
pb	https://github.com/paulboone/ticgit (fetch)
pb	https://github.com/paulboone/ticgit (push)
amateo@amateo-EXCALIBUR:ticgit $ git remote rename pb paul
amateo@amateo-EXCALIBUR:ticgit $ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
paul	https://github.com/paulboone/ticgit (fetch)
```

```
amateo@amateo-EXCALIBUR:ticgit $ git remote remove paul
amateo@amateo-EXCALIBUR:ticgit $ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
```

---

## Ramas
### ¿Qué es una rama?

![Rama y su historial de confirmaciones](img/branch-and-history.png)

???
- Continuar el trabajo a partir de otro, en paralelo
- Uno de los puntos fuertes de Git
- Rama es un apuntador móvil apuntando a las confirmaciones
- En cada confirmación, la rama va avanzando automáticamente

---

## Ramas
### Crear una rama

```
git branch testing
```

![Dos ramas apuntando al mismo historial](img/two-branches.png)

---

## Ramas
### HEAD

![Apuntador HEAD en master](img/head-to-master.png)

???
- Apuntador especial que indica en qué punto nos encontramos
---

## Ramas
### Cambiar de rama

```
$ git checkout testing
$ git checkout -b testing
```

![Apuntador HEAD apuntando a rama actual](img/head-to-testing.png)

---

## Ramas
### Cambiar de rama

```
$ echo "test" >> test.rb
$ git commit -a -m "cambio de prueba"
```

![](img/advance-testing.png)

???
- Se observa cómo ha avanzado el puntero de la rama `testing`, pero no el de la rama `master`
---

## Ramas
### Cambiar de rama

```
$ git checkout master
```

![](img/checkout-master.png)

???
- Mueve el apuntador HEAD a la rama master
- Actualiza el directorio de trabajo
---

## Ramas
### Cambiar de rama
```
$ echo "otro cambio" >> test.rb
$ git commit -a -m "otro cambio"
```

![](img/advance-master.png)

???
- Dado que una rama no es más que un apuntador, no cuesta nada crear y destruir ramas.
- Deberíamos utilizar ramas frecuentemente, siempre.

---

## Ramas
### Ramificar y Fusionar

1. Trabajas en un sitio/aplicación web.
2. Creas una rama para una incidencia/funcionalidad sobre la que trabajar.
```
git checkout -b new_feature
```
3. Realizas el trabajo (pruebas, etc.)

```
amateo@amateo-EXCALIBUR:test $ echo "Índice" > index.html
amateo@amateo-EXCALIBUR:test $ git add index.html && git commit -m "Crea página índex"
[new_feature 2299cd7] Crea página índex
 1 file changed, 1 insertion(+)
 create mode 100644 index.html

amateo@amateo-EXCALIBUR:test $ git log
commit 2299cd7f6f107141a5779caa45cf56277b071526 (HEAD -> new_feature)
Author: Ángel L. Mateo <amateo@um.es>
Date:   Mon Oct 28 16:39:30 2019 +0100

    Crea página índex

commit 8d895918611510e71d7743313cd8241221bc9f80 (master)
Author: Ángel L. Mateo <amateo@um.es>
Date:   Thu Oct 24 16:58:56 2019 +0200

    Commit inicial
```

---

## Ramas
### Ramificar y Fusionar
4. Fusionas el trabajo (merge)

```
amateo@amateo-EXCALIBUR:test $ git checkout master 
Cambiado a rama 'master'


amateo@amateo-EXCALIBUR:test $ git merge new_feature
Actualizando 8d89591..2299cd7
Fast-forward
 index.html | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 index.html


amateo@amateo-EXCALIBUR:test $ git log
commit 2299cd7f6f107141a5779caa45cf56277b071526 (HEAD -> master, new_feature)
Author: Ángel L. Mateo <amateo@um.es>
Date:   Mon Oct 28 16:39:30 2019 +0100

    Crea página índex

commit 8d895918611510e71d7743313cd8241221bc9f80
Author: Ángel L. Mateo <amateo@um.es>
Date:   Thu Oct 24 16:58:56 2019 +0200

    Commit inicial
```

???
- `Fast-forward`: Git ha movido el apuntador hacia adelante, ya que la confirmación apuntda en la rama estaba directamente encima.
---

## Ramas
### Ramificar y Fusionar

1. Trabajas en un sitio/aplicación web.
2. Creas una rama para una incidencia/funcionalidad `iss1`
3. Realizas trabajo en `iss1`
4. Creas una rama para otra incidencia/funcionalidad `iss2`
5. Realizas trabajo en `iss2`
6. Fusionas el trabajo de `iss1`
7. Fusionas el trabajo de `iss2`
8. Limpias ramas de trabajo `iss1` e `iss2`
---

## Ramas
### Ramificar y Fusionar

1. Trabajas en un sitio/aplicación web.
2. Creas una rama para una incidencia/funcionalidad `iss1`
3. Realizas trabajo en `iss1`

```
amateo@amateo-EXCALIBUR:test2 $ git checkout -b iss1
Cambiado a nueva rama 'iss1'


amateo@amateo-EXCALIBUR:test2 $ echo "fichero 3" > fichero_3.txt && git add fichero_3.txt && git commit -m 'Crea fichero 3'
[iss1 f6c8a5c] Crea fichero 3
 1 file changed, 1 insertion(+)
 create mode 100644 fichero_3.txt

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
f6c8a5c (HEAD -> iss1) Crea fichero 3
2299cd7 (master, iss2) Crea página índex
8d89591 Commit inicial
```

---

## Ramas
### Ramificar y Fusionar

<ol start="4">
<li>Creas una rama para otra incidencia/funcionalidad `iss2`</li>
<li>Realizas trabajo en `iss2`</li>
</ol>

```
amateo@amateo-EXCALIBUR:test2 $ git checkout master
Cambiado a rama 'master'

amateo@amateo-EXCALIBUR:test2 $ git checkout -b iss2
Cambiado a nueva rama 'iss2'

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
2299cd7 (HEAD -> iss2, master) Crea página índex 
8d89591 Commit inicial

amateo@amateo-EXCALIBUR:test2 $ echo "fichero 4" > fichero_4.txt && git add fichero_4.txt && git commit -m 'Crea fichero 4' 
[iss2 6ae6335] Crea fichero 4
 1 file changed, 1 insertion(+)
 create mode 100644 fichero_4.txt

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
6ae6335 (HEAD -> iss2) Crea fichero 4
2299cd7 (master) Crea página índex
8d89591 Commit inicial
```

---

## Ramas
### Ramificar y Fusionar

<ol start="6">
<li>Fusionas el trabajo de `iss1`</li>
</ol>

```
amateo@amateo-EXCALIBUR:test2 $ git checkout master 
Cambiado a rama 'master'


amateo@amateo-EXCALIBUR:test2 $ git merge iss1
Actualizando 2299cd7..f6c8a5c
Fast-forward
 fichero_3.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 fichero_3.txt


amateo@amateo-EXCALIBUR:test2 $ git log --oneline
f6c8a5c (HEAD -> master, iss1) Crea fichero 3
2299cd7 Crea página índex
8d89591 Commit inicial
```

---

## Ramas
### Ramificar y Fusionar

<ol start="7">
<li>Fusionas el trabajo de `iss2`</li>
</ol>

```
amateo@amateo-EXCALIBUR:test2 $ git checkout iss2
Cambiado a rama 'iss2'

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
6ae6335 (HEAD -> iss2) Crea fichero 4
2299cd7 Crea página índex
8d89591 Commit inicial
```

???
- Resaltar que en este momento, ya no se ve el puntero `mater` en la historia de `iss2`

---

## Ramas
### Ramificar y Fusionar

<ol start="7">
<li>Fusionas el trabajo de `iss2`</li>
</ol>

```
amateo@amateo-EXCALIBUR:test2 $ git checkout master 
Cambiado a rama 'master'

amateo@amateo-EXCALIBUR:test2 $ git merge iss2
Merge made by the 'recursive' strategy.
 fichero_4.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 fichero_4.txt

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
943ea49 (HEAD -> master) Merge branch 'iss2'
6ae6335 (iss2) Crea fichero 4
f6c8a5c (iss1) Crea fichero 3
2299cd7 Crea página índex
8d89591 Commit inicial
```

???
- Se hace un `merge` la fusión ahora no es simplimente avanzar el puntero HEAD
---

## Ramas
### Ramificar y Fusionar

<ol start="8">
<li>Limpias ramas de trabajo `iss1` e `iss2`</li>
</ol>

```
amateo@amateo-EXCALIBUR:test2 $ git branch -d iss1
amateo@amateo-EXCALIBUR:test2 $ git branch -d iss2

amateo@amateo-EXCALIBUR:test2 $ git log --oneline
943ea49 (HEAD -> master) Merge branch 'iss2'
6ae6335 Crea fichero 4
f6c8a5c Crea fichero 3
2299cd7 Crea página índex
8d89591 Commit inicial
```

???
- Han desaparecido los punteros `iss1` e `iss2`.

---
## Ramas
### Gestión de ramas

```
amateo@amateo-EXCALIBUR:test2 $ git branch
  iss3
  iss4
* master

amateo@amateo-EXCALIBUR:test2 $ git branch -v
  iss3   13ab76e Crea fichero 5
  iss4   a1e85cb Crea fichero 6
* master 13ab76e Crea fichero 5

amateo@amateo-EXCALIBUR:test2 $ git branch --merged
  iss3
* master

amateo@amateo-EXCALIBUR:test2 $ git branch -d iss4
error: La rama 'iss4' no ha sido fusionada completamente.
Si está seguro de querer borrarla, ejecute 'git branch -D iss4'.

```

???
- `git branch` tiene más funciones que crear y borrar ramas
- `*`: Indicar la rama activa
- Opciones `--merged` y `--no-merged` para mostrar solo las que no tienen (o si tienen) trabajos por fusionar.
- Opciones `-d` y `-D` para borrar

---
## Ramas
### Ramas de largo recorrido

![Ramificado progresivo](img/lr-branches-1.png)

---
## Ramas
### Ramas de largo recorrido
![Ramificado progresivo](img/lr-branches-1.png)

---
## Ramas
### Ramas de largo recorrido
![Ramificado progresivo](img/lr-branches-2.png)

???
- Fusionar varias una rama a otra varias veces
- Tener ramas siempre abiertas: `master` (producción), `develop` (desarrollo/pruebas) y `features`

---
## Ramas
### Ramas remotas

- Referencias al estado de las ramas en los repositorios remotos
- No las puedes mover, se mueven automáticamente al actualizar por la red
- Indican el estado en que se encontraba el repositorio la última vez que conectaste con él
- `<remote>/<rama>`

```
amateo@amateo-EXCALIBUR:curso $ git branch -av
* inicio                977095d Sigo avanzando
  remotes/origin/inicio e909bf4 Versión inicial
  remotes/origin/master 85b56f4 Versión inicial
```

---
## Ramas
### Ramas remotas
![](img/remote-branches-1.png)

---
## Ramas
### Ramas remotas
![](img/remote-branches-2.png)
???
- Alguien hace trabajo y lo sincroniza con el remoto (`190a3`)
- Tú realizas trabajo en tu copia local (`893cf`)
---
## Ramas
### Ramas remotas
![](img/remote-branches-3.png)

???
- Sincronizas tu copia con el remoto mediante `get fetch`
- Se crea una ramifición para indicar la distinta evolución

---
## Ramas
### Publicar

```
$ git push origin serverfix
Counting objects: 24, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (24/24), 1.91 KiB | 0 bytes/s, done.
Total 24 (delta 2), reused 0 (delta 0)
To https://github.com/schacon/simplegit
 * [new branch]      serverfix -> serverfix
```

- `serverfix` es un atajo: `refs/heads/serverfix:refs/heads/serverfix`
- Coge mi rama `serverfix` y actualiza con ella la rama `serverfix` del remoto

---
## Ramas
### Publicar

```
amateo@amateo-EXCALIBUR:curso $ git push origin inicio:inicio2
Contando objetos: 3, listo.
Delta compression using up to 4 threads.
Comprimiendo objetos: 100% (3/3), listo.
Escribiendo objetos: 100% (3/3), 1.89 KiB | 1.89 MiB/s, listo.
Total 3 (delta 1), reused 0 (delta 0)
To gitlab.atica.um.es:amateo.um.es/curso-intro-git.git
 * [new branch]      inicio -> inicio2
```

---
## Ramas
### Hacer seguimiento a las ramas

- Ramas locales que se relacionan directamente con una rama remota.

```
amateo@amateo-EXCALIBUR:curso $ git branch -av
* inicio                 977095d Sigo avanzando
  remotes/origin/inicio  e909bf4 Versión inicial
  remotes/origin/inicio2 977095d Sigo avanzando
  remotes/origin/master  85b56f4 Versión inicial
```
---
## Ramas
### Hacer seguimiento a las ramas

```
amateo@amateo-EXCALIBUR:curso $ git checkout --track origin/inicio2
Rama 'inicio2' configurada para hacer seguimiento a la rama remota 'inicio2' de 'origin'.
Cambiado a nueva rama 'inicio2'


amateo@amateo-EXCALIBUR:curso $ git checkout -b inicio3 origin/inicio2
Rama 'inicio3' configurada para hacer seguimiento a la rama remota 'inicio2' de 'origin'.
Cambiado a nueva rama 'inicio3'

amateo@amateo-EXCALIBUR:curso $ git branch -vv
  inicio  977095d Sigo avanzando
  inicio2 977095d [origin/inicio2] Sigo avanzando
* inicio3 977095d [origin/inicio2] Sigo avanzando
```
---
## Ramas
### Hacer seguimiento a las ramas

```
amateo@amateo-EXCALIBUR:curso $ git branch --set-upstream-to=origin/inicio
Rama 'inicio' configurada para hacer seguimiento a la rama remota 'inicio' de 'origin'.

amateo@amateo-EXCALIBUR:curso $ git status
En la rama inicio
Tu rama está adelantada a 'origin/inicio' por 1 commit.
  (usa "git push" para publicar tus commits locales)
```
---
## Ramas
### Traer y fusionar

```
amateo@amateo-EXCALIBUR:curso $ git pull
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0)
Desempaquetando objetos: 100% (3/3), listo.
Desde gitlab.atica.um.es:amateo.um.es/curso-intro-git
   977095d..070b889  inicio     -> origin/inicio
Actualizando 977095d..070b889
Fast-forward
 curso_git_ticarum.md | 141 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
 1 file changed, 139 insertions(+), 2 deletions(-)
```
- Equivalente a `git fetch` más `git merge`

---
## Ramas
### Eliminar ramas remotas

```
amateo@amateo-EXCALIBUR:curso $ git branch -vv
* inicio  070b889 [origin/inicio] mas commits
  inicio2 977095d [origin/inicio2] Sigo avanzando
  inicio3 977095d [origin/inicio2] Sigo avanzando

amateo@amateo-EXCALIBUR:curso $ git push origin --delete inicio2
To gitlab.atica.um.es:amateo.um.es/curso-intro-git.git
 - [deleted]         inicio2

amateo@amateo-EXCALIBUR:curso $ git branch -vv
* inicio  070b889 [origin/inicio] mas commits
  inicio2 977095d [origin/inicio2: desaparecido] Sigo avanzando
  inicio3 977095d [origin/inicio2: desaparecido] Sigo avanzando
```

