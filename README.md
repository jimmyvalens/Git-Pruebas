` Configuración de usuario `

- git config --global user.name "nombre apellido"
- git config --global user.email "correo@correo.com"


- git init

    Crea un repositorio local de Git.

- git add [nombre_archivo]

    Guarda los cambios hechos en el archivo indicado en el repositorio.

- git add .

    Guarda los cambios hechos en todos los archivos del proyecto.

- git commit -m "mensaje descriptivo"

    Crea un punto de control en el repositorio local.

- git log

    Muestra el historial de commits.

- git status

    Muestra el estado en el que se encuentran los ficheros del proyecto.

- git restore --staged [nombre_archivo]

    Saca un archivo del "stagin area" que se ha incluido previamente con "git add".

- git restore [nombre_archivo]

    Deshace los últimos cambios hechos en el archivo que se encuentra en el stagin area.
    
GITHUB

Para subir el repositorio local a Github: 

- Creamos el repositorio en Github
- Conectamos nuestro repositorio local con el repositorio creado en Github

    git remote add origin [url_del_repositorio_creado_en_Github]

- Subimos el repositorio local al repositorio de GitHub

    git push -u origin main

- Subir cambios a Github

    git add .
    git commit -m "mensaje"
    git push

- Clonar repositorio de Github

    Vamos a Github copiamos la url del repositorio a clonar
    Volvemos a nuestro sitema de archivos y nos ubicamos en la carpeta donde queremos clonar el repositorio
    git clone [url_del_repositorio_de_Github_a_clonar] 

- Actualizar repositorio local con los cambios que se hayan hecho en el repositorio de Github, este paso será siempre el primero antes de trabajar en un repositorio de un equipo de trabajo

    git pull

- Branches (ramas)
  Una rama la podemos ver como una copia del directorio principal, en la cual podemos realizar cambios sin modificar el contenido del directorio principal (rama main), esto se hace para añadir nuevas funcionalidades al código, teniendo así una nueva versión sin sobreescribir la original. A su vez cada rama puede dar lugar a la creación de nuevas ramas

    - Crear y moverse a una nueva rama

        git checkout -b(de branch) [nombre_de_la_nueva_rama] ó git switch -c(de change) [nombre_de_la_nueva_rama] (más moderno)

    - Ver todas las ramas y la rama en la que nos encontramos

        git branch

    - Moverse entre las ramas

        git checkout [nombre_de_la_rama] ó git switch [nombre_de_la_rama]

    - Volcar, fusionar o mergear el contenido de una rama con otra

        - Nos ubicamos en la rama a donde queremos traer los cambios
        - git merge [nombre_de_la_rama] (de donde traeremos los cambios)

- PULL REQUEST

Cuando trabajamos en equipo y nos han encomendado desarrollar alguna parte del código, es necesario que el equipo revise lo que hemos hecho antes de fusionarlo con el código de la rama main del proyecto o a la rama donde debe agregarse este código, para esto sirven las PULL REQUEST:

- En el repositorio que hemos clonado creamos una nueva rama para trabajar.
- Realizamos nuestro trabajo en esa rama como lo hemos venido haciendo hasta ahora
- Subimos los cambios al repositorio de Github en su propia rama (si no existe la creamos)
- Dentro de la interfaz de Github haremos un "pull-request" para que nuestro equipo de trabajo revise nuestro código y lo mergee a la rama correspondiente, al crear el pull-request se mostrará todos los commits que hemos realizado en los ficheros y el equipo de trabajo lo mergeará si es necesario.

- CONFLICTOS

Los conflictos se pueden dar por varias razones entre ellas cuando los desarrolladores de un equipo han hecho o pretenden subir cambios al repositorio de Git sobre un mismo código sin tener actualizado el repositorio local. Github no sabe con cual versión quedarse y esto se debe solucionar revisando manualmente cada conflicto y eligiendo cual es la versión que vamos a mentener. Github mostrará un aviso de que existen conflictos cuando hagamos un pull-request o merge.

Los conflictos se pueden resolver desde la interfaz de Github o desde nuestro editor sobre nuestro repositorio local:

- Nos posicionamos en la rama donde estamos trabajando
- git pull origin main (esto traerá de Github todos los cambios hechos en la rama main, incluso los conflictos)

GIT PULL VS. GIT FETCH

- git pull trae los cambios del repositorio remoto y automáticamente actualiza nuestro repositorio local.
- git fetch descarga los cambios del repositorio remoto sin sobreescribir el repositorio local, esto permite que podamos revisar los cambios que otro desarrollador haya hecho en el repositorio y decidir si queremos aplicarlos al nuestro con merge

FORK

Hacer un fork es hacer una copia exacta de un repositorio de Github a nuestra cuenta para poder hacer los cambios que deseemos, esta copia mantendrá un vínculo al repositorio original y podríamos solicitar un pull-request a su propietario para que acepte o no los cambios que hemos hecho, es así como se trabaja en proyectos colaborativos.

Eliminar Repositorios y ramas

Un repositorio se puede aliminar en Github desde la sección settings, para eliminar una rama debemos visualizar todas las ramas y clicar en el icono del cubo de basura, esta acción se puede revertir solamente si no hemos pasado a la pestaña de código.

Aunque hayamos eliminado una rama en el repositorio remoto y hecho git pull para actualizar el repositorio local, la rama eliminada seguirá apareciendo en local, para eliminarla hacemos:

- git branch -D [nombre_de_la_rama]

GIT STASH

Este comando permite llevar los cambios que hemos hecho por error en una rama hacia la rama donde queríamos realmente hacer esos cambios, este comando funciona si no hemos hecho "git add" de los cambios.

- git stash (recoge los cambios que se han hecho en la rama equivocada y los guarda en un stash, un lugar donde no tienen efecto)

- git stash pop (ubicados en la rama correcta trae los cambios gurdados en el stash)