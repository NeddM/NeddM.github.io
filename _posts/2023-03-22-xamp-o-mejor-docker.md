---
layout: post
title: ¿XAMP para Linux? ¡Mejor Docker!
description: >
  ¡La mejor manera de visualizar tu proyecto en Linux es Docker!
sitemap: false
accent_image: 
  background: url('https://cdn.swish.ink/a9af59c2-0fdb-4a2a-9a9f-719eeb17b3b0/media/docker-wordpress.png') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
hide_last_modified: true
invert_sidebar: true
---

# Introducción
Como ya sabéis, últimamente he estado muy interesado en la creación de temas y plugins para WordPress, pero durante este trayecto me he encontrado con una gran duda. _¿Cómo me hago un live-server de PHP?_.


Yo nunca antes había programado con PHP, y por lo que leí por internet, era necesario el uso de un software como _XAMP_, _LAMP_ o _Laragon_. Pero yo no quería depender de esos software, ya que por un tiempo usé XAMP en Windows, y la verdad, notaba que el rendimiento de mi PC no era el mejor después de realizar la instalación. Quizás sea sólo sensación mía, pero yo sospechaba mucho que ese software tuviera virus, nunca me he llegado a fiar del todo...


Así que después de buscar alternativas por internet, pensé que podría crearme mi propio servidor usando un archivo __docker compose__, y creo que ha sido la mejor opción. Primero porque así gano más experiencia con Docker, aunque sea algo realmente simple, pero nunca está de más encontrar soluciones a problemas del día a día, y crear la solución de manera “manual”. Siempre he sido partidario de crearme mis propias aplicaciones para problemas en los que quizás ya existían herramientas para ello.

# Archivo docker-compose.yml
Por lo tanto, sin más, me puse al lío. El archivo de __docker compose__ es el siguiente:

```docker
version: "3"

services:
  db:
    image: mariadb:10.9.5
    volumes:
      - data:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=123456
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=nedd
      - MYSQL_PASSWORD=123456

  web:
    image: wordpress:php8.1
    depends_on:
      - db
    volumes:
      - ./target:/var/www/html
    environment:
      - WORDPRESS_DB_USER=nedd
      - WORDPRESS_DB_PASSWORD=123456
      - WORDPRESS_DB_HOST=db
    ports:
      - 8080:80

volumes:
  data:
```


Como vemos, es bastante sencillo, simplemente necesitamos un contenedor con la base de datos que en este caso es un __mariadb:10.9.5__, y otro contenedor WordPress que en este caso es __wordpress:php8.1__.


También hay definidas varias variables de entorno. En tu caso tú pon las variables que más te gusten. De todas formas, tendrás que crear un usuario una vez inicies el contenedor, así que no te preocupes mucho por ellas, simplemente son variables para que se entiendan los dos contenedores entre ellos.


Bueno, una vez tenemos listo nuestro archivo de _docker compose_, ¡vamos a ponerlo en marcha!. La primera vez va a tardar mucho más en encenderse, ya que se tienen que descargar las imágenes de los contenedores, pero cuando lo usemos diariamente vamos a observar que encender nuestro servidor es muy sencillo y muy rápido.


En la carpeta donde tenemos guardado nuestro archivo _docker-compose.yml_, escribimos:

```docker
docker compose up -d
```


En el caso de que quieras ver los registros de las actividades que se realizan al momento, puedes quitar el `-d`, yo pienso que no son datos relevantes así que dejo los contenedores corriendo en modo _detatch_.

# ¿Cómo puedo ver la web?
Cuando nuestros contenedores estén en marcha vamos a dirigirnos a nuestro navegador web favorito, y vamos a entrar en la dirección de nuestro contenedor:

```
localhost:8080
```

El puerto podemos cambiarlo si queremos, aunque el puerto 8080 es fácil de recordar así que yo prefiero dejarlo tal que así.
