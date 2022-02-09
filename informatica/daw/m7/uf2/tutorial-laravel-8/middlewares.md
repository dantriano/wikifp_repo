---
title: Middleware
description: 
published: true
date: 2022-01-10T16:57:57.041Z
tags: 
editor: markdown
dateCreated: 2022-01-10T16:57:54.035Z
---

# Que son els Middlewares?

> Pots trobar més informació de com utilitzar els Request a l'apartat 
[Pildora 11: Validaciones de Formulario](/ca/informatica/daw/m7/uf2/laravel#pildora-11-validaciones-de-formulario)
{.is-info}

# Posem-ho en práctica :collision:

En este ejemplo veremos un middleware que se crea automaticamente al instalar el modulo de autentificacion Breeze

```php

namespace App\Http\Middleware;

use App\Providers\RouteServiceProvider;
use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;

class RedirectIfAuthenticated
{
    /**
     * Handle an incoming request.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Closure(\Illuminate\Http\Request): (\Illuminate\Http\Response|\Illuminate\Http\RedirectResponse)  $next
     * @param  string|null  ...$guards
     * @return \Illuminate\Http\Response|\Illuminate\Http\RedirectResponse
     */
    public function handle(Request $request, Closure $next, ...$guards)
    {
        $guards = empty($guards) ? [null] : $guards;

        foreach ($guards as $guard) {
            if (Auth::guard($guard)->check()) {
                return redirect(RouteServiceProvider::HOME);
            }
        }

        return $next($request);
    }
}
```