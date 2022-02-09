---
title: Instalació i Configuracio
description: Crear un nou projecte de Laravel
published: true
date: 2022-01-08T01:28:19.675Z
tags: 
editor: markdown
dateCreated: 2021-12-29T17:28:05.094Z
---

# Instalació

Començarem per instalar Laravel al nostre PC. Aquesta comanda es per crear un nou projecte:

```
curl -s https://laravel.build/tutorial-laravel | bash
```
Per iniciar el projecte ho farem utilitzant el modul **SAIL** que proporciona les eines de PHP, npm, Compose, etc necessaries per utilitzar i executar Laravel.

> A partir d'aquest moment **totes** les comandes de Laravel les executarem a continuació de la sentencia: ./vendor/bin/sail 
{.is-info}

```
./vendor/bin/sail up -d
```
> Si hi ha algun error analitzeu el missatge que us dona. Es posible que el port utilitzat **80** estigui en us. Canvieu aquest port per un altre a l'arxiu **docker-compose.yaml**
{.is-warning}


El primer cop que executeu el projecte en un nou ordinador heu d'instalar tots els paquests utilitzant els gestors de paquets composer i npm

```
./vendor/bin/sail composer install
./vendor/bin/sail npm install
./vendor/bin/sail npm run dev
```

Ara ya está el projecte preparat i funcionant accedint a la direcció: [http://localhost](http://localhost).

> Si moveu el projecte a un altre PC amb **Git** (push/pull) heu d'executar la següent comanda. Això es degut a que el módul SAIL no es puja mai al repositori i per tant s'ha de baixar a má el primer cop que baxeis el projecte a un nou PC.
{.is-danger}


```
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v $(pwd):/var/www/html \
    -w /var/www/html \
    laravelsail/php81-composer:latest \
    composer install --ignore-platform-reqs
```
    

[Documentacio Instalació](https://laravel.com/docs/8.x/installation)

## Instalació del modul de gestion del guard

Ara instalarem el nostre primer modul adicional de Laravel per administrar la funció de register/login. Tot i que aixó ho explicarem més endevant. 


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


La comanda anterior ens ha creat vistes d'exemple com: login, register, password forget, etc. De moment, ho ignorem per fer-ho servir en el [tema d'autenticació](/ca/informatica/daw/m7/uf2/tutorial-laravel-8/autenticacio)

[Mes informació sobre Breeze](https://laravel.com/docs/8.x/starter-kits#laravel-breeze)
