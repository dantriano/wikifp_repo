---
title: Ejercicios Llistes Acces
description: 
published: true
date: 2021-10-10T09:18:21.864Z
tags: 
editor: markdown
dateCreated: 2021-10-09T19:34:01.684Z
---

- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}


Ara fes:

1. Fent ús de la comanda getfacl, indica la comanda i el resultat per al directori a41. Comproveu que amb l'usuari a42 podeu entrar al directori a41, però no podeu crear-hi ni fitxers ni directoris (mkdir prova).
1. Utilitzant la comanda setfacl, afegiu permisos d'escriptura per a l'usuari a42 a la carpeta a41. Indiqueu la comanda que heu fet servir.
1. Aquest és un exemple per tal de donar permisos de lectura i execució a l'usuari 'fernando' sobre el fitxer 'prova':
```
setfacl -m user:fernando:r-x prova
```
Comproveu els canvis que s'han produït als permiso del directori a41 amb la comanda 'getfacl' respecte als obtinguts a la pregunta 9.

