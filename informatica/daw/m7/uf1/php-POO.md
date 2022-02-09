---
title: PHP - Programacion Orientada a Objeto
description: 
published: true
date: 2021-09-29T15:45:08.926Z
tags: 
editor: markdown
dateCreated: 2021-09-29T11:14:30.963Z
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

# :orange_book: Apunts


La **Programación Orientada a Objetos (POO)**  es cuando planteamos clases y definimos objetos de las mismas (Este es el objetivo del tutorial, aprender la metodología de programación orientada a objetos y la sintaxis particular de PHP 5 para la POO)


## POO

Una **clase** es un molde del que luego se pueden crear múltiples objetos, con similares características.

Un **objeto** es una entidad independiente con sus propios datos y programación. Las ventanas, menúes, carpetas de archivos pueden ser identificados como objetos; el motor de un auto también es considerado un objeto, en este caso, sus datos (atributos) describen sus características físicas y su programación (métodos) describen el funcionamiento interno y su interrelación con otras partes del automóvil (también objetos).

Debemos crear una **clase** antes de poder crear **objetos** (instancias) de esa clase. Al crear un objeto de una clase, se dice que se crea una instancia de la clase o un objeto propiamente dicho.

### Tabset {.tabset}

####  :pencil2: Ejemplo
**Implementa una clase llamada `Persona` que tendrá como atributo (variable) el nombre de una persona y dos métodos (funciones), uno de dichos métodos `inicializar()` definirá el atributo nombre y el otro método `imprimir()` mostrará en la página el contenido del mismo.**


#### :clipboard: Solución

```php
//persona.php
<?php
class Persona {
  private $nombre;
  public function inicializar($nom)
  {
    $this->nombre=$nom;
  }
  public function imprimir()
  {
    echo $this->nombre;
    echo '<br>';
  }
}

$per1=new Persona();
$per1->inicializar('Juan');
$per1->imprimir();
$per2=new Persona();
$per2->inicializar('Ana');
$per2->imprimir();
?>
```


###

Para más información, leer el siguiente enlace: 

