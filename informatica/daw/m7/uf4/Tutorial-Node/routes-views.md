---
title: Node - Routes & Views
description: 
published: true
date: 2022-03-22T15:59:38.004Z
tags: 
editor: markdown
dateCreated: 2022-03-09T15:38:49.818Z
---

# Routes

Definiremos nuestro primer archivo de routes

```js
/*
  /routes/index.js
*/
const express = require('express');
const router = express.Router();
const path = require('path');

//Middleware para mostrar datos del request
router.use (function (req,res,next) {
  console.log('/' + req.method);
  next();
});

//Analiza la ruta y el protocolo y reacciona en consecuencia
router.get('/',function(req,res){
  res.sendFile(path.resolve('views/index.html'));
});

module.exports = router;

```
# Views

Definiremos nuestro primer archivo de routes
```html
/*
  /views/index.html
*/
<html>
  Hello World
</html>
```

# Añadir nuevos elementros en nuestra aplicación

```js
//app.js                                                                 
var express = require('express');
var app = express();

/*
app.get('/', function (req, res) {
  res.send('Hello World!');
});
*/
const index = require('./routes/index');
const path = __dirname + '/views/';

app.set('view engine', 'html');
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path));

app.use('/', index);

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});



```