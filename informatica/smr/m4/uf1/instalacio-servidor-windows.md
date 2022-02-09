---
title: Instal·lació servidor Windows
description: 
published: true
date: 2022-02-09T14:07:20.224Z
tags: 
editor: markdown
dateCreated: 2022-02-09T11:46:36.005Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M4 - Sistemes Operatius en Xarxa
- :calendar: **Durada**: 8h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/1qa_I7NfkmivkkdyP7MuP6aWkyItOsqNZ/embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/1qa_I7NfkmivkkdyP7MuP6aWkyItOsqNZ/pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts

## Seguridad pasiva y seguridad activa
La **seguridad pasiva** está formada por aquellas medidas de seguridad que se implantan para, una vez producido el incidente de seguridad, minimizar su repercusión y facilitar la recuperación del sistema
  * Alarmas de acceso no autorizado
  * Análisis de registros
  * Sistema de alimentación ininterrumpidos
  * Copias de seguridad de los datos
 
La **seguridad activa** comprende el conjunto de defensas o medidas cuyo objetivo es evitar o reducir los riesgos que amenazan al sistema.
  * Evitar el acceso a la información a usuarios no autorizados
  * Evitar la entrada de virus
  * Evitar leer mensajes ajenos mediante encriptación


## Caracteristicas de un sistema seguro 
Las características que determinan la seguridad de un sistema informático son:

**Integridad**: Asegura que los datos del sistema no han sido alterados ni cancelados por personas o entidades no autorizadas y que el contenido de los mensajes recibidos es el correcto

  * **Confidencialidad**: Proporciona protección contra la revelación deliberada o accidental de los datos en una comunicación
  * **Disponibilidad**: Permite que la información esté disponible cuando lo requieran las entidades autorizadas.
  * **Autenticación o identificación**: El sistema debe ser capaz de verificar que un usuario identificado que accede a un sistema es quien dice ser.
  * **No repudio o irrenunciabilidad**: Proporciona al sistema una serie de evidencias irrefutables del autor de un hecho. Consiste en no poder negar haber emitido una información que se emitió y de no poder negar la recepción cuando ha sido recibida.
<note important>Si alguna de estas características falla nuestro sistema se convierte en vulnerable a posibles ataques</note>
## Seguridad física y seguridad lógica 
Son tareas y mecanismos **físicos** cuyo objetivo es proteger al sistema y por tanto, indirectamente, a la información de peligros físicos.

  * **Respaldo de datos**: Guardar copias de seguridad de la información en lugares seguros.
  * **Dispositivos físicos de protección**: Pararrayos, detectores de humo, alarmas contra intrusos, sistemas de alimentación...

Son los mecanismo y herramientas de **seguridad lógica** los que tienen como objetivo proteger digitalmente la información.

  * **Antivirus**: Tienen la capacidad de evitar que entre sofware malicioso y de **eliminarlo** cuando un equpo ya ha sido infectado. Protege la integridad de la información.
  * **Analisis forenses**: Realizar la revision de la información de registro para identificar el alcance del daño y poder tomar medidas
  * **Desplegar la información perdida**: Restaurar las copias de seguridad o almacenada en discos secundarios.
  * **Realizar particiones de disco**: Guardar la información en particiones de disco diferentes a las del SO.
  
  # :pencil: Exercicis
  **:thought_balloon:Activitats**
  
1. [Diferències client<->servidor](activitat1)
2. [Servei de xarxa](xarxa)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [Instal·lació Windows Server](install-win-server)
1.   [Autentificación dos pasos](practica-autenticacion-dos-pasos)
