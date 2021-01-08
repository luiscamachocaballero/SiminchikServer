# Huqariq

Huqariq es una aplicaciones móvil, que permite la recolección de Speech-Corpus (Grabaciones de audio) de lenguas nativas de América.
Uno de las principales características de Huqariq es que permite al usuario escuchar un audio (prompt) para posteriormente grabarlo. Esta funcionalidad es conveniente en lenguas donde la mayoría de los hablantes no tienen conocimiento en la escritura de su propia lengua, la cúal es el caso de la mayoría de lenguas nativas, por consiguiente facilita la recolección de corpus.  


**Table of Contents**

- [Prerequisitos](#prerequisitos)
- [Entorno de configuración](#entorno-de-configuración)
- [Instalación de requerimientos](#instalación-de-requerimientos)
- [Qillqaq](#qillqaq)
  - [Usando modelo de lengauje](#usando-modelo-de-lenguaje)
  - [Sin modelo de lenguaje](#sin-modelo-de-languaje)
- [Huqariq](#huqariq)
- [Tarpuriq](#tarpuriq)
- [Instalación de Gunicorn](#instalación-de-gunicorn)
- [Servidor en marcha](#servidor-en-marcha)
- [Recomendaciones](#recomendaciones)
- [Documentación](#documentación)
- [Contacto](#contacto)

## Prerequisitos

* [Python 3.6](https://www.python.org/)
* [SOX](http://sox.sourceforge.net/)
* [MySQL](https://www.mysql.com)

## Entorno de configuración

Configure un entorno virtual y actívelo:

```bash
virtualenv siminchik -p python3
. venv/bin/activate
```

## Instalación de requerimientos

Primero, se debe actualizar el sistema:

```bash
sudo apt-get update
sudo apt-get upgrade
```

Segundo, debe clonar el repositorio

```bash
sudo git clone https://github.com/rjzevallos/SiminchikServer
```

Tercero, instalar los requerimientos usando el archivo requirements.txt

```bash
cd SiminchikServer
sudo pip install -r requirements.txt
```

Cuarto, instalar el parquete de procesamiento de audio ffmpeg

```bash
sudo apt-get install ffmpeg
```

Quinto, creamos una base de datos en mysql

```bash
sudo mysql -p
create database app_quechua;
use app_quechua;
source ../db/siminchik.sql;
```

## Qillqaq

Para poder usar el Automatic Speech Recognition, se debe descargar el modelo entrenado

```bash
sudo wget https://github.com/rjzevallos/QillqaqServer/releases/download/v0.01/5-gram.binary
sudo wget https://github.com/rjzevallos/QillqaqServer/releases/download/v0.01/output_graph.pb
sudo wget https://github.com/rjzevallos/QillqaqServer/releases/download/v0.01/quz_trie
```

## Prueba del modelo

Hay 2 formas de probar el modelo

### Usando el modelo de lenguaje

```bash
deepspeech --model output_graph.pbmm --alphabet quz_alphabet.txt --lm 5-gram.binary --trie quz_trie --audio hatispa.wav
```

### Sin modelo de lenguaje

```bash
deepspeech --model output_graph.pb --alphabet quz_alphabet.txt --audio hatispa.wav
```


## Huqariq

La aplicaciones para recolectar speech corpus cuenta actualmente con alrededor de 4,000 prompts del Quechua Chanca y Collao.
A continuación se muestra la distribución de prompts por cada variedad.


| Variedad             | Cantidad             |
| -------------------- | ---------------------|
| Chanca               | 1428                 |
| Collao               | 2966                 |
| -------------------- | ---------------------|
| Total                | 4394                 |


La cantidad de prompts se recolecta con la aplicación Tarpuriq que se muestra en el apartado siguiente.



## Tarpuriq

La aplicaciones para prompts que sirven como alimento para Huqariq cuenta actualmente con alrededor de 8,000 frases del Quechua Chanca y Collao.
A continuación se muestra la distribución de los textos por cada variedad.


| Variedad             | Cantidad             |
| -------------------- | ---------------------|
| Chanca               | 3887                 |
| Collao               | 3401                 |
| -------------------- | ---------------------|
| Total                | 8288                 |


Los textos que sirven como base para la grabaciones de los prompts fueron recolectados de los diccionarios realizados por el Ministerio de Educación de Perú, asi mismo, por otros diccionarios como el "Diccionario Funcional de Quechua-Ingles" de Clodoaldo Soto Ruiz y el libro "Autobiografía" de Gregorio Condori Mamani.


## Instalación de Gunicorn

Primero, se debe instalar guniron

```bash
pip install gunicorn
```

Segundo, verificamos con el siguiente comando para asegurarnos de que el servicio se esté ejecutando

```bash
gunicorn --workers 3 --bind 0.0.0.0:5000 -m 007 wsgi:app
```


## Servidor en marcha

Solo debemos correr el siguiente comando para lanzar el servidor Siminchik.

```bash
nohup gunicorn --workers 3 --bind 0.0.0.0:5000 -m 007 wsgi:app
```

## Recommendations

El servidor debe ser ubuntu 16.04 LTS, 16GB RAM, 125GB SSD.


## Documentación

La documentación se encuenta en el siguiente enlace: https://docs.google.com/document/d/1nOP5HCoASVtoykoC3LNMzKZEPyz-cU86YubEAo4COxw/edit

## Contacto

Estamos felices de poder ayudarlo:

rodolfojoel.zevallos01@estudiant.upf.edu y
camacho.l@pucp.pe

