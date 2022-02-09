---
title: GraphQL
description: 
published: true
date: 2022-02-08T15:12:24.935Z
tags: 
editor: markdown
dateCreated: 2022-02-07T14:19:58.624Z
---

# Cóm funciona la REST API de Laravel?

> Pots trobar més informació de com utilitzar la API REST a l'apartat 
[GRAPHQL LARAVEL](/ca/informatica/daw/m7/uf3/graphql)
{.is-info}

# Posem-ho en práctica :collision:
Primero descargamos el proyecto del tutorial:
https://github.com/dantriano/m7-laravel8-tutorial/tree/api

```php
/*
* Instalamos los paquetes necesarios de GraphQL
*/

composer require nuwave/lighthouse
php artisan vendor:publish --tag=lighthouse-schema
composer require mll-lab/laravel-graphql-playground

```
## Definir los type, query y mutations
La definición de los types se realiza en archivos con extensión .graphql. Crearmos uno por cada tipo de dato (modelo) de nuestro proyecto Laravel. Y los importaremos a un archivo central **graphql/schema.graphql** que es el que utilizará GraphQL para definir todo su funcionamiento.
```graphql
"""
graphql/schema.graphql
"""
#import user.graphql
#import product.graphql
```

> Se importan archivos .graphql en otras ubicaciones con el prefijo #import
{.is-info}

## Definir el GraphQL de Usuario

```graphql
"""
graphql/user.graphql
Definimos  el type, algunos query y mutations del usuario
"""

type User {
  id: ID!
  name: String!
  email: String!
}

extend type Query {
  user(id: ID! @eq): User @find
  users: [User!]! @all
}

extend type Mutation {
  createUser(name: String!, email: String!, password: String!): User @create
}
```
Podemos probar si funciona con la siguiente query:

```graphql
"""
Peticion para introducir en: http://localhost/graphql-playground
"""

{
  one:user(id: 1) {
    id
    name
    email
  }
  two:user(id: 2) {
    id
    name
    email
  }
  users {
    id
    name
    email
  }
}
```


## Definir el GraphQL de Producto

```graphql/product.graphql
"""
Definimos  el type, algunos query y mutations del usuario
"""

type Product {
  id: ID!
  name: String!
  desc: String
  price: String
  category: Category
}

type Category {
  id: ID!
  name: String!
}

extend type Query {
  product(id: ID! @eq): Product @find
  products: [Product!]! @all
}

```

Podemos probar si funciona con la siguiente query:

```graphql
"""
Peticion para introducir en: http://localhost/graphql-playground
"""

{
  product(id: 1) {
    id
    name
    category{
      id
      name
    }
  }
}
```

## Generar documentación API
En GraphQL la documentación se genera automaticamente ya que esta vinculada a la definicion de los types , los querys y los mutations