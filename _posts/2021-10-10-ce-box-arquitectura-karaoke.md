---
layout: post
title: "CE Box, Arquitectura Karaoke"
date: 2021-10-10
---



El siguiente proyecto es el primer proyecto del curso SOA4ID el cual consiste en la creacion de una karaoke en una arquitectura monolitica.
Pero para poder desarrollar el diseño de la arquitectura es necesario entender que es una arquitectura monolotica.

Una arquitectura monolitica es aquella donde todo el proyecto esta hosteada en un mismo lugar, es decir sus componentes compartes mismos recursos y memoria. Eso no quiere decir que su construccion sea en el mismo lugar, lo que quiere decir es que a la hora de su compilacion se empaqueta todo en un mismo modulo.

Este tipo de arquitecturas son necesarias donde las aplicaciones necesitan ser autosuficientes y/o necesitan que su procesamiento sea mas rapido.

Tomando esto en cuenta se puede diseñar la arquitectura del sistema.

## Nivel 1

El sistema tiene en primera instancia va a ser accedido por un publico general que tenga acceso a internet. 
![Nivel1]({{site.url}}/assets/images/Karaoke-Nivel1.jpg)

Estos usuarios van a acceder a la pagina web de karaoke. El sistema va a estar escuchando al usuario una vez que empiece a cantar y va a estar informando al sistema de procesamiento 

## Nivel 2

En este nivel se expande el sistema para poder seleccionar los lenguajes de programacion adecuados para el sistema
![Nivel2]({{site.url}}/assets/images/Karaoke-Nivel-2.jpg)

En este segundo nivel sacamos que el sistema no necesita ninguna aplicacion movil, simplemente se puede usar una pagina web responsive para cualquier tipo de pantalla. Esta decision esta basada de acuerdo a las especificaciones del proyecto.


Esta pagina web ademas se va a conectar a un sistema de Backend que proporciona un api donde permitiria hacer las consultas sobre el manejo de usuarios y canciones. Ademas mantengo el sistema de reconocimiento de voz conectado a la api permiento procesar ir generando por ususario un puntaje de acierto.
Al ser una web-app sencilla la mejor opcion con el framework es Angular, permite versatilidad y libertad para el manejo de la app y la conexion con un api service. Pero no permite la expacion a una app movil por lo que en este caso es una buena opcion.

Para el desarrollo de la api, al ser una app sencilla que permita conectar la base de datos y generar metodos de GET/POST/PATCH/DELETE por lo que la opcion mas sencilla y simple de usar es nodeJS
Y por ultimo la base de datos, es una base de datos sencilla pero que su consulta permita hacer busquedas a sus datos y sus atributos sensibles a mayusculas/minusculas por lo que la mejor opcion para este caso es una Base de Datos de Mongo en este caso con un schema de moongose

Es esencial en este punto señalar el sistema de integracion continua y las pruebas unitarias que va a realizar el sistema de DevOps para que el desarrollo de la app sea lo mas libre de errores posible

## Nivel 3
En el tercer nivel toca diseñar la parte interna del backend

![Nivel3]({{site.url}}/assets/images/Karaoke-Nivel-3.jpg)

Tenemos entonces los principales modulos de trabajo.El modulo de autenticacion que esta formado por auth Middleware donde se validara que el usuario se autentice, el modulo de inicio de sesion y el modulo de seguridad donde permitira registrar y verificar credenciales.

Para el Karaoke tenemos el Songs Services y Songs Controller que permitira extraer la canciones y ejercer operaciones sobre ellas respectivamente. Todas estas como se habia dicho anteriormente se conectaran a una base de datos mongoDB

## Nivel 4
