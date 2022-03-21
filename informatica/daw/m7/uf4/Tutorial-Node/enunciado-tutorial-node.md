---
title: Enunciado Tutorial Node
description: 
published: true
date: 2022-03-21T16:37:47.039Z
tags: 
editor: markdown
dateCreated: 2022-03-21T16:37:47.039Z
---

1) Crear una pagina home (/) con un formulario:

````html
<form method="post" action="/mayor">
 <label for="name">¿Como te llamas?</label>
 <input type="text" name="name" id="name">   
 <label for="age">¿Qué edad tienes?</label>
 <input type="text" name="age" id="age">   
 <input type="submit" value="Enviar"/>
</form>
````

2) Crear una pagina (/edad) que reciba los datos y diga si el usuario es mayor de edad o menor.

3) Gestionar la petición desde un Controller llamado "User" y un metod llamado "isMayor"

4) Guardar en Mongo todas las peticiones de todos los usuarios (Su nombre y edad)