# WSL Data Science Toolkit

Luego de mucha prueba y error, el siguiente flujo de trabajo en WSL ha sido el que me he resultado más cómodo.

1. Instalar WSL
    - https://docs.microsoft.com/en-us/windows/wsl/install-win10
    - Recomiendo instalar Ubuntu como distribución de linux.
2. Abrir tu distribución para configurar usuario entre otros.
3. [Opcional] Instalar `cmder`, una interfaz de terminal que puede manejar WSL.
4. Instalar miniconda
    1. Abrir tu terminal WSL. En cmder presionar `Ctrl+T` y seleccionar `{WSL::bash}`.

    2. Ir al home utilizando `cd ~`.

    3. Ejecutar `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`, el cual correspone al [link](https://docs.conda.io/en/latest/miniconda.html) del instalador de miniconda para Linux.

    4. Seguir las instrucciones de instalación de miniconda de la [documentación oficial](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html).

    5. Configuración personal:
        - _Do you wish the installer to initialize Anaconda3 by running conda init?_: Yes
        - Cerrar la terminal.
        - Abrir la terminal y ejecutar `conda config --set auto_activate_base false`.
    
        Con esto la versión de Python por defecto es la que viene instalada en la distribución. Cuando desees utilizar un ambiente de conda hay que activarlo.

    6. Dejar como canal por defecto conda-forge siguiendo las siguientes [instrucciones](https://conda-forge.org/).

    7. Eliminar el instalable de miniconda con `rm  Miniconda3-latest-Linux-x86_64.sh` en la ruta donde fue descargado.

5. Crear un entorno virtual solo para jupyter:
    - En la terminal ejecutar `conda create -n jupy pip jupyterlab nodejs nb_conda_kernels`. El nombre del ambiente lo puedes escoger tu, yo escogí `jupy`.

6. Crear un entorno virtual de trabajo, por ejemplo, yo suelo crear uno como este:
    - `conda create -n ds pip ipykernel numpy pandas matplotlib altair scikit-learn scipy vega_datasets seaborn pandas-profiling`

7. Para utilizar jupyter basta con que abras la terminal, actives el entorno de jupyter (`conda activate jupy`) y luego ejecutes `jupyter lab --no-browser`. Finalmente copia y pega la url con el token en tu navegador y verás que están todos los kernels de Python correspondientes.

8. [Opcional] Configurar GitHub. 
    - Para configurar tu nombre de usuario y correo electrónico seguir el siguiente [link](https://help.github.com/es/github/using-git/setting-your-username-in-git). En caso de usar más de un correo electrónico es recomendable configurarlo para cada repositorio y no de manera global.
    - Puedes guardar la contraseña de tu cuenta de GitHub en el caché según la [documentación oficial](https://help.github.com/es/github/using-git/caching-your-github-password-in-git). En tu computador personal puedes incluso guardarla por siempre ejecutando `git config --global credential.helper store`.
    - Como una buena práctica te recomiendo tener una carpeta con todos los repositorio de git. Yo usualmente utilizo la ruta `/mnt/c/Users/{USERNAME}/Documents/git`.

9. [Opcional] Crear un alias para moverse rápidamente a la carpeta de repositorios.
    - En el archivo .bashrc agregar la siguiente linea `alias cdgit="cd /mnt/c/Users/{USERNAME}/Documents/git"` o reemplazar por la carpeta donde tienes los repositorios.
10. [Opcional] Instalar Visual Studio Code.
    - La instalación es un poco estándar: [link](https://code.visualstudio.com/docs/setup/setup-overview).
    - Configurar VS Code para WSL: [link](https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl).
    - Algunas extensiones que encuentro útiles:
        - Settings Sync
        - Better Comments