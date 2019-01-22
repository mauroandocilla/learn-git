# ¿Qué es Git?

Es un sistema de control de versiones distribuido.

## ¿Qué es un sistema de control de versiones?

Es un sistema que permite registrar cada cambio que se realiza a un archivo o archivos a lo largo del tiempo.

## Tipos de sistemas de control de versiones

-   Local: solo se encuentra en la computadora donde se trabaja.
-   Centralizado: no depende unicamente de un computador donde se trabaja y donde se hacen los cambios, sino depende de un servidor donde se almacena el repositorio, aqui se encuentran estos cambio y se distribuyen hacia los demas computadores.
-   Distribuido: cada uno de los que participan en el proyecto, tienen copia del proyecto que se realiza, por eso no dependemos de un solo computador que almacene toda la información.

## Git ¿Qué beneficios tiene?

-   Velocidad: Puedes trabajar fluidamente desde tu computador
-   Diseño sencillo: El codigo es robusto con las herramientas necesarias, como viajar en el tiempo
-   Fuerte apoyo en el desarrollo no lineal: No trabaja de manera lineal, la linea del tiempo tiene bifurcaciones de manera independiente al proyecto principal
-   Completamente distribuido: Cada quien puede tener una copia del proyecto.
-   Capaz de manejar grandes proyectos; Linux, Django, Laravel, etc. usan git.

Git almacena referencias a los archivos que no se han cambiado.
Cualquier trabajo es local, puedes trabajar en cualquier parte incluso sin internet.

## Estados de Git

-   Working Directory: Es donde trabajamos de manera local, pero para guardarlo hay que pasarlo al Staging Area
-   Staging Area: Es el área de preparación, se almacenan justo antes de hacer commit
-   Git Repository: El repositorio donde almacenaremos los cambios del proyecto

## Instalación

Linux:

```sh
sudo apt-get install git
```

macOs

http://git-scm.com/download/mac

windows

https://git-scm.com/download/win

## Configuraciones básicas

```sh
git config --global user.email xyz@mail.com
git config --global user.mauro "Nombre Apellido"
git config --global color.ui true
git config --list
```

## Git comandos

### Iniciar un repositorio

**git init** crea un repositorio de manera local y lo hará en la carpeta donde estamos posicionados o se le puede pasar [nombre_de_la_carpeta] y creará la carpeta con ese nombre.

```sh
git init
git init nombre_carpeta
```

Para borrar un repositorio, vamos a usar el comando rm -rf .git.

```sh
rm -rf .git
```

### git add | rm | status (Agregando, quitando y observando estados de los archivos)

-   **git add -A** Agrega todos los archivos del Working Directory al Staging Area.
-   **git add [file/directory]** Agrega un archivo o carpeta del Working Directory al Staging Area.
-   **git add -n [file/directory]** Simula el agregado de un archivo o directorio al Staging Area pero la verdad no lo hace.
-   **git rm --cached [file/directory]** Elimina un archivo o carpeta del Staging Area y lo deja en el Working Directory.
-   **git rm --f [file/directory]** Fuerza la eliminación de un archivo o carpeta del Staging Area tanto así que hasta lo borra del Working Directory.
-   **git status** Muestra el estado de los archivos o directorios.
-   **git status -s** Muestra el estado de los archivos o directorios -s formato corto.
-   **git status -b** Mostrar la información de la rama y el seguimiento, incluso en formato corto..

Los archivos que salen en rojo: Se encuentran en el Working Directory.
Los archivos que salen en verde: Se encuentran en el Staging Area.

```sh
touch index.html
git status
git add index.html
git rm --cached index.html
```

### git commit (Confirmando cambios)

-   **git commit -m ["message"]**: Es bueno ser descriptivos con el mensaje para saber lo que se hizo en ese commit y para informar al resto de personas.
-   **git commit –-amend**: concatena nuevos cambios con cambios previos.
-   **git log**: nos muestra la historia de todos los commits que hemos realizados.

```sh
git commit -m "mensaje"
git commit –-amend
git log
```

