# Huqariq

Huqariq es una aplicaciones móvil, que permite la recolección de Speech-Corpus (Grabaciones de audio) de lenguas nativas de América.
Uno de las principales características de Huqariq es que permite al usuario escuchar un audio (prompt) para posteriormente grabarlo. Esta funcionalidad es conveniente en lenguas donde la mayoría de los hablantes no tienen conocimiento en la escritura de su propia lengua, la cúal es el caso de la mayoría de lenguas nativas, por consiguiente facilita la recolección de corpus.  


**Table of Contents**


- [Servidor](#servidor)
  - [Arquitectura](#arquitectura)
  - [Módulo de Registro](#módulo-de-registro)
  - [Módulo de Audio](#módulo-de-audio)
  - [Módulo de Fonémas](#módulo-de-fonémas)
  - [Módulo de Calidad](#módulo-de-calidad)
- [Aplicación Móvil](#aplicación-móvil)
  - [Repositorio App](#repositorio-app)
- [Recomendaciones](#recomendaciones)
- [Documentación](#documentación)
- [Contacto](#contacto)

## Servidor

### Módulo de Registro

El módulo de registro es el encargado de aceptar las peticiones de registro de nuevos usuario, ademas de validar si el usuario puede registrase. A continuación se muestra los datos requeridos para la creación de un usuario nuevo.

| Dato                 | Descripción                                                                  |
| -------------------- | ---------------------------------------------------------------------------- |
| `email`              | Es el correo electronico que brinda para registrase a la aplicación          | 
| `contraseña`         | La contraseña es un string que es cifrada                                    |
| `DNI`                | Es el documento de identidad de los usuario de nacionalidad Peruana          |
| `Nombres`            | Nombres completos del usuario                                                |
| `Apellidos`          | Apellidos completos del usuario                                              |
| `Departamento`       | Departamento donde nacio el usuario.                                         |
| `Provincia`          | Provincia donde nacio el usuario.                                            |
| `Distrito`           | Distrito donde nacio el usuario                                              |
| `Variedad`           | Variedad dialectica la cual es nativo hablante                               |


#### Validación de email

Para poder registrase en la aplicación el usuario debe colocar un email que exista, ademas no haberse registrado con ese anteriormente. Para asegurar la veracidad del email, se implemento el siguiente código:

`af`

#### Validación del DNI

Con el fin de saber los nombres y apellidos reales del usuario, hemos implementado un método que con el DNI podemos obtener los nombres y apellidos del usuario de la base de datos de RENIEC mediante el siguiente código:

`af`

#### Validación de variedad

Para conocer realmente que variedad de dialecto habla el usuario, se implemento un módulo con el fin que el usuario puede responder algunas preguntas y saber que variedad sabe hablar, cabe mencionar que se realiza esto debido a que la mayoria de personas hablantes nativas no conocer la variedad que habla.

`af`


### Módulo de Audio

### Módulo de Fonémas

### Módulo de Calidad

## Aplicación Móvil


## Recommendations

El servidor debe ser ubuntu 16.04 LTS, 16GB RAM, 125GB SSD.


## Documentación

La documentación se encuenta en el siguiente enlace: https://docs.google.com/document/d/1nOP5HCoASVtoykoC3LNMzKZEPyz-cU86YubEAo4COxw/edit

## Contacto

Estamos felices de poder ayudarlo:

rodolfojoel.zevallos01@estudiant.upf.edu y
camacho.l@pucp.pe

