---
title: Registres d'incidencies
description: 
published: true
date: 2021-10-20T18:19:15.618Z
tags: 
editor: markdown
dateCreated: 2021-08-25T22:14:41.242Z
---

- :notebook_with_decorative_cover: **Cicle/Modul**: Sistemes MicroInformatics / M6. Seguretat informatica
- :calendar: **Durada**: 4h
- :computer: **Material necessari**:PC - Projector
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###
- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}


# :cinema: Presentacions

# :orange_book: Apunts

Consulta las siguientes paginas para ver al detalle cada uno de los registros de Linux donde aparecen los diferentes tipos de errores

[https://www.eurovps.com/blog/important-linux-log-files-you-must-be-monitoring/](https://www.eurovps.com/blog/important-linux-log-files-you-must-be-monitoring/)
[https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)
[https://geekland.eu/logs-en-linux/](https://geekland.eu/logs-en-linux/)
[https://stackify.com/linux-logs/](https://stackify.com/linux-logs/)

També s'enregistra l'activitat del usuari emmagatzemant les comandes executades per ell i que están a: `/home/USER_YOU_WANT_TO_VIEW/.bash_history`

# :pencil: Exercicis


1. Describe con tus palabras como funciona el comando journalctl

1. Muesta el registro de las actividades de tu partición de disco

1. Muesta el registro los intentos de login fallidos a tu máquna. (Prueba hacer un su root para forzar que haya algun intento fallido).

```
journalctl -q SYSLOG_FACILITY=10 SYSLOG_FACILITY=4
```

4. Ahora vamos a instalar el sistema visual de Gnome Logs. 
```
sudo dnf install gnome-logs
```
Contesta a las preguntas a continuación:


1. Si alguien intenta realizar un acceso con una contraseña erronea, en qué pestaña lo encontraremos? Haz una prueba con su root poniendo una password falsa. Puedes verlo en el registro?
1. Si tu tarjeta grafica empieza a tener un problema de memory overflow, en qué pestaña podriamos encontrarlo?
1. En la pestaña Aplicacion di cual ha sido el ultimo error registrado. Busca información de lo que puede significar.

> La próxima vez que se te congele el ordenador podrás mirar en el log qué lo ha provocado.
{.is-success}



