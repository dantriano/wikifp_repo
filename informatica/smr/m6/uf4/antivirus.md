---
title: Malwares i antivirus
description: 
published: true
date: 2022-03-07T16:04:45.531Z
tags: 
editor: markdown
dateCreated: 2022-03-07T15:27:28.537Z
---

- :books: **Cicle Formatiu**: Sistemes Microinformatics i Xarxes
- :notebook_with_decorative_cover: **Modul**: M6 - Seguretat informatica
- :calendar: **Durada**: 12h
- :computer: **Material necessari**:PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
{.links-list}

# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRJvjg4kmxmzT2XySR0LrmehnWXf3dtT41Xk3g4uWewyUMuUf7sHsOAzOYvmFyzT70BauFxAhg-4AAh/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vRJvjg4kmxmzT2XySR0LrmehnWXf3dtT41Xk3g4uWewyUMuUf7sHsOAzOYvmFyzT70BauFxAhg-4AAh/pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts
## Malware
Son piezas de codigo que tienen como objetivo alterar el normal funcionamiento de un sistema informatico. 

Existen diferentes maneras de categorizar los malwares existentes (y cada  año se crean y mas peligroso tipos de malware)

Podemos clasificarlos por el tipo de alteración o daño que producen en el equipo:

- Interrupción: se produce cuando un recurso, herramienta o la propia red deja de estar disponible debido al ataque.

- Intercepción: se logra cuando un tercero accede a la información del ordenador o a la que se encuentra en tránsito por la red.

- Modificación: se trata de modificar la información sin autorización alguna. Aqui entraría por ejemplo el Ramsomware que codifica la información de los discos duros.

- Fabricación: se crean productos, tales como páginas web o tarjetas magnéticas falsas.

O tambien podemos utilizar la claseificación en función de su manera de propagarse por los diferentes sistemas

- Virus: se autocopia para propagarse utilizando la interacción del usuario hasta infectar todos los archivos del sistema.

- Troyanos: entran camuflado en un PC y al ejecutarse inician una rutina secundaria

- Gusanos: se autocopia como los virus pero estos utilizan subritanas  ejecutadas en la maquina para llevar a cabo su replicación.


## Antivirus

Un antivirus es un programa informático que intenta identificar, detener y
eliminar virus informáticos y otros tipos de software malicioso (malware).

Sus principales funciones son:

- Detectar (escanear) archivos en busca de malware por algunos de los métodos de detección.

- Suprimir: proceder a la eliminación del malware del sistema. A veces permite restaurar archivos dañados, sobretodo si son del sistema

Las tecnologías y tecnicas utilizadas por los antivirus para la eliminación de los malwares son:

- Detección basada en firmas: es el método más común. Analiza el fichero y lo compara contra una base de datos de virus conocidos. No es eficaz en malware desconocido.

- Detección heurística: analiza el fichero en busca de patrones que habitualmente se encuentran en los virus. Permite, a veces, detectar virus que aún no se han reportado. Por ejemplo consumo de recursos excesivos, aumento exponencial de su tamaño

- Detección basada en el comportamiento: analiza el comportamiento del ejecutable, detectando acciones sospechosas (borrado de ficheros, abertura de puertos, etc.)

- Detección en sandbox: ejecuta el programa sospechoso en un entorno virtual seguro, del cual no se puede salir, y realiza una detección basada en comportamiento.


## Analisis forense

En ocasiones los antivirus no pueden detectar ciertos malwares debido a que no los tienen en su base de datos.

> Las bases de datos de virus como **VirtusTotal** ayudan a que los antivirus se mantengan actualizados con los nuevos tipos de ataques, sus comportamiento y como erradicarlos
{.is-info}


![svchosts-virus_total.webp](/informatica/smr/m6/uf4/svchosts-virus_total.webp)

En estos casos es necesario utilizar herramientas de forense informatico que nos ayuden a analizar nuestro equipo de manera manual.

Es el caso de lor programas como Process Explorer, Process Monitor o Autoruns que nos permiten listar todos los procesos de nuestros equipo e información sobre ellos (firmas, comportamientos, etc)

![manual-malware-removal-step2.webp](/informatica/smr/m6/uf4/manual-malware-removal-step2.webp)

## Referencias

https://www.pcrisk.es/guias-de-desinfeccion/9184-svchost-exe-virus#a3

https://docs.microsoft.com/en-us/sysinternals/downloads/autoruns

https://dasmalwerk.eu/

https://protegermipc.net/2017/06/22/donde-descargar-virus-malware/

https://docs.microsoft.com/en-us/sysinternals/downloads/procmon

https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer

  # :pencil: Exercicis
  **:thought_balloon:Teorics**
  
1. [Infección y desinfección de un SO Windows](infectar-desinfectar-windows)


