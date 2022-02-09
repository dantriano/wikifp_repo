---
title: PHP - Practica Galeria de Imagenes
description: 
published: true
date: 2021-10-05T10:04:54.853Z
tags: 
editor: markdown
dateCreated: 2021-10-05T09:32:59.469Z
---

El objetivo de esta práctica es crear una aplicación que permita mediante un formulario subir fotografias para ser mostradas posteriormente en una galeria de imagenes. Cada fotografia tendrá asignado un titulo que se mostrará debajo de la fotografía. Toda esta información, no se almacena en Base de Datos, sino en un archivo de texto que relaciona cada fotografia con su titulo. Este archivo deberá ser leido/escrito desde PHP.

### Tabset {.tabset}
  
####  Lista de fotos
Ejemplo del archivo `fotos.txt` donde almacenamos la ruta de la foto y su titulo. En este caso lo separamos por el simbolo ###
```
Clase con alumnos###pictures/teacher.png
Montaña Bonita###pictures/mountain.png
````

####  index.php
**Este archivo no ha de ser modificado.**
Muestra el menu principal con los dos botones:
- Añadir Foto
- Ver Galeria

Tendreis que añadir al proyecto todo lo necesario para que esta pagina pueda funcionar correctamente.
```php
<?php include_once('_header.php') ?>
<div class="card">
    <div class="card-body">
        <div class="bd-example">
            <a type="button" class="btn btn-primary" href="addPicture.php">Add picture</a>
            <a type="button" class="btn btn-success" href="gallery.php">View Gallery</a>
        </div>
    </div>
</div>
<?php include_once('_footer.php') ?>
````
Deberá mostrar los mensajes de exito o error cuando se ha realizado la operación de subir fotografia:

<div align="center" class="row justify-center">
  <div class="col-6">
  
![upload_success.png](/informatica/m6/upload_success.png){.align-center}

  </div>
  <div class="col-6">
    
![upload_error.png](/informatica/m6/upload_error.png){.align-center}

  </div>
</div>

#### uploadManager.php
En este archivo gestionaremos todo lo referente a la **subida de archivos** incluyendo la **gestión de errores** mediante excepciones y la escritura del archivo `fotos.txt` con la información del archivo subido (titulo,ruta)


 ```php
 /*
 * Función que se encarga de subir un archivo y moverlo a la carpeta /pictures 
 * que almacena todas las fotos.
 * Return: Devuelve la ruta final del archivo.
 */
function uploadPicture(){}

 /*
 * Función que se encarga de añadir al archivo fotos.txt el titulo y la ruta de la 
 * fotografía recien subida
 * Entradas: 
 *       $file_uploaded: La ruta del archivo 
 *       $title_uploaded: El titulo del archivo
 * Return: null
 */
function addPictureToFile($file_uploaded,$title_uploaded){}

/*
* Clase personalizada extendida de Exception que utilizaremos para lanzar errores
* en la subida de archivos. Por ejemplo:
* throw new UploadError("Error: Please select a valid file format.");
*/
class UploadError extends Exception{}
 ``` 

Una vez finalizada la subida del archivo (o lanzado un error) hay que **redirigir** al usuario a la pagina de home pasando por parametro el estado final de la operación (sucess o error):
- header("Location: index.php?upload=success");
- header('Location: index.php?upload=error&msg=' . urlencode($e->getMessage()));

> Este archivo puede estructurarse en forma de Class o mediante funciones
{.is-info}

####  Class/PictureClass.php
Clase que estructura los datos de las imagenes
```php
class Picture
{
	/*Constructor*/
	function __construct($title, $fileName){}

	/*
  *Getters. Lo que quiere decir que los atributos de 
  *title y filename son private
  */
	public function title(){}
	public function fileName(){}
}
````
####  Class/GalleryClass.php
Clase que estructura los datos de la galeria. Al cargar la galeria lo que estaremos haciendo es crear un array de tipo **Picture**

```php
class Gallery
{
	private $_gallery = [];
	
  /*Constructor: Recibe la ruta del archivo fotos.txt*/
	function __construct($fileName){}

	/*
  *Recorre el archivo fotos.txt y para cada linea, crea un 
  *elemento Picture que lo añade al atributo $_gallery[]
  */
	function loadGallery(){}

	/*
  *Getters.
  */
	public function getGallery(){}
}
````

####  addPicure.php
Pagina con el formulario para subir fotografia y su titulo

####  gallery.php
Pagina que muestra la galeria de fotografias obteniendolas gracias a la clase GalleryClass.php

### Ejemplo de la práctica
1. Menu principal

<div align="center" class="row justify-center">
  <div class="col-6">
    
![menu_gallery.png](/menu_gallery.png){.align-center}
 </div>
   </div>
2. Subir fotografias.
    <div align="center" class="row justify-center">
  <div class="col-6">
    
![upload_picture.png](/upload_picture.png){.align-center}
  </div>
       </div>
Una vez subida se ha de redirigir al usuario a la pagina principal donde se mostrará un mensaje de si se ha subido con exito o no:

<div align="center" class="row justify-center">
  <div class="col-6">
  
![upload_success.png](/informatica/m6/upload_success.png){.align-center}

  </div>
  <div class="col-6">
    
![upload_error.png](/informatica/m6/upload_error.png){.align-center}

  </div>
</div>

3. Ver galeria de fotos

<div align="center" class="row justify-center">
  <div class="col-8">
    
![gallery.png](/gallery.png){.align-center}
 </div>
  </div>
