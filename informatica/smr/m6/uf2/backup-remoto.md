---
title: Backups en Red (NAS)
description: 
published: true
date: 2021-11-11T16:45:24.513Z
tags: 
editor: markdown
dateCreated: 2021-11-11T12:57:33.963Z
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
<p align="center"><iframe src="" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir]()

# :orange_book: Apunts

Siguiendo el sentido común, lo ideal sería almacenar la información de backup en una maquina diferente al origen de los datos. La mejor manera de conseguir esto es transfiriendo los datos a traves de la red a un dispositivo externo. Para esto, existe un dispositivo que está especialmente diseñado para la transferencia (lectura y escritura) de datos de manera optima a traves de los protocoles de red, los dispositivos de **almacenamiento conectado en red**, Network Attached Storag **(NAS)**

Estos dispositivos tienen un conjunto de bahía en las que se conectan los discos duros en los que se almacenará la información y un sistema operativo propio optimizado especialmente su acometido.

![nas0.jpeg](/informatica/smr/m6/nas0.jpeg){.align-center}

A continuación veremos dos de los servicios que podemos utilizar para realizar copias y sincronización de datos de manera remota

# Rsync: Sincronización de datos  en red 
Rsync es un programa de **sincronización** de archivos, es decir, funciona a nivel de archivo así que al haber modificaciones copia todo el archivo no sólo lo diferente. Sirve para crear una imagen exacta del contenido en un dispositivo remoto (o en otra ubicación en local)

> Rsync funciona a nivel de archivo (lo copia todo si hay modificaciones).
{.is-info}


Tiene multitud de opciones, tanto en local como entre diferentes servidores. Por lo tanto
dispone de dos modos de funcionamiento básicos:
## Rsync Local
Rsync funciona como una herramienta de copiado normal entre el origen y destino
locales que se indiquen. En este modo, rsync copia la totalidad de archivos, al entender
que es más rápido copiar la información completa que calcular las diferencias que
puede haber entre origen y destino. Esto se aplica igualmente cuando nuestras rutas
locales son puntos de montaje por red.

## Rsync Remoto
Para usar rsync remoto es necesario que, además de tenerlo en el origen, esté
instalado en el equipo remoto.

  * Rsync como demonio: Rsync realizará las transferencias utilizando el puerto TCP/873. El demonio RSYNC puede ser ejecutado de forma independiente o mediante la utilización de inetd.
  * Rsync en una shell remota: Rsync utilizará una shell remota como ssh o rsh para ejecutar rsync una vez se haya iniciado sesión en el equipo remoto.


## ¿Cómo funciona Rsync?
La sintaxis de rsync es bastante sencilla:

````
rsync -opciones origen destino
````

En local, por ejemplo:

  ````
  cd /home/carmen/rsync
  rsync archivo1.txt archivo2.txt
  ````


![ejemplo_rsync.png](/informatica/smr/m6/ejemplo_rsync.png){.align-center}

Rsync también puede realizar transferencias de archivos entre diferentes hosts, siempre
que entre ellos tengan visibilidad usando red y utilizará por defecto el servicio SSH
como medio de transporte para mover los datos. Es importante saber que aunque
tengamos SSH instalado en ambos equipos, RSYNC es un paquete diferente por lo que
debemos asegurarnos de que rsync está instalado incluso aun teniendo un servidor ssh
funcionando.

````
rsync -e "ssh -p 1234" archivo1 usuario@host.dominio:/tmp/
````

## Ventajas de Rsync
**Rsync** nos proporciona una interesante lista de opciones que le hacen especialmente
adecuado para transferencias repetitivas (o puntuales)

  * Soporta el copiado de permisos de usuarios, grupos, así como enlaces y dispositivos
  * Dispone de opciones de exclusión similares a las de tar.
  * No necesita privilegios de root (salvo que sean necesarias para acceder a los orígenes o destinos)
  * Soporta la utilización de claves públicas para transferencias automatizadas.
  * Si utilizamos el transporte mediante SSH, nuestra transferencia es cifrada de forma automática, dándole mayor seguridad.

## ¿Qué transfiere Rsync?

