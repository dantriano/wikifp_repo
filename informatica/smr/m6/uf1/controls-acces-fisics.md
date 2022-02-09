---
title: Controls d'acces fisics
description: 
published: true
date: 2021-10-09T19:22:24.012Z
tags: 
editor: markdown
dateCreated: 2021-08-25T21:47:48.618Z
---

- :notebook_with_decorative_cover: **Cicle/Modul**: Sistemes MicroInformatics / M6. Seguretat informatica
- :calendar: **Durada**: 4h
- :computer: **Material necessari**:PC - Projector
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###
- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}


# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTtHa-PTWSXBr6HLCP2oJ4ADdjJ4nRHjcJizSl_BLpjLTJdBIaMjJbmoK5D4eHb_GCMprlLpsWAxCfq/embed?start=false&loop=false&delayms=60000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Presentació](https://docs.google.com/presentation/d/e/2PACX-1vTtHa-PTWSXBr6HLCP2oJ4ADdjJ4nRHjcJizSl_BLpjLTJdBIaMjJbmoK5D4eHb_GCMprlLpsWAxCfq/pub?start=false&loop=false&delayms=60000)
# :orange_book: Apunts


## Control de acceso físico

Una de las mayores debilidades de los sistemas automatizados de control de acceso es el hecho de que la mayoría de los sistemas no pueden realmente controlar el número de personas que ingresan a las instalaciones luego de una autenticación positiva de credenciales de acceso, así como tampoco controlar el ingreso de dispositivos prohibidos, los cuales pueden ser transportados de forma encubierta. Ingresar de forma no autorizada o transportar dispositivos prohibidos son prácticas conocidas como “tailgating” o “piggybacking”.

**Tailgating**, se puede hacer de forma encubierta, donde el intruso espera cerca de la parte exterior de la puerta y entra rápidamente una vez que el empleado abandona la zona. Esta técnica se utiliza con mayor frecuencia durante los fines de semana y por las noches, en los que las acciones de un intruso pueden pasar desapercibidas. Pero también el tailgating puede hacerse abiertamente, donde el intruso se presenta al empleado y mediante técnicas de ingeniería social puede utilizar al personal para mantener la puerta abierta para él y permitirle el acceso.

**Piggybacking** es la técnica en la cual una persona (personal autorizado o intruso) ingresa a un área restringida objetos, equipos u otros dispositivos prohibidos.

Uno de las mejores soluciones para este tipo de prácticas es el uso del dispositivo conocido como **mantrap**.

**Mantrap** a veces llamados portales de seguridad, es esencialmente un pequeño ambiente diseñado con dos puertas que permite “atrapar” a los que desean ingresar a un área segura de una instalación. Este dispositivo mantrap permite verificar las credenciales de la persona, (ya sea mediante un sistema automatizado o un empleado) y, o bien permitir el acceso o activar alertas que indican un intento de entrada no autorizada.

La aplicación más simple de una mantrap implica dos puertas: uno conecta el interior del dispositivo mantrap a la zona segura, y otro que conecta a la zona no segura.

A continuación se indica un breve resumen de cómo funciona una versión automatizada de estos sistemas de seguridad, en este caso, se supone que se cuenta con equipos de autenticación en ambas puertas.

![mantrap.jpeg](/informatica/m6/mantrap.jpeg){.align-center}
<kbd>Imatge 01: Esquema d'una zona protegida amb un sistema Mantrap </kbd> {.text-center}

1. Una persona que desee acceder a un área segura presenta las credenciales necesarias en la puerta 1. Estas credenciales pueden incluir una tarjeta de acceso, PIN, biometría o alguna combinación de los mismos. En caso de una autenticación correcta, la puerta de la trampa 1 se desbloquea automáticamente, lo que permite la entrada al interior del mantrap.

2. La puerta 1 del mantrap a continuación se bloquea, evitando que otras personas entren en el mantrap. Un buen mantrap automática implementará algún sistema, o una combinación de los sistemas, para evitar que más de una persona pueda entrar a la vez. Si se detecta más de un individuo, se le niega el acceso y las alertas se disparan.

3. La persona al interior del mantrap, presenta las credenciales de seguridad a la puerta 2 (estos pueden ser los mismos que para la puerta 1 o diferente). Cuando se verifican estas credenciales, a la persona se le permite la entrada a la zona segura. Luego se procede a cerrar y bloquear la puerta 2.


# :pencil: Exercicis


## Teorics
