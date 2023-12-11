---
layout: project
title: 'Nonsible'
caption: ¡Nonsible es una alternativa a Ansible programada en Rust!
description: >
  Software programado en Rust como alternativa a Ansible.
  Había funciones y comportamientos en Ansible que a mi me dejaban un poco que desear... Por eso decidí tomar mi propio camino y crear Nonsible.
date: 10 Oct 2023
image: 
  path: /assets/img/projects/Nonsible1.png
  srcset: 
    1920w: /assets/img/projects/Nonsible1.png
    960w:  /assets/img/projects/Nonsible1.png
    480w:  /assets/img/projects/Nonsible1.png
links:
  - title: Repositorio
    link: https://github.com/NeddM/nonsible
accent_color: '#808080'
accent_image:
  background: '#93C460'
theme_color: '#93C460'
sitemap: false
---

# Nonsible

# Introducción
__Nonsible__ nace por cubrir algunas de las necesidades o problemáticas que no cubre Ansible. Pensé que sería buena idea construir un software similar, que permita realizar tareas mediante conexiones SSH independientemente del sistema operativo en el que se ejecute.

Además está desarrollado en __Rust__. Un lenguaje más moderno y más rapido que el que usa Ansible (Python).


# Ventajas de Nonsible

La primera ventaja que nos encontramos es que se trata de un software multiplataforma. Podemos correr nuestras tareas y ejecuciones independientemente del sistema operativo que la esté ejecutando.

También es un software perfecto para realizar pequeñas tareas. Ya que puedes realizarlas tanto de manera imperativa, como respondiendo las preguntas que te lanza el prompt de la aplicación. Haciendolo muy interactivo e intuitivo.

Es un software muy fácil de escalar y de modular. Ya que podemos declarar todas nuestras tareas y conexiones en distintos archivos _YAML_. 

# Maneras de usar el software

Considero que es un software que se adapta a las necesidades de cada individuo, ya que se puede ejecutar de manera interactiva; respondiendo todas las preguntas que te lanza el prompt. También podemos correr el programa de manera semi-interactiva; que nos permite añadir el archivo _YAML_ de conexiones, y ejecutar las tareas de manera interactiva. Y por último también podemos correr el programa de manera desatendida (mi favorita); de esta manera podemos tener todas nuestras conexiones y nuestras tareas modularizadas en un repositorio y depender de ellas ejecutándolas directamente desde una pipeline o un workflow.

# Labels y Matchlabels
Recientemente he añadido una nueva funcionalidad que nos permite ejecutar ciertas tareas dependiendo de las labels que se tengan asignadas en las conexiones y en las tareas.

Esto puede ser muy util para tareas como la de instalar un WordPress, donde también tenemos que realizar la instalación de una base de dato MySql, y quizás no lo queremos todo en el mismo equipo.


# Argumentos para mejorar nuestra experiencia
Nonsible también dispone de algunos argumentos que nos pueden servir a la hora de realizar nuestras instalaciones y ejecuciones.

Algunos de estos argumentos nos permite continuar con la ejecución en el caso de que no se haya podido conectar a algún equip, o continuar con la ejecución si una tarea falla... 

¡Podrás encontrar mucha más información en el README.md del [repositorio de Nonsible](https://github.com/NeddM/Nonsible)!
