---
layout: project
title: 'Temtem Smash or Pass'
caption: Aplicación Smash or Pass del videojuego Temtem.
description: >
  Se trata de una aplicación de Smash or Pass de un videojuego en el que trabajan algunos amigos.
  Simplemente es un projecto por pasar el rato, ¡nada serio!

date: 9 Apr 2023
image: 
  path: /assets/img/projects/temsmash.png
  srcset: 
    1920w: /assets/img/projects/temsmash.png
    960w:  /assets/img/projects/temsmash.png
    480w:  /assets/img/projects/temsmash.png
links:
accent_color: '#F8A028'
accent_image:
  background: '#66B895'
theme_color: '#66B895'
sitemap: false
---

# Temtem Smash or Pass

# Introducción
Desde hace muchos años tengo relación con un amigo que trabaja en Crema Games, una empresa de videojuegos española que ha conseguido bastante éxito a partir de su proyecto llamado __Temtem__.

Temtem es un videojuego inspirado en Pokemon, aunque a la hora de jugar no tenga nada que ver con ese otro juego. Las mecánicas son distintas, la dificultad es bastante más grande en Temtem, no existe el factor suerte... Un juego muy interesante.

Pues recientemente vi una web de smash or pass de pokemon, y pensé que sería interesante hacer algo parecido con los Temtems, así también practico un poco el tema de crear APIs y bases de datos en MongoDB.

# Funcionamiento
La web está desarrollada con __ReactJS__, y como he comentado anteriormente, también hace uso de una base de datos en __MongoDB__.

La aplicación es sencilla; consigue los datos de los Temtem de la base de datos, y envía los votos al servidor, de manera que recopilo todos los votos que se realizan en la web, y puedo ver los datos desde Mongodb Compass.


Una vez el cliente pulsa un botón, la aplicación mostrará los votos totales de todo el público, y cuando pasen 2 segundos aproximadamente pasará al siguiente Temtem, así hasta que se complete toda la lista.


También he aprovechado y he montado la base de datos en un contenedor Docker, además lo he hosteado en uno de los VPS que tengo alquilados. ¡Funciona genial y es muy sencillo!

# Conclusión
Me propuse hacer una aplicación con MongoDB durante las vacaciones, y me ha parecido una idea graciosa. He disfrutado mucho haciendo este proyecto, me ha parecido tan interesante que me voy a informar más sobre crear APIs con NextJS.
