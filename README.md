<img
  src="https://git-scm.com/images/logos/logomark-orange@2x.png"
  width="50"
  align="left"
/>

# Git - Guía de comandos 
>Git es un sistema de control de versiones open source, que te ayudará a gestionar cualquier proyecto que tengas en mente desde la terminal de comandos. Para descargar e instalar Git visita el [sitio oficial](https://git-scm.com/download/).

### `$ git config`
Configura tu usuario con tu nombre y correo.
```sh
# ejecutar solo una vez.
$ git config --global user.name "your name"
$ git config --global user.email "your email"
```
------
### `$ git init`
Inicia un repositorio local dentro de un "directorio de trabajo" (carpeta) previamente creado en tu ordenador.
```sh
$ git init
```
------
### `$ git remote`
Conecta un repositorio local a un repositorio remoto.
```sh
$ git remote add origin username@host:/path/to/repository
```
------
### `$ git clone`

Si no has iniciado un repositorio local, puedes clonar un repositorio remoto directamente en tu ordenador.
```sh
$ git clone username@host:/path/to/repository
```
------
### `$ git add`
Añade los archivos modificados.
```sh
# añade todos los archivos del "directorio de trabajo".
$ git add --all

# añade un archivo específico.
$ git add <file_name>

# añade únicamente los archivos de un sub-carpeta del "directorio de trabajo".
$ git add .

# Elige ('Y' o 'N') para los cambios que se quieran añadir.
$ git add -p
```
------
### `$ git commit`
Después de añadir los cambios el siguiente paso ejecutar un 'commit' con un mensaje descriptivo.
```sh
$ git commit -m "Commit message"
```
------
### `$ git push`
Finalmente al ejecutar 'push' se enviarán los cambios al repositorio remoto.
```sh
# envía todos los cambios al repositorio remoto.
$ git push --all

# envía los cambios una rama del repositorio remoto.
$ git push origin <branch_name>
```
------
### `$ git branch` & `$ git checkout`
Las ramas son utilizadas para desarrollar funcionalidades aisladas y/o paralelas.
```sh
# muestra todas las ramas locales.
$ git branch

# muestra todas las ramas remotas.
$ git branch -r

# muestra todas las ramas locales y remotas.
$ git branch -a

# muestra todas las ramas locales y remotas que han sido fusionadas.
$ git branch -a --merged

# muestra todas las ramas locales y remotas que no han sido fusionadas.
$ git branch -a --no-merged

# elimina una rama.
$ git branch -d <branch_name>

# elimina una rama remota.
$ git branch -rd origin/<branch_name>
$ git push origin --delete <branch_name>

# moverse entre las ramas.
$ git checkout <branch_name>

# crea una nueva rama.
$ git checkout -b <new_branch>

# copia la rama en local.
$ git checkout -b <test-branch> origin/<test-branch>

# descarta los cambios no confirmados con el último contenido de "HEAD"
$ git checkout -- <file_name>

# una rama nueva no estará disponible para otros usuarios a menos que la subas al repositorio remoto.
$ git push origin <branch_name>
```
------
### `$ git pull`
Actualiza el repositorio local con cambios que tiene el repositorio remoto.
```sh
$ git pull origin master
```
------
### `$ git merge`
Fusiona otra rama a tu rama activa. Git intentará fusionar automáticamente los cambios.
```sh
# 1ro. Debes moverte a la rama que absorberá la fusión (esta será la rama activa).
$ git checkout origin/master

# 2do. Con "$ git merge" fucionas otra rama con la rama activa.
$ git merge <other_branch_name>

# si te equivocas al fusionar ramas que no querías, puedes cancelar la fusión.
$ git merge --abort

# no siempre será posible que Git fusione automáticamente todos los cambios causando conflictos. Eres responsable de fusionar esos conflictos manualmente al editar los archivos mostrados por Git. Después de modificarlos, necesitas añadirlos como fusionados con:
$ git add <file_name>

# antes de fusionar los cambios, revisarlos.
$ git diff <source_branch> <target_branch>
```
------
### `$ git diff`
```sh
# ver todos los cambios (non-staged) realizados en un repositorio local.
$ git diff

# ver todos los cambios (staged) realizados en un repositorio local.
$ git diff --cached

# comprueba los cambios entre el "directorio de trabajo" y los commit's el repositorio remoto.
$ git diff --stat origin/master
```
------
### `$ git tag`
Es recomendable crear un tag para cada nueva versión publicada.
```sh
$ git tag 1.0.0 <code_sha_commit>
```
------
### `$ git log`
```sh
# muestra la lista de todos los commits.
$ git log

# muestra la lista de los commit de manera gráfica.
$ git log --graph --oneline --decorate --all

# muestra más detalles de un commit en específico.
$ git cat-file <code_sha_commit> -p
```
------
### `$ git fetch` & `$ git reset`
```sh
# busca las ramas remotas.
$ git fetch <branch_name>

# restablece la versión del commit más reciente.
$ git reset HEAD -- filename

# restablece la versión anterior al commit más reciente.
$ git reset HEAD^ -- filename

# restablece todos los cambios en el "directorio de trabajo".
$ git reset --hard

# mover el "HEAD" a un commit específico.
$ git reset --hard <code_sha_commit>
```
