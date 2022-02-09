---
title: Politiques de contrasenya
description: 
published: true
date: 2021-10-28T15:50:52.001Z
tags: 
editor: markdown
dateCreated: 2021-08-25T22:10:04.882Z
---

- :notebook_with_decorative_cover: **Cicle/Modul**: Sistemes MicroInformatics / M6. Seguretat informatica
- :calendar: **Durada**: 8h
- :computer: **Material necessari**:PC - Projector
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###
- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)

{.links-list}


# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTtHa-PTWSXBr6HLCP2oJ4ADdjJ4nRHjcJizSl_BLpjLTJdBIaMjJbmoK5D4eHb_GCMprlLpsWAxCfq/embed?start=false&loop=false&delayms=60000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Presentació](https://docs.google.com/presentation/d/e/2PACX-1vTtHa-PTWSXBr6HLCP2oJ4ADdjJ4nRHjcJizSl_BLpjLTJdBIaMjJbmoK5D4eHb_GCMprlLpsWAxCfq/pub?start=false&loop=false&delayms=60000)
# :orange_book: Apunts


## Contraseñas Robustas en Linux 

El control sobre la complexitat i xifratge de contrasenyes es fa mitjançant el servei PAM (Pluggable Authentication Module). Gràcies a PAM podem comunicar-nos amb les aplicacions a través dels mètodes d'autenticació que vulguem de forma transparent. Això ens permet integrar les utilitats d'un sistema Unix clàssic (login, ftp, telnet...) amb esquemes diferents del típic password com per exemple: claus d'un sol ús, lectors biomètrics, targetes inteligents... PAM ens ofereix una sèrie de mòduls instal·lables i configurables per a diferents finalitats, per exemple pam_cracklib, que serveix per determinar si una contrasenya creada o modificada amb la comanda passwd és suficientment forta. Per instalar-lo executarem:

```
sudo apt-get install libpam-cracklib
```

Una de les comandes d'assignació de contrasenyes a usuaris en sistemes GNU/Linux sol ser passwd. El seu arxiu de configuració es troba a **/etc/pam.d/passwd**. Aquest sòl fer referència a aquest altra **/etc/pam.d/common-password**. En aquest arxiu li podem indicar les característiques dels mòduls a utilitzar. En el nostre cas el pam_cracklib.so (per controlar la complexitat de les contrasenyes d'usuari) i pam_unix.so (preinstalat i el més usat per defecte)

Exemple de dues línies de configuració convencionals:
```
password requisite pam_cracklib.so dcredit=-1 ucredit=-1 lcredit=-1 minlen=1
password     [success=1 default=ignore]    pam_unix.so obscure sha512 remember=5
```

a) La **primera línia** inclou el mòdul de verificació cracklib, indica que la longitud mínima sigui 12 (minlen), i que ha de contenir dígits (dcredit), majúscules (ucredit) i minúscules (lcredit).

  * **minlen** Minlen es realmente una medida de la **complejidad**, no simplemente de longitud. Especifica una puntuación de complejidad que debe alcanzarse por una contraseña para ser considerado como aceptable. A la longitud se le suman los creditos conseguidos por el uso de ciertos caracteres. Por ejemplo, si especifica 10, el usuario deberá especificar como mínimo nueve caracteres en minúscula (con el crédito predeterminado de letras en minúscula de 1) para cumplir con los criterios de longitud mínima.
  * **dcredit** Especifica el crédito máximo para incluir dígitos en la contraseña. El valor predeterminado es un crédito; si especifica un crédito de 3, por ejemplo, el usuario recibirá un crédito por dígito hasta un máximo de tres créditos para reducir el requisito de minlen. Si especifica un valor negativo, como -2, los usuarios deberán especificar como mínimo dos dígitos en su contraseña.
  * **ucredit** Especifica el crédito máximo para incluir letras en mayúscula en la contraseña. El valor predeterminado es un crédito; si especifica un crédito de 2, por ejemplo, el usuario recibirá un crédito por letra en mayúscula hasta un máximo de dos créditos para reducir el requisito de minlen. Si especifica un valor negativo, como -1, los usuarios deberán especificar como mínimo una letra en mayúscula en su contraseña.
  * **lcredit** Especifica el crédito máximo para incluir letras en minúscula en la contraseña. El valor predeterminado es un crédito; si especifica un crédito de 2, por ejemplo, el usuario recibirá un crédito por letra en minúscula hasta un máximo de dos créditos para reducir el requisito de minlen. Si especifica un valor negativo, como -1, los usuarios deberán especificar como mínimo una letra en minúscula en su contraseña.
  * **ocredit** Especifica el crédito máximo para incluir caracteres no alfanuméricos (a menudos, referidos com símbolos, como #, & o *) en la contraseña. El valor predeterminado es un crédito; si especifica un crédito de 1, por ejemplo, el usuario recibirá un crédito por carácter no alfanumérico hasta un máximo de un crédito para reducir el requisito de minlen. Si especifica un valor negativo, como -2, los usuarios deberán especificar como mínimo dos caracteres alfanuméricos en su contraseña.
  * **difok ** Establece el número de caracteres que deben ser diferentes de los de la contraseña anterior

b) La **segona línia** l'argument Obscure realitza una mínima comprovació de la complexitat de la contrasenya: si aquesta és massa simple o una modificació fàcilment reproduïble a partir de l'anterior, mentre que sha512 defineix l'algoritme que es farà servir per guardar el hash en el fitxer shadow . Altres arguments interessants que podem afegir són remember un valor de 5, no permetrà la reutilització de les últimes cinc contrasenyes emmagatzemades en
<code>/etc/security/opasswd</code>

Podeis comprobar aqui cuanto costaria crackear una contraseña:
(howsecureismypassword.net)[https://howsecureismypassword.net/]

Pots generar una password segura amb:
(passwordmeter.com)[http://passwordmeter.com”]
## Llistes d'accés (ACL)

En linux, a mes dels permisos de carpetas que poden tenir unes aplicacions més limitades, tenim un sistema de **llistes d'access "Access Control List" (ACL)** que ens permet configurar tot l'arbre de directoris seguint unes llistes de acces. Aquest sistema s'utilitza quan el numero d'usuaris es elevat i necessitem fer moltes combinacions de permissos.

#### Activar ACL
Per tal de poder donar permisos concrets a un fitxer o directori cal activar les llistes d'accés (acl). Això es fa editant el fitxer <kbd>/etc/fstab</kbd>, tot afegint la comanda `acl` sobre la partició pertinent, **ja que cada partició EXT te la seva propia llista d'access**

```
#En aquest cas /home apunta a /dev/sda6. Compte amb el vostre cas!! 

UUID=563e6381-321b-4625-b348-b98afba842ff /home ext4 defaults,acl 0 2
```
Com podem observar només hem d'activar el flag **acl** a la linea de muntatge

> Abans de fer-ho (com a super-usuari), feu una còpia del fitxer amb la comanda 'cp /etc/fstab /etc/fstab.original', per si de cas!
{.is-warning}

Una vegada realitzat, cal tornar a muntar la partició, que en el nostre exemple és '/home':
```
mount /home -o remount
```
També cal comprovar que tenim disponibles les comandes que ens permetran definir permisos de manera granular: **setfacl**, **getfacl**. En cas contrari cal realitzar-ne la instal·lació:

```
apt-get install acl
```
#### Llistar ACL
Per observar la llista d'acces que s'esta aplicant en aquest moment podem utilitzar la comanda
```
getfacl [ruta de la carpeta]
```
Aquesta comanda mostrará la llista de tots els usuaris y grups del sistema indicant per a cada cas, quin tipus d'access te sobre aquella carpeta.

#### Modificar ACL
Per defecte només tindrem els permissos tipics de Linux **rxw, propietari, group, others**. Per aixó tenim aquesta comanda que ens permitirá ser mes especifics en funció de cada usuari.

Para lograr que un usuario en particular pueda acceder también a un directorio, se ejecuta setfacl, con la opción -m para modificar la lista de control de acceso, [u,g,o]:[usuario,grupo]:[r,w,x] y la ruta del directorio como argumentos.

```
setfacl -m u:user10:rX /home/user20
```
En l'exemple anterior afagirem permisos a user10 sobre la carpeta user20 permitit la seva lectura. Fixeu-vos que la X (execució) está en mayuscula, aixó indicará que es podrán abrir subcarpetes pero no permetrá l'execució d'arxius.

#### Mes informació d'ACL i exemples
Aqui teniu més informació sobre les comandes del ACL:
[https://www.alcancelibre.org/staticpages/index.php/uso-getfacl-getfacl](https://www.alcancelibre.org/staticpages/index.php/uso-getfacl-getfacl)

## Hackear Contraseñas

Dependiendo del SO existen diferentes maneras de poder hackear una contraseña y poder entrar en el sistema. La **fuerza bruta** consiste en descubrir la contraseña mediante la combinación (aleatoria o no) de todos los posibles caracteres hasta encontrar aquel que sea aceptado por el sistema.

Para evitar este tipo de ataque existen diferentes formulas: bloquear el sistema despues de varios intentos, pedir una segunda clave (factor de dos pasos) o hacer que el usuario tenga algún tipo de dispositivo físico (USB) o biometrico ademas de la clave. Pero el mejor sistema de todos es la utilización de **contraseñas robustas**.

### John The Ripper

Este es un programa que fuerza un sistema de fuerza bruta y que esta disponible para todos los S.O. Es facil de utilizar y nos ayudará a entender como funciona este sistema de hackeo.

#### Instalación

Podemos instalar John The Ripper como cualquier otro paquete de Linux:

<kbd>sudo apt install john</kbd>

Pero tenemos que tener presente que la versión 1.8 tiene limitadas algunas funcionalidades que son necesarias para hackear las contraseñas en las ultimas distribuciones de Linux. 

> Instalaremos la versión 1.9 o posterior de John The Ripper utilizando el gestor de paquetes SNAP
>
> [Instrucciones Instalación](https://snapcraft.io/install/john-the-ripper/raspbian)
{.is-info}

John The Ripper actua sobre el archivo de Linux en el que están las contraseñas `/etc/shadow` por lo tanto bastará con ejecutar:

<kbd>john /etc/shadow</kbd>

> Si nos sale el siguiente error es porque debemos de fusionar la lista de contraseñas con la lista de usuarios, que en algunas distribuciones de Linux están separadas. Esto lo podemos hacer con la aplicacion **unshadow** que nos proporciona John
>
> <kbd>/usr/sbin/unshadow /etc/passwd /etc/shadow > mypasswords</kbd>
{.is-warning}

La configuración básica de John solo permite hackear las contraseñas debiles. Es decir aquellas que tienen combinaciones sencillas de caracteres. Si el usuario ha introducido contraseñas más complejas, deberemos usar **diccionarios**.

#### Diccionarios y reglas

Un diccionario es un archivo con una lista de palabras que John utilizará para hacer combinaciones y aplicarlas como contraseñas. Cuando utilizamos un diccionario hay que especificar qué reglas utilizar con esas palabras. Si no ponemos reglas, probará las palabras del diccionario directamente, lo qual es bastante improbable que funcione.

Las **reglas** especifican como utilizar las palabras del diccionario. Gracias a ellas podemos ampliar la cantidad de combinaciones posibles. No podemos utilizar TODAS las reglas existentes porque sino darían como resultado para cada palabra del diccionario millones de combinaciones. Tenemos que afinar qué reglas utilizar.

Veamos un ejemplo de utilizar un diccionario con reglas. Primero creamos un archivo con la lista de palabras "candidatas": 

<kbd>lista.txt</kbd>
```
craig666
```

Iniciamos John aplicandole la lista de palabras 'lista.txt' con una regla que alterna las mayusculas 'Toggle':

<kbd>john --rules=Single --wordlist=passwords.txt --stdout</kbd>

> Nos fijamos que el comando anterior **NO** intenta hackear /etc/shadow, sino que simplemente mostrará por pantalla --stodout las combinaciones generadas del diccionario.
{.is-warning}

Obtendremos por pantalla el siguiente resultado. Si la contraseá es alguna de esas palabras, John conseguirá hackearla cuando la apliquemos al archivo /etc/shadow

```
Craig666
craig688
cRaig666
CRaig688
crAig666
CrAig688
CRaig666
cRaig688
cRAig666
CRAig688
CrAig666
crAig688
CRAig666
cRAig688
```
#### Ejemplos

La versión definitiva para hackear `/etc/shadow` sería:

```
/usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/mypass
john /tmp/mypass --rules=Single --wordlist=lista.txt
john /tmp/mypass --show 
```

[https://miloserdov.org/?p=5477](https://miloserdov.org/?p=5477)
[https://www.golinuxcloud.com/john-the-ripper-password-cracker/](https://www.golinuxcloud.com/john-the-ripper-password-cracker/)
[https://countuponsecurity.files.wordpress.com/2016/09/jtr-cheat-sheet.pdf](https://countuponsecurity.files.wordpress.com/2016/09/jtr-cheat-sheet.pdf)
[https://www.redeszone.net/tutoriales/seguridad/crackear-contrasenas-john-the-ripper/](https://www.redeszone.net/tutoriales/seguridad/crackear-contrasenas-john-the-ripper/)
[https://byte-mind.net/ataques-de-fuerza-bruta-con-john-the-ripper/](https://byte-mind.net/ataques-de-fuerza-bruta-con-john-the-ripper/)

# :pencil: Exercicis
  **:thought_balloon:Teorics**
  
1. [Politiques de contrasenya](ejercicios-politica-contrasenya)
1. [Permisos](ejercicios-permisos)
1. [Listas de acceso](ejercicios-llistes-acces)
  
  **:busts_in_silhouette:Pràctiques**
  
1.   [John the ripper](practica-john-ripper)
1.   [Contraseñas robustas en Ubuntu](practica-contrasenya-robusta)
1.   [Fuerza bruta y contraseña robusta](practica-fuerza-bruta-contrasenya-sobusta)

