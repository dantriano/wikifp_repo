---
title: PHP - Comunicación entre páginas
description: 
published: true
date: 2021-10-04T17:21:55.086Z
tags: 
editor: markdown
dateCreated: 2021-09-28T23:50:36.918Z
---

- :books: **Cicle Formatiu**: Desenvolupament d'Aplicacions Web
- :notebook_with_decorative_cover: **Modul 7**:  Desenvolupament web en entorns servidor
- :scroll:**UF1**: Programació web en entorn servidor
- :calendar: **Durada**: 2h
- :computer: **Material necessari**:PC, Server PHP, Server Web
- :busts_in_silhouette: **Agrupació**: Per treballar individualment

###

- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](sol)
{.links-list}

# :cinema: Presentacions

<p align="center"><iframe width="640" height="400" src="https://www.loom.com/embed/d8ae67e7eb824caeadfc8dd68df27bf1" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></p>

# :orange_book: Apunts

Hasta ahora hemos puesto en práctica sentencias de PHP que funcionaban en una sola pagina .php al ser cargada. Pero como usuarios de Internet sabemos que una aplicación web consta de una serie de paginas interconectadas entre si a traves de **hipervinculos** (http://web.com/pagina_1.php). En esta sección veremos como podemos traspasar informacióno entre las diferentes paginas que componen una aplicación web.

## Las superglobals $_GET y $_POST

PHP nos ofrece un conjunto de herramientas para llevar a cabo la transferencia de datos entre las paginas. Las mas importantes son las superglobales. Variables de tipo **array** que almacenan en cada una de sus posiciones la información que recibe una web al ser cargada. Esta información viaja a traves del protocolo HTTP y puede estar contenida tanto en la URL ($_GET) como de manera "invisible" ($_POST)

La **superglobal $_GET** representa un array de variables que se transfiere a un script PHP con ayuda de un URL.

Cuando construimos un hipervinculo para visitar una pagina de nuestra aplicación deberemos de establecer la ruta en la que se encuentra el archivo. Pero si ademas queremos enviarle cierta información deberemos añadir a dicha URL un "carro" de valores separados por el simbolo **$**

La **superglobal $_POST** viaja de manera "oculta" y permite enviar mas cantidad de información. Mientras que los datos que se transfieren mediante el método GET se entregan como parámetros URL (visible al usuario) y ademas esta limitado a un numero de caracteres, la transferencia de datos vía $_POST se realiza en el cuerpo de una petición HTTP. Esto permite a los desarrolladores transferir grandes cantidades de datos de un script a otro.

Ya que no está vinculado a la URL, la manera de transferir la información entre scripts serán los formularios escritos en HTML.

### Tabset {.tabset}

####  :pencil2: Ejemplo
**Crea una URL en la que pasemos el nombre y la edad del usuario actual y posteriormente recuperalo con las superglobales $_GET:**

www.ejemplo-blog.es/hola.php?name=Pedro&edad=18

#### :clipboard: Solución


Gracias a las superglobales no necesitamos recurrir a bases de datos para acceder a información, ya que esta está se almacena en la memoria del servidor PHP. Para poder acceder a ella utilizamos en este caso la **superglobal $_GET**. Al ser un array solo deberemos de acceder a la **key** con el nombre que le hayamos dado en la URL.

 ```php
 //hola.php
<?php
$variable1 = $_GET['name'];
$variable2 = $_GET['edad'];
echo "Hola " . $variable1 . " ahora mismo tienes " . $variable2 . "años!";
?>
 ``` 
Nos fijamos que el archivo que contiene este script es el de **hola.php**, aquel al cual se esta apuntando con el hipervinculo anterior.



## Los formularios
Como hemos dicho anteriormente los formularios nos sirven para traspasar datos entre diferentes scripts (o paginas) de nuestra aplicación. Para ello debemos tener en centa que cada uno de los atributos que acompañan a las etiquetas `<form>` y `<input>` tienen un uso especifico


| Etiqueta  | Atributo  | Utilidad     |                                           
  |---	|---|---|
  | form      | action    | Define el destino (pagina) a la que se envia la información                                                                                  |
| form      | method    | Define cual de las dos superglobales recibiran la información. Sus posibles valores son 'get' o 'post'                                       |
| input     | name      | Define la **key** con la que se guardará la información. Puede tomar cualquier valor de texto y no se puede repetir en el mismo formulario   |
| input     | value     | El valor que se enviará al script. Es opcional, ya que en la mayoría de casos el valor será introducido por el usuario en el campo de texto  |

### Tabset {.tabset}

####  :pencil2: Ejemplo
**Crea un formulario que envie a otra pagina los datos personales de una persona en formato POST. Escribe el codigo del script que recibe esta información para mostrarla en pantalla.**


#### :clipboard: Solución
En este caso deberemos escribir el script de dos paginas diferentes, la que envia la información y la que la recibe.

 ```html
 //envio.php
<form method="post" action="recibo.php" >
Por favor, envía la newsletter a: <br />
Tu nombre: <input type="text" name="nombre" /><br />
Tu apellido: <input type="text" name="apellido" /><br />
Tu correo electrónico: <input type="text" name="email" /><br />
<input type="hidden" name="tipo" value="VIP"/>
<input type="submit" value="Enviar formulario" />
</form>
 ``` 


 ```php
 //recibo.php
<?php
$nombre = $_POST["nombre"];
$apellido = $_POST["apellido"];
$email = $_POST["email"]; 
$tipo = $_POST["tipo"]; 
echo "Hola " . $nombre . " " . $apellido . ", <br /> 
Te has registrado con el siguiente correo electrónico: " . $email . ". <br/> Ademas eres un usuario ".$tipo;
?>
 ``` 

> Fijaros que el único campo que tiene **value** es el que es de tipo hidden, ya que estos campos son invisibles y no editables por los usuarios
{.is-warning}

## Paso de valores por array
Es posible utizar arrays para pasar varios valores utilizando un mismo nombre.
### Tabset {.tabset}

####  :pencil2: Ejemplo
**Crea un formulario que envie a otra pagina una lista de personas en formato POST. Escribe el codigo del script que recibe esta información para mostrarla en pantalla.**


#### :clipboard: Solución
En este caso deberemos escribir el script de dos paginas diferentes, la que envia la información y la que la recibe.

 ```html
 //envio.php
<form method="post" action="recibo.php" >
Persona 1: <input type="text" name="nombre[]" /><br />
Persona 2: <input type="text" name="nombre[]" /><br />
Persona 3: <input type="text" name="nombre[]" /><br />
<input type="submit" value="Enviar formulario" />
</form>
 ``` 


 ```php
 //recibo.php
<?php
$nombres = $_POST["nombre"];
for($i=0;$i<size($nombres);$i++){
echo $nombres[$i]."<br />";
?>
 ``` 


# :pencil: Exercicis

  
1. [Ejercicios formularios I](php-ejercicios-formulario-1)
1. [Ejercicios formularios II](php-ejercicios-formulario-2)