Rsync realiza una comparación de tamaño y fecha de modificación antes de comenzar
a transferir un fichero. Si ambos son iguales, considera el archivo no-cambiado y lo
ignora. (Esto puede llevar a problemas si la aplicación que genera o modifica los
archivos mantiene siempre la misma fecha de modificación).
Si encuentra cambios en tamaño o fecha de modicación, rsync actúa diferente en caso
de funcionamiento local o remoto


## Rsync local con modificaciones
Pongamos que tenemos archivo1.txt y queremos hacer una copia. Si hacemos rsync
directamente lo copiará entero porque en el destino no existe. Pero si añadimos algo,
aunque sea un carácter, también lo copiará todo. ¿Por qué? Porque es más rápido
copiarlo todo al ver que ha sido modificado que mirar carácter por carácter a ver qué
parte ha sido modificada.

## Rsync Remoto con modificaciones
Utilizando el mismo ejemplo que en local copiamos el archivo en remoto y lo copia
entero porque no estaba anteriormente. Cambiamos un carácter y volvemos a usar
rsync en este caso sólo copiará una parte del archivo diferenciando de rsync en local.
¿Por qué? Porque intenta ahorrar ancho de banda y tiempo de transferencia copiando
sólo lo modificado. ¿Para qué va a usar el doble si sólo hemos modificado dos cosas?
 
