---
title: Node Middlewares
description: 
published: true
date: 2022-03-22T16:28:52.080Z
tags: 
editor: markdown
dateCreated: 2022-03-22T16:09:10.584Z
---

Los todas las funciones que definimos en Node puede utilizarse como middlewares siempre que contengan el atributo **next** en su declaración. De esta manera podemos asociar a una misma url diferentes acciones

Modificaremos el controlador para utilizar las funciones como middlewares:

```js
//controllers/user.js
  
    var User = require('../models/user');  
  
    //Metodo que almacena en DB  
    var add = (req, res, next)=>{  
        var user = new User({name: req.body.name, age: req.body.age});  
        req.result=user;
      	next();
    };  
    
    var isMayor = (req, res, next)=>{  
       if(req.body.edad>=18) req.isMayor=true
       else req.isMayor=false
      	next();
    };

    //Metodo que devuelve un valor a la vista
    var view =  (req, res)=>{  
        if(req.result)
      		res.sendFile(path.resolve('views/index.html'),{req.isMayor});
      	else
          res.sendFile(path.resolve('views/error.html'));
    };  

module.exports{
  add,
  isMayor,
  view
}
```

Por ultimo vemos como hacer para que una unica URL realice dos acciones independientes (consecutivamente). Primero añade a la base de datos y luego carga la vista
```js
// routes/index.js

//Definimos la ruta donde encontrar los controladores usando la libreria Path
var path = require("path");
var ctrlDir = path.resolve("controllers/");

//Importamos el controllador
var userCtrl = require(path.join(ctrlDir, "user"));
var router = express.Router();

//Link routes and functions  

    app.post('/isMayor', userCtrl.add);
    app.post('/isMayor', userCtrl.isMayor);
    app.post('/isMayor', userCtrl.view);  
 ```