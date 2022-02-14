---
title: Instal·lació del servei LDAP
description: 
published: true
date: 2022-02-14T16:35:14.694Z
tags: 
editor: markdown
dateCreated: 2022-02-14T16:19:08.308Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M4 - Sistemes Operatius en Xarxa
- :calendar: **Durada**: 10h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/1OF6uOObEZp473v0hrHUMolfHzCF0S6KL/embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/1OF6uOObEZp473v0hrHUMolfHzCF0S6KL/pub?start=false&loop=false&delayms=60000)

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
## Què és LDAP?
LDAP correspon a les sigles de Lightweight Directory Access Protocol o Protocol d’Accés a Directoris Lleugers.
Podem entendre el sistema LDAP com una base de dades, tot i que la seva estructura i funcionament és molt distinta d’una convencional. L’estructura de LDAP està **optimitzada per a realitzar lectura**, però les funcions d’escriptura son lentes.

A l’LDAP la informació està **estructurada en forma d’arbre**. Aquest arbre s’anomena arbre d’informació del directori o DIT (Directory Information Tree).
| |
| :--:|
| ![Esquema d'arbre LDAP](/informatica/m04/esquemaarbreldap.png) |


| | |
| :-- | :--: |
| Tradicionalment, aquesta estructura ha reflectit límits geogràfics i organitzatius. A la part superior de l’arbre s’han representat els països, i a sota, els estats, les organitzacions , les unitats organitzatives, les persones, els ordinadors, les impressores, els documents o altres conceptes. | ![esquematradicionalldap.png](/informatica/m04/esquematradicionalldap.png) |
| L’arbre del directori també es pot estructurar en funció dels noms de domini d’Internet (DNS). Aquesta pràctica està cada vegada més estesa, ja que permet trobar un servidor LDAP realitzant una consulta DNS. Aquest tipus de representació és el més habitual a dia d’avui a l’hora d’implementar serveis de directori per administrar dominis informàtics. | ![esquemaactualldap.png](/informatica/m04/esquemaactualldap.png) |

## Elements de l'LDAP
- **Arrel**: és l’equivalent al que coneixiem com a **domini**. El seu nomenament serà del tipus example.com. No obstant, estarà separat de la següent manera als formats de LDAP: dc=example,dc=com
- **Unitats Organitzatives**: Al igual que a windows server, utilitzem les UO per organitzar la informació. La diferència, aquesta vegada el sistema si utilitza l’estructura de UO per l’**organització de l'arbre** (BDD).
- **Objectes**: Són les **puntes *finals* o *fulles* de l'arbre**, tot i que poden tenir subtipus. Contenen la informació de cadascun dels elements. Són semblants als objectes que s’utilitzen a programació. Contenen els atributs característics de l'objecte.
- **Entrada**: Cada node (*fulla*) de l’arbre s’anomena entrada. Una entrada és una **col·lecció d’atributs identificada per un nom distintiu** (distinguished name o DN). Aquest DN és únic al directori i fa referència a l’entrada de manera unívoca (de la mateixa manera que un identificador caracteritza de manera unívoca un registre en una base de dades relacional).
Aquest nom representa la **ruta des de la posició de l’entrada fins a l’arrel** de l’arbre (base, segons la nomenclatura LDAP). Com que se suposa que un directori es fa servir per emmagatzemar els objectes d’una organització determinada, la base serà la ubicació d’aquesta organització. Així, la base es converteix en el sufix de totes les entrades del directori.
- **Atributs**: **Les entrades estan formades per un conjunt d’atributs**. Cada atribut d’una entrada té un tipus i un valor (SINGLE-VALUE) o més (MULTI-VALUE, que és el comportament predeterminat). El tipus d’atribut té associat els valors permesos i el seu comportament a l’hora de fer comparacions, ordenacions o treballar amb subcadenes.
Els tipus són habitualment cadenes de text mnemòniques, com poden ser cn per fer referència a common name (nom comú), sn a surname (cognom) o mail a email address (adreça de correu electrònic).
La sintaxis dels valors dependrà del tipus de l’atribut, per exemple, l’atribut cn podria contenir el valor “Marc Freixas”, l’atribut mail podria contenir un valor com “mfreixas@example.com” i un atribut jpegPhoto contindria una imatge en format binari.

    - [ ] *Podeu trobar exemples i referències a l'apartat [ldapadd - estructura bàsica del fitxer](#ldapadd-estructura-bàsica-del-fitxer).*


# :pencil: Exercicis
  **:thought_balloon:Activitats**
  
1. [Arbre de domini LDAP](arbre-LDAP)
2. [PHPLDAPADMIN](php-ldap)
3. [Instal·lació del servei LDAP](install-LDAP)
  