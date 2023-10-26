---
layout: project
title: 'pyPurped & pyClipMaker'
caption: No solo un script de Python, ¡también es un canal de YouTube!
description: >
  This is how I use Hydejack on my personal site. 
  Much of the development is informed from my experience of using it myself, creating a tight feedback loop.
date: 2 Jan 2023
image: 
  path: /assets/img/projects/pypurped-imagen.png
  srcset: 
    1920w: /assets/img/projects/pypurped-imagen.png
    960w:  /assets/img/projects/pypurped-imagen.png
    480w:  /assets/img/projects/pypurped-imagen.png
links:
  - title: Link
    url: https://github.com/NeddM/pyPurped
accent_color: '#B200AB'
accent_image:
  background: '#36007F'
theme_color: '#36007F'
sitemap: false
---

# Historia
Para empezar a hablar sobre este proyecto considero importante que conozcamos un poco sobre el pasado de la música [Chopped and Screwed](https://es.wikipedia.org/wiki/Chopped_and_screwed). Fue un género creado por [Dj Screw](https://en.wikipedia.org/wiki/DJ_Screw) en Houston, Texas, en la década de los 90.

Es un género que se basa en ralentizar canciones y añadirle algo de reverb a la canción ralentizada. A veces también podemos encontrar algunos cortes creativos, pero eso ya depende del DJ. Es muy curioso porque con la canción ralentizada podemos escuchar de manera mucho más clara los instrumentos que se usan en las canciones, los samples, las voces de los cantantes, etc…

![Dj Screw en su estudio](https://mixmag.net/assets/uploads/images/_facebook/DJ-Screw-1.jpg)

Es un género muy extendido por todo el mundo, sobre todo por Estados Unidos, y también es un recurso que los artistas usan actualmente como un recurso musical, para por ejemplo terminar canciones.

Este género también es llamado de otras maneras, como _Slowed and reverb_ o _Slowed and purped_.

Por ello he decidido bautizar este script con el nombre de __pyPurped__, por Python y por el género.

# pyPurped
El uso del script es muy sencillo. Está programado en Python, y vamos a necesitar algunas dependencias para que funcione correctamente.

```shell
pip install AudioSegment
pip install youtube_dl
```

Una vez tenemos las dependencias instaladas, hay que clonar el repositorio de [pyPurped](https://github.com/NeddM/pyPurped). La idea es añadir los enlaces de las canciones en el archivo _Enlaces.txt_, pero es importante que los enlaces se introduzcan sin espacios, y uno abajo del otro, como se muestra en el siguiente ejemplo.

```
https://youtu.be/ockzzfKbFOE
https://youtu.be/L8aIUhkeoxI
```

Incluso también podemos añadir un sólo enlace con una playlist.

Con sólo introducir el enlace, el script se encargará automáticamente de descargar las canciones, renombrarlas, borrar las canciones descargadas y mantener sólo las canciones ralentizadas.

Podrás encontrar las canciones en la carpeta llamada _Procesado_.

# pyClipMaker
Yo que soy una persona de escucharme discos completos, empecé a crearme muchos de mis discos favoritos ralentizados, pero me enfrenté a algunos problemas.

El primer problema es que no tenía una plataforma gratuita en la que pudiera disfrutar la música, igual que disfruto de la música normalmente. Pensé que Youtube sería una muy buena alternativa, ya que puedo subir los videos que yo quiera, y realmente no me importa que se detecte el copyright de las canciones y no llevarme nada de ingresos. De hecho lo prefiero, quiero que los beneficios vayan a los artistas, yo simplemente quiero disfrutar de la música ralentizada.

Una vez tuve decidido que quería subir las canciones a YouTube, empecé a montar yo mismo los videos del primer disco que tenía pensado subir, y eso me llevó varias horas, horas que realmente las considero perdidas.

Pensé que sería buena idea crear un script que me montara los videos automáticamente, y ahí nace mi siguiente script [pyClipMaker](https://github.com/NeddM/pyClipMaker).

Se trata de otro script en Python, que usa la dependencia de _moviepy_ para crearme clips de videos.

```shell
pip install moviepy
```

El uso del script es muy sencillo. Simplemente tenemos que añadir las canciones que queramos convertir a clip de video, dejaremos las canciones en la raíz del proyecto.

Luego tenemos que añadir una imagen, que será la imagen que ser verá de manera estática durante todo el video, como las canciones que se suben automáticamente a YouTube.

Ejecutamos el script, y todos los clips de video aparecerán en una carpeta llamada _procesado_. Posteriormente se borrarán las canciones para que no quede basura en nuestra carpeta del proyecto, y podamos seguir creando videos como si fuera una cadena de producción.

# Canal de YouTube de pyPurped
Por último, ya sólo quedaba crear el canal de YouTube de __pyPurped__, donde he estado subiendo contenido cuando he tenido tiempo, y varias canciones han conseguido bastantes visitas y buenos comentarios. ¡Lo que significa que es trabajo está bien hecho!.

En la descripción de todas las canciones aviso que no quiero ningún beneficio por el proyecto, simplemente es un proyecto para que podamos disfrutar de las canciones ralentizadas.

<iframe width="560" height="315" src="https://www.youtube.com/embed/z7DOzecYPEk?si=3xdprtlf16jhrUq_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Despedida
Este ha sido mi primer artículo en mi web, espero que lo hayas disfrutado o que te haya servido. ¡Que tengas un buen día!
