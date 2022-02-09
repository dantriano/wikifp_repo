---
title: Ejercicios Politica Contrasenya
description: 
published: true
date: 2021-10-09T19:31:45.486Z
tags: 
editor: markdown
dateCreated: 2021-10-09T19:31:43.507Z
---

- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}

### Claves de usuario

1. Quines són les característiques recomanades per tal que una contrassenya sigui suficientment segura?
1. Utilitzant la web “passwordmeter.com”, genera una clau que tingui un percentatge de 100% i que sigui fàcil de recordar. Indica quina és la clau i còpia i enganxa els resultats obtinguts del web.
1. Ubuntu guarda la configuració dela política de claus al fitxer /etc/pam.d/common-password. Quina és la política mínima?
1. Quines diferències trobeu entre els paràmetres de configuració que permet Ubuntu i els que permet Windows XP?
1. Quin sentit té aplicar un màxim de longitud a lesclaus?
1. Creeu un usuari anomenat 'dummy' amb la clau que heu generat a la pregunta 2.
1. On guarda Fedorales claus del sistema? Fes-ne una breu descripció. Podem veure-les amb la comanda 'cat' de visualització de fitxers? Per què?
### Polítiques d’expiració de Claus
També podem aplicar polítiques d’expiració de Claus. És a dir, que forcem a l’usuari a renovar la clau cada cert temps. Amb la comanda chage, podem veure l’estat de les Claus d’un usuari:

1. Quina comanda ens permet veure l’estat d’expiració de la nostra clau?
1. Amb la comanda “sudo chage -l dummy” per exemple podem veure l'estat actual d'aquest compte d'usuari i entre les dades que sens mostra consta l'estat d'expiració de la seva clau, concretament a la línia “Password expires”, en aquest cas no expira mai. Mostra el resultat de la comanda anterior i explica què vol dir cada línia.
1. Amb quina comanda podem canviar la data d'expiració de la nostra clau ('dummy') de tal manera que compleixi els següents valors?
- Configuració 1: la clau expira cada 2 dies.
- Configuració 2: la clau expira cada 20 dies. Després de expirar si l’usuari no te activitat en 1 dia la compta es desactiva. A l’endemà l’usuari rebrà l’avís. Afegeixuna captura de pantalla per a cada configuració mostrant el llistat de configuración d’expiració de Claus. 
- Afegeix, també, una captura d’una clau caducada i de l’avís que envía al usuari.
4. Busca informació de com es pot fer les configuraciones del exercici anterior amb un SO Windows. Es poden aplicar politiques tan especifiques com a Linux? Com?
