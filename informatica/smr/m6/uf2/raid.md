---
title: RAID
description: 
published: true
date: 2021-11-29T14:12:57.020Z
tags: 
editor: markdown
dateCreated: 2021-11-22T13:38:38.997Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M6 - Seguretat informatica
- :calendar: **Durada**: 4h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRgotgZQ_cWpXEZksIZ2wdZYAyPxIiNtYqiFuIvO1IlUzABDLB5xbzLk_y2vkRTKeXEHjoL0PryTvgR/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vRgotgZQ_cWpXEZksIZ2wdZYAyPxIiNtYqiFuIvO1IlUzABDLB5xbzLk_y2vkRTKeXEHjoL0PryTvgR/pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts
La finalidad de un sistema RAID (**Redundant Array of Independent Disks** o «matriz de discos independientes redundantes») es la de proteger los datos en caso de que un disco duro falle, o en algunos casos tiene como función principal mejorar la velocidad de lectura de varios discos que conforman un único volumen. Existen diferentes tipos de raid, de los mas utilizados serían:

  * Volúmenes Seccionados (stripped) (RAID-0).
  * Volúmenes Reflejados (RAID-1).
  * Volúmenes Seccionados Tolerantes a Fallos (RAID-5).



> Leed el siguiente articulo donde explica la diferencia de cada una de estas variaciones
> 
> [RAID de discos duros](https://hardzone.es/tutoriales/montaje/raid-discos-duros/)
>[Calculadora RAID](http://www.raid-calculator.com/)
>[Qué hacer si falla un disco de RAID](http://macwinuxuarios.blogspot.com/2010/03/que-hago-si-falla-un-disco-en-mi-raid.html)
{.is-success}




# RAID en Windows


## Discos Básicos:
Un disco básico puede dividirse en una o más particiones.
Para utilizar una partición, hay que formatearla con un sistema de archivos y asignarle una unidad. La partición formateada se conoce como volumen básico.
Los discos básicos usan la MBR y tienen la limitación de que sólo se puede crear en ellos como máximo cuatro particiones primarias, con una unidad lógica cada una de ellas.

## Discos dinámicos:
Los discos dinámicos se dividen en volúmenes en lugar de particiones.
El volumen debe formatearse y hay que asignarle una unidad antes de utilizarlo. Al volumen formateado se denomina volumen dinámico.
Los volúmenes permiten mayor flexibilidad que las particiones, por ejemplo, se puede extender un volumen único en varios discos.
los cambios en los discos surten efecto en el sistema sin necesidad de reiniciar el equipo

![raid_windows.png](/informatica/smr/m6/raid_windows.png){.align-center}

## Tipos de volúmenes dinámicos
### Volúmenes Simples.:
Se trata de un volumen formado por una o varias porciones del mismo disco. Solo pueden crearse en discos dinámicos y se pueden reflejar. Los volúmenes simples son lo mas parecido a las particiones en los discos básicos.
Los volúmenes simples pueden extenderse si añadimos porciones del mismo disco o de otros discos, pero no se puede reducir su tamaño una vez extendido ni eliminar porciones que se añadieron, sólo se podrá eliminar el volumen completo. Un volumen simple puede extenderse por otros discos hasta ocupar un máximo de 32 discos dinámicos.

### Volúmenes Distribuidos:
Es la extensión de un volumen simple por más de un disco.
Se trata de un volumen formado por varias porciones de varios discos. Sólo pueden crearse en discos dinámicos y no soportan opciones de tolerancia a fallos.
Los volúmenes distribuidos se pueden extender añadiendo porciones del mismo disco. Al extender un volumen distribuido, ocurrirá igual que en los simples, que no se podrá desasignar espacio.



  # :pencil: Exercicis
  **:thought_balloon:Teorics**
  
1. [Questionari](questionari)
1. [Calcul de paritat del RAID5](paritat-raid5)

1. [Configuracio de RAID en un servidor de Backup](servidor-raid-y-backaup)
