## Flask

# Introduccion

Flask es un "micro" framework web, programado en Python que utiliza las librerías Jinja2 y Werkzeug.
Posee herramientas para crear desde una API REST hasta una aplicación basada en la arquitectura MVC.
Por lo general en Educalabs usamos esta herramienta para el desarrollo de microservicios dentro de las aplicaciones, por lo cual en esta guía se presentará nuestra forma estandarizada de crear APIs REST para los microservicios.

# Requisitos

* Python >= 3.5
* pip3
* virtualenv
* Dentro del entorno: gunicorn, flask_cors, psycopg2

```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install python3-dev python3-pip nginx
sudo pip3 install virtualenv
```


# Entorno de desarrollo

Primero se debe crear un directorio en el que queramos tener la aplicación. Luego crearemos un entorno virtual de desarrollo

```bash
mkdir <nombre_aplicacion>
cd <nombre_aplicacion>
virtualenv pyenv
source myprojectenv/bin/activate
pip3 install gunicorn flask flask_cors psycopg2
```


# Archivo Base (main.py)

Para comenzar, utilizaremos un archivo base llamado main.py, el cual cargará la aplicación, importará las librerías mínimas para la aplicación, y contendrá las rutas de nuestra API.
El archivo base será de esta forma:
```Python
# Flask Libs
from flask import Flask
from flask import request, Response, send_from_directory, render_template, request
from flask_cors import CORS, cross_origin
# System libs
import json
# Other libs
from db import DB
from functions import *
import libreria_hecha_en_educalabs

app = Flask(__name__)
CORS(app)

@app.route("/ruta", methods = ["GET", "POST", "PUT"])
def get_predicition():
    # Para evitar problemas con Chrome
    resp.headers['Access-Control-Allow-Origin'] = '*'

    if request.method == "GET":
        result = 'GET request is not allowed'
        status = 501

    elif request.method == "POST":
        result = "POST request is allowed :)"
        status = 200

    elif request.method == "PUT":
        result = 'PUT request is not allowed'
        status = 501

    resp = Response(json.dumps(result), status=status, mimetype='application/json')
    return resp

```


# Archivo de base de datos
En educalabs tenemos un estándar de programación en Flask a la hora de usar bases de datos.
Como solo hacemos microservicios en Flask, no utilizamos active records y se realizan las consultas con SQL directo con cursores de la libreria Psycopg2.
La base de datos debe estar en PostgreSQL.

```Python

```





# Deployment
