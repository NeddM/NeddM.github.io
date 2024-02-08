---
layout: project
title: 'APIs que realizan webscraping'
caption: Algunas APIs que realizan webscraping con Go y demás lenguajes.
description: >
  Hablo un poco sobre el webscraping. Me parece algo interesante y que haciendo uso del ingenio se pueden crear aplicaciones muy completas.

date: 17 Jun 2023
image: 
  path: /assets/img/projects/webscraping1.png
  srcset: 
    1920w: /assets/img/projects/webscraping1.png
    960w:  /assets/img/projects/webscraping1.png
    480w:  /assets/img/projects/webscraping1.png
links:
  - title: API
    link: https://rapidapi.com/Nedd/api/noticias-economia-espanol/
accent_color: '#809E62'
accent_image:
  background: '#965CB1'
theme_color: '#965CB1'
sitemap: false
---

# APIs que realizan webscraping

Me fascina el mundo de las APIs, realmente me sorprende mucho que existan APIs tan completas, con tal cantidad de datos. Y lo que más me sorprende es que se reciben los datos de una manera muy rápida.

Este funcionamiento supone un background bastante cerrado, por más que se busca información cuesta mucho encontrar una metodología que seguir de manera religiosa; unas buenas prácticas por decirlo de alguna manera. Pero la manera de crear estas APIs parecen prácticamente secreto de sumario.

## ¿Cómo empezó todo esto?
Hace ya dos años me interesé por el web scraping. Hice mucho uso de _Beautiful Soup_, que se trata de un paquete de Python que permite filtrar la información de una página web a partir de etiquetas HTML y sus atributos, como podrían ser sus clases CSS o su HREF.

Cuando estudiaba el grado de telecomunicaciones un profesor siempre decía una frase muy usada, al menos aquí en España, que era: _cada maestrillo tiene su librillo_. Y qué razón tenía… En este mundo de las APIs a partir de web scraping hay que poner esa frase en práctica.

Hay que tener en cuenta incluso la velocidad en la que se realiza el escaneo, y la manera más eficiente de mantenerlo. Ya que el web scraping en muchas páginas web viola los términos y condiciones. Nuestra misión es intentar pasar desapercibidos, como si nuestros robots fueran humanos. Para ello los desarrolladores han realizado todo tipo de bilguerías, como por ejemplo navegar a otros menús no tan interesantes a la hora de buscar información. O por ejemplo hacer uso de algoritmos algo más aleatorios.

También es una buena opción crear una base de datos, y guardar los datos en tu red conforme vas consiguiendo información. De esta forma, se evita que se busque la misma información dos veces, ya que ese proceso carga mucho la red, y el objetivo siempre es el mismo. Es una evidencia de que eres una API.

Todo esto y mucho más son cosas que tienes que ir probando por ti mismo, y encontrar cual es la manera más eficiente de realizar la recolección de datos.

He creado varias APIs de este tipo, algunos ejemplos son un scraper de precios de videojuegos en distintas páginas web, donde sufrí un parche de la empresa, que evita que se pueda seguir consiguiendo los datos de esa manera.

## Algunos ejemplos
La última API de este tipo que he creado fue con el lenguaje de programación Go. Ahora mismo está en producción y se encarga de buscar noticias sobre economía. Recolecta las últimas noticias y se las devuelve al cliente que está usando la API.


Es interesante porque se realiza un scrape de muchas webs, y hay que preparar una función distinta para cada una de ellas porque ninguna de las webs son iguales unas a otras.

[Puedes hacer uso de esta API en esta web](https://rapidapi.com/Nedd/api/noticias-economia-espanol/).

Para lanzar la API a producción se necesita tener conocimientos de DevOps, ya que para poder ofrecer el servicio hay que hostearlo en algún servidor. 

Yo decidí construir una imagen en Docker, y la hosteo en uno de mis servidores VPS. El servidor se encargará de realizar el scrapeo, y devolverá todos los datos en formato JSON.

Con el tiempo se encontrarán alternativas para que mejoren todo este proceso, ya sea que consuma menos gasto (porque mantener el VPS online conlleva un gasto), o mejorar la manera en la que se scrapea, por ejemplo haciendo uso de varios proxies.

## Conclusión
El mundo del backend y las APIs es muy amplio, mucha gente opina que sólo se tiene que saber gestionar los datos, ¿y eso les parece poco?. Pienso que esto de hacer web scraping va más allá de saber programar, hay que saber disimular, tener la picardía de como realizar algunos logins, etc...

Yo seguiré creando este tipo de scripts, que aunque yo los estaba realizando en el lenguaje Go, tambien he probado con otro tipo de lenguajes más optimizados, como lo son Rust o JavaScript. Además este tipo de APIs permite generar pequeños ingresos pasivos, que nunca vienen mal, aunque sean para pagar los VPS.
