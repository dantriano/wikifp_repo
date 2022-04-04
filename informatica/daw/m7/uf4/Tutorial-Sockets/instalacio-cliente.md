---
title: Instalación Socket Cliente
description: 
published: true
date: 2022-04-04T14:37:16.930Z
tags: 
editor: markdown
dateCreated: 2022-04-04T14:37:16.930Z
---

# Instalació

Cuando iniciamos el **servidor** de socket, automaticamente nos proporciona una archivo js que podemos utilizar en nuestro frontend para que podamos utilizarlo desde el navegador. Este archivo siempre lo encontraremos en la ruta <kbd>/socket.io/socket.io.js</kbd> de nuestro servidor de socket.

El primer paso, por lo tanto es añadir este script a nuestras vistas


```js
script(type='text/javascript', src='http://localhost:2000/socket.io/socket.io.js')
script(type='text/javascript', src='/js/chat.js')
```

Podemos observar que ademas hemos añadido un archivo **chat.js** que crearemos nosotros mismos donde pondremos todas las funcionalidades que ha de ejecutar el cliente (enviar/recibir mensajes) del servidor socket.

```js
//Cuando todos los elementos de nuestra web se hayan cargado:
document.addEventListener("DOMContentLoaded", function (event) {
  //Nos conectamos al servicio de socket.
  //La constante socket será nuestro vinculo con el servidor donde definiremos todas las accioens
  const socket = io("http://localhost:2000");

    /*
   * Acciones que se realizan cuando se detecta el evento "connected" lanzado por el servidor
   */
  socket.on("connected", (data) => {
    console.log(data.msg);
  });

}

```

Con esto, cada vez que cargamos la pagina con este script veremos que se produce la conexión (permanente) entre el cliente y el servidor.

# Eventos

Ahora que ya tenemos la conexión establecida deberemos de configurar la parte del cliente para que sepa **enviar** y **recibir** los mensajes intercambiados por el servidor.

![bidirectional-communication-socket.png](/informatica/daw/m7/uf4/bidirectional-communication-socket.png){.align-center}

```js
//Accion a realizar cuando se da al boton de enviar
document.getElementById("send").addEventListener("submit", (e) => {
    //Obtenemos todos los elementos del formulario para trabajar con ellos
    e.preventDefault();
    var msgInput = document.getElementById("msg");
    var chatBox = document.getElementById("chat");
    var msg = msgInput.value;

    //Mostramos el mensaje en la ventana para el usuario que lo envia
    chatBox.innerHTML += `Yo: ${msgInput.value}<br>`;

    // Definimos el mensaje que vamos a enviar
    var toSend = { user: "Yo", text: msg };

    //Enviamos el mensaje al servidor utilizando el evento "broadcast" definido por nosotros
    socket.emit("broadcast", toSend);

  });


```
