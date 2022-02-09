---
title: API
description: 
published: true
date: 2022-01-31T12:52:41.612Z
tags: 
editor: markdown
dateCreated: 2022-01-25T13:50:03.331Z
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
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSH9VtTsZIJR82wR_tgJH8VWtjuoOlbxeYXbUjhs1wMtJDkVt2eThW6uOEdQXV_-3Lgflprz00dt2Qw/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vSH9VtTsZIJR82wR_tgJH8VWtjuoOlbxeYXbUjhs1wMtJDkVt2eThW6uOEdQXV_-3Lgflprz00dt2Qw/pub?start=false&loop=false)

# :orange_book: Apunts

Por sus siglas en inglés, Application Programming Interface (Interfaz de programación de aplicaciones), es un conjunto de reglas, métodos, especificaciones y formalidades técnicas contenidas en librerías de desarrollo que dictan cómo se comunica un módulo de software con otro. 

> Una API es un puente de intercambio de información entre programas, servicios digitales o partes de estos.  
{.is-info}


## TERMINOLOGÍA Y CONCEPTOS FUNDAMENTALES

Para el desarrollo y utilización de las API se requiere conocer los siguientes términos y conceptos:

- **Recursos:** son los datos remotos que consultaremos a través de las API.
- **Colecciones:** conjuntos de recursos clasificados y organizados.
- **Endpoints:** son URLs definidas por las API que responden a las peticiones realizadas por la aplicación.
- **Peticiones:** son procedimientos definidos en un protocolo web de transmisión de datos para realizar operaciones con estos, como requerirles, enviarlos, modificarlos o crear nuevos.
- **Protocolo web:** especificación que establece las reglas de intercambio de datos. En el caso de las API remotas se utiliza el protocolo HTTP.
- **HTTP:** por sus siglas en inglés, Hypertext Transfer Protocol (protocolo de transferencia de hipertexto), se trata de un conjunto de métodos y reglas para llevar a cabo la transferencia de datos a través de internet. Todo lo que conocemos como la web funciona dentro del marco de este protocolo.


Las API generalmente utilizan los métodos HTTP para manejar los recursos remotos conectándose al endpoint correspondiente. Los más utilizados son GET, POST, PUT y DELETE.

- **GET** solicita el recurso o la colección de recursos al servidor remoto. 
- **POST** envía datos al servidor y le solicita que cree una nueva entrada remota con estos. Generalmente se utiliza para manejar el envío de información escrita en formularios.
- **PUT** le indica al servidor que actualice determinado recurso o que lo cree en caso de que no exista.
- **DELETE** lleva a cabo el borrado de un recurso remoto.

Algunos de estos métodos devuelven códigos de estado HTTP que dan el parte del resultado: 

- Códigos 2xx (Operación exitosa)
- Códigos 3xx (Redirección)
- Códigos 4xx (Errores en el cliente)
- Códigos 5xx (Errores en el servidor)

Una API también define el **formato** de los datos que se van a transmitir a través de ella. Entre los más populares están **XML** (eXtensible Markup Language) y **JSON** (JavaScript Object Notation)  

https://www.academiaweb.ca/que-es-una-api/


