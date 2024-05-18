---
layout: project
title: "Github Workflow Finder"
caption: ¡Extensión de Google Chrome para ayudarte a trabajar con Github Actions!
description: >
  Extensión para Chromium que nos permite abrir referencias hacia Reusable Workflows o Custom Actions de manera sencilla.
date: 11 May 2024
image:
  path: /assets/img/projects/github-workflow-finder/portada-workflow-finder.png
  srcset:
    1920w: /assets/img/projects/github-workflow-finder/portada-workflow-finder.png
    960w: /assets/img/projects/github-workflow-finder/portada-workflow-finder.png
    480w: /assets/img/projects/github-workflow-finder/portada-workflow-finder.png
links:
  - title: Descarga la extensión
    link: https://chromewebstore.google.com/detail/github-workflow-finder/cnbkejpmllmplddidfjpifgghdapdlid?hl=es&authuser=3
accent_color: "#4a58f0"
accent_image:
  background: "#262732"
theme_color: "#30112250"
sitemap: false
---

# Github Workflow Finder

## ¿Qué es Github Workflow Finder?

Github Workflow Finder es una **extensión para Google Chrome**, y por supuesto, una extensión para cualquier otro navegador **Chromium** como pueden ser _Microsoft Edge_, _Brave_, _Opera_...

La premisa de desarrollar esta extensión fue por un problema muy repetitivo para las personas que trabajan con la tecnología **Github Actions**. A la hora de abrir un _Workflow Reusable_ o una _Custom Action_ teníamos que hacer una serie de acciones que rompían un poco con el flujo de trabajo que se estaba siguiendo.

Muy comunmente si tienen que seguir trazas de _Workflows Reusables_ y de _Custom Actions_ para comprobar si estas están realizando las tareas que esperamos. Estas trazas solemos seguirlas en la misma página web de **Github**, y hasta ahora, no había manera de abrir fácilmente una de estas referencias.

## Ejemplo de cómo se solían abrir estas referencias

Aquí muestro un ejemplo de cómo se abre esta referencia, en este ejemplo voy a abrir una referencia a una de mis _Custom Actions_.

La referencia que nos encontramos en los workflows es similar a esta:

```yaml
uses: actions/checkout@v3
```

Nosotros los _DevOps_ cuando queremos abrir este tipo de referencias lo que solemos hacer es copiar esta referencia completa y duplicar esta misma pestaña del navegador en la que nos encontramos ahora mismo.

![Copiamos la referencia](/assets/img/projects/github-workflow-finder/workflow-finder-1.png)
![Duplicamos la pestaña](/assets/img/projects/github-workflow-finder/workflow-finder-2.png)

Abrimos esta pestaña duplicada, y vamos a borrar todo el enlace, hasta que nos quedamos con `https://github.com/`.

![Borramos todo el slug restante](/assets/img/projects/github-workflow-finder/workflow-finder-3.png)

Una vez tenemos esto, vamos a pegar la referencia que hemos copiado. Vamos a borrarle la parte de la rama, y nos vamos a quedar sólo con el _propietario_ y el _repositorio_ `actions/checkout`.

![Referencia sin la rama](/assets/img/projects/github-workflow-finder/workflow-finder-4.png)

Ahora tendríamos montada casi la URL que buscamos: `https://github.com/actions/checkout`.

Lo que tenemos que hacer a continuación es _pulsar enter_, y vamos a abrir la rama o el tag que buscamos a mano, de manera que llegamos a la referencia exacta que estamos llamando.

![Abrimos el tag o la rama](/assets/img/projects/github-workflow-finder/workflow-finder-5.png)

Si hablamos de _Workflows Reusables_ la cosa se complica un poco más, porque además tenemos que borrar de la referencia hasta el directorio `.github`.

## Cómo solventa la extensión este problema

Desde la primera versión, la manera en la que abrimos los enlaces es abriendo el popup de la extensión, pegando la referencia, y haciendo click en buscar. Ya esto acorta mucho la tarea tediosa que teníamos que hacer para abrir la referencia.

![Buscamos desde el popup](/assets/img/projects/github-workflow-finder/portada-workflow-finder.png)

Ahora, la manera más simple de abrir estas referencias es seleccionado la referencia a la que nos queremos dirigir, luego hacemos click derecho, y hacemos click sobre el botón de _Abrir en una nueva pestaña_.

![Abrir en una nueva pestaña](/assets/img/projects/github-workflow-finder/open-newtab-workflow-finder.png)

De esta manera, no tenemos ni que copiar datos. Simplemente seleccionamos y nos dirigimos hacia ese Reusable Workflow o Custom Action.

## Tecnologías usadas

Para mi, el desarrollo de una extensión de navegador era un mundo completamente nuevo. Nunca antes había desarrollado algo así.

Descubrí que el stack tecnológico es el mismo que el de desarrollo web.

-   **HTML** para construir el esqueleto de nuestra extensión.
-   **CSS** para darle color y estilo. Dejarlo bonito en general.
-   **Vanilla JavaScript** para añadirle las funcionalidades que necesitamos.

Por suerte ya he estado trabajando recientemente con _JavaScript_ y con _TypeScript_, te recomiendo que vayas a ver mi entrada sobre cómo crear [**Custom Actions con TypeScript**](https://neddm.github.io/blog/2024-02-08-crea-github-action-con-typescript/).

## Conclusión

A veces se hace complicado desarrollar herramientas nuevas que no hayan sido pensadas anteriormente, lo cual es algo bueno, porque siempre vamos a tener un stack de tecnologías diferentes que hagan lo mismo, pero nos permitirán tener el derecho a decidir.

Con este proyecto he sentido que he puesto solución a un problema o incomodidad que no estaba solventado anteriormente, ya que suele ser una tecnología que sólo tocan los _DevOps_, que en general no se dedican a crear extensiones de navegador.

Pensé que esta solución podría ser interesante para algunos compañeros míos de trabajo, por eso se la compartí una vez que la aplicación ya pasó los procesos de análisis de Google. Y la verdad que están contentísimos que que ahora su trabajo sea mucho más fluido.

Puedes descargar esta extensión en la [Google Chrome web store](https://chromewebstore.google.com/detail/github-workflow-finder/cnbkejpmllmplddidfjpifgghdapdlid?hl=es)
