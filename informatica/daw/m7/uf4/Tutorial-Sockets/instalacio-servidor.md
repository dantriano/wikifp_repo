---
title: Instalación Socket Servidor
description: 
published: true
date: 2022-04-04T11:28:57.040Z
tags: 
editor: markdown
dateCreated: 2022-04-04T11:28:57.040Z
---

# Instalació

Lo primero que debemos tener claro es que con la comunicación Socket participan dos actires bien diferenciados: servidor (node) y cliente (navegador) 

![bidirectional-communication2.png](/informatica/daw/m7/uf4/bidirectional-communication2.png){.align-center}

Empezaremos por instalar el paquete en nuestro servidor:

```
npm install socket.io
```

Ahora tenemos dos opciones:
1. Instalar en nuestro servidor web (puerto 80) el servicio de socket. Utilizando el mismo puerto e IP.
2. Crear un nuevo servicio diferenciado del de WEB dedicado únicamente a la comunicación de socket.


En nuestro caso vamos a utilizar un servicio aparte para que sea más claro de entender. Crearemos un archivo io.js que contendrá todo nuestra aplicación de Socket.io:

```js
//io.js
const socketPort =  2000;
const { Server } = require("socket.io");
const socketServer = require("http").createServer();

socketServer.listen(socketPort, (err, res) => {
  if (err) console.log(`ERROR: Connecting APP ${err}`);
  else console.log(`Server is running on port ${socketPort}`);
});
const io = new Server(socketServer);
```

Con esto ya tenemos nuestro servidor de Socket escuchando por el puerto 2000. Ahora bien, para que dos servicios diferentes puedan comunicarse hay que habilitar los persmisos **Cross-Origin Resource Sharing (CORS)** [mas info](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

```js
//io.js
const io = new Server(socketServer, {
  cors: {
    origin: "http://localhost:3000", //Esta será la dirección de vuestra web
  },
});
```

# First connection

Ahora que nuestro servidor está escuchando todas las peticiones de conexión de los clientes, nos toca programar los comportamientos que tendrá con cada **evento**.

Empezaremos a hacer reaccionar nuestro servidor a las nuevas conexiones. Cada vez que un cliente se conecta a nuestro servidor de socket, le contestaremos **(emit)** enviandole un json con un mensaje de bienvenida:

```js
io.on("connection", (socket) => {
  console.log("Nuevo cliente conectado");
  socket.emit("connected", {
    msg: "Bienvenido al chat",
  });
});
   
```
El destinatario de ese mensaje será el cliente que se conectó porque si os fijais estamos "dentro" de la rección **on(connection)**.

> La comunicación siempre se hara entre cliente-->servidor-->cliente. 
**Dos cliente NUNCA pueden comunicarse directamente sin pasar por el servidor**
{.is-danger}

