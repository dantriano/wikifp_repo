---
title: PHP - Practicas POO I
description: 
published: true
date: 2021-10-06T16:04:42.536Z
tags: 
editor: markdown
dateCreated: 2021-09-29T15:45:05.959Z
---

**1. Crear una pagina que permite ingresar los datos de un alumno(`ficha_alumno.php`). Al enviar el formulario aparecerá en una nueva página (`ficha_alumno_view.php`)  todos los datos introducidos anteriormente, incluida la fotografía:**

- Nombre
- Apellido
- Fotografia (Upload file)
- Dirección
- Comentarios
- Lista Asignaturas Matriculadas (Checkbox)

> Para el alumno debereis de crear una objecto de la Clase Persona (`Persona.php`) que os ayude a gestionar sus datos.
{.is-warning}


### Tabset {.tabset}
  
####  Class/PersonaClass.php

Definieremos la clase que gestiona la información de cada persona

```php
class Persona
{
	
  /*
  * Setters. Para añadir y modificar valores
  */
  public function setName(){}
	public function setSurname(){}
	public function setPicture(){}
	public function setAddress(){}
  ....
  
	/*
  * Getters. Lo que quiere decir que los atributos de la clase son private
  */
	public function getName(){}
	public function getSurname(){}
	public function getPicture(){}
	public function getAddress(){}
  ....
}
````

> Tened especial cuidado con la visibilidad de los atributos, ya que solo podran ser accesibles mediante **getters** y **setters**
{.is-warning}

####  Class/UploadClass.php

Definieremos la clase que gestiona la subida de archivos

```php
class Upload
{
	/*
  * Constructor: Inicia la subida del archivo
  * Entrada: 
  * 	$name: Nombre del elemento del formulario del que gestionamos el $_FILE
  */
	function __construct($name){}
	
  /*
  * upload: Función que hace las operaciones necesarias para subir el archivo
  * al servidor
  */
  public function upload(){}
  
	/*
  * Getters. Lo que quiere decir que los atributos de la clase son private
  */
	public function getPath(){}
  

}
  /*
  * OPCIONAL:
  * Clase personalizada extendida de Exception que utilizaremos para lanzar errores
  * en la subida de archivos. Por ejemplo:
  * throw new UploadError("Error: Please select a valid file format.");
  */
  class UploadError extends Exception{}
````

####  ficha_alumno_view.php

En esta pagina gestionaremos la subida de archivos y despues cargaremos todas las personas subidas en el formulario anterior.

```php
include('Class/UploadClass.php');
include('Class/PersonaClass.php');

$upload = new Upload("foto");
//Imprimimos la ruta de la imagen subida
echo $upload->getPath();

$persona = new Persona();
$persona->setPicture($upload->getPath());
```
#
![upload_person.png](/informatica/daw/m7/upload_person.png){.align-center}![uploaded_person.png](/informatica/daw/m7/uploaded_person.png){.align-center}!

