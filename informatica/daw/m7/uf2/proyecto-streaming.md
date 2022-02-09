---
title: Proyecto Streaming
description: 
published: true
date: 2022-01-17T13:58:54.767Z
tags: 
editor: markdown
dateCreated: 2021-11-07T17:09:27.110Z
---

- :calendar: **Durada**: 6 setmanes
- :computer: **Material necessari**:PC amb SO compatible, Framework
- :busts_in_silhouette: **Agrupació**: Per treballar en grup
- :notebook_with_decorative_cover: **Descripció**: En aquesta pràctica veurem com desenvolupar una plataforma de streaming que validará els usuaris i obtindrá la informació desde una Base de Dades

# Objectiu
Hey de desenvolupar en cada grup una plataforma de Streaming que sigui capaç de autenticar els usuaris i els mostri les seves pelicules favorites i reproduirles.

## Usuaris i funcionalitats
Existeixen dos perfils diferents. Usuaris y administradors. Les seves accions serán:

**Usuaris:**
- Podrán enregistrarse i loguearse
- Cambiar les seves dades personals
- Utilitzar el buscador per trobar pelicules i series
- Visualitzar per streaming les pelicules (si están **autoritzats**)
- Desar les pelicules en favorits
- Realitzar un proces de pagament (fictici)
- :couple: No hacen el proceso de pago. Cualquier usuario logueado ve la pelicula

*Es consideren **autoritzats** tots els usuaris que han realitzat el proces de pagament i hayan sigut validats previament per un administrador

**Administradors:**
- Llistar els usuaris
- Afegir/modificar les pelicules i la seva informació: Titol, descripció, enllaç, categoria, etc...
- Autorizar usuaris que hagin finalitzat el proces de pagament.
- Bloquejar comptes d'usuaris
- :couple: No cal que facin l'autorització del pagament

**Sistema:**
- Enviar un correu de confirmació quan un usuari es registra per verificar el seu mail.
- El sistema emmagatzemará el tipus de pelicules/series que visualitza un usuari per tal de recomenar-li pelicules/series del mateix tipus. 
- :couple: No cal que facin el sistema de recomenacions

> Totes les parts del projecte han de ser conegudes per tots els participants
> {.is-warning}

Este proyecto puede realizarse en cualquiera de los siguientes Framworks definido previamente por el profesor:

- Laravel 8.0

> Cada sprint ha de realizarse por uno o dos miembros del grupo y ser validado (testing) por otra persona diferente al que lo desarrolló
{.is-warning}

# Sprints User Interface

