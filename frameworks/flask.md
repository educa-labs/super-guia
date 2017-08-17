## Flask

# Introduccion

Flask es un "micro" framework web, programado en Python que utiliza las librerías Jinja2 y Werkzeug.
Posee herramientas para crear desde una API REST hasta una aplicación basada en la arquitectura MVC.
Por lo general en Educalabs usamos esta herramienta para el desarrollo de microservicios dentro de las aplicaciones, por lo cual en esta guía se presentará nuestra forma estandarizada de crear APIs REST para los microservicios.

# Requisitos

* Ubuntu >= 16.04
* Python >= 3.5
* pip3
* virtualenv
* Dentro del entorno: gunicorn, flask_cors, psycopg2

En el terminal:
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

Con esto ya tendremos nuestro entorno preparado con las librerias necesarias para desarrollar nuestra aplicación.
Para agregar otras librerias de python basta con instalar con pip, pero siempre entrando en el entorno virtual.

```bash
source myprojectenv/bin/activate
pip3 install <libreria_de_python>
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
        db = DB() # DB se ve en la siguiente sección.
        result = db.some_query(request.get_json(force=True))
        status = 200

    elif request.method == "PUT":
        result = 'PUT request is not allowed'
        status = 501

    resp = Response(json.dumps(result), status=status, mimetype='application/json')
    return resp

```
La libreria CORS permite evitar problemas de Cross Origin Requests.
En el código se ve un ejemplo de los métodos que se admiten el request (GET, POST, PUT, etc), y un control de flujo que decide que hacer para cada uno de los métodos.
Cabe mencionar que el ```mimetype=application/json``` indica que el retorno será de tipo JSON, que es el protocolo que usaremos para nuestros microservicios basados en cliente/servidor.


# Archivo de base de datos
En educalabs tenemos un estándar de programación en Flask a la hora de usar bases de datos.
Como solo hacemos microservicios en Flask, no utilizamos active records y se realizan las consultas con SQL directo con cursores de la libreria Psycopg2.
La base de datos debe estar en PostgreSQL.

```Python
import psycopg2 as psql
DB_NAME = "aplication_production"
DB_USER = "user"
DB_PASS = "password"
DB_HOST = "api.myapplication.com"
DB_PORT = "5432"
class DB():

    def __init__(self):
        while True:
            try:
                self.conn = psql.connect("dbname={} user={} password={} host={} port={}".format(
                DB_NAME, DB_USER, DB_PASS, DB_HOST, DB_PORT
                ))
                self.cur = self.conn.cursor()
                break
            except:
                pass

    def init_db(self):
        self.cur.execute("CREATE TABLE Objects(id serial, name text)")
        self.conn.commit()

        return        

    def some_query(self, data, **kwargs):
        # do the shit
        data = {"status": True}
        # Nunca retornamos un dump de Json aqui, porque podemos reutilizar
        # alguna función de la clase DB.
        return data
```
El constructor de la clase inicializa la conexión y deja un curso listo para ejecutar consultas.
La función ```init_db``` es la que contendrá los queries minimos para migrar la base de datos.
Cada función restante hará consultas distintas para cumplir con las funcionalidades deseadas.  



# Deployment
