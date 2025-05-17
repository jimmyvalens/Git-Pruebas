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