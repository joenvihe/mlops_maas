# Analítica como un Servicio
## MAAS - SAAS

En este repositorio les presentare una arquitectura alternativa para el desarrollo y despliegue de un modelo y solucion como servicio, el MaaS y SaaS respectivamante.

## HERRAMIENTAS

Previamente se deben instalar las siguientes aplicaciones en windows:
- [GIT](https://git-scm.com/download/windows)
- [DOCKER](https://docs.docker.com/desktop/windows/install/)
- [ANACONDA](https://www.anaconda.com/products/individual)

## CREACION DE CUENTAS

Se crearan las cuentas en los siguientes servicios:
- [DOCKER_HUB](https://hub.docker.com/)
- [OKTETO](https://www.okteto.com/)
- [HEROKU](https://dashboard.heroku.com/login)

## LIBRERIAS DE PYTHON

La lista de librerias y sus versiones lo encontraran a detalle en el archivo requirements.txt
- Cookiecutter:  Data science project structure
- dvc: Version control of the data assets and to make pipeline
- mlflow: For model registry
- EvidentlyAI: To evaluate and monitor ML models in production
- Pytest: To implement the unit tests

## DISEÑO DE ARQUITECTURA

## PASOS A REALIZAR
- Crear el entorno de trabajo en python: **Ejecutarlo en el aplicativo ANACONDA POWERSHELL**
```bash
conda create -n envMLops python=3.7
conda activate envMLops
pip install -r requirements.txt
```

- Crear la plantilla de cookiecutter
```bash
cookiecutter https://github.com/drivendata/cookiecutter-data-science
```
![cookiecutter_config](/img_readme/cookiecutter.png?raw=true "Linea de Comandos")

- Comentamos el segmento /data/ dentro del .gitignore, esta carpeta se utilizara con el DVC

- Ingresar a la carpeta que se creo con la plantilla de cookiecutter:  **cd .\mlops_maas**.

- Crear repositorio git en la web de github.
![repositorio_git](/img_readme/repositoriogit.png?raw=true "repositorio git")

- Subir tu proyecto con los comandos que se te brindan al crear la cuenta. **Ejecutarlo en el aplicativo Git Bash**
```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<USUARIO_CUENTA_GITHUB>>/mlops_maas.git
git push -u origin main
```

- Se sube el archivo de data entrie ***bank.csv** a la carpeta **./data/external/**

- Se inicializa DVC el contralodor de versiones de la Data
```bash
>dvc init
>cd ./data/external
>dvc add bank.csv
```

- Se ejecuta el notebook y se genera la data para entrenamiento, el archivo resultante es **./data/external/BankAnalysis.csv**

- Se agrega al controlador de versiones
```bash
>dvc add BankAnalysis.csv
```



## AUTOR: Jorge Enrique Vicente Hernández

- [@web_personal](http://joenvihe.herokuapp.com/)
- [@repositorio_git](https://github.com/joenvihe)