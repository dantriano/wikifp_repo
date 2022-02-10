---
title: Creació d'elements de l'Active Directory
description: 
published: true
date: 2022-02-10T16:35:14.389Z
tags: 
editor: markdown
dateCreated: 2022-02-10T16:27:48.379Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M4 - Sistemes Operatius en Xarxa
- :calendar: **Durada**: 12h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/1PrIC6T45JNhdRQ4DfTV4s4YtsvNIgeMp//embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/1PrIC6T45JNhdRQ4DfTV4s4YtsvNIgeMp//pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts

## Conceptes
- **Grups de seguretat**:  S’utilitzen per simplificar la gestió sobre els permisos dels recursos de sistema.
- **Grups de distribució**: S’utilitzen quan volem instal·lar software des del controlador de domini.
- **Àmbit de grup**: L’àmbit d’un grup determina la visibilitat que te dins del domini, així com les característiques que poden concedir als objectes que conté.
- **Plantilles**: Son comptes d’usuari creades amb propietats per defecte que s’aplicaran als usuaris amb eixes necessitats.
- **Relació de confiança**: Les relacions de confiança serveixen per establir comunicació entre diferents dominis o boscos, amb la finalitat d’administrar des d’un sol punt de la xarxa tots els objectes i recursos existents.

## Directori i domini

- Als dominis s’emmagatzema de forma centralitzada la información administrativa i de seguretat.
- Windows server utilitza el concepte Directori Actiu (AD, Active Directory) per emmagatzemar i implementar aquesta configuració.
- El AD es un servei  de xarxa que desa a una base de dades tota la informació referent als recursos de xarxa i permet l'accés dels usuaris. Així es transforma en un model per organitzar, controlar i administrar de manera centralitzada l'accés als recursos de la xarxa.
- Quan instal·lem un AD a un equip amb Windows Server, el convertirem en un servidor o Controlador de domini.
- Els clients del domini tenen accés a la informació emmagatzemada en els controladors de domini (comptes d’usuari, grup, equip, etc.). El AD és, per tant, una eina fonamental d’administració per a tota l’estructura de l’empresa.
- Un dels avantatges del AD és separar l’estructura lògica de l’organització (dominis) de l’estructura física (topologia de xarxa).


# :pencil: Exercicis
  **:thought_balloon:Activitats**
  
1. [Activa el dns](activa-dns)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [Instal·lació del Direcoti Actiu a Windows Server](active-directory)