[Tutorial Clases y Objetos](https://www.tutorialrepublic.com/php-tutorial/php-classes-and-objects.php)


## Atributos

Los atributos son las características, cualidades, propiedades distintivas de cada clase. Contienen información sobre el objeto. Determinan la apariencia, estado y demás particularidades de la clase. Varios objetos de una misma clase tendrán los mismos atributos pero con valores diferentes.

Cuando creamos un objeto de una clase determinada, los atributos declarados por la clase son localizadas en memoria y pueden ser modificados mediante los métodos.

Lo más conveniente es que los atributos sean privados para que solo los métodos de la clase puedan modificarlos.

## Metodos

Los **métodos** son como las funciones en los lenguajes estructurados, pero están definidos dentro de una clase y operan sobre los atributos de dicha clase. Para encontrar los métodos de una clase hay que preguntarse qué puede hacer la clase.

El objetivo de un método es ejecutar las actividades que tiene encomendada la clase a la cual pertenece.

> Los atributos de un objeto se modifican mediante llamadas a sus métodos.
{.is-info}

```php
<?php
class CabeceraPagina {
  private $titulo;
  private $ubicacion;
  public function inicializar($tit,$ubi)
  {
    $this->titulo=$tit;
    $this->ubicacion=$ubi;
  }
  public function graficar()
  {
    echo '<div style="font-size:40px;text-align:'.$this->ubicacion.'">';
    echo $this->titulo;
    echo '</div>';
  }
}

$cabecera=new CabeceraPagina();
$cabecera->inicializar('El blog del programador','center');
$cabecera->graficar();
?>
```

## Constructor

El constructor es un método especial de una clase. El objetivo fundamental del constructor es inicializar los atributos del objeto que creamos.

Básicamente el constructor remplaza al método inicializar que habíamos hecho en el concepto anterior.

Las ventajas de implementar un constructor en lugar del método inicializar son:

El constructor es el primer método que se ejecuta cuando se crea un objeto.
El constructor se llama automáticamente. Es decir es imposible de olvidarse llamarlo ya que se llamará automáticamente.
Quien utiliza POO (Programación Orientada a Objetos) conoce el objetivo de este método.
Otras características de los constructores son:

El constructor se ejecuta inmediatamente luego de crear un objeto y no puede ser llamado nuevamente.
Un constructor no puede retornar dato.
Un constructor puede recibir parámetros que se utilizan normalmente para inicializar atributos.
El constructor es un método opcional, de todos modos es muy común definirlo.
Veamos la sintaxis del constructor:

```php
  public function __construct([parámetros])
  {
    [algoritmo]
  }
```
Debemos definir un método llamado <code>__construct</code> (es decir utilizamos dos caracteres de subrayado y la palabra construct). El constructor debe ser un método público (public function).

Además hemos dicho que el constructor puede tener parámetros.


## Llamadas a metodos

Hasta ahora todos los problemas planteados hemos llamado a los métodos desde donde definimos un objeto de dicha clase, por:

```php
$cabecera=new CabeceraPagina('El blog del programador','center');
$cabecera->graficar();
```

Utilizamos la sintaxis:

`[nombre del objeto]->[nombre del método]`

Es decir antecedemos al nombre del método el nombre del objeto y el operador ->

Ahora bien que pasa si queremos llamar dentro de la clase a otro método que pertenece a la misma clase, la sintaxis es la siguiente:

```php
$this->[nombre del método]
```

Es importante tener en cuenta que esto solo se puede hacer cuando estamos dentro de la misma clase.

## Public/Private

Hasta ahora hemos dicho que los atributos conviene definirlos con el modificador private y los métodos los hemos estado haciendo a todos public.

Analizamos que implica disponer un atributo privado (private), en el concepto anterior definíamos dos atributos para almacenar la cantidad de filas y columnas en la clase Tabla:

 ` private $cantFilas; `
 ` private $cantColumnas;`
 
Al ser privados desde fuera de la clase no podemos modificarlos:

```php
$tabla1->cantFilas=20;
/*El resultado de ejecutar esta línea provoca el siguiente error:
Fatal error: Cannot access private property Tabla::$cantFilas*/
```

No olvidemos entonces que los atributos los modificamos llamando a un método de la clase que se encarga de inicializarlos (en la clase Tabla se inicializan en el constructor):

Ahora vamos a extender este concepto de modificador de acceso a los métodos de la clase. Veíamos hasta ahora que todos los métodos planteados de la clase han sido públicos. Pero en muchas situaciones conviene que haya métodos privados (private).

Un método privado (private) solo puede ser llamado desde otro método de la clase. No podemos llamar a un método privados desde donde definimos un objeto.

Con la definición de métodos privados se elimina la posibilidad de llamar a métodos por error.
```php
<?php
class Tabla {
  private $mat=array();
  private $cantFilas;
  private $cantColumnas;
  public function __construct($fi,$co)
  {
    $this->cantFilas=$fi;
    $this->cantColumnas=$co;
  }
  
  public function cargar($fila,$columna,$valor)
  {
    $this->mat[$fila][$columna]=$valor;
  }

  private function inicioTabla()
  {
    echo '<table border="1">';
  }

  private function inicioFila()
  {
    echo '<tr>';
  }
  
  private function mostrar($fi,$co)
  {
    echo '<td>'.$this->mat[$fi][$co].'</td>';
  }

  private function finFila()
  {
    echo '</tr>';
  }

  private function finTabla()
  {
    echo '</table>';
  }

  public function graficar()
  {
    $this->inicioTabla();
    for($f=1;$f<=$this->cantFilas;$f++)
    {
      $this->inicioFila();
      for($c=1;$c<=$this->cantColumnas;$c++)
      {
        $this->mostrar($f,$c);
      } 
      $this->finFila();
    }
    $this->finTabla();
  }
}

$tabla1=new Tabla(2,3);
$tabla1->cargar(1,1,"1");
$tabla1->cargar(1,2,"2");
$tabla1->cargar(1,3,"3");
$tabla1->cargar(2,1,"4");
$tabla1->cargar(2,2,"5");
$tabla1->cargar(2,3,"6");
$tabla1->graficar();
?>
```

Tenemos tres métodos públicos:

```php
public function __construct($fi,$co)
public function cargar($fila,$columna,$valor)
public function graficar()
```

Y cinco métodos privados:

```php
private function inicioTabla()
private function inicioFila()
private function mostrar($fi,$co)
private function finFila()
private function finTabla()
````
Tengamos en cuenta que cuando definimos un objeto de la clase Tabla solo podemos llamar a los métodos públicos. Cuando documentamos una clase debemos hacer mucho énfasis en la descripción de los métodos públicos, que serán en definitiva los que deben llamarse cuando definamos objetos de dicha clase.

Uno de los objetivos fundamentales de la POO es el encapsulamiento. El encapsulamiento es una técnica por el que se ocultan las características internas de una clase de todos aquellos elementos (atributos y métodos) que no tienen porque conocerla otros objetos. Gracias al modificador private podemos ocultar las características internas de nuestra clase.

Cuando uno planea una clase debe poner mucha atención cuales responsabilidades (métodos) deben ser públicas y cuales responsabilidades no queremos que las conozcan los demás.

# :pencil: Exercicis

  
1. [POO I](php-ejercicios-poo-1)
1. [Practicas POO I](php-practicas-poo-1)

