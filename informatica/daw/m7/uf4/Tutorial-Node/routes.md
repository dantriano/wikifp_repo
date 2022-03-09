---
title: Node- Routes
description: 
published: true
date: 2022-03-09T15:38:49.818Z
tags: 
editor: markdown
dateCreated: 2022-03-09T15:38:49.818Z
---

# Instalació

Aquesta comanda es per isntalar el gestor de paquets NPM i crear un nou projecte:

```
apt install npm
mkdir node-tutorial
npm init
## entry point: app.js 
```

Node es un servidor básic de JavaScript, pero poder oferir pagines webs instalarem el framework Express.
```
npm install express --save
```

> El parametro --save hace que sea permanente en el package.json de manera que cuando descarguemos nuestro proyecto en otro PC ya nos instalará Express automaticamente
{.is-info}

![node-estuctura.png](/informatica/daw/m7/uf4/node-estuctura.png){.align-center}

# Configuració per testeig

Ahora que nos funciona podremos añadir cualquier paquete en package.json que nos ayude en el desarrollo de nuestra aplicación (devDependencies) o paquetes que sirvan para el funcionamiento de la propia aplicación (Dependencies)

Añadimos nodemon a nuestro **package.json** para manetener activa nuestra aplicación y escuchar cambios que provocarán un reinicio del programa:
```
"dependencies": {....},
"devDependencies": {
    "nodemon": "^1.18.10"
} 
```

Instalamos el nuevo paquete:
`npm install`

Y a continuación modificamos nuestro script "test" para que ejecute **nodemon** sobre el archivo de nuestra aplicación **app.js**
```
"scripts": {
    "test": "nodemon app.js", 
    "start": "node app.js"
},
```

`npm run test`
> Podemos crear tantos scripts como queramos: test, start, migrate, etc... que se ejecutarán con el comando
> npm run [nombre script]
{.is-info}

