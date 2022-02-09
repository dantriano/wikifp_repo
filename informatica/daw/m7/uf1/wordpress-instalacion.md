---
title: Wordpress - Instalación
description: 
published: true
date: 2021-10-27T13:01:32.533Z
tags: 
editor: markdown
dateCreated: 2021-10-18T10:49:08.467Z
---

# Instlación básica

La mayoria de empresas de hosting proporcionan un servicio de instalación de Wordpress automatizada. En nuestro caso lo haremos manualmente.

1. Descargar los archivos necesarios para la instalación de https://wordpress.org/download/
2. Colocar esos archivos en la raiz de nuestro servidor PHP (Docker, Wamp, etc).
3. Seguir los pasos de la guia oficial (u otra de Internet)



# Instalación con Docker

Otra opción es utilizar un contenedor especialmente preparado por Wordpress. Esta es la opción que utilizaremos para trabajar en clase

```
version: "3.9"
    
services:
  db:
    image: mysql:5.7
    volumes:
      - ./db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - ./wordpress_data:/var/www/html
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress

```

Una vez instalado podemos proceder a la configuración de nuestra página.

# Configuración
## Acceso a wordpress local
La mejor manera de trabajar en local con varias personas, si no disponemos de un servidor donde alojar nuestra web, es estableciendo una URL inventada en nuestro archivo `/etc/hosts` que apunte a la IP del ordenador que está ejecutando nuestro Wordpress. 

![hosts.png](/informatica/daw/m7/hosts.png){.align-center}

Gracias a esto conseguiremos que todos los recursos (CSS, imagenes, enlaces) apuntes a la URL correctamente.
![home_wordpress.png](/informatica/daw/m7/home_wordpress.png){.align-center}

> Si no realizamos este paso al inicio de la instalación deberemos de configurar la URL desde las opciones del propio Wordpress en:
>
>**Ajustes > Ajustes Generales > Dirección de WordPress (URL) y Dirección del sitio (URL)**
{.is-danger}

![wordpress_url.png](/informatica/daw/m7/wordpress_url.png){.align-center}

> Despues de trabajar con nuestra pagina web es importante hacer un `push` de git para subir nuestros cambios tanto en la base de datos como en los archivos del Wordpress.
{.is-warning}


## Instalación de plantillas y plugins
1. Importar la plantilla elegida e instalarla.
2. Instalar todos los plugins necesarios para nuestro proyecto.

Si ejecutamos nuestro wordpres de manera local, veremos que nos pedirá configurar un servicio FTP para instalar Plugins y Plantillas desde el asistente de Wordpres. Sin embargo, esto no es necesario, ya que podemos cargar manualmente cualquier plantilla o plugin si la descargamos y la descomprimimos en la carpeta correspondiente del arbol de directorios de Wordpress.

**1. Descargamos el plugin o plantilla desde la web oficial (no desde el gestor del propio Wordpress)**

![wordpress_plugin_download.png](/informatica/daw/m7/wordpress_plugin_download.png){.align-center}

**2. Subir el archivo (descomprimido) a la carpeta que corresponda**
<kbd>/wordpress_data/wp-content/plugins</kbd>
o
<kbd>/wordpress_data/wp-content/themes</kbd>

![wordpress_plugin_upload.png](/informatica/daw/m7/wordpress_plugin_upload.png){.align-center}

A partir de ese momento veremos que el template o el plugin subidos apareceran en el menu de Wordpress listos para ser activados.

![wordpres_plugin_activate.png](/informatica/daw/m7/wordpres_plugin_activate.png){.align-center}

# Plantilla personalizada
Podemos crear plantillas personalizadas para aplicar a paginas concretas. Esto se hace añadiendo nuevos archivos .php en la carpeta de la template que estamos utilizando en nuestra web. Al poner en la cabecera un nombre de template `Template Name` conseguiremos que se muestre automaticamente en el editor de las paginas.

````php
<?php

/**
 * Template Name: Lista Custom Fields
 * Template Post Type: page
 *
 */
?>
````
<div align="center" class="row justify-center">
  <div class="col-6">
    
![template_custom.png](/informatica/daw/m7/template_custom.png){.align-center}
    
  </div>
  </div>

Ese archivo .php será el que se cargará al visitar la pagina. De esta manera podemos estructurar el contenido como queramos y añadir los plugins o contenido en las posiciones que queramos. A continuación vemos un ejemplo de plantilla personalizada.

```php
<?php

/**
 * Template Name: Lista Custom Fields
 * Template Post Type: page
 *
 */

//Carga el Header propio de la template
get_header();
?>

<main id="content" class="neve-main" role="main">
					<?php
          //Carga el titulo y contenido que el 
          //usuario introduce en el editor de la pagina
					the_title();
					the_content();
					?>
</main>

<?php //Carga el Footer y el menu del footer propio de la template ?>
<?php get_template_part('template-parts/footer-menus-widgets'); ?>
<?php get_footer(); ?>

```

# Campos personalizados

Wordpress solo permite crear por defecto páginas y blogs. Pero hay veces que necesitamos manejar datos más complejos y poderlos mostrar de manera mas personalizada a lo largo de nuestra página. Para ello, utilizaremos un plugin llamado: [Advance Custom Feilds](https://www.advancedcustomfields.com) 

Aqui podeis ver algunos ejemplos de templates:
- [Templates open source](https://www.formget.com/open-source-wordpress-themes/)
- [Templates de Wordpress Oficiales](https://es.wordpress.org/themes/)

Podeis instalar la versión gratuita desde el propio gestor de Plugins o [descargando el .zip](/informatica/daw/m7/advanced-custom-fields.tar.xz)

![advance-custom-fields.png](/informatica/daw/m7/advance-custom-fields.png){.align-center}

Complemento adicional para crear tablas [Table field](https://es.wordpress.org/plugins/advanced-custom-fields-table-field/)

Una vez hemos insertado información en los nuevos campos creados con Adance Custom Fields, deveremos de mirar la [documentacion](https://www.advancedcustomfields.com/resources/) con tal de saber como mostrar esos campos en nuestra plantilla mediante codigo PHP
