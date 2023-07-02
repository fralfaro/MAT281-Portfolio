# Instrucciones de uso

El objetivo de este portafolio es que el estudiante aprenda a utilizar `Github` y posea material demostrable de las habilidades aprendidas en el curso. Las instrucciones se dividen en la configuración del repositorio personal, configuración del repositorio del curso y en un flujo típico a lo largo del semestre.


## Configuración inicial para el curso

1. Crear cuenta de GitHub [aquí](https://github.com/join).
2. Instalar [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
    - En Windows lo ideal sería instalar _Git for Windows_.
    - También existe una alternativa con interfaz gráfica, [GitHub Desktop](https://desktop.github.com/) pero no es recomendable, pues uno de los objetivos del curso es aprender los fundamentos de Git.
3. Configurar tu forma de acceder a GitHub. [Recomendaciones.](https://help.github.com/en/articles/which-remote-url-should-i-use)
    - Recomendado pero menos seguro: HTTPS
        * Te podría ser útil configurar [_credential helper_ ](https://help.github.com/en/articles/caching-your-github-password-in-git) para recordar tu usuario en tu computador.
    - Más engorroso pero más seguro: SSH
        * Sigue [estas instrucciones](https://help.github.com/en/articles/connecting-to-github-with-ssh).
4. Ir al repositorio [MAT281-Portfolio](https://github.com/fralfaro/MAT281-Portfolio) y presionar el botón *__Use this template__* <img src="../images/template.png" width=80>.
5. Nombar el nuevo repositorio como __mat281_portfolio__ y dejarlo en modo público.
7. Se recomienda crear un directorio en el computador personal para repositorios de Git. Por ejemplo en `~/Documents/git/`.
6. Clonar el repositorio recién creado. Dependiendo de tu configuración de Git, reemplazar `{username}` por el nombre de usuario personal de GitHub uno de los siguientes comandos en la terminal (usuarios de Windows probablemente tengan que utilizar _Git Shell_.)
    - HTTPS: `git clone https://github.com/{GITHUB_USER}/mat281_portfolio.git`
    - SSH: `git clone git@github.com:{GITHUB_USER}/mat281_portfolio.git`
7. En el archivo `README.md` editar los campos personales:
    - Nombre y si se desea algún link a perfil profesional, por ejemplo Linkedin o GitHub.

## Configurar repositorio del curso

1. Clonar el repositorio del curso (no puede estar dentro de la carpeta de tu portafolio) ejecutando:
`git clone https://github.com/{TEACHER_GH_USER}/MAT281_{PERIOD}.git`
donde `{TEACHER_GH_USER}` es el usuario del profesor a cargo del curso y `{PERIOD}` es el año-semestre en que se dictó. Por ejemplo, para el segundo semestre de 20XX los valores son `fralfaro` y `20XX` respectivamente. 
2. En el transcurso del semestre, para actualizar se debe ejecutar `git pull` en la terminal dentro del directorio del repositorio. Por ejemplo, si el repositorio está en la ruta `~/Documents/git/MAT281_20XX`:
    - `cd ~/Documents/git/MAT281_20XX`
    - `git pull`
    - __¡IMPORTANTE!__ Para no tener problemas al _pullear_ no deben existir conflictos con el repositorio original, la mejor forma de evitar esto es no editar ningún archivo y realizar todos los laboratorios/tareas/etc. en el repositorio personal del curso.

## Flujo típico de uso

1. Al comenzar el semestre creaste y clonaste tu repositorio personal del curso y clonaste el repositorio oficial del curso. Deberías tener estructura de directorios similar a esta:
    ```
    - your_git_folder
    |
    |- MAT281_20XX
    |  |
    |  |- ...
    |
    |- mat281_portfolio
        |
        |- ...
    ```
1. Al comenzar cada clase actualizas el contenido en el respositorio oficial del curso, es decir, ejecutas `git pull` dentro de la carpeta `MAT281_20XX`.
1. Copia el archivo ipynb del laboratorio y pégalo en la carpeta `mat281_portfolio\labs`.
1. Abrir desde `jupyter lab` el archivo correspondiente a la clase que se encuentre en el __repositorio personal__.
1. Realiza el laboratorio, tarea o proyecto y guarda los cambios.
1. Agregar, _commitear_ y _pushear_ los cambios, lo típico sería:
    ```
    cd ~/Documents/git/mat281_portfolio
    git add lab_xx.ipynb any_other_file
    git commit -m "Laboratorio xx."
    git push origin master
    ```
    Con esto se verán reflejados los cambios en tu cuenta de GitHub.
