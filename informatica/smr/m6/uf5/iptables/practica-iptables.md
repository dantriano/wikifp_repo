---
title: Practica Iptables
description: 
published: true
date: 2022-03-30T12:40:45.180Z
tags: 
editor: markdown
dateCreated: 2022-03-30T12:40:45.180Z
---



- :calendar: **Durada**: 4h
- :computer: **Material necessari**:PC amb SO compatible, SAI, Documentació SAI, Altres PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup
- :notebook_with_decorative_cover: **Descripció**: En aquesta pràctica configurarem una maquina per fer de Firewall

### Objectiu
Heu d'aconseguir durant el temps establert a la pràctica, instalar un Debian amb Iptables a on es conectaran altres PC (gateway).

> Tots els passos han d'estar correctament documentats.
> {.is-warning}


### Preparació
Baixar la maquina virtual [Debian](https://drive.google.com/file/d/1RBveHm0YttsZGJkSKW8vVnBHGDQuBKNY/view?usp=sharing) e instalar Iptables. Esta maquina virtual deberá ser la puerta de enlace residencial del resto de equipos que quieran conectarse a Internet.

![firewall.jpg](/informatica/smr/m6/m5/firewall.jpg){.align-center}

- **enp0s3**: La interfaz que da al exterior, configurada como nos sea conveniente.
- **enp0s8**: Esta es la interfaz que da a la red interna, con una dirección IP estática (en este caso 10.0.0.1/24).

### Configurar Firewall para ser Gateway

1. Permitir la conunicación entre las dos tarjetas de red:
```
/etc/sysctl.conf
net.ipv4.ip_forward = 1
```
2. Permitir la conunicación entre las dos tarjetas de red:
Crear un archivo de reglas IPTABLES llamado iptables.sh.
Para ejecutarlo solo deberemos de ejecutar:
```
sh iptables.sh
```

Escribimos las reglas necesarias para que permitir la comunicación entre las tarjetas de red
```
# Primero borramos todas las reglas previas que puedan existir
iptables -F
iptables -X
iptables -Z
iptables -t nat -F
# Aceptamos las conexiones locales
iptables -A INPUT -i lo -j ACCEPT

# Hacemos pasar los paquetes que salgan por enp0s3 como si procedieran del firewall (masquerade)
iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE

# Permitimos los paquetes que vienen de la tarjeta de red que hace de Gateway y las respuestas (related,established)
iptables -A INPUT -i enp0s8 -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

Ref:
https://www.linuxsysadmin.ml/2018/03/un-gateway-con-debian-iptables-y-dnsmasq.html

> En este punto deberemos de ser capaces de conectar cualquier PC al firewall y poder navegar.
{.is-info}

Establece en otro PC la soguiente configuración:


### Configurar Firewall con filtros

Analitza el Softare de monitorarge i explica les principals funcionalitats que detectes.

IP: 10.0.0.1
NetMask: 255.255.255.0
**Gategway: 10.0.0.1**  //Gracias a esta linea podemos conectarnos a Internet a traves del Firewall
DNS: 8.8.8.8

:pencil2: Creat per Dan Triano {.text-right}