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
- Cookiecutter

## DISEÑO DE ARQUITECTURA

## PASOS A REALIZAR
- Crear el entorno de trabajo en python
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
- Ingresar a la carpeta que se creo con la plantilla de cookiecutter: el mio **.\mlops_maas**.
- Crear repositorio git en la web de github.
![repositorio_git](/img_readme/repositoriogit.png?raw=true "repositorio git")
- Subir tu proyecto con los comandos que se te brindan al crear la cuenta.
```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<USUARIO_CUENTA_GITHUB>>/mlops_maas.git
git push -u origin main
```

## AUTOR: Jorge Enrique Vicente Hernández

- [@web_personal](http://joenvihe.herokuapp.com/)
- [@repositorio_git](https://github.com/joenvihe)