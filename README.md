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

- Se ejecuta el notebook **Data_Analysis_ML_bootcamp.ipynb** y se genera la data para entrenamiento, el archivo resultante es **./data/external/BankAnalysis.csv**

- Se ejecuta el notebook **Feature_Engineering_and_modelling.ipynb** y se genera el modelo .pkl, el archivo resultante es **saved_rf_model.pkl**


- Se agrega al controlador de versiones
```bash
>dvc add BankAnalysis.csv
```

- Se crea el archivo de configuracion en la raiz **params.yaml**

- Se crea el archivo **./src/data/load_data.py** que carga la data de la carpeta **./data/external/** a la carpeta **./data/raw/**

- Se crea el archivo **./src/data/split_data.py** que divide la data en test y train creando dos archivos dentro de la carpeta **./data/processed/**

- Se crea el archivo **./src/models/train_model.py** donde se experimenta con los modelos cambiando parametros del archivo **params.yaml** y tambien el MLFLOW hace seguimiento de los performance de los modelos y los cuales se podra visualizar facilmente en el **dashboard de mlflow**

- Se crea el archivo **./src/models/production_model_selection.py** donde se selecciona el modelo que ha tenido un mejor performance entre todos los modelos registrados y lo guarda como artefacto en la carpeta **./models/** 

- Despues de crear los archivos en la carpeta **src**, se crea el model pipeline para generar elmodelo. DVC  sera usado para crear el pipeline. Para ello se crea el archivo **dvc.yaml** dentro de la carpeta raiz.

- Se levanta el servidor del MLFLOW en otro CMD:
```bash
>mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./artifacts --host 127.0.0.1 -p 5000
```

- Se ejecuta el pipeline dvc, puede salir un error de metric.acuraci pero se vuelve a ejecutar
```bash
>dvc repro
```

- Al cambiar los hiperparametros del modelo se genera una nueva version del modelo y se guarda en el **model regestry** del mlflow
![model_regestry_mlflow](/img_readme/model_regestry_mlflow.png?raw=true "model regestry mlflow")

## AUTOR: Jorge Enrique Vicente Hernández

- [@web_personal](http://joenvihe.herokuapp.com/)
- [@repositorio_git](https://github.com/joenvihe)