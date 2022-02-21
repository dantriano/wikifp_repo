---
title: Criptografia
description: 
published: true
date: 2022-02-21T14:25:02.902Z
tags: 
editor: markdown
dateCreated: 2022-02-21T14:23:45.526Z
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
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vS4G2t0KmhIKnoxemgfBWWc5x0BPb10FFvbO1vL7o2CaItJ0hjU5rG3RRWclatJf-C0J_RRte0cjb0H/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vS4G2t0KmhIKnoxemgfBWWc5x0BPb10FFvbO1vL7o2CaItJ0hjU5rG3RRWclatJf-C0J_RRte0cjb0H/pub?start=false&loop=false&delayms=60000)

# :orange_book: Apunts

## Criptografia Simetrica

La criptografía simétrica solo utiliza una clave para cifrar y descifrar el mensaje, que tiene que conocer el emisor y el receptor previamente y este es el punto débil del sistema, la comunicación de las claves entre ambos sujetos, ya que resulta más fácil interceptar una clave que se ha transmitido sin seguridad (diciéndola en alto, mandándola por correo electrónico u ordinario o haciendo una llamada telefónica).

![cripot_clave_secreta.jpeg](/informatica/smr/m6/cripot_clave_secreta.jpeg){.align-center}

Teóricamente debería de ser más fácil conocer la clave interceptándola que probándola una por una por fuerza bruta, teniendo en cuenta que la seguridad de un mensaje cifrado debe recaer sobre la clave y nunca sobre el algoritmo (por lo que sería una tarea eterna reventar la clave, como comenté en un ejemplo de ataque por fuerza bruta).

Y otro inconveniente que tiene este sistema es que si quieres tener un contenido totalmente confidencial con 10 personas tienes que aprenderte o apuntarte (siendo esta forma menos segura) las 10 claves para cada persona.


## Criptografia Asimetrica
También llamada criptografía de clave pública es el método criptográfico que usa un par de claves para el envío de mensajes. Las dos claves pertenecen a la misma persona que ha enviado el mensaje.

En este caso, cada usuario del sistema criptográfico ha de poseer una pareja de claves:

  * Clave privada: será custodiada por su propietario y no se dará a conocer a ningún otro.
  * Clave pública: será conocida por todos los usuarios.

Esta pareja de claves es complementaria: lo que cifra una SÓLO lo puede descifrar la otra y viceversa.

### Obtención de las claves
Estas claves se obtienen mediante métodos matemáticos complicados de forma que por razones de tiempo de cómputo, es imposible conocer una clave a partir de la otra.

Una clave privada o private key, es una clave secreta generada por el proceso de criptografía asimétrica. Un tipo de criptografía es el tipo ECDSA, usando la curva elíptica secp256k1. Este es un tipo especial de criptografía asimétrica, que nos brinda un alto nivel de seguridad.

Gracias al uso de este sistema criptográfico, se pueden generar un número casi infinito de claves privadas. De hecho, casi cualquier número de 256 bits es una clave privada válida. Es decir, con este sistema somos capaces de producir 2^256 combinaciones de claves distintas. Tantas que al ritmo de creación actual tardaríamos al menos 4 trillones de años en crearlas todas. Su diversidad y la dificultad de calcularlas es precisamente lo que hace tan seguro este sistema.

> Al ritmo de creación actual de claves tardaríamos al menos 4 trillones de años en crearlas todas
{.is-info}


## Mensajes cifrados con clave asimetrica===
Pongamos un ejemplo ilustrativo a lo largo de este documento para comprender mejor estos conceptos. Ana y Bob tienen sus pares de claves respectivas: una clave privada que sólo ha de conocer el propietario de la misma y una clave pública que está disponible para todos los usuarios del sistema.

![clave_simetrica.jpeg](/informatica/smr/m6/clave_simetrica.jpeg){.align-center}
Además, los métodos criptográficos garantizan que esta pareja de claves sólo se puede generar una vez, de modo que se puede asumir que no es posible que dos personas hayan obtenido casualmente la misma pareja de claves. Empleando dichas claves para la comunicación entre dos interlocutores:

  * Si el remitente usa la clave pública del destinatario para cifrar el mensaje, una vez cifrado, sólo la clave privada del destinatario podrá descifrar este mensaje, ya que es el único que la conoce. Por tanto se logra la confidencialidad del envío del mensaje, nadie salvo el destinatario puede descifrarlo.
  * Si el propietario del par de claves usa su clave privada para cifrar el mensaje, cualquiera puede descifrarlo utilizando su clave pública. En este caso se consigue por tanto la identificación y autentificación del remitente, ya que se sabe que sólo pudo haber sido él quien empleó su clave privada (salvo que alguien se la hubiese podido robar). Esta idea es el fundamento de la firma electrónica.

### Funcionamiento básico

![clave_simetrica_funcionamiento.jpeg](/informatica/smr/m6/clave_simetrica_funcionamiento.jpeg)

- Ana escribe un mensaje a Bob y quiere que sólo él pueda leerlo. Por esta razón lo cifra con la clave pública de Bernardo, accesible a todos los usuarios.
  - Se produce el envío del mensaje cifrado no siendo necesario el envío de la clave.
  - Sólo Bernardo puede descifrar el mensaje enviado por Ana ya que sólo él conoce la clave privada correspondiente.

Con este sistema conseguimos:

  * El beneficio obtenido consiste en la supresión de la necesidad del envío de la clave, siendo por lo tanto un sistema más seguro.
  * El inconveniente es la lentitud de la operación. Para solventar dicho inconveniente, el procedimiento que suele seguirse para realizar el cifrado de un mensaje es utilizar un algoritmo de clave pública junto a uno de clave simétrica.

### Algoritmo clave Pública junto con clave simétrica
El uso de claves asimétricas ralentiza el proceso de cifrado. Para solventar dicho inconveniente, el procedimiento que suele seguirse para realizar el cifrado de un mensaje es utilizar un algoritmo de clave pública junto a uno de clave simétrica. A continuación veremos cómo se produce el cifrado de un mensaje, mediante el cual obtenemos plena garantía de confidencialidad.

![clave_simetrica_sesion.jpeg](/informatica/smr/m6/clave_simetrica_sesion.jpeg){.align-center}
- Ana escribe un mensaje a Bob. Lo cifra con el sistema de criptografía de clave simétrica. La clave que utiliza se llama Clave de Sesión y se genera aleatoriamente.
  - Para enviar la Clave de Sesión de forma segura, esta se cifra con la clave pública de Bob, utilizando por lo tanto criptografía de clave asimétrica.
  - Envío de la Clave de Sesión y del mensaje, ambos cifrados, a Bob.
  - Bob recibe el mensaje cifrado con la clave de sesión y esta misma cifrada con su clave pública. Para realizar el proceso inverso (descifrado), en primer lugar Bob utiliza su clave privada para descifrar la Clave de Sesión.
  - Una vez ha obtenida la Clave de Sesión, utiliza esta para poder descifrar el mensaje.

Con este sistema conseguimos:

  * Confidencialidad: sólo podrá leer el mensaje el destinatario del mismo.
  * Integridad: el mensaje no podrá ser modificado.

Pero todavía quedan sin resolver los problemas de autenticación y de no repudio. Para ello, veremos el concepto de Firma Digital.


### Firma Digital
Una de las principales ventajas de la criptografía de clave pública es que ofrece un método para el desarrollo de firmas digitales. La firma digital permite al receptor de un mensaje verificar la autenticidad del origen de la información así como verificar que dicha información no ha sido modificada desde su generación. De este modo, la firma digital ofrece el soporte para la autenticación e integridad de los datos así como para el no repudio en origen, ya que el originador de un mensaje firmado digitalmente no puede argumentar que no lo es.

Una firma digital está destinada al mismo propósito que una manuscrita. Sin embargo, una firma manuscrita es sencilla de falsificar mientras que la digital es imposible mientras no se descubra la clave privada del firmante.

La firma digital se basa en la propiedad ya comentada sobre que un mensaje cifrado utilizando la clave privada de un usuario sólo puede ser descifrado utilizando la clave pública asociada. De tal manera, se tiene la seguridad de que el mensaje que ha podido descifrarse utilizando la clave pública sólo pudo cifrarse utilizando la clave privada. La firma digital, por tanto, es un cifrado del mensaje que se está firmando pero utilizando la clave privada en lugar de la pública.


![clave_simetrica_firma.png](/informatica/smr/m6/clave_simetrica_firma.png){.align-center}
### HASH

Sin embargo, ya se ha comentado el principal inconveniente de los algoritmos de clave pública: su lentitud que, además, crece con el tamaño del mensaje a cifrar. Para evitar éste problema, la firma digital hace uso de funciones hash. Una función hash es una operación que se realiza sobre un conjunto de datos de cualquier tamaño de tal forma que se obtiene como resultado otro conjunto de datos, en ocasiones denominado resumen de los datos originales, de tamaño fijo e independiente el tamaño original que, además, tiene la propiedad de estar asociado unívocamente a los datos iniciales, es decir, es prácticamente imposible encontrar dos mensajes distintos que tengan un resumen hash idéntico.


![clave_simetrica_hash.jpeg](/informatica/smr/m6/clave_simetrica_hash.jpeg)

### Claves privadas en Bitcoin
Una clave privada de 256 bits como las que se generan en Bitcoin, generalmente tiene la siguiente forma:

```
A5373D44C6D87DC0FA6A6738334369F4553213303DA61F20BD67FC233AA37485
```
Esta forma se explica por las siguientes reglas:

Una clave privada de 256 bits, está dividida en una secuencia de 64 caracteres.
El rango de los caracteres respeta la ordenación hexadecimal, con un rango que va de A-F y de 0-9.
Sin embargo, las claves bajo este formato son complejas de manejar para los usuarios. Es por ello, que para diversas tareas en Bitcoin, se ha creado un algoritmo para simplificarlas. Esto con el objetivo de ponerlas a buen resguardos, pues no olviden que son la llave para acceder a nuestro monedero. Este sistema creado por Bitcoin se llama; formato de importación Base 58.

Este formato de importación Base 58, no es más que un algoritmo especial que transforma nuestra clave privada, en una cadena criptográfica más corta y sencilla. Por ejemplo, de nuestra clave privada anteriormente dada, obtenemos:

```
C7w8CPTv25oeXXFPz3nnXCPQw7KPaCXHZD9DYWQ66TCg
```

Esta notación es la que más habitualmente vemos en Bitcoin como una clave privada. Se usa este formato, gracias a que incorpora una serie de elementos que ayudan a asegurar que el mismo es correcto, algo imposible con el formato original de clave privada. Adicionalmente, es más sencillo de manejar y su implementación en software, ayuda a mejorar los niveles de seguridad de los monederos.

Es precisamente este esquema de seguridad el que permite que el uso de las claves pública y privadas sea tan seguro. Y dado que las claves privadas son la llave que permite gastar los bitcoins, es imprescindible mantenerlas seguras. Las claves privadas pueden guardarse en archivos informáticos, pero al tratarse de simples números pueden también imprimirse en papel. Incluso muchos recomiendan cifrar en otro sistema las claves privadas, para agregar una capa más de seguridad.

Casos de uso de esta tecnología podemos verlo en el software PGP. Este sistema creado por Phil Zimmerman, permite utilizar criptografía asimétrica para enviar mensajes de forma segura. Otra variante muy conocida y utilizada es GPG desarrollado por Werner Koch, que utiliza el estándar OpenPGP.

El mismo sistema se utiliza también en las comunicaciones SSL/TLS de los sitios seguros de Internet. Prácticamente todo en Internet usa algún tipo de cifrado asimétrico, y ejemplo de ello este Academy

## Referencias

https://academy.bit2me.com/que-es-clave-privada/

https://securit.blog/criptografia/criptografia-asimetrica-clave-privada-y-clave-publica/

https://www.genbeta.com/desarrollo/tipos-de-criptografia-simetrica-asimetrica-e-hibrida


  # :pencil: Exercicis
  **:thought_balloon:Teorics**
  
1. [Conexión a servidor con clave publica/privada](practica-clave-publica-privada)


