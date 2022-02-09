---
title: Laravel
description: 
published: true
date: 2022-01-10T16:58:59.532Z
tags: 
editor: markdown
dateCreated: 2021-11-07T16:47:46.473Z
---

- :notebook_with_decorative_cover: **Cicle/Modul**: DAW / M7. Desenvolupament Entorn Servidor
- :calendar: **Durada**: 48h
- :computer: **Material necessari**:PC - Projector
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###
- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}


# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTy7xOxzKZB2ngJ9uGgNUHxEhKbG8M6QEdCgZW8j6aD3bgaa4PTHOj5C6RwpEG3oxw3gu6CpvTnIsrf/embed?start=false&loop=false&delayms=3000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vTy7xOxzKZB2ngJ9uGgNUHxEhKbG8M6QEdCgZW8j6aD3bgaa4PTHOj5C6RwpEG3oxw3gu6CpvTnIsrf/pub?start=false&loop=false&delayms=60000)
# :orange_book: Apunts


## Pildora 1: Instalación de Laravel


> **UPDATE 2021**
> A partir de las nuevas versiones Laravel 8.0 viene con su propio contenedor Docker (Sail)
> https://laravel.com/docs/8.x/installation
{.is-info}

La versión Laravel 8 incluye un contenedor con todos los servicios necesarios para ejecutar una plataforma Laravel: PHP, correo, Mysql, ServidorWeb, etc

![sail_1.png](/informatica/daw/m7/sail_1.png){.align-center}

Para pode utilizar las herramientas de Laravel: **artisan**, **migrate**, etc, debereis ejecutarla dentro de la maquina virtual **Sail** que se inicializa con docker.

![sail_2.png](/informatica/daw/m7/sail_2.png)

> A continuación están las instrucciones para Laravel 7 cuando no venian los servicios integrados.
{.is-danger}

Para poder ejecutar aplicaciones Laravel debemos preparar nuestro entorno con tres servicios:
  - Servidor Web
  - Base de Datos
  - Servidor PHP

Para facilitar el trabajo teneis disponible un docker con todos estos servicios ya instalados y preparado para funcionar en cualquier equipo con Docker instalado:

https://github.com/dantriano/docker-laravel-server

Instrucciones:

