---
title: Instal·lació i gestió de serveis de domini
description: 
published: true
date: 2022-02-10T16:16:37.431Z
tags: 
editor: markdown
dateCreated: 2022-02-10T16:01:20.653Z
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
<p align="center"><iframe src="hhttps://docs.google.com/presentation/d/1xXbMROod92PrJZ6QodK5v6nWgO5zqVF5/embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/1xXbMROod92PrJZ6QodK5v6nWgO5zqVF5/pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts

## Conceptes
- **Domini**: Estructura fonamental. Permet agrupar els objectes que s’administren de forma estructural i jeràrquica.
- **Unitat organitzativa** (UO): És la unitat jeràrquica inferior al domini. Pot estar composada per diversos objectes o altres UO.
- **Grups**: Conjunts d’objectes del mateix tipus, que s’utilitzen per a l’assignació de drets d’accés als recursos. Normalment son usuaris.
- **Objectes**: Formen una representació d’un recurs de xarxa, poden ser usuaris, impressores, ordinadors, unitats d’allotjament...
- **Espai de noms**: El AD utilitza les nomenclatures del DNS per assignar els noms als dominis. Poden estar formats per 2 o + paraules separades per punts. Aquesta jerarquía és nomenada Espai de noms (max:67 Char i 127 lvl)
- **Resolució de Noms**: Domain Name Server (DNS) converteix els noms dels host en direccions IP i al contrari.
- **Controlador de domini**: És un Servidor Windows amb DA instal·lat. El servidor emmagatzema, manté i gestiona la base de dades d’usuaris i recursos de la xarxa.
- **Nom de domini**: Són les denominacions assignades als ordinadors de la xarxa. Per exemple, Cicles.es seria el domini arrel.
- **Arbre de domini**: És el conjunt de dominis formats pel nom de domini arrel i la resta de dominis contigus. CF1.edt.org o CF2.edt.org
- **Bosc d’arbres de dominis**: És el conjunt d’arbres de domini.

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
2. [Servei de xarxa](xarxa)
3. [Desactivar Windows Update](windows-update)
4. [Aturada Virtual Windows](/ca/informatica/smr/m4/uf1/maquines-virtuals/aturada)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [Instal·lació Windows Server](install-win-server)
