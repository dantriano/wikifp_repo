---
title: Laravel autenticacio
description: Autenticació amb Guard de Laravel
published: true
date: 2022-01-08T00:38:20.952Z
tags: 
editor: markdown
dateCreated: 2021-12-29T17:26:56.407Z
---

# Autentificacio en Laravel: Guard

Laravel te desenvolupat un nucli (**provider**) d'autentificació denominat **guard**. Aquest provider esta perfectament disenyat per ser utilitzat desde totes les parts de Laravel: rutes, controladors, vistes, requests, etc.
>  Es molt recomenable utilitzar el provider **guard**  en comptes de gestionar nosaltres mateixos la gestion de l'autentificació
{.is-info}

A continuació veiem com funciona internament el **Guard**:

1. Desde un controlador creat per nosaltres, realitzem un **atempt** (intent) d'autentificació al guard. Li pasarem unes credencials (usuario, mail, password) que el es contrastarán amb la taula **users**
1. Si no troba aquesta combinació de credencials a la base de dades ens tornará un missatge (codi) d'error
1. Si troba la combinació de credencials creará una **sessió** al servidor (vinculat a l'equip de l'usuari) que emmagatzemará el seu status com a **autentificat**. Aquesta sessió es mantindrá activa fins a una data de caducitat o fin a tancar la sessió.
1. Cada cop que es vulgui carregar una pagina restringuida o enviar un formulari podem fer que aquestes acciones consultin al **guard** si l'usuari te la sessió de d'autentificat activa.

![auth_attempt.png](/auth_attempt.png){.align-center}

# Posem-ho en práctica :collision:
A continuació afegirem a la nostra aplicació la capacitat d'autenticar i registrar els usuaris per que tinguin access a zones restringuides del nostre sistema. Només instalant breeze ja dispondrem de totes les funcionalitats (incluent vistes) per tenir un sistema de register/login a la nostra web

## Instalació del modul de gestion del guard

El que si podem fer es instalar algún modul que ens faciliti la gestió del **guard** i que ens instali exemples ja funcionant en el nostre projecte de manera que ens sigui més facil utlitzar-lo. En aquest tutorial utilitzarem un módul ja creat que instalarem al nostre projecte amb **composer** denominat **breeze**. Es podría fer a mà per requereix un esforç i temps innecessaris ja que tenim multitul de móduls que ens ofereixen aquesta funcionalitat.

````
composer require laravel/breeze --dev
````

La següent comanda instalará tot lo necessari (vistes, contradors, models, routes...) per poder gestionar les acciones de Register/Login:

````
php artisan breeze:install

npm install
npm run dev
php artisan migrate

````

[Mes informació sobre Breeze](https://laravel.com/docs/8.x/starter-kits#laravel-breeze)

## Vistes
Ens instalará un conjunt de vistes on tindrem, per exemple, els formularis de login, register, reset password, etc. Pero a mes ens dona una página "Dashboard" que només es accessible per als usuaris autentificats.
![auth_views.png](/informatica/daw/m7/auth_views.png){.align-center}

Podem veure que **blade** te bona comunicació amb el provider del guard ja que permet definir mostrar o no els diferents elements en funció de si l'usuari está autentificat o no.
![auth_blade.png](/informatica/daw/m7/auth_blade.png){.align-center}

## Routes

Podem observar que l'arxiu de les rutes també ha sigut modificat per afegir la ruta cap al Dashboard.

![auth_routes.png](/informatica/daw/m7/auth_routes.png){.align-center}
També s'ha creat un nou arxiu de rutes que s'importará al web.php on es concentren totes les URL referents a les pagines de login, register, recovery password, etc. El podreu trobar a <kbd>./routes/auth.php</kbd>


> Si detecteu que la instalació ha sobrescrit arxius que havieu creat, heu d'afegir les lineas eliminades consultant el vostre repositori.
{.is-danger}

## Controllers

A més del módel **User** que normalment ve amb la instalació
 original de Laravel 8, el nou módul **laravel/breeze** haurá creat un conjunt de controladors a <kbd>app/Http/Controllers/Auth</kbd> que serveixen per gestionar totes les **accions de login/register** posibles:
 
 - Registre
 - Autentificació
 - Reset Password
 - Confirmar mail
 
![auth_controllers.png](/auth_controllers.png){.align-center}