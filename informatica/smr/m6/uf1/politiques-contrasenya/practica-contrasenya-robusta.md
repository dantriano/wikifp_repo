---
title: Practica- Contrasenya Robusta
description: 
published: true
date: 2021-10-09T19:37:12.074Z
tags: 
editor: markdown
dateCreated: 2021-10-09T19:37:10.136Z
---

- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}
### Contraseña robusta


Configurad el Ubuntu para que solo pueda aceptar contraseñas robustas. Despues intentad crackear una contraseña siguiendo un patron de fortaleza alta. Los pasos a seguir son los siguientes:


1. Instaleu pam-cracklib i afegiu les lineas de exemple del punt anterior a l'arxiu common-password. Descriu que fan aquestes lineas.
1. Utilitzant la comanda passwd canvieu la contrasenya d'un usuari i comproveu que es compleixen les regles descrites.
1. Torna a modificar pam-cracklib per cumplor aquestes condicions:
- Longitud minima 7
- Al menos 2 mayusculas
- Almenos 4 digitos
- Si se escriben tres simbolos no-alfanumericos se acorta en un caracter la longitud minima