- **01. Instalacion Laravel**
Instala con Docker un servidor PHP en el que ejecutar la instalación de Laravel (Hello World)
a) Conexión con el servidor. http://netflix.edu
b) Instalación Laravel
c) Git del proyecto
- **02. Diagrama de casos de uso**
Realizar un diagrama donde se especifiquen todas las acciones que pueda realizar un usuario (con sus diferentes perfiles)
- **03. Diagrama de base de datos**
Realizar el diagrama de la base de datos
- **04. Mockups**
Realizar los mockups de cada una de las páginas:
a) Home
b) Lista de Peliculas
c) Resultado de busqueda
d) Pantalla de Login
e) Formulario de registro
-> Usuarios :hourglass:(1h)
f) Formulario de pago. :couple: No hacen esta pagina 
g) Formulario datos de usuario
h) Visualizar streaming
i) Pagina favoritos/recomendados :couple: No hacen los recomendados
- **05. Lista de URLs** :hourglass:(3h)
Crear la lista de URLs que conformarán la web con una breve descripción (incluida la información que se mostrará y la tabla de la DB donde se encuentra esa información)
- **06. Crear la base de datos**  :hourglass:(3h)
Usar las herramientas del Framework para crear la base de datos (tablas y contenido dummy)
- **07. Programar las vistas (solo HTML) de la aplicación diseñadas en los Mockups con las herramientas del Framework y Bootstrap utilizando información dummy**  :hourglass:(5h)
a) Fer unicament les vistes de frontend (sense el admin)
b) Routes on es relacionen les URL amb les vistes que es volen carregar.
- **08. Crear la página de la home.**  :hourglass:(3h)
- **09. Crear la pagina que lista las peliculas**
a) Controller que carga la vista de todas las peliculas
b) Model que devuelve la lista de peliculas
c) Controller que recibe la petición de filtro de peliculas
d) Model que devuelve la lista de peliculas filtradas
- **10. Crear el proceso de registro**
a) Controller que carga la vista del formulario
b) Verificador de formulario
c) Controller que procesa los datos del formulario
d) Model que guarda los datos del formulario
e) Control de usuario ya existe
- **11. Crear el proceso de login guardando las credenciales en session/cookie utilizando las herramientas del Framework**
a) Controller que carga la vista del formulario
b) Verificador de formulario
c) Controller que procesa los datos del formulario
d) Model que gestiona los datos del formulario
~~e) Si autorizado cargar los datos en session/cookies~~
- **12. Crear la página del resultado de busqueda**
- **13. Crear la página de streaming**
- **14. Crear la lista de favoritos**
Con tal de implementar las sessiones en el proyecto, los favoritos se cargaran en **session** en vez de en la base de datos. Así cuando el usuario le da a "Añadir a favoritos" lo que realmente está haciendo es añadirl una nueva pelicula a su sesión (sin DB). Cuando cargue la página de favoritos se listarán aquellas peliculas guardadas en la session.
- **15. Crear la página de formulario de pago**. :couple: NO la hacen
{.links-list}

# Sprints Dashboard

- **01. Instalacion Vue**
a) Crear un **nuevo** proyecto de Laravel que será el portal del administrador de Netflix. Deberá acceder mediante el subdominio [http://dashboard.netflix.edu](#)
b) Configurar Vue.js en Laravel
- **02. Diagrama de casos de uso**
Realizar un diagrama donde se especifiquen todas las acciones que pueda realizar el administrador
- **03. Diagrama de base de datos**
Revisar si el diagrama de base de datos necesita modificaciones para la gestion del administrador
- **04. Mockups**
Realizar los mockups de cada una de las páginas:
a) Lista de usuarios
b) Lista de peliculas
c) Información/Modificar de usuario
d) Pagina de autorización de pagos. :couple: No hacen esta página
e) Insertar/modificar pelicula
- **05. Lista de URLs CRUD/RESTApi**
Crear la lista de direcciones CRUD (Create-Read-Update-Delete) que conformarán la RESTApi de la aplicación.
- **06. Modificar la base de datos**
Usar las herramientas del Framework para modificat la base de datos (tablas y contenido dummy) si fuera necesario
- **07. Programar las vistas (solo HTML) de la aplicación diseñadas en los Mockups con Bootstrap utilizando información dummy**
a) NO utilizar todavia Vue en estas vistas. Se implementará en las tareas posteriores
b) Configurar las rutas de Laravel para que habrán cada una de las vistas
- **08. Configurar Laravel para aceptar peticiones exteriores API:**
a) Instalar el modulo de **Laravel Sanctum**
b) Crear la ruta de **login** en `routes/api.php` donde se enviará por AJAX las credenciales del administrador
c) Crear un controlador que al recibir el user/pass del administrador lo verifique con Auth y devuelva un **token** generado por Sanctum.
d) Crear una ruta de **/api/test** en `routes/api.php` que consulte la lista de peliculas a las peticiones con un token valido
{.links-list}
>  A partir de este momento se implementarán en cada vista los componentes de Vue que consultarán a la API. Todas las peticiones han de estar validadas (token) para ser respondidas.
{.is-info}
- **9. Crear la pagina de lista de usuarios**
- **10. Crear admin de usuario**
- **11. Crear la pagina de lista de peliculas/series**
- **12. Crear admin de peliculas/series**
- **13. Crear la pagina de autorización de pagos** :couple: No hacen esta página


{.links-list}