---
title: Requests de Laravel
description: Request en Laravel
published: true
date: 2021-12-31T04:36:55.583Z
tags: 
editor: markdown
dateCreated: 2021-12-29T23:22:35.743Z
---

# Que son els Requests?
Request es una clase que ens ofereix Laravel per tractar la comunicació que rep desde els formularis de les vistes. Podem establir diferents configuracions per exemple:

- Restringir l'enviament de la informació per formulari només a usuaris autenticats
- Crear restrinccions per els camps (inputs) de manera que només s'acceptin aquells que cumpleixen les normes: email, telefons, formats especifics, etc
- Definir els missatges d'error/informació per a l'usuari en cas que no es cumpleixin les regles anterior.


> Pots trobar més informació de com utilitzar els Request a l'apartat 
[Pildora 11: Validaciones de Formulario](/ca/informatica/daw/m7/uf2/laravel#pildora-11-validaciones-de-formulario)
{.is-info}

Podem utilitzar la clase Request directament a cualsevol controlador, pero normalment es crean noves clases (una per formmulari) que s'extenen de Request:

```php
//app/Http/Requests/PostRequest.php

class PostRequest extends FormRequest
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
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
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
            'title.required' => 'A title is required',
            'body.required' => 'A message is required',
        ];
    }
}
```

Un cop definides les regles i els missatges d'error només hem d'agegir la clase dintre dels parametres del metode del controlador on s'enviará el formulari (action).

```php
//app/Http/Controllers/PostController.php

public function save(PostRequest $request)
{
  //This option allow to keep the value in the view Form using:
  $request->flash();

  //Obtenim el valor de cada input
  if ($request->filled('title')) {
      $title = $request->input('title');
  }
  if ($request->filled('body')) {
      $body = $request->input('body');
  }
}
```



# Posem-ho en práctica :collision:
A continuació afegirem a la nostra aplicació la capacitat de emmagatzemar en sessió els productes que l'usuari afegeix a la seva cistella de la compra.

## Guardar un nou producte a la BD desde un formulari 

Quan estem a una botiga online i afegim productes a la nostra cistella, no volem que s'esborrin quan cambiem de página. La millor manera de mantenir consistencia d'aquestes dades (sense haver de emmagatzemarles a la base de dades) es mitjançant les sessions.

Primer haurem de crear el formulari a la vista encarregada de crear nous products. Fixe-vos en la localització on es visualitzaran els **missatges d'error** en cas que es produeixen invalidacions de les dades.

````php
//resources/views/new_product.blade.php

<form id="filterForm" method="post" action={{ route('saveProduct') }} enctype="multipart/form-data">
{{ csrf_field() }}
  <div class="form-group">
    <label for="name">Name</label>
    <input id="name" type="text" name="name" value="" class="form-control">
    @error('name')
       <div class="error">{{ $message }}</div>
    @enderror
  </div>
  <div class="form-group">
    <label for="price">Precio</label>
    <input id="price" type="number" name="price" value="" class="form-control">
    @error('price')
       <div class="error">{{ $message }}</div>
    @enderror
  </div>
  <div class="form-group">
     <label for="desc">Descripcion</label>
     <input id="desc" type="text" name="desc" value="" class="form-control">
  </div>
  <div class="form-group">
     <label for="desc">Categoria</label>
     <select class="form-control" id="category" name="category">
     @foreach ($categories as $cat)
       <option value="{{$cat->id}}">{{$cat->name}}</option>
     @endforeach
     </select>
  </div>
  <div class="form-group">
    <label for="imagen">Imagen</label>
    <input type="file" name="imagen" />
  </div>
  <div class="form-group">
    <input type="submit" value="Guardar" class="btn btn-primary">
  </div>
</form>

@if(app('request')->has('success'))
@if (session('error'))
<div class="alert alert-danger">
    {{ session('error') }}
</div>
@else
<div class="alert alert-success">
    Producto guardado con exito
</div>
@endif
@endif
````

Un cop tenim el formulari haurem de crear la clase que extend del Request amb les validacinos i missatges que vulguem per controlar el funcionament del formulari

```php

namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;
use Illuminate\Http\JsonResponse;

class ProductListRequest extends FormRequest
{
    /**
     * Considerem que aquest formulari ho pot enviar tothom sense autorizació
     */
    public function authorize()
    {
        return true;
    }

    /**
     * Definimos solo un par de validaciones. Habría que hacerlo con todos los campos
     */
    public function rules()
    {
        return [
            'name' => 'required|unique:products|max:255',
            'price' => 'required',
        ];
    }
    
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

```


A continuació crearem dos metodes al controlador de productes que ens permeti emmagatzemar i borrar una llista de productes a sessió.

````php
//app/Http/Controllers/ProductController.php

use App\Http\Requests\ProductListRequest;

public function save(ProductListRequest $request, UploadFileProvider $UploadFileService)
    {
        $success = false;
        try {
        		if ($request->hasFile('imagen')) {
              //Use uploadService (can throw UploadFileException)
              $this->uploadService = $UploadFileService;
              $this->uploadService->uploadFile($request->file('imagen'));
						}
            //Creamos un nuevo producto instanciando el modelo de Product
            $product = new Product;
            if ($request->hasFile('imagen')) 
            	$product->imagen  = $request->imagen->getClientOriginalName();
              
            $product->name = $request->input('name');
            $product->desc  = $request->input('desc');
            $product->price  = $request->input('price');
            $product->category_id  = $request->input('category');
            //Save new product (can throw QueryException)
            $success = $product->save();
        } catch (UploadFileException $exception) {
            $this->error = $exception->customMessage();
        } catch (\Illuminate\Database\QueryException $exception) {
            $this->error = "Error con los datos introducidos: ".$exception->getMessage();
        }
        //Redirigimos a la pagina del formulario de nuevo producto pasandole el resultado de registro
        return redirect()->action([ProductController::class, 'new'], ['success' => $success])->withError($this->error);
    }

````
