---
title: Eventos de Socket
description: 
published: true
date: 2022-04-04T15:53:17.027Z
tags: 
editor: markdown
dateCreated: 2022-04-04T15:53:17.027Z
---

# Eventos

Ahora que ya tenemos la conexión establecida deberemos de configurar la parte del cliente para que sepa **enviar** y **recibir** los mensajes intercambiados por el servidor.

> Recordad que hay que gestionar el envio y la recepción de mensajes por separado
{.is-info}


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
