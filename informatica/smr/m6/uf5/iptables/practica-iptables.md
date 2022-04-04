---
title: Practica Iptables
description: 
published: true
date: 2022-04-04T14:49:08.086Z
tags: 
editor: markdown
dateCreated: 2022-03-30T12:40:45.180Z
---



- :calendar: **Durada**: 4h
- :computer: **Material necessari**:PC amb SO compatible, SAI, Documentació SAI, Altres PC
- :busts_in_silhouette: **Agrupació**: Per treballar en grup
- :notebook_with_decorative_cover: **Descripció**: En aquesta pràctica configurarem una maquina per fer de Firewall

# Objectiu
Heu d'aconseguir durant el temps establert a la pràctica, instalar un Debian amb Iptables a on es conectaran altres PC (gateway).

> Tots els passos han d'estar correctament documentats.
> {.is-warning}


# Preparació
Baixar la maquina virtual [Debian](https://drive.google.com/file/d/1RBveHm0YttsZGJkSKW8vVnBHGDQuBKNY/view?usp=sharing) e instalar Iptables. Esta maquina virtual deberá ser la puerta de enlace residencial del resto de equipos que quieran conectarse a Internet.

![firewall.jpg](/informatica/smr/m6/m5/firewall.jpg){.align-center}

- **enp0s3**: La interfaz que da al exterior, configurada como nos sea conveniente.
- **enp0s8**: Esta es la interfaz que da a la red interna, con una dirección IP estática (en este caso 10.0.0.1/24).

## Configurar Firewall para ser Gateway

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

## Conectamos un PC a nuestro Firewall


Analitza el Softare de monitorarge i explica les principals funcionalitats que detectes.

IP: 10.0.0.10
NetMask: 255.255.255.0
**Gategway: 10.0.0.1**  //Gracias a esta linea podemos conectarnos a Internet a traves del Firewall
DNS: 8.8.8.8

> Es necesario definir el DNS en el host para que podais tener internet
> /etc/resolv.conf
> nameserver 8.8.8.8
{.is-danger}


# Configurar Firewall con filtros

Configura un script para poder tener todos estos filtros.

1. Nuestro firewall por defecto acepta todas las conexiones
2. Queremos denegar las conexiones HTTP y HTTPS a toda nuestra LAN
3. Queremos permitir que un ordenador (10.0.0.10) de la red tenga conexión HTTP y HTTPS
4. Denegamos acceso por ssh a los ordenadores del aula (los hosts)
5. Cerramos el rango de puertos 1 al 1024 desde cualquier origen.
6. Cerramos el rango de puertos 1 al 1024 desde cualquier origen EXCEPTO el puerto HTTP y HTTPS para que la ip 10.0.0.10 pueda navegar por la web
7. Se desea bloquear el ping al cortafuegos ICMP desde cualquier máquina.
8. Rechazamos todo el tráfico cuyo destino sea nuestra red LAN 10.0.0.0/24 y entre por la interfaz enp0s3 del Firewall.
9. Denegamos SMTP, POP3 y FTP (correo electrónico y ftp) en la LAN 10.0.0.0/24 
10. Denegamos SMTP, POP3 y FTP (correo electrónico y ftp) pero permitimos que lo utilice ordenador 10.0.0.20 
11. Volem descartar una connexió concretament la pàgina www.marca.com (nslookup / http://www.hcidata.info/) mitjançant iptables ja que volem que les altres persones que es connecten aquest ordinador aprofiten més el temps.
12. Listamos todas las reglas que se aplican con: iptables -L -n


# Comprobamos cómo quedan las reglas

Documenta la demostración que el iptables funciona en los pasos:
- 2
- 5 (puedes comprobarlo con un NMAP)
- 7

:pencil2: Creat per Dan Triano {.text-right}