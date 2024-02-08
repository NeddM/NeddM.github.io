---
layout: project
title: 'Regadío automático para IES La Marisma'
caption: ¡Mi proyecto de fin de grado!
description: >
  Este es un proyecto completo, donde desarrollo el Front-end con React, el Back-end se aloja en Google Firebase, y hace uso de un microcontrolador NodeMCU ESP8266.

date: 10 Jun 2023
image: 
  path: /assets/img/projects/regadio1.png
  srcset: 
    1920w: /assets/img/projects/regadio1.png
    960w:  /assets/img/projects/regadio1.png
    480w:  /assets/img/projects/regadio1.png
accent_color: '#283FCE'
accent_image:
  background: '#5D98F5'
theme_color: '#5D98F5'
sitemap: false
---

# Regadío automático para IES La Marisma

## Contexto
Todo comenzó una mañana, mientras estaba en clase con mis compañeros charlando en un cambio de hora mientras llegaba mi profesor. Una vez llegó el profesor a clase, nos comentó que tenía pensado hacer un sistema de riego automático para los chicos de la FP de jardinería; sería como un proyecto para el instituto.

El profesor comentó que quería hacer el proyecto en PHP, con un servidor hosteado en el instituto. Y yo le comenté que quería ayudarle, aunque nunca había programado en PHP. Luego olvidamos un poco el tema, porque el profesor estaba buscando empresas para que nosotros los alumnos podamos realizar las prácticas. Pero un buen día pensé que yo podría continuar con el proyecto, y eso hice.

## ¿Cómo está realizado el proyecto?
Yo decidí que iba a hacer un proyecto, pero no sabía programar en PHP, aunque hoy día si que he programado en ese lenguaje, pero en aquel momento no sabía que herramientas podría usar si hubiese decidido realizarlo en PHP. Pensé que lo mejor sería realizar el proyecto en lenguajes y tecnologías que yo conozca y tenga fluidez usandolas, y eso hice.

Por eso, aquí voy a separar el proyecto en tres partes distintas. Frontend, backend y micro controlador.

## Front end
Como ya comenté anteriormente, mi profesor comentó que su idea era realizar el frontend con PHP, de manera que fuera una interfaz web sencilla. En aquel momento yo no había programado nunca con PHP, así que decidí realizar el frontend con __ReactJS__.

Lo vi una buena alternativa por varios motivos:

1. El primer motivo es que tengo mucha más soltura usando React, pienso que con el tiempo se hace bastante sencillo crear proyectos web muy completos y modulares.
2. El segundo motivo es que ReactJS está muy bien optimizado, por lo que la aplicación web podría correrla en local cualquier equipo, aunque sea antiguo, que es la idea.
3. Es fácilmente porteable a React Native, por lo que se podría crear una aplicación para Android o para iOS, y la herramienta funcionaría de una manera muy similar a la que ya funciona en su versión ReactJS. Sólo habrían que hacer algunos cambios en la interfaz y listo.

La interfaz tiene tres menús distintos. Uno se trata de una página _Sobre Nosotros_, que sólo es una pestaña informativa, no es muy relevante en el funcionamiento del script. Luego tenemos un menú llamado _Programar riego_, este es el menú que más usaremos, ya que es donde vamos a iniciar el riego en nuestro jardín. Por último, tenemos un menú de _Historial_, donde podemos ver el historial de los riegos que se han realizado.

La interfaz como vemos es bastante sencilla, pero tiene justo lo que necesitamos. Tenemos tres inputs, para definir la duración de nuestro riego, y un botón para iniciar y parar el riego.

## Backend
En cuanto al backend, mi profesor pensó que sería buena opción usar una base de datos SQL, y yo pienso que podría haber realizado el backend de la misma manera, pero meditándolo bastante pensé que tendríamos que mantener online el servidor, pienso que no es un sistema tan independiente.

Yo decidí hostear el backend en __Google Firebase__. Creé una base de datos, y la conecté con la web, de manera que la información se actualiza desde la página web y desde el microcontrolador.


De esta manera, el backend estaría siempre disponible y de manera gratuita, ya que Google Firebase sólo requiere que se realice un pago si se realizan muchísimas peticiones al día, o si se excede de usuarios simultáneos.

En nuestro proyecto solamente vamos a tener un usuario simultáneo, y no se realizan tantas peticiones al día, no estamos ni cerca del límite que se nos establece. 

Por eso, pienso que usar Google Firebase es una buena decisión, además, así convierto el proyecto en algo más personal, con ideas que se me han ocurrido a mi mismo.

## Microcontrolador
En este caso sí que he usado la misma herramienta que me comentó el profesor, se trata de un microcontrolador __NodeMCU ESP8266__. Nos comentó que era un microcontrolador que funcionaba con _Arduino_, aunque no es de la marca Arduino. También que este modelo lleva incorporado WI-FI, lo cual lo hace bastante interesante. Y también nos comentó que es de un tamaño muy reducido, que nunca está de más.

Yo no sabía que para programar un Arduino se usaba el lenguaje C, es la primera vez que uso ese lenguaje, y he creado el script dando muchos palos de ciego, pero finalmente lo conseguí.

El microcontrolador se conecta a la base de datos de Google Firebase, y comprueba algunos datos. Si en los datos detecta que se tiene que poner a regar, él empezará a regar durante el tiempo que se le ha ordenado. Lo tengo programado para que inicie su funcionamiento mediante los pines, y que se active la luz led que lleva incorporado el microcontrolador. Lo he comprobado con lámparas y funciona perfectamente.

## Conclusión
Es uno de los proyectos más completos y reales que he realizado hasta el momento. Es increíble como usando tecnologías puedo automatizar tantas cosas, me parece muy interesante el mundo del _IoT (Internet of Things)_. Lo primero que pensé después de comprobar que todo funcionaba como yo me imaginaba varios meses antes, pensé en lo asombroso que sería domotizar toda mi casa el día que pueda comprarme una. Simplemente vi unas posibilidades inimaginables dentro de mi cabeza.

Ahora mismo tengo una caja con varios controladores para hacer pruebas, porque es algo que pienso que puede serme de muchísima utilidad en el futuro.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4TiylisdZuE?si=VgNeh4R2PEwguCmj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
