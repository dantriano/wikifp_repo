---
title: Sessions de Laravel
description: Gestió de sessions a Laravel
published: true
date: 2021-12-29T23:53:36.821Z
tags: 
editor: markdown
dateCreated: 2021-12-29T17:49:43.166Z
---

# Sessió
Les sessions son arxius de dades que s'emagatzemen al servidor de PHP (o altres llenguatges) i permeten una persistencia *relativa* de les dades. Donen funcionalitat a les págines web que d'aquesta manera poden conservar algunes dades sense estar constantment fent peticions a la base de dades. Es habitual utilitzarles per:

- Mantenir els productes en una cesta de compra
- Emmagatzema credencials per ser consultats a cada pagina quan l'usuari navega per la web
- Emmagatzema preferencies per millorar l'experiencia de l'usuari

![session_php.jpeg](/informatica/daw/m7/session_php.jpeg){.align-center}

**Aquesta informació es manté al servidor fins que l'usuari tanca la conexió (el navegador).**

> Moltes vegades es complementen les sessions (servidor) amb les cookies (navegador), per donar mes persistencia a les dades de sessió.
{.is-success}

> Pots trobar més informació de com utilitzar els Request a l'apartat 
[Pildora 12: Sesiones](/ca/informatica/daw/m7/uf2/laravel)
{.is-info}

# Posem-ho en práctica :collision:
A continuació afegirem a la nostra aplicació la capacitat de emmagatzemar en sessió els productes que l'usuari afegeix a la seva cistella de la compra.

## Administrant sessions al controlador

Quan estem a una botiga online i afegim productes a la nostra cistella, no volem que s'esborrin quan cambiem de página. La millor manera de mantenir consistencia d'aquestes dades (sense haver de emmagatzemarles a la base de dades) es mitjançant les sessions.

A continuació crearem dos metodes al controlador de productes que ens permeti emmagatzemar i borrar una llista de productes a sessió.

````php
//app/Http/Controllers/ProductController.php

use Illuminate\Http\Request;
use App\Http\Requests\ProductListRequest;

public function addToChart(ProductListRequest $request)
{
	$carrito = $request->session()->get('carrito', []);
	array_push($carrito, $request->input('productname'));
	$request->session()->put('carrito', $carrito);

	//Redirect to page who send the request:
	return redirect(url()->previous());
}

public function emptyChart(Request $request)
{
	$request->session()->forget('carrito');
	return redirect()->route('welcome');
}
````

Podem observar que s'utilitza la llibreria **Request** per gestinonar tant les dades del formulari com les sessions de Laravel. En aquest exemple guardem a la sessió **carrito** un array de productes.

- ```$request->session()->forget('nomSessio')```:Esborra la sessió amb key 'nomSessio'
- ```$request->session()->put('nomSessio', ['prod1','prod2'])```: Emmagatzema en 'nomSessio' un array d'elements. Tambe pot guardar altres tipus de dades.

- ```$request->session()->get('nomSessio',[])```: Retorn els contingut de la sessió 'nomSessio'.  **Si no esta definida la sessió, retorna el valor per defecte []**

## Enviant dades per guardar en sessió

Podem emmagatzemos cualsevol tipus de dades a les sessions. Al nostre cas enviarem l'informació d'un producte mitjançant un formulari.

```php
//views/product.blade.php

@forelse ($productos as $prod)

<form method="post" action={{ route('addToChart') }}>
	{{ csrf_field() }}
	<input type="hidden" name="productid" value="{{$prod->id}}">
  <input type="hidden" name="productname" value="{{$prod->name}}">
  <input type="submit" value="Add product to shipping »" class="btn btn-secondary">
</form>

@endforelse
````
L'ún que hem de fer després es definir les rutes per fer les crides al controller corresponent

```php
//routes/web.php

Route::post('/products/addToChart', [ProductController::class, 'addToChart'])->name('addToChart');
Route::get('/products/emptyChart', [ProductController::class, 'emptyChart'])->name('emptyChart');
````
        
## Mostrant en una view dades de sessió
Un cop tenim les dades en una sessió les podem utilitzar en cualsevol part del nostre programa, ja sigui en el controller o les vistes. En aquest cas, veurem com llistar els productes que hi son a la nostra sessió.

````php
<li class="nav-item dropdown">
  <a class="nav-link dropdown-toggle" href="#" id="dropdown01" data-bs-toggle="dropdown" aria-expanded="false">Numero de produtos: {{sizeof(app('request')->session()->get('carrito',[]))}}</a>
  <ul class="dropdown-menu" aria-labelledby="dropdown01">
     @forelse (app('request')->session()->get('carrito',[]) as $producto)
       <li>
         <a class="dropdown-item" href="#">{{$producto}}</a>
       </li>
     @empty
       <li>
         <a class="dropdown-item" href="#">No products in chart </a>
       </li>
     @endforelse
  </ul>
</li>
@if(app('request')->session()->has('carrito'))
   <li class="nav-item">
       <a class="nav-link" type="button" class="btn btn-primary" href={{ route('emptyChart') }}>Borrar Carrito</a>
  </li>
@endif
````

- ```app('request')->session()->get('nomSessio',[])```: D'aquesta manera podem obtenir el contingut de la sessió directament en la vista. Tot i que també es habitual llegir-la al controlador com ho hem vist a l'apartat anterior.
