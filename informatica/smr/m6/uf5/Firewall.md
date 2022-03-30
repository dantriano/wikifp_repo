---
title: Firewalls
description: 
published: true
date: 2022-03-30T12:10:55.076Z
tags: 
editor: markdown
dateCreated: 2022-03-30T12:10:55.076Z
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
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRmefvzaAI0JbxZjO2wH0HPUcS9aQQ3tcBMzb0UGA2NOcJomuSeE2Xki-1ZPZKZfP-9M2pe24rXxOOD/embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vRmefvzaAI0JbxZjO2wH0HPUcS9aQQ3tcBMzb0UGA2NOcJomuSeE2Xki-1ZPZKZfP-9M2pe24rXxOOD/pub?start=false&loop=false)

# :orange_book: Apunts

Un **cortafuegos** (o 'firewall') es un sistema tecnológico cuya misión es la de dar paso o prohibir conexiones entre equipos informáticos, en base a una serie de reglas preestablecidas.
## Reglas
  * Filtro según puerto: Se establece la posiblidad o no de filtrar todos los paquetes que se mueven a traves de puertos determinados. Por ejemplo, podemos permitir las conexiones FTP abriendo el puerto 21 y denegar conexiones SSH cerrando el 22.
  * Filtro por protocolo: Se puede (aparentemente) filtrar en función del protocolo del paquete que atraviese el firewall. Por ejemplo, permitir los paquetes ICMP (ping) pero denegar los paquetes HTTP (web).
  * Filtro por IP: Se puede filtrar los paquetes cuyo origen o destino sea una IP (pública o privada) determinada

## Tipo
**Físicos:** Pueden venir integrados en los routers o ser dispositivos independientes situados entre el punto de acceso a Internet y el switch que se encarga de distribuir la conexión entre los ordenadores de una misma intranet. Muy usados en instituciones y grandes empresas.


{{ :smx:m6:uf5:image.jpeg?nolink&600 |}}

**Lógicos:** La alternativa más usada por los usuarios de a pie; sólo protegen el ordenador en el que están instalados, y en muchos casos vienen integrados en el propio sistema operativo (como ocurre con las últimas versiones de Windows, Mac y Linux), sin que eso impida sustituirlos por cortafuegos de terceros.

{{ :smx:m6:uf5:captura_de_pantalla_2021-04-07_a_las_13.47.46.png?nolink&600 |}}

## Ubicación
**Cortafuegos de red**: Consiste en un elemento en la red que regula las conexiones
entre los diferentes segmentos de la red. Aparte de las posibles
conexiones hacia el cortafuegos mismo, la función principal que tiene
es filtrar el tráfico que pasa.

{{ :smx:m6:uf5:firewall.png?nolink&600 |}}

**Cortafuegos personales (o de sistema)**: instala como otra aplicación
del sistema y la función que tiene es filtrar el tráfico que se dirige,
tanto conexiones entrantes (conexiones que provienen de otros
sistemas) como conexiones salientes ( conexiones que se originan en
el mismo sistema), que pueden ser causadas por otras aplicaciones.

## Limitaciones

No protegen de errores de seguridad de los servicios a los que
permite el tráfico.
  * No protege de ataques entre equipos conectados en el mismo segmento que el tráfico no pasa por el cortafuegos.
  * Es posible encapsular tráfico dentro otros protocolos ( ICMP , DNS , etc.), lo que permite crear túneles que comunican dos extremos por medio de un cortafuegos, por lo tanto si se abre un puerto en el cortafuegos, no es posible asegurar que el
protocolo que a priori debería circular por este puerto sea, forzosamente, el protocolo que pasa en realidad. Para detectar esta situación, sería necesario inspeccionar los paquetes.
  
  # :pencil: Exercicis
  
1. [Firewalls](ejercicios-firewalls)
  
