---
title: Base de datos Mongo
description: 
published: true
date: 2022-03-14T18:27:05.802Z
tags: 
editor: markdown
dateCreated: 2022-03-14T16:10:17.349Z
---

# Instalació Mongo y mongoose

Podemos utilizar docker para instalar mongo y mongoose (web  admin) ya que la comunicación ente node y Mongo se realiza mediante peticiones a la URL del servidor de Mongo: mongodb://YourUsername:YourPasswordHere@127.0.0.1:27017/your-database-name

```js
version: "3.8"
services:
  mongodb:
    image: mongo
    container_name: mongodb
    environment:
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=pass12345
    volumes:
      - ./mongodb-data:/data/db
    networks:
      - mongodb_network
    ports:
      - 27017:27017

  mongo-express:
    image: mongo-express
    container_name: mongo-express
    environment:
      - ME_CONFIG_MONGODB_SERVER=mongodb
      - ME_CONFIG_MONGODB_ENABLE_ADMIN=true
      - ME_CONFIG_MONGODB_ADMINUSERNAME=root
      - ME_CONFIG_MONGODB_ADMINPASSWORD=pass12345
      - ME_CONFIG_BASICAUTH_USERNAME=admin
      - ME_CONFIG_BASICAUTH_PASSWORD=admin123
    depends_on:
      - mongodb
    networks:
      - mongodb_network
    ports:
      - 8081:8081
    restart: unless-stopped

volumes:
  mongodb-data:
    name: mongodb-data
networks:
  mongodb_network:
    name: mongodb_network
```

# Conectar Node a Mongo

Cargamos el paquete que gestionará la conexión con la base de datos
```
 "dependencies": {  
    "express": "*",  
    "mongoose":"*"  
}    
```
Y en nuestra aplicación:
```js
//Load app dependencies  
var express = require('express'),  
  mongoose = require('mongoose'),  
  http = require('http');  
var app = express();  
mongoose.connect(
  `mongodb://root:admin1234@localhost:27017/tutorial?authSource=admin`,
  { useCreateIndex: true, useUnifiedTopology: true, useNewUrlParser: true },
  (err, res) => {
    if (err) console.log(`ERROR: connecting to Database.  ${err}`);
    else console.log(`Database Online: ${process.env.MONGO_DB}`);
  }
);
```

Ahora que estaremos preparados para utilizar mongo en nuestra aplicación.

# Model
Asi como ocurria en otros lenguajes, node tambien utiliza el sistema de **model** para representar la capa de datos y conectara a las tablas de Moodle

```js
// models/user.js
var mongoose = require('mongoose'),  
    Schema = mongoose.Schema;  
  
var userSchema = new Schema({  
    name: String,  
    age: String  
});  
  
//Export the schema  
module.exports = mongoose.model('User', userSchema); 
```
# Uso del modelo en los Controllers
En los controladores importaremos los modelos que vayamos a utilizar y de manera sencilla podremos usar acciones como insertar o buscar en nuestra base de datos
- find
- findOne
- find

Puedes consultar [aqui](https://mongoosejs.com/docs/queries.html) mas queries

```js
//controllers/user.js
module.exports = function(app){  
  
    var User = require('../models/user');  
  
    //Create a new user and save it  
    user = function(req, res){  
        var user = new User({name: req.body.name, age: req.body.age});  
        user.save();  
        res.end();  
    };  
  
    //find all people  
    list = function(req, res){  
        User.find(function(err, users) {  
            res.send(users);  
        });  
    };  
  
    //find person by id  
    find = (function(req, res) {  
        User.findOne({_id: req.params.id}, function(error, user) {  
            res.send(user);  
        })  
    });  
  
    //Link routes and functions  
    app.post('/user', user);  
    app.get('/users', list);  
    app.get('/user/:id', find);
}
