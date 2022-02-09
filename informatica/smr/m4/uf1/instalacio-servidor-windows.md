---
title: Instal·lació servidor Windows
description: 
published: true
date: 2022-02-09T14:38:43.689Z
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

## Xarxa informàtica

Una xarxa de computadors, també anomenada xarxa d'ordinadors o xarxa informàtica, és un **conjunt d'equips connectats** per mitjà de cables, senyals, ones o qualsevol altre mètode de transport de dades, que **comparteixen informació** (arxius), **recursos** (CD‐ROM, impressores, etc.) **i serveis** (accés a internet, e‐mail, xat, jocs, etc.).

Dintre d'aquestes xarxes d'ordinadors trobem l'estructura de servidor i client.
- **Servidors**: Centralitzen la gestió de la infraestructura així com els serveis.
- **Clients**: Es connecten al servidor per utilizar els recursos o accedir als serveis que ofereix.

## Elecció segons l'entorn

Durant l'elecció d'un nou servidor cal tenir en comptes diverses característiques de l'entorn on s'executarà. Aquestes característiques afectaran no sols al Sistema Operatiu (*S.O.*) sino també al hardware o situació física del servidor.
Les més importants a tenir en compte son les següents:
- **Nivell de seguretat**: segons les dades o els recursos que s'utilitzen caldrà tenir en compte en nivell de seguretat. Això afectarà no sols a polítiques de backups o contrasenyes, sino que també pot influir en la localització física de les màquines o el sistema operatiu a utilitzar.
- **Nombre d’usuaris**: És important tenir en compte per quants usuaris estem realitzant el disseny del directori actiu, així com també les tasques i recursos que aquests consumiran.
- **Nombre d’equips**: El nombre d'equips és important per calcular el nombre de connexions simultànees que pot tenir el nostre servidor. També igual que els usuaris, caldrà tenir en compte quines tasques realitzen a l'entorn. 
- **Ampliacions posteriors**: Cal tenir en compte si la nostra xarxa te intenció de crèixer, ja que el nostre servidor haurà de creixer en conseqüència.
- **Nivell d’interoperabilitat a la xarxa**: La interoperabilitat és la capacitat d'una xarxa o d'un sistema per treballar amb altres elements distints al seu propi, per exemple, serveis propis de linux amb servidors windows o clients linux amb un servei de windows. També podem trobar avui dia el fet dels entorns portables com tauletes o mòbils.

## Sistema d’arxius:
- **FAT (File Allocation Table)**: Aquest sistema detalla a través d’una taula a quins sectors es troba cada arxiu. FAT divideix el disc dur en blocs, el qual es limitat i deuen ser del mateix tamany. Normalment no s’utilitza a servidors ja que no permet gestionar privilegis o permisos d’accés en xarxa de forma segura.

- **NTFS (New Technology File System)**: Va ser desenvolupat especialment per a Windows Server. Ofereix mesures de seguretat extra per a l’accés en xarxa d’arxius i directoris. Es poden assignar privilegis de forma individual per a cada grup d’usuaris.

## Actualitzacions al servidor
Els servidors solen ser l’**objectiu d’atacs**. Pot haver passat temps des que hem adquirit el SO fins la seva instal·lació o que s’hagin trobat vulnerabilitats.
Per això és important mantenir actualitzat el sistema i fer-ho quan abans possible. És **important llegir cada actualització i com pot afectar a la configuració i funcionament**.
Abans d’aplicar una actualització cal assegurar-se que tot funciona correctament. Es recomanable tenir **equipaments de prova**, màquines virtuals, que ens permeten comprovar falles.


# :pencil: Exercicis
  **:thought_balloon:Activitats**
  
1. [Diferències client<->servidor](activitat1)
2. [Servei de xarxa](xarxa)
3. [Desactivar Windows Update](windows-update)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [Instal·lació Windows Server](install-win-server)