### git tag (Etiquetando confirmaciones)

Como muchos VCSs, Git tiene la habilidad de etiquetar (tag) puntos específicos en la historia como importantes. Generalmente la gente usa esta funcionalidad para marcar puntos donde se ha lanzado alguna versión (v1.0, y así sucesivamente). En esta sección aprenderás cómo listar las etiquetas disponibles, crear nuevas etiquetas y qué tipos diferentes de etiquetas hay.

-   **git tag -a [version] -m ["message"]** Registra un tag, Crea una etiqueta anotada
-   **git tag -l** Lista los tags existentes.
-   **git tag [version]&ensp;[commit_hash]** Le registra un tag a un Commit en especifico por medio de su HASH.
-   **git tag -f -a [version] -m ["message"]&ensp;[commit_hash]** Permite renombrar un tag.
-   **git tag -d [version]** Elimina un tag.
-   **git tag -n** Para ver la lista de tag y los mensajes asociados.

Descripcion de opciones:

-   **-a** anotación
-   **-m** mensaje
-   **-l** lista de etiquetas
-   **-f** renombrar
-   **-d** borrar

```sh
git tag -a 0.5 -m 'mensaje'
git tag -a v1.4 -m 'my version 1.4'
git tag -l
git tag -f -a 0.1 -m 'iniciando el proyecto' 5d9c9227cda4b11983fe08139ad7fd9a84b61596
```

### git log (Historia proyecto)

-   **git log** nos muestra la historia de todos los commits que hemos realizados.
-   **git log --oneline** muestra el id commit y el título del commit.
-   **git log --decorate** muestra donde se encuentra el head point en el log.
-   **git log --stat** Explica el número de líneas que se cambiaron brevemente.
-   **git log -p** Explica el número de líneas que se cambiaron y te muestra que se cambió en el contenido.
-   **git shortlog** Indica que commits ha realizado un usuario, mostrando el usuario y el titulo de sus commits.
-   **git log --graph --oneline --decorate** y
-   **git log --pretty=format:"%cn** hizo un commit %h el dia %cd" - Muestra mensajes personalizados de los commits.
-   **git log -3** Limitamos el número de commits.
-   **git log --after="2018-1-2"**,
-   **git log --after="today"** y
-   **git log --after="2018-1-2" --before="today"** Commits para localizar por fechas.
-   **git log --author="Name Author"** Commits realizados por autor que cumplan exactamente con el nombre.
-   **git log --grep="text"** Busca los commits que cumplan tal cual está escrito entre las comillas.
-   **git log --grep="text" –i** Busca los commits que cumplan sin importar mayúsculas o minúsculas.
-   **git log – [file]** Busca los commits en un archivo en específico.
-   **git log -S "text"** Buscar los commits con el contenido dentro del archivo.

### git diff (Revisando los cambios entre versiones)

-   **git diff [commit_hash]** Muestra las diferencias del commit [commit_hash] contra el ultimo commit de la rama en la que actualmente estamos (generalmente master)
-   **git diff [commit_hash_1]&ensp;[commit_hash_2]** Muestra las diferencias del commit [commit_hash_1] contra el commit [commit_hash_2]

### git reset

-   **git reset --soft [commit_hash]** elimina un commit pero no los archivos del commit, en lugar de ello los deja en el staging area, listos para hacer un nuevo commit.
-   **git reset --mixed [commit_hash]** Posiciona en el sha del commit indicado y elimina todos los commits que están por delante del actual. No mantiene los cambios en "stage", los mismos estarán en "working directory". Esto es útil para corregir algún error cometido en los archivos a enviar a "stage".
-   **git reset --hard [commit_hash]** Si realizamos git reset --hard elimina del Working Directory los archivos que estén en Staging área (lo que se encuentra en el HEAD). Si realizamos git reset --hard y no tenemos nada en el Staging área, podemos tener archivos recientes que están en untracked files no va a eliminar nada del Working Directory, regresa hasta el commit del [commit_hash], si escoges el [commit_hash] del primer commit realizado, se eliminaran los demás commits. Puedes recuperar si te sabes el [commit_hash] de tu último commit, del mas reciente realizado, volverán todos los commits. Importante guardar los SHA de los commits en un archivo. Solo por si acaso..

