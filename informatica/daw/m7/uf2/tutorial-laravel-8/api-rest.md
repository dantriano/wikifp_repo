---
title: Laravel: API Rest 
description: 
published: true
date: 2022-02-02T16:34:35.882Z
tags: 
editor: markdown
dateCreated: 2022-01-31T12:52:18.856Z
---

# Cóm funciona la REST API de Laravel?

> Pots trobar més informació de com utilitzar la API REST a l'apartat 
[REST API LARAVEL](/ca/informatica/daw/m7/uf3/rest)
{.is-info}

# Posem-ho en práctica :collision:
Primero descargamos el proyecto del tutorial:
https://github.com/dantriano/m7-laravel8-tutorial/tree/api

```
/*
* Creamos los Resources y Collections de User y Products
*/

php artisan make:resource UserResource
php artisan make:resource ProductResource
php artisan make:resource UserCollection
php artisan make:resource ProductCollection
```

## Obtener la lista de usuarios

```php
/*routes/api.php
* Obtenemos todos los usuarios accediendo directamente al Collection de user
*/

Route::get('/users', function () {
    return new UserCollection(User::all());
});
```
A continuación contruimos en el Collection la estructura de los datos que serán devueltos (json):

> En los **Resources** podemos definir (limitar) los campos que serán devueltos al usuario
> En las **Collections**, en cambio, podemos ademas de incluir la información de un Resource, añadir otra información que "extra" que no necesariamente proceda de la base datos. 
{.is-info}


```php
/*
*   App/Http/Resources/UserResource.php
*
* Definimos los elementos de la tabla usuario (modelo) que serán devueltos.
*/
namespace App\Http\Resources;
use Illuminate\Http\Resources\Json\JsonResource;

class UserResource extends JsonResource
{
    public function toArray($request)
    {
 			return [
            'id' => $this->id,
            'name' => $this->name,
            'email' => $this->email
        ];
    }
}
```

```php
/*
*   App/Http/Resources/UserCollection.php
*
* Definimos la estructura del json.
* Para obtener los datos de un modelo asociado a un collection usamos:
*  $this->collection 
*/
namespace App\Http\Resources;
use Illuminate\Http\Resources\Json\ResourceCollection;

class UserCollection extends ResourceCollection
{
    public function toArray($request)
    {
 			return [
            'data' => $this->collection,
            'links' => [
                'self' => 'link-value',
            ],
        ];
    }
}
```


## Guardar un nuevo producto y obtener sus datos
```php
/*routes/api.php
* Llamamos al controlador que se encarga de guardar nuevos productos
*/

Route::post('/product', [ProductController::class, 'store']);

```
```php
/*App\Http\Controllers/ProductController.php
* Creamos el metodo de guardar un nuevo producto con los datos recibidos por formulario. 
* Al preveer que es una petición de API podemos devolver el resultado en formato JSON
*/

		public function store(Request $request)
    {
        $product = Product::create($request->all());
        return response()->json($product, 200);
    }
```

> Fijemonos que en las peticiones de información se usa el protocolo GET y en las de insertar o guardar el protocolo POST
{.is-success}

![ejemplo_api_post.png](/informatica/daw/m7/ejemplo_api_post.png){.align-center}

## Relaciones entre modelos

En ocasiones tal vez queramos obtener información de dos tablas en una misma consulta. Esto podemos hacerlo si las tablas estan relacionadas a nivel de base de datos (clave primaria-foraneo) y están bien configuradas las [relaciones en el modelo](https://laravel.com/docs/8.x/eloquent-relationships) (hasOne/hasMany/belongsTo)


```php
class ProductResource extends JsonResource
{
    public function toArray($request)
    {
 			return [
            'id' => $this->id,
            'category' => new CategoryResource($this->category),
        ];
}
        
```

## Generar documentación API
Una parte muy importante en la creación de API es la de generar una documentación clara para poder pasar a los clientes y que estos sepan exactamente qué deben enviar y como se les devolverá la información.

Para instalarlo basta con seguir las [instrucciones del componente Beyondco](https://beyondco.de/docs/laravel-apidoc-generator/getting-started/installation) (versión Laravel)

Cuando queramos generar nuestro archivo de documentación solo tendremos que ejectura:
```
php artisan apidoc:generate
```