---
title: PHP - Ejercicios formularios 2
description: 
published: true
date: 2021-09-29T15:31:22.632Z
tags: 
editor: markdown
dateCreated: 2021-09-29T10:18:46.211Z
---

**1. Crea un programa que mostrará una tabla con nombre de jugadores y los goles marcados en cada partido.**

Habrá un formulario inicial (futbol_01.php) en el que pregunta el numero de jugadores y de partidos. Una vez enviado saldrá una pantalla nueva (futbol_02.php) en la que haya los campos necesarios para introducir tanto el nombre como los goles de todos los jugadores/partidos indicados en el formulario inicial. Por ultimo, al enviar este formulario se creará una array multidimensional con toda esta información. Se deberá de recorrer este array de manera que el resultado por pantalla (futbol_03.php) sea una tabla parecida a esta

<div align="center" class="row justify-center">
  <div class="col-10">
    
![tabla-goles.png](/tabla-goles.png){.align-center}

</div>
</div>

**2. Crear una aplicació composta per 3 paginas PHP amb formularis que permeti ingresar el nom y preu d'una llista de productes.**

- Primera página (prod_list_01.php): Formulari on s'ingresa el numero de productes
<div align="center" class="row justify-center">
  <div class="col-6">
  
   ![num_products.png](/num_products.png){.align-center}

  </div>
</div>

- Segona página(prod_list_02.php): Formulari on s'ingresa el nom y el preu de tots els productes
<div align="center" class="row justify-center">
  <div class="col-6">
  
   ![insert_products.png](/insert_products.png){.align-center}
  
  </div>
</div>

- Tercera página(prod_list_03.php): Taula on llista tots els productes. Si algun producte no s'ha introduit ni nom ni preu ha de apareixer la frase "Product not inserted"
<div align="center" class="row justify-center">
  <div class="col-6">
  
![list_products.png](/list_products.png){.align-center}
    
  </div>
</div>