### git branch (Múltiples variantes del repositorio)

Una rama es una línea alterna del tiempo (del proyecto). La rama por defecto es master, la rama de GitHub Pages es gh-pages y cuando se trabaja como colaborador se identifica el proyecto principal con la rama upstream.

-   **git branch [branch]** Crea una nueva rama.
-   **git checkout -b [branch]** Crea una nueva rama y se posiciona en ella.
-   **git branch -l** Lista todos las ramas que existen.
-   **git branch -d [branch]** Elimina una rama. Con -D se fuerza el borrado.
-   **git branch -m [old_branch]&ensp;[new_branch]** Permite renombrar una nueva rama.

### git checkout (Moviéndonos entre ramas y versiones)

-   **git checkout [branch/commit_hash]** Permite moverse entre ramas o entre los Commits de una rama.
-   **git checkout -b [branch]** Crear una nueva rama con base a su ubicación actual (head) y luego se sitúa sobre ella.
-   **git checkout [file]** Descarta los cambios que se hayan hecho de un archivo en el Working Directory (o que hayan sido añadidos en el Staging Area) con base al último commit enviado.
-   **git checkout -- [file]** Desechar cambios en el directorio de trabajo.
-   **git checkout -f** Descarta todos los cambios que se hayan hecho en el Working Directory (o que hayan sido añadidos en el Staging Area) con base al último commit enviado.

**Nota Importante!** Si existen archivos modificados en el Working Directory o agregados en el Staging Area, estos cambios los mantendrá a pesar de que se cambie entre ramas. Para asegurar que los cambios que se están realizando se mantengan en esta rama es necesario realizar un git add y un git commit de los archivos modificados antes de cambiar a otra rama.

### git merge (Mezclando ramas y resolviendo conflictos)

-   **git merge [branch]** Fusiona una rama con la actual (con la rama en la que nos encontramos posicionados).

En Git se pueden mezclar ramas, al realizar una fusión ocurrirá que la operación se realizó con éxito (Fast-Forward) o que la operación presentó unos conflictos (Manual Merge).

**Fast-Forward** Es lo que ocurre cuando ocurre un cambio en una rama y al fusionarla con la otra no presenta conflictos ¿por qué no presenta problemas? Porque solo en una rama ocurrió un cambio en la misma línea de código por lo tanto se agrega la nueva y se reemplaza la vieja.
**recursive/auto-merging** ambas ramas salieron al mismo tiempo y hay algo nuevo en la rama que la otra no recuerda, por eso hace la mezcla recursiva.
**Manual Merge** Es lo que ocurre cuando en ambas ramas se realizaran modificaciones afectando las mismas líneas de código ¿que pasa con esto? Sencillo, Git te pedirá que elijas con cual fragmento de código (cambio) te quedarás y lo dividirá con unas flechas, por ejemplo:

```sh
<<<<< [Rama A]
[Aquí estará el código de la modificación número 1]
=====
[Aquí estará el código de la modificación número 2]
>>>>> [Rama B]
```

### git rebase (Reescribe la historia de tu proyecto)

-   **git rebase [branch]** hace prácticamente lo mismo que merge, cambiamos la historia de nuestro proyecto sin crear bifurcaciones del proyecto. Es mejor usar merge. Usar solo git rebase de manera local.

**git rebase -i [branch]**: de manera interactiva, nos abrira el editor que tengamos definido en la configuración de git.

### git stash (Guardando cambios temporalmente)

¿Qué tal si aún no estás listo para confirmar ningún cambio? Stash es un estado que tenemos como intermedio. Para esto debemos ir a alguna de nuestras ramas y usando el comando git stash que nos permite hacer cambios, pero no confirmarlos.