- [Instalación de Docker](https://www.youtube.com/watch?v=nhnHyHRdpfk)
- [Docker en nuestro proyecto Laravel](https://www.loom.com/share/cbd8a5cc4f5049bd84fb163cdadbb5bc)

Descargar, modificar la ruta de PROJECT_PATH en el archivo .env con tu carpeta de Laravel y compilar con:

<code>
docker-compose up -d 
</code>

Una vez iniciado el servicio podrás acceder a tu web desde http://localhost:80 

Si necesitas utilizar Artisan ejecutar desde la misma carpeta [docker-nginx-php-mysql]:

<code>
docker-compose exec app php artisan [command]
</code>



## Pildora 2: Composer & Artisan

Antes de entrar en la estructura de este framework es importante mencionar y explicar un par de herramientas que se incluyen en los poryectos de Laravel que nos permite crear y administrar los proyectos y sus dependencias.

### Composer 
<iframe width="560" height="315" src="https://www.youtube.com/embed/Oxvx02aPgAw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=Oxvx02aPgAw)

### Artisan

[Qués es Artisan](https://styde.net/artisan-interfaz-linea-comandos-de-laravel)

## Pildora 3: Estructura de un proyecto Laravel
<iframe width="560" height="315" src="https://www.youtube.com/embed/zCCOUwLQ4Rc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=zCCOUwLQ4Rc)


## Pildora 4: Rutas 
<iframe width="560" height="315" src="https://www.youtube.com/embed/2C0kBwLmqmY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=2C0kBwLmqmY)



## Pildora 5: Vistas
<iframe width="560" height="315" src="https://www.youtube.com/embed/cibjtqCWNio" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=cibjtqCWNio)



## Pildora 6: Plantillas de Blade
<iframe width="560" height="315" src="https://www.youtube.com/embed/brvk7mzy6_U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=brvk7mzy6_U)

[Manual de Blade](https://laravel.com/docs/master/blade)

## Pildora 7: Rutas y Vistas
<iframe width="560" height="315" src="https://www.loom.com/embed/e28ca672ac0845d78f3368b880568b63" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.loom.com/share/e28ca672ac0845d78f3368b880568b63)


## Pildora 8: Controllers
<iframe width="560" height="315" src="https://www.loom.com/embed/18e8da9d033f441c9b6e0e8d3ba0fdfa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.loom.com/share/18e8da9d033f441c9b6e0e8d3ba0fdfa)


## Pildora 9: DB Migrations & Seeds 
<iframe width="560" height="315" src="https://www.loom.com/embed/398463c5f40841e2b31128e52a1d44a6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.loom.com/share/398463c5f40841e2b31128e52a1d44a6)

[Documentación Migrations](https://laravel.com/docs/master/migrations)
## Pildora 10: Models 
<iframe width="560" height="315" src="https://www.loom.com/embed/278589e9a9bf48659bee9835ef522dcb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.loom.com/share/278589e9a9bf48659bee9835ef522dcb)



## Pildora 11: Validaciones de Formulario 
Para poder crear formularios en Laravel necesitamos varios elementos:

### Vistas con formularios 
Desde una vista se enviá un formulario a una dirección **action**:
```php
<form method="post" action={{ route('updateName',['id' => 5]) }} enctype="multipart/form-data">
{{ csrf_field() }}
  <label for="name">Name</label>
  <input id="name" type="text" name="name" value="" class="form-control">
  <input type="submit" value="Guardar" class="btn btn-primary">
</form>
```
### Rutas a las que enviar los datos

En las rutas definimos el controlador que se encargará de gestionar la información del usuario.
```php
Route::put('/user/{id}', [UserController::class, 'update'])->name('updateName');
```
### Controlador (y Request) que gestiona qué se hace con los datos

En el controlador podemos "captar" los datos del formulario mediante la clase **Request**, que pondremos como primer parametro del metodo que gestionará nuestra petición.

```php

namespace App\Http\Controllers;
use Illuminate\Http\Request;

class UserController extends Controller
{
    /**
     * Update the specified user.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  string  $id
     * @return \Illuminate\Http\Response
     */
    public function update(Request $request, $id)
    {
        $name = $request->input('name');
        return response('El nombre del usuario '.$id.' será:'. $name, 200);
    }
}
```

### FormRequest
El FormRequest es una "extensión" de la clase Request, que permite no solo obtener los datos sino hacerlos ademas pasar por una serie de validaciones
````
<?php

namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;
use Illuminate\Http\JsonResponse;

class ProductListRequest extends FormRequest
{
    /**
     * Determine if the user is authorized to make this request.
     *
     * @return bool
     */
    public function authorize()
    {
        return true;
    }

    /**
     * Get the validation rules that apply to the request.
     *
     * @return array
     */
    public function rules()
    {
        return [
            'name' => 'required|unique:products|max:255',
            'price' => 'required',
        ];
    }
    /**
     * Get the error messages for the defined validation rules.
     *
     * @return array
     */
    public function messages()
    {
        return [
            'name.required' => 'Por favor define un nombre para el producto',
            'name.unique' => 'Este producto ya existe en la base de datos',
            'name.max' => 'Este producto ya existe en la base de datos',
            'price.required' => 'El precio no puede estar vacio',
        ];
    }
  }
}
````
<iframe width="560" height="315" src="https://www.youtube.com/embed/hhgYB5NQlOs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=hhgYB5NQlOs)


<iframe width="560" height="315" src="https://www.youtube.com/embed/YSuk0wPrgww" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Abrir](https://www.youtube.com/watch?v=YSuk0wPrgww)

## Pildora 12: Sesiones

<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRHOxujQbBJfChTKy8LpWVhmmX8_991tmUJpRcmjeKN-nEf_lu7ofJRXoOMkQPzX2eQQ14I89skwL8D/embed?start=false&loop=false" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

[Abrir](https://docs.google.com/presentation/d/e/2PACX-1vRHOxujQbBJfChTKy8LpWVhmmX8_991tmUJpRcmjeKN-nEf_lu7ofJRXoOMkQPzX2eQQ14I89skwL8D/pub?start=false&loop=false&delayms=60000)

## Pildora 13: Bootstrap 

## Pildora 14: Middleware
Los middleware son funciones que son ejecutadas **antes** de llegar al controlador al que se está llamando. Esto nos permite ejecutar varias acciones intermedias que pueden ser útiles y facilitar la estructuración de nuestro codigo. Entre estas funciones pueden ser:
- Verificar que el usuario tiene permisos para hacer dicha acción
- Obtener o Modificar datos necesarios en el controlador de destino
- Registro de logs de las acciones realizadas por el usuario

![middleware.png](/informatica/daw/m7/middleware.png){.align-center}

```php
namespace App\Http\Middleware;
use Closure;
class CheckAge
{
    /**
     * Handle an incoming request.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Closure  $next
     * @return mixed
     */
    public function handle($request, Closure $next)
    {
        if ($request->age <= 18) {
            return redirect('home');
        }
        return $next($request);
    }
}
```

## Otros enlaces de interes

https://riptutorial.com/laravel/example/4292/making-a-model
https://richos.gitbooks.io/laravel-5/content/capitulos/chapter7.html
https://laravel.com/docs/master/eloquent
https://laravel.com/docs/master/queries
https://styde.net/paquete-laravel-ui-en-laravel-6/
https://styde.net/integrar-bootstrap-con-blade-en-laravel/
https://styde.net/layouts-con-blade/






# :pencil: Exercicis




