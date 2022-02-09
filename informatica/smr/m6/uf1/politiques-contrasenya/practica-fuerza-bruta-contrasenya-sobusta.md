---
title: Practica de Fuerza Bruta i Contrasenya Robusta en Linux
description: 
published: true
date: 2021-11-04T16:47:57.766Z
tags: 
editor: markdown
dateCreated: 2021-10-10T00:56:45.818Z
---



- :calendar: **Durada**: 2h
- :computer: **Material necessari**: Raspberry o PC amb SO compatible, programa John the Ripper
- :busts_in_silhouette: **Agrupació**: Per treballar en grup
- :notebook_with_decorative_cover: **Descripció**: En aquesta pràctica veurem com trobar les contrasenyes d'un equip per força bruta i com obligar a l'usuari a ficar contrasenyes segures.

### Objectiu
Heu d'aconseguir durant el temps establert a la pràctica, trobar els arxius "**secrets**" d'un usuari a un PC. A més heu de configurar l'equip perque no tingui aquesta falta de seguretat 

> Tots els passos han d'estar correctament documentats.
> {.is-warning}

![bruteforce.jpeg](/informatica/smr/m6/bruteforce.jpeg){.align-center}

### Preparació
Instal·lar la imatge del SO proporcionada.
SO Raspberry
[SO VirtualBox](https://drive.google.com/file/d/1I2qgZ5l4DGWg6e2kYX377j0dfrGaQ3pJ/view?usp=sharing)
ISARD: M6-Fedora

**Les dades del vostre usuari son:**
u: alumno
p: alumno

**Les dades del usuari amb la documentació secreta:**
u: profesor

Sabem d'aquest usuari que es un friqui de la mitologia Grega, potser aixó en ayuda a l'hora de saber la seva contrasenya.

Recordem algunes de les regles aplicables a les paraules de diccionari:
--rules:Single
--rules:Wordlist
--rules:Extra
--rules:Jumbo (all the above)
--rules:KoreLogic
--rules:All (all the above)

**El document secret:**
examen.doc

### Que hem de fer?
:pencil: Repte 1: Aconseguir l'arxiu "examen.doc" per força bruta. Quina era la password?
:pencil: Repte 2: Modificar la configuració del S.O. perque tots els usuaris hagin de ficar contrasenyes mes segures.
:pencil: Repte 3: Com a Hakers no hem de deixar rastre del nostre intent per hackear la contrasenya. 
Busca el lloc on s'ha deixat rastre de la nostra activitat.
S'ha enregistrat en els logs del Linux els nostres intents de força bruta? Perque?
