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

- Actualizar repositorio local con los cambios que se hayan hecho en el repositorio de Github

    git pull

- Esta línea es solo para probar git pull
