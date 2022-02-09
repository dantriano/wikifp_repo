---
title: Servidor Backup amb RAID
description: 
published: true
date: 2021-12-15T20:26:44.288Z
tags: 
editor: markdown
dateCreated: 2021-11-29T14:12:53.330Z
---



- :calendar: **Durada**: 6h
- :computer: **Material necessari**:PC amb SO compatible
- :busts_in_silhouette: **Agrupació**: Per treballar en grup
- :notebook_with_decorative_cover: **Descripció**: Configuració d'un servidor de Backups amb rdiff i RAID

### Objectiu
Heu de configurar un servidor per realitzar Backups amb rdiff i configurant els disc durs amb el RAID més adient justificant les vostres decisions i documentant tot el process.

El servidor ha de poder realitzar conexió al teu PC personal per realitzar el backup.

> Tots els passos han d'estar correctament documentats.
> {.is-warning}

![raid-nas.png.wdthumb.1280.1280.webp](/informatica/smr/m6/raid-nas.png.wdthumb.1280.1280.webp){.align-center}

### Preparació
Busqueu la documentació necessaria per configurar el RAID i el servei de rdiff

Instala les eines necessaries per fer el RAID "mdadm"
Instala rdiff en el sistema Linux del servidor

### RAID

Escull una configuració de RAID i aplica-la als disc durs que tens disponibles al servidor. Explica per que has escullit aquella configuració.

### Backup
 
Defineix i explica les politica de backup: quan i de quins arxius farás els backups justificant la teva resposta, tenint en compte la capacitat que tens per emmagatzemar les dades. **Cada membre del grup fará els backups del seu PC**

Configura el rdiff i el Cron per realitzar les copies de seguretat seguint aquests parametres.
 - S'ha de fer una copia completa cada dia a les 19h
 - S'ha de fer una copia diferencial cada hora
 - S'han d'eliminar les copies de seguretat que tinguin una antigitat major a 3 dies.
 - Analitza els backups i explica qué pots explicar sobre ells: Son tots backups complets? Están comprimits? Hi han mes arxius apart dels que hi havia al PC original?
 
>  Per comprovar que funciona prova de canviar el rellotge del sistema
{.is-warning}

>  Si utilitzeu el CRON no podreu introduir les contrasenyes necessaries per fer el SSH. Només es podrá fer amb les public key del PC. Si no ho sabem fer, no cal comprovar el funcionament del cron, pero si de les sentencies per separat.
{.is-danger}

### Opcional: Administrador de Backups web
Podeu instalar un gestor de Backups basat en web per poder visualitzar les copies que s'han realitzar i fer operacions de restauracions de forma intuitiva i sençilla. Per fer això hey d'instalar el paquet Rdiffweb i configurar-lo:

https://www.ochobitshacenunbyte.com/2020/10/20/copias-de-seguridad-en-linux-con-rdiffweb-y-rdiff-backup/


:pencil2: Creat per Dan Triano {.text-right}