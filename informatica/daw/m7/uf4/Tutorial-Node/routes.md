---
title: Node- Routes
description: 
published: true
date: 2022-03-09T16:00:44.634Z
tags: 
editor: markdown
dateCreated: 2022-03-09T15:38:49.818Z
---

# Routes

Definiremos nuestro primer archivo de routes

```node
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

```node
  GNU nano 5.4                                                       app.js                                                                 
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