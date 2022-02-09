---
title: Ejercicios Permisos
description: 
published: true
date: 2021-10-09T19:33:00.311Z
tags: 
editor: markdown
dateCreated: 2021-10-09T19:32:58.373Z
---

- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}

### Permisos
1. Descriu els diferents nivells de protecció que podem establir en un ordinador, tot resumint el que es pot protegir en cada cas.
1. Entra a la BIOS del teu ordinador i descriu les opcions de protecció que permet. (per fer a casa)
1. Al Fedora edita el menú d'arranc ' Grub' per tal que es mostri durant 5 segons. Fes també que ens demani una clau d'accés, que ha de ser '1234'. Descriu els canvis que has realitzat per a cada opció. Comprova que funciona.
1. Afegiu al vostre sistema tres usuaris amb la comanda 'adduser'. Els tres usuaris han de dir-se **'a41' i 'a42' i 'a43'**. Indica les comandes que has fet servir en cada cas i comprova que pots accedir-hi. Per canviar d'usuari pots fer-ho amb la comanda `sudo su <usuari>`. Heu de tenir en compte que per tal que puguem canviar a usuari 'root' des de els nous usuaris cal editar el fitxer <kbd>/etc/sudoers</kbd> i afegir-hi una línia semblant a: `a41 ALL=(ALL) ALL`. Això és especific de Ubuntu, per motius de seguretat.
1. Indica els permisos de propietari, grup i altres que té la carpeta '/home/a41' de l'usuari que acabem de crear (és la carpeta personal de l'usuari).
1. Amb la comanda `groups <usuari>` podeu veure els grups als que pertany cada usuari. Indiqueu a quin grup pertany cada usuari que heu creat.
1. Amb el que s'ha vist fins ara, podríem fer que només l'usuari a42 tingués accés total (rwx) a la carpeta de l'usuari a41? Explica-ho amb detall.
