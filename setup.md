# Instrucciones de uso

El objetivo de este portafolio es que el estudiante aprenda a utilizar `Git` y posea material demostrable de las habilidades aprendidas en el curso. Las instrucciones se dividen en la configuración del repositorio personal, configuración del repositorio del curso y en un flujo típico a lo largo del semestre.

En particular, se debe configurar `Binder` con tal de poder ejecutar el código del estudiante desde cualquier computador sin la necesidad de descargar, por eso es necesario que al subir los laboratorios, tareas o proyectos estos se suban en conjunto a los datos necesarios.

## Configuración inicial para el curso

1. Crear cuenta de GitHub [aquí](https://github.com/join).
    - Es recomendable aprovechar el correo UTFSM y reclamar el [_Student Pack_](https://education.github.com/students) de GitHub. Uno de sus beneficios es acceder a una membresía Pro y así tener repositorios privados.
2. Instalar [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
    - En Windows lo ideal sería instalar _Git for Windows_.
    - También existe una alternativa con interfaz gráfica, [GitHub Desktop](https://desktop.github.com/) pero no es recomendable, pues uno de los objetivos del curso es aprender los fundamentos de Git.
3. Configurar tu forma de acceder a GitHub. [Recomendaciones.](https://help.github.com/en/articles/which-remote-url-should-i-use)
    - Recomendado pero menos seguro: HTTPS
        * Te podría ser útil configurar [_credential helper_ ](https://help.github.com/en/articles/caching-your-github-password-in-git) para recordar tu usuario en tu computador.
    - Más engorroso pero más seguro: SSH
        * Sigue [estas instrucciones](https://help.github.com/en/articles/connecting-to-github-with-ssh).
4. Ir al repositorio [mat281_portfolio_template](https://github.com/FranciscoAlfaroMedina/mat281_portfolio_template) y presionar el botón *__Use this template__*.
5. Nombar el nuevo repositorio como __mat281_portfolio__ y dejarlo en modo público.
7. Se recomienda crear un directorio en el computador personal para repositorios de Git. Por ejemplo en `~/Documents/git/`.
6. Clonar el repositorio recién creado. Dependiendo de tu configuración de Git, reemplazar `{username}` por el nombre de usuario personal de GitHub uno de los siguientes comandos en la terminal (usuarios de Windows probablemente tengan que utilizar _Git Shell_.)
    - HTTPS: `git clone https://github.com/{GITHUB_USER}/mat281_portfolio.git`
    - SSH: `git clone git@github.com:{GITHUB_USER}/mat281_portfolio.git`
7. En el archivo `README.md` editar los campos personales:
    - Línea 14: `[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/{GITHUT_USER}/mat281_portfolio/master?urlpath=lab)` donde deber cambiar `{GITHUB_USER}` por tu usuario de GitHub.
    - Línea 16: Nombre y si se desea algún link a perfil profesional, por ejemplo Linkedin o GitHub.

## Configurar repositorio del curso

1. Clonar el repositorio del curso (no puede estar dentro de la carpeta de tu portafolio) ejecutando:
`git clone https://github.com/{TEACHER_GH_USER}/MAT281_{PERIOD}.git`
donde `{TEACHER_GH_USER}` es el usuario del profesor a cargo del curso y `{PERIOD}` es el año-semestre en que se dictó. Por ejemplo, para el segundo semestre de 2020 los valores son `FranciscoAlfaroMedina` y `2020` respectivamente. 
2. En el transcurso del semestre, para actualizar se debe ejecutar `git pull` en la terminal dentro del directorio del repositorio. Por ejemplo, si el repositorio está en la ruta `~/Documents/git/MAT281_2020`:
    - `cd ~/Documents/git/MAT281_2020`
    - `git pull`
    - __¡IMPORTANTE!__ Para no tener problemas al _pullear_ no deben existir conflictos con el repositorio original, la mejor forma de evitar esto es no editar ningún archivo y realizar todos los laboratorios/tareas/etc. en el repositorio personal del curso.

## Flujo típico de uso

1. Al comenzar el semestre creaste y clonaste tu repositorio personal del curso y clonaste el repositorio oficial del curso. Deberías tener estructura de directorios similar a esta:
    ```
    - your_git_folder
    |
    |- MAT281_2020
    |  |
    |  |- ...
    |
    |- mat281_portfolio
        |
        |- ...
    ```
1. Al comenzar cada clase actualizas el contenido en el respositorio oficial del curso, es decir, ejecutas `git pull` dentro de la carpeta `MAT281_2020`.
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

## Verifica que todo funcione correctamente!

Después de cada _commit_, prueba que Binder está bien configurado, ya que Binder necesita realizar una nueva imagen/contenedor de tu repositorio. Además, durante el curso se han instalado librerías o actualizado otras, por lo que debes editar el archivo `binder/environment.yml` de tu respostorio.

Ejemplo:

- _Pusheaste_ la tarea del módulo de análisis datos (`m02_homework`)
- Vas a tu repositorio y ejecutas Binder haciendo click en el icono de Binder configurado anteriormente.
- Se va a tardar un par de minutos en crear la nueva imagen y lanzar la instancia de Jupyter Lab (__NO__ Jupyter Notebook!).
- Al estar lista la instancia de Jupyter Lab, abre el notebook `m02_homework.ipynb` que debe estar en la carpeta `m02_data_analysis/m02_homework`.
- Haz click en `Kernel -> Restart Kernel and Run All Cells`.
- Si al ejecutar `from PIL import Image` te arroja el error `ModuleNotFoundError: No module named 'PIL'` es porque no agregaste `pillow` a tu archivo `environment.yml`
    * Recuerda que las librerías instaladas en tu computador personal no se traspasan mágicamente a la instancia de Binder en tu repositorio, debes especificar las librerías en el famoso archivo `environment.yml`.
- En el caso que se te presente el caso anterior debes agregar la dependencia `pillow` y `environment.yml` te quedaría __algo__ como esto:

```yml
name: mat281
channels:
  - conda-forge
  - defaults
dependencies:
  - jupyterlab=1.2.0
  - jupyter_contrib_nbextensions
  - matplotlib
  - numpy
  - pandas
  - pandas-profiling
  - pip
  - python=3.7
  - scikit-learn
  - scipy
  - seaborn
  - statsmodels
  - pillow
```

- Luego vuelves a hacer un _push_ con este cambio.
- Levantas la instancia de Binder en tu repostorio y vuelves a probar a ejectuar todas las celdas de `m02_homework.ipynb`.
- Repite el proceso hasta que todos tus entregables no tengan problema.

Finalmente, recuerda que la estructura de las carpetas es importante, así como los archivos que están en tu repositorio. Mostrar orden y pulcridad demuestra profesionalismo y seriedad. Recuerden que este repositorio será su carta de presentación el día de mañana.