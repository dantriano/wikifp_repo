---
title: Identidad Digital
description: 
published: true
date: 2022-01-24T16:06:20.530Z
tags: 
editor: markdown
dateCreated: 2022-01-24T13:51:12.402Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M6 - Seguretat informatica
- :calendar: **Durada**: 12h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQUptNnWQRe9N5Zye0Tgg-qiQjqRZm6WXmd7DdRd8E5BvdkJ4Eqg-RT5PiVXvzWe9Sr5V5Ynu7Bglt1/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vQUptNnWQRe9N5Zye0Tgg-qiQjqRZm6WXmd7DdRd8E5BvdkJ4Eqg-RT5PiVXvzWe9Sr5V5Ynu7Bglt1/pub?start=false&loop=false)

# :orange_book: Apunts
La administración pública pone a nuestra disposición diferentes recursos para poder tener una **identididad digital** con la que poder realizar tramites oficiales online. Algunos de ellos son:
- Certificado digital
- Firma Digital
- Cl@ave Pin

> Actualmente hay un portal llamado **Cl@ve** que centraliza todos estos metodos y permite que el usuario elija el que mejor le convenga 
[https://clave.gob.es/]()
{.is-success}


# Certificado digital
El certificado digital es un **archivo expedido por la administración** que nos identifica con un codigo unico y que podemos utlitzar para identificarnos en la red.

## Solicitud de certificado digital
Existen varios organismos que permiten generar tu certificado digital: seguridad social, Ayuntamientos, oficinas de empleo...


Sigue los pasos indicados en la documentación oficial del certificado que quieras obtener

[Certificado Digital Estatal](https://www.fnmt.es/documents/10179/30421/20160722+Folleto+Certificado+Digital/a8801dab-b512-445f-81e5-d44df16afe5b)
[Certificado Catalán (idCAT)](https://www.idcat.cat/ca/solicitar)


> Para poder pedir el certificado antes hay que instalar un programa del FNMT (organismo de certificación)
{.is-danger}


![errores_dependencias.png](/informatica/smr/m6/errores_dependencias.png){.align-center}
```
sudo apt --fix-broken install
sudo apt install libcanberra-gtk-module
sudo dpkg -i '/home/users/inf/inf/dtriano/Downloads/configuradorfnmt_1.0.1-0_amd64.deb'
```


## Instalación del certificado digital

Una vez descargado deberas de añadir el certificado en tu navegador o sistema operativo (iOS) para poderlo utilizar en las páginas que visitas. Tambien existen aplicaciones moviles en los que puedes añadir el certificado para hacer esas operaciones con el movil.

Lo mejor es seguir las instrucciones oficiales teniendo MUY en cuenta los navegadores **y sus versiones** y los Sistemas Operativos

[Instrucciones Instalar certificados](https://www.sede.fnmt.gob.es/preguntas-frecuentes)

# Cl@ave Pin
La Cl@ve Pin es una identidad digital basada en el movil. En vez de un archivo descargable podemos utilizar un codigo recibido a nuestro movil via SMS para confirmar que somos nosotros (propietarios del movil) quienes estamos realizando la gestión.

## Solicitud de la Cl@ave Pin
Para poder disponer de Cl@ve Pin necesitaras dos cosas:
- Un movil (Android o iOS)
- Una dirección postal (residencia oficial) donde te enviarán un codigo de activación

Una vez activado siguiendo las [instrucciones oficiales](https://clave.gob.es/clave_Home/PIN24H/Obtencion-clave-pin.html) solo necesitaras tener a mano tu movil cada vez que quieras hacer una gestión con la administración.

## Instalación de la Cl@ve Pin

Puedes instalarte la aplicación Cl@ave en tu movil para recibir el codigo a traves de esta en vez de por SMS.
![5c_app.png](/informatica/smr/m6/5c_app.png){.align-center}

# Firmar documentos

Para poder firmar documentos (PDF, Word) debereis, ademas de tener el certificado, tener instalado un programa llamado **Autofirma**

Consulta [aqui la documentaciñon oficial](https://firmaelectronica.gob.es/Home/Descargas.html) para realizar su instalación.

Una vez instalado, el programa buscará los certificados instalados en tu equipo para que elijas con cual quieres firmar el documento
![autofirma.jpeg](/informatica/smr/m6/autofirma.jpeg){.align-center}

## Comprobar firmas
> Los documentos firmados con Autofirma se pueden validar y comprobar el autor de la firma en la web 
https://valide.redsara.es/valide/
{.is-info}


  # :pencil: Exercicis

1. [Crear identidad digital](crear-identidad-digital)
