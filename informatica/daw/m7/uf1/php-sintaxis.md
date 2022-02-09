---
title: PHP - Sintaxis
description: 
published: true
date: 2021-09-29T16:37:41.651Z
tags: 
editor: markdown
dateCreated: 2021-09-27T10:58:01.597Z
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
- [:clipboard: Resultats *Accedeix als resultats dels exercicis (Només professors)*](./resultats#uf1)
{.links-list}

# :cinema: Presentacions

<p align="center"><iframe src="https://www.loom.com/embed/d91bc26292af42aa8561e8cfbb2e7bc8" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreenframeborder="0" width="700" height="400" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

# :orange_book: Apunts

En este bloque daremos los primeros pasos para ver de que manera se construyen las sentencias mas básicas en PHP.

## Scripts

Una de las ventajas de PHP es que permite intercalar lenguaje PHP con HTML. Cuando queremos realizar alguna operacion de PHP lo que haremos será insertar un **script** en el codigo HTML.  

> Un servidor PHP puede leer archivo .html o .php, pero solo ejecutará scripts PHP en este utlimo. Si realizamos un script en un archivo con extension .html se mostrara en la página como texto plano.
{.is-info}


Los scripts de PHP siempre se basan en el mismo esquema. La etiqueta PHP de apertura **<?php** señaliza que se va a iniciar un entorno de scripts. A esto le sigue el propio código PHP en forma de órdenes o instrucciones y finaliza con el cierre **?>** Todas las sentencias finalizan con el **;**

### Tabset {.tabset}

####  :pencil2: Ejemplo
**Crea un script para mostrar la información del servidor que lo ejecuta:**

Crear un archivo con extension **.php**, por ejemplo  <kbd>info.php</kbd> en el que llamamos a una de las funciones diponibles en PHP que nos devuelve una pagina HTML con toda la información técnica del servidor.
#### :clipboard: Solución


 ```php
 <?php phpinfo(); ?>
 ``` 

Para poder visualizarla solo hay que ir a la URL del archivo creado http://localhost/info.php

## Salida por pantalla
Si lo que queremos es escribir una cadena de texto deberemos de utilizar la instrucción **echo** seguido de la cadena entre comillas **'** Esto es el texto **'**.

```php
<?php echo '<h1>Hello World</h1><p>Mi primer programa</p>'; ?>
```


> **Crea un script para muestre un texto de cabecera h1 y un parrafo por pantalla:**
> Cómo el resultado de la ejecución de los scripts será leido por un cliente web, podemos insertar etiquetas HTML dentro de las comillas para que el cliente las interprete.
{.is-info}




## Subcarpetas y URL


Los archivos que estan almacenados en servidor se puedes organizar por carpetas, pero en ese caso hay que tener en cuenta que la estructura de carpetas y subcarpetas queda reflejado en la URL a la hora de ejecutar los scripts.

![mvc-joomla.jpeg](/informatica/daw/m7/mvc-joomla.jpeg){.align-center}

> En la imagen anterior podemos imaginar que si la carpeta **joomla** es la raiz de mi aplicación web, deberemos de utilizar URLs que respeten esa estructura como por ejemplo: 
>
> http://localhost/components/com_ejemplo/ejemplo.php
> http://localhost/components/views/views1/view.html.php
{.is-warning}







## Variables
PHP permite la utlización de variables, las cuales nos darán gran capacidad de dinamismo y nos permitirán posteriormente hacer operaciones propias de cualquier lenguaje de prorgamación: condicionales, bucles, operaciones aritmeticas, etc.

Cada variable consta del símbolo del dólar(**$**), seguido del nombre de la variable. Las variables se utilizan en los scripts de PHP para integrar datos externos en páginas web. En este sentido se puede hablar de valores muy variados que van desde números simples y cadenas de caracteres hasta textos completos o estructuras de documentos HTML.  

**PHP diferencia entre siete tipos de variables:**
| Tipos de variables 	| Descripción 	| 
|---	|---|
| String  | Un string es una secuencia de caracteres, que puede tratarse de una palabra, de una frase, de un texto o de la totalidad del código HTML de una página web.                                                          |
| Integer             | Un integer es un número entero y sin decimales que puede ser positivo o negativo.                                                                                                                                      |
| Float               | Un float es un número de punto flotante, es decir, un valor numérico con decimales. En los lenguajes de programación, la coma se escribe con un punto (.). PHP permite colocar hasta 14 caracteres detrás de la coma.  |
| Boolean             | Las variables booleanas son el resultado de una operación lógica y solo comprenden dos constantes: TRUE (verdadero) y FALSE (falso). Este tipo de variables se aplica cuando se trabaja con condiciones.               |
| Array               | Un array es una variable que puede albergar varios elementos. Se trata de una agrupación de diversos datos estructurados formando una matriz.                                                                          |
| Object              | La variable object permite a los programadores definir tipos de datos propios y se aplica en la programación orientada a objetos. Las variables del tipo object no se incluyen en nuestro tutorial de PHP.             |
| NULL                | NULL representa una variable sin valor. Para las variables del tipo NULL, este es el único valor.                                                                                                                      |
> Los valores para las variables del tipo integer y float no se escriben entre comillas (p. ej., $ejemplo = 24; o $ejemplo = 2.7;)
{.is-info}

Ahora gracias a las variables podemos por ejemplo variar el contenido de la salida por pantalla en de manera dinamica.

### Tabset {.tabset}

####  :pencil2: Ejemplo
**Crea un saludo que cambie en función del nombre almacenado en una variable <kbd>$name</kbd>**
#### :clipboard: Solución

```php
<?php
$author = "John Doe";
echo "<h1>Hello World!</h1>
<p>This dynamic web page was created by $author.</p>";
?>
```
![vars-php.png](/informatica/daw/m7/vars-php.png){.align-center}



##  Concatenación

PHP al igual que otros lenguajes permite concatenar (unir) cadenas y variables. En este caso se utiliza el simbolo **.** y podemos unir tanto diferentes cadenas, como cadenas con variables. Siguiendo el ejemplo parecido al ejercicio anterior podemos escribir la siguiente concatenación:

```php
<?php
$author1 = "John Doe";
$author2 = "Max Mustermann";
echo '<h1>Hello World!</h1> 
<p>This dynamic web page was created by ' . $author1 . ' and ' . $author2 . '.</p>';
?>
```
> Fijaros que en el ejercicio anterior se utilizaban comillas dobles y en este simples. Porque? 
{.is-warning}


## Comentarios


Si se quiere destacar toda una línea como comentario y excluirla de la interpretación, se utilizará la almohadilla **(#)** o las dos barras **(/ /)**


Asimismo, también se pueden insertar comentarios que comprenden varias líneas. Para ello, se puede marcar el inicio de una sección con comentarios con una barra seguida de un asterisco(/*) y el final con un asterisco seguido de una barra (*/).

```php
<?php
/*
Esto no se ejecutará
*/
echo '<h1>Hello World!</h1>
<p>This is my first PHP page.</p>';
//Esta linea sera invisible en la ejecución
#Y esta tambien!
?>
```


## HTML+PHP



Como ya hemos mencionado podemos crear archivos .php que contengan tanto codigo HTML como PHP, esto es especialmente util para crear grandes cantidades de codigo HTML si necesidad de "enguarrar" el codigo con **echos**


```php
<h1>Esta cabecera no será ejecutada por PHP pero si aparecerá en mi WEB</h1>
<?php
$nombre="Pedro";
echo '<p>Hola'. $nombre .', esto si es ejecutado por PHP porque tu nombre cambia con cada usuario</p>';
?>
<p>Este parrafo en cambio, al no necesitar ningun tipo de operacion de computación lo escribo directamente</p>
```

> Los simbolos **<?php** y **?>** delimita el codigo ejecutable por PHP del que no. Ademas en las ultimas versiones de PHP se puede empezar por **<?** que es mucho mas corto ;)
{.is-info}

En el caso de instrucciones de control (IF, WHILE) PHP permite ejecutar el codigo HTML que existe entre las llaves, incluso si este está fuera de las etiquetas `<?php ?>` 

```php
//Ejemplo IF
<?php for($i=0;$i<10;i+++){?>

<p>Esta linea se escribirá 10 veces</p>

<?php } ?>

//Ejemplo WHILE
<?php 
$cont=0;
while($cont>0){?>

<p>Esta linea NUNCA se escribirá</p>

<?php } ?>
```


## Calculos aritmeticos

Hasta ahora hemos visto la utilización de las variables para concatenar sus valores con cadenas de texto. En este apartado veremos las posibilidades que tenemos de realizar operaciones matematicas, es decir cuando los valores de las variables sean enteros (int) o flotantes (float).
<note tip>En PHP no es necesario decirle de manera expresa si una variable contiene texto o numeros, todas las variables se declaran con el simbolo **$**. La diferencia es que las cadenas de texto van entre 'comillas' y los numeros, no. </note>

Como ocurre en otros lenguajes, se utiliza los parentesis para establecer la prioridad entre operaciones cuando existen varias en una misma sentencia.

**A continuación podemos ver el formato para realizar las posibles operaciones aritmeticas.**


| Operador aritmético    | Operación       | Resultado                                            |
|---|---|---|
| $numero1 + $numero2    | **Adición**         | Suma de $numero1 y $numero2                          |
| $numero1 - $numero2    | **Sustracción**     | Diferencia de $numero1 y $numero2                    |
| $numero1 * $numero2    | **Multiplicación**  | Producto de $numero1 y $numero2                      |
| $numero1 / $numero2    | **División**        | Cociente de $numero1 y $numero2                      |
| $numero1 * * $numero2  | **Exponenciación**  | Resultado de elevar $numero2 a la potencia $numero1  |

Como ocurre en otros lenguajes, se utiliza los parentesis para establecer la prioridad entre operaciones cuando existen varias en una misma sentencia.

### Tabset {.tabset}

####  :pencil2: Ejemplo
Haz un programa que realize en una misma sentencia un conjunto de diferentes operaciones aritmeticas utilizando tanto numero como valores almacenados en variables
#### :clipboard: Solución

```php
<?php
$numero1 = 2.5;
$numero2 = 3.7;
$resultado = 2 * ($numero1 + 5) * ($numero2 - 3) * sqrt(81);
echo "Resultado: " . $resultado; 
?>
```
![vars-php.png](/informatica/daw/m7/vars-php.png){.align-center}


Si nos fijamos vemos que **sqrt()** no forma parte de la lista de oepraciones aritmeticas en el cuadro, y esto es porque en realidad es una función incluida en PHP que devuelve como resultado la raiz cuadrada del numero dado.

# :pencil: Exercicis

  
1. [Sintaxis basica de PHP](php-sintaxis-basica)