| **Opción**  | **¿Qué hace?**         |
|-- | -- |
|  -r                     | Recursividad en el origen de la copia.\\ Copia todo de la ruta que le damos hacia\\ abajo.                                                                                                       |
|  -u                     | Modo actualización. Revisa y sólo se lleva\\ las partes de los archivos modificados (por\\ fecha o peso).                                                                                        |
|  -o -g                  | (-o owner -g group)\\ Transfiere la propiedad de los archivos pero\\ con el UID. Si el UID de origen difiere del\\ de destino habrá un problema, por ejemplo,\\ dándole permisos a otro usuario  |
|  -p                     | -p Transfiere los permisos del archivo.                                                                                                                                                          |
|  t                      | Conserva las fechas de modificación de los\\ archivos                                                                                                                                            |
|  -l                     | Conserva los enlaces simbólicos, existan\\ en el destino o no.                                                                                                                                   |
|  --remove-source-files  | Elimina los archivos de origen una vez\\ copiados.                                                                                                                                               |
|  --delete               | Borra los archivos del destino que no estén\\ en origen para tener una copia exacta.                                                                                                             |
|  -z                     | Comprime los archivos durante la\\ transferencia.                                                                                                                                                |
|  --progress             | Informará del avance de la transferencia.                                                                                                                                                        |
|  -e                     | Permite especificar opciones que usaremos\\ en la shell remota. Por ejemplo al usar ssh:\\ **-e “ssh -p 1234” -otras-opciones\\ origen destino**                                                 |
|  -W                     | Activa la copia completa de los archivos,\\ para no dedicar tiempo a calcular los\\ diferenciales.                                                                                               |
|  -a                     | Modo archivado: recursivo, copia enlaces,\\ mantiene los permisos, la fecha de\\ modificación, la información de grupos,\\ propietarios y los archivos de dispositivos.                          |
|  --exclude='pattern     | Excluye los archivos y directorios que\\ obedecen el patrón.                                                                                                                                     |
|  --include='pattern'    | Incluye los archivos y directorios que\\ obedecen el patrón.                                                                                                                                     |
|  --max-size=size        | Excluye todos los archivos que superen el\\ límite superior.                                                                                                                                     |
|  --min-size=size        | Excluye todos los archivos y ficheros que\\ no lleguen al límite inferior.                                                                                                                       |
|  --bwlimit=kpbs         | Límite del ancho de banda en kilo bytes por\\ segundo.                                                                                                                                           |
|  --dry-run              | Hace una prueba de cómo iría todo sin\\ copiar nada (ideal para pruebas                                                                                                                          |
|  --stats                | Muestra estadísticas de la transferencia de\\ los archivos                                                                                                                                       |
|  --progress             | Indica el progreso de la operación de copia |


# Rdiff-backup: Backup diferencial en red


**rdiff-backup** es capaz de realizar una copia casi exacta del directorio origen,
preservando toda la información de los recursos: permisos, usuarios y grupos, fecha de
modificación, enlaces simbólicos, ficheros fifos, etc., manteniéndola
independientemente de la plataforma y sistema de ficheros donde se almacene, gracias
a que toda esa información se guarda en ficheros independientes de metadatos.
Además seremos capaces de recuperar una foto exacta de un determinado día,
restaurando el estado que en ese momento tenía nuestro directorio (fichero eliminados,
modificados, etc..).

Otra característica importante es la eficiencia del espacio usado. Los backups
incrementales que utilizan herramientas como backup-manager, realizan una copia
completa de los recursos modificados, en cambio, rdiff-backup sólo almacena las
fracciones de datos que realmente han cambiado.
El backup de recursos remotos es otro de sus puntos fuertes y que considero
importante destacar. La transferencia de recursos remotos esta optimizada; sólo se
transfiere por la red la información que realmente ha cambiado, haciendo un uso
eficiente del ancho de banda. El único requisito es que en la máquina remota también
se encuentre instalado rdiff-backup.

## ¿Cómo funciona rdiff-backup?
La sintaxis de rdiff-backup es de la forma:
````
rdiff-backup origen destino
````


![ejemplo_rdiff.png](/informatica/smr/m6/ejemplo_rdiff.png){.align-center}

Vemos que además de la carpeta con el archivo que tenía dentro en el origen ha creado
otra llamada rdiff-backup-data con los archivos que guarda directamente al hacer cada backup:

![rdiff_result.png](/informatica/smr/m6/rdiff_result.png){.align-center}

- Directorio origen local y destino local
  ````
  rdiff-backup /home/carmen/rdiff/origen /home/carmen/rdiff/destino
  ````

- Directorio origen remoto y destino local

  ````
   rdiff-backup root@portatil::/etc /mnt/backup/etc
  ````
 
- Directorio origen local y destino remoto

  ````
  rdiff-backup /etc root@portatil::/mnt/backup/etc
  ````
  
 A continuación vemos un ejemplo de directorio destino donde se guardan no solo los archivos que se hacen backups sino todos los metadatos, logs y modificaciones (incrementales) que ha sufrido desde que se hizo el primer backup (total):
 
![rdiff-meta.png](/informatica/smr/m6/rdiff-meta.png){.align-center}
  
## Restaurando ficheros
Podremos utilizar los comandos cp o rdiff-backup. La posibilidad de utilizar cp existe
porque rdiff-backup no comprime o realiza un procesamiento especial de los ficheros
origen, sino que mantiene la misma estructura y permisos de la original.

Aunque podamos usar cp lo recomendable es utilizar rdiff-backup porque nos aporta
muchas más posibilidades de restauración que cp.

El proceso de restauración es muy similar al de backup; únicamente tendremos que
añadir la opción -r (restore-as-of) junto con la marca de tiempo a restaurar, el directorio
donde se encuentra el backup y el directorio donde queremos que se restaure.

El formato de la marca de tiempo es bastante potente; podremos indicar por ejemplo
que nos restaure la copia de hoy usando la palabra “now”, restaurar la copia de hace 10
días usando “10D” o incluso indicarle los minutos y segundos “5m4s”.


Por ejemplo, el siguiente comando restaura el directorio home de la copia realizada el
10 de Enero de 2010 en /tmp/home.

````
rdiff-backup -r 2010-01-10 /mnt/backup/home /tmp/home
````


Otro ejemplo, restauramos la copia actual situada en la máquina remota benji en el
directorio /temp.

````
rdiff-backup -r now backup@benji::/mnt/backup /temp
````

## Eliminando Backup antiguos
La opción –remove-older-than nos permitirá realizar este proceso. Al igual que la opción
de restauración, tendremos que indicarle una marca del tiempo a partir de la cual
borrará los backup incrementales.

Por ejemplo, si queremos eliminar de nuestro directorio de backup las versiones de los
ficheros con más de 2 semanas deberíamos ejecutar:


````
rdiff-backup –remove-older-than 2W /mnt/backup
````


## Filtrado de ficheros
Con include-globbing-filelist le indicamos a rdiff-backup el fichero que contiene el listado
de directorios que serán copiados. Debemos añadir una línea por cada patrón, pudiendo
tener los signos – y + que indican cuales serán eliminados o añadidos respectivamente.

Vamos a verlo con un ejemplo. Supongamos que queremos hacer un backup de los
directorios /etc, /opt y /home pero no queremos copiar ni los directorios .m2 ni nobackup
de los directorios de los usuarios. Lo primero nos creamos un fichero llamado
files_backup.txt con el siguiente contenido.

  ````
  /home/*/nobackup
  /home/*/.m2
  /etc
  /opt
  /home
  ````

Ejecutamos:
````
  rdiff-backup –include-globbing-filelist files_backup.txt / /mnt/backup
````

## Opciones 

- -l podremos obtener el listado con los cambios incrementales de un fichero:
  ````
  rdiff-backup -l /mnt/backup/file
  ````

- –list-changed-since podremos saber cuántos ficheros han cambiado desde unamarca de tiempo en concreto. Por ejemplo con el siguiente comando estamos viendo que ficheros han cambiado en los últimos 10 días:
  ````
  rdiff-backup –list-changed-since 10D /mnt/backup/etc
  ````


- --list-at-time lista todos los ficheros que estuvieron presentes en un determinado momento. Esto incluye tanto fichero eliminados como aquellos que no han sido modificados.

- -r restaurar. Podemos añadir el tiempo, por ejemplo, para hacerlo desde el más reciente:
  ```` 
  rdiff-backup -r now
  ````

- O hace tres días:
  
  ````
  rdiff-backup -r 3D
  ````

Si no existe un backup en ese momento lo hará con el de antes. Así que en este caso si
no hay uno de hace 3 días pero sí uno de hace 2 y otro de hace 4, cogerá el de 4
porque es el de ANTES del tiempo que le hemos dicho.

- -l listar las fechas y horas cuando fueron hechos los backups de una partición:

  ````
  rdiff-backup -l /media/sdb1/rdiff-backups/192.168.0.1/sda5
  ````


## Comparación

**Rsync** es a nivel de archivos por lo tanto si hay cambios -en el peso o en la fecha de
modificación- copiará todo el archivo al destino. Aunque tiene la opción de modificación,
si le añadimos -u sólo copiará las diferencias.

En cambio **rdiff-backup** es a nivel de bloques con lo que si hay cambios sólo copiará los
bloques con diferencias.

Esto, en ambos casos, tiene ventajas y desventajas.

Rsync usará mucho más ancho de banda y tiempo de transferencia porque al haber
modificaciones tiene que copiar todos los archivos. Pero rdiff ocupa mucha más CPU al
tener que comparar los archivos modificados para sólo copiar las diferencias con lo que,
al hacer esto, usará menos ancho de banda y tiempo de transferencia.

Así pues rdiff es más lento pero mantiene una versión histórica, comprimida en gzip
para no usar demasiado espacio, para poder recuperar una versión anterior si hay algún
cambio accidental.

En cuanto a opciones, rsync tiene muchísimas para poder hacer todo como queramos y
nos dé más libertad. En cambio rdiff tiene una lista corta de opciones ya que sus
programadores quisieron hacer algo potente y sencillo.

Ambos nos dan la opción de hacer copias de seguridad a nivel local y también en
remoto vía ssh. Para poder hacerlo los dos tienen que estar instalados tanto en el
origen como en el destino.

Si no estamos cómodos trabajando con estas herramientas en la terminal rsync tiene
varias versiones gráficas.


![rsync_grafica.png](/informatica/smr/m6/rsync_grafica.png){.align-center}

  # :pencil: Exercicis
  **:thought_balloon:Teorics**
  
1. [Seguridad Pasiva](ejercicios-seguridad-pasiva)
1. [Seguridad en CPD](ejercicios-seguridad-cpd)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [Llavero USB](practica-llavero-usb)
1.   [Autentificación dos pasos](practica-autenticacion-dos-pasos)