-   **git stash** Guarda el trabajo actual de manera temporal. (Archivos modificados o eliminados)
-   **git stash -u** Crea un stash con todos los archivos. (Añadiendo los creados Untracked)
-   **git stash list** Permite visualizar todos los stash existentes.
-   **git stash clear** Elimina todos los stash existentes.
-   **git stash show stash@{num_stash}** Muestra los archivos cambiados en ese stash.
-   **git stash show -p stash@{num_stash}** Muestra los archivos cambiados en ese stash en detalle.
-   **git stash drop stash@{num_stash}** Elimina un stash específico.
-   **git stash apply** Aplica el stash más reciente. El que tiene num_stash=0.
-   **git stash apply stash@{num_stash}** Aplica los cambios de un stash específico.

El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.

Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [file].

Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

### Cherry pick eligiendo commits selectivamente

Si estás trabajando en una rama, pero de repente notas que hiciste un cambio en la rama que no debías, para esto podemos usar cherry-pick. Este comando nos puede salvar la vida, ya que nos permite sacar cambios específicos de una rama y mezclarlos en otra.

-   **git cherry-pick [commit_hash]** mover el commit [commit_hash] de otro branch al branch actual.

## Repositorio remoto comandos (Github)

### git clone/fork (Clonando repositorios remotos)

Clonar un repositorio en un nuevo directorio
Un fork va a clonar el proyecto y nos va a crear un nuevo proyecto en el GitHub.

-   **git clone [route]** copia el repositorio al directorio actual
-   **fork** hace una copia de un repositorio externo a nuestra cuenta

### Añadiendo una llave ssh a GitHub

Si quieres mantener tu seguros dentro de GitHub es importante usar llaves ssh con el comando ssh-keygen -t rsa -b 4096 -C "xyz@mail.com".

-   **ssh-keygen -t rsa -b 4096 -C ["mail"]** crea una llave ssh. El correo debe de ser el mismo que se encuentra en Github

### git remote (Añadiendo un repositorio remoto a uno local)

Tenemos que crear una conexión entre tu repositorio local y tu repositorio remoto para que puedas compartirlo con la comunidad. Para esto vamos a usar un nuevo comando que en este caso es git remote. Por convención lo nombramos "origin". Para borrarlo podemos usar git remote remove y el nombre del repositorio.

-   **git remote add [repository]&ensp;[route]** conecta un repositorio remoto con uno local. Por defecto el nombre es origin
-   **git remote -v** lista las conexiones remota
-   **git remote remove [repository]** remueve una conexión remota

```sh
git remote add origin git@github.com
git remote -v
git remote origin
```

### git pull/fetch (Descargando cambios desde un repositorio remoto)

Vamos a compartir nuestro código con el repositorio remoto. Antes de poder enviar cambios tengo que tener los mismos cambios en el repositorio remoto que en el repositorio local. Para traer los cambios del repositorios remoto vamos a usar el comando git fetch. Este comando recibe dos parámetros 1. desde donde y hacia donde van. Luego de traer los cambios, debemos mezclarlos con la rama que estamos usando en local. Para esto usamos git merge.

-   **git fetch [repository]&ensp;[branch]** Descargar objetos y referencias de otro repositorio.
-   **git merge [repository/branch] --allow-unrelated-histories** hace un merge del fetch con el repositorio local.
-   **git pull [repository]&ensp;[branch]** hace un fetch y merge en un solo paso, obtener e integrar con otro repositorio o una rama local

```sh
git fetch origin master
git merge origin/master --allow-unrelated-histories
git pull origin master
```

### git push (Enviando cambios al repositorio remoto)

Sube los cambios hechos en tu ambiente de trabajo a una rama de trabajo tuya y/o de tu equipo remota.

-   **git push [repository]&ensp;[branch]** envia de la rama local actual al repositorio rama remoto.
-   **git push [repository]&ensp;[branch] --tags** envia de la rama local actual al repositorio rama remoto, mas todos los tags creados en la rama local actual.
-   **git push --all [repository]** push a todos los branch y tags

```sh
git push origin master
git push origin master --tags
git push origin otra_rama
```
