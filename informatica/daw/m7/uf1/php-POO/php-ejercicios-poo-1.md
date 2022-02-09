---
title: PHP - Ejercicios POO I
description: 
published: true
date: 2021-09-29T11:16:05.191Z
tags: 
editor: markdown
dateCreated: 2021-09-29T11:12:23.194Z
---

**1. Confeccionar una clase Empleado, definir como atributos su nombre y sueldo. Definir un método inicializar que lleguen como dato el nombre y sueldo. Plantear un segundo método que imprima el nombre y un mensaje si debe o no pagar impuestos (si el sueldo supera a 3000 paga impuestos)**

**2. Implementar una clase que muestre una lista de hipervínculos en forma horizontal (básicamente un menú de opciones)**

> //Metodo que añade un nuevo enlace al menu
> cargarOpcion()
> //Metodo que visualiza el menu en una pagina HTML
> mostrar()

<kbd>En este caso no hace falta formulario</kbd>

**3. Confeccionar una clase CabeceraPagina que permita mostrar un título, indicarle si queremos que aparezca centrado, a derecha o izquierda, además permitir definir el color de fondo y de la fuente. Todo esto son propiedades del objecto Titulo**

> //Establece los valores de los atributos
> inicializar()
> //Metodo que visualiza el menu en una pagina HTML
> mostrar()


**4Confeccionar una clase CabeceraPagina que permita mostrar un título, indicarle si queremos que aparezca centrado, a derecha o izquierda, además permitir definir el color de fondo y de la fuente. Pasar los valores que cargaran los atributos mediante un constructor.**

> //No utilizar metodo de inicializar
> //Metodo que visualiza el menu en una pagina HTML
> mostrar()

**5. Confeccionar una clase Tabla que permita indicarle en el constructor la cantidad de filas y columnas. Definir otro metodo que podamos cargar un dato en una determinada fila y columna además de definir su color de fuente y fondo. Finalmente debe mostrar los datos en una tabla HTML**

```php
<?php
class Tabla {
  private $mat=array();
  private $cantFilas;
  private $cantColumnas;
  public function __construct($fi,$co)
  {
    //Hacer esta funcion
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
    //Hacer esta funcion
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
````

**6. Confeccionar una clase Menu. Permitir añadir la cantidad de opciones que necesitemos. Mostrar el menú en forma horizontal o vertical, pasar a este método como parámetro el texto “horizontal” o “vertical”. El método mostrar debe llamar alguno de los dos métodos privados mostrarHorizontal() o mostrarVertical().**

```php
<?php
class Menu {
  private $enlaces=array();
  private $titulos=array();
  public function cargarOpcion($en,$tit)
  {
    $this->enlaces[]=$en;
    $this->titulos[]=$tit;
  }
  private function mostrarHorizontal()
  {
    //hacer esta funcion
  }
  private function mostrarVertical()
  {
    for($f=0;$f<count($this->enlaces);$f++)
    {
      echo '<a href="'.$this->enlaces[$f].'">'.$this->titulos[$f].'</a>';
      echo "<br>";
    }
  }
 
  public function mostrar($orientacion)
  {
    //hacer esta funcion
  }
}
 
$menu1=new Menu();
$menu1->cargarOpcion('http://www.lanacion.com.ar','La Nación');
$menu1->cargarOpcion('http://www.clarin.com.ar','El Clarín');
$menu1->cargarOpcion('http://www.lavoz.com.ar','La Voz del Interior');
$menu1->mostrar("horizontal");
echo '<br>';
$menu2=new Menu();
$menu2->cargarOpcion('http://www.google.com','Google');
$menu2->cargarOpcion('http://www.yahoo.com','Yhahoo');
$menu2->cargarOpcion('http://www.msn.com','MSN');
$menu2->mostrar("vertical");
?>
````

**7.Codificar la clase CabeceraDePagina que nos muestre un título alineado con un determinado color de fuente y fondo. Definir en el constructor parámetros predeterminados para los colores de fuente, fondo y el alineado del título.**

> //establece caracteristicas del menu
> __construct()
> //Muestra el menu
> graficar()
