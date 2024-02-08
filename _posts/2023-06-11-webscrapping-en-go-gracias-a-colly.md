---
layout: post
title: Webscrapping en Go, gracias a Colly
description: >
  ¡Una manera distinta de realizar webscrapping!
sitemap: false
accent_image: 
  background: ('https://miro.medium.com/v2/resize:fit:835/1*T7h7z9jamTFyf4U8yQZ_TQ.png') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
hide_last_modified: true
invert_sidebar: true
---

![Header image](https://miro.medium.com/v2/resize:fit:835/1*T7h7z9jamTFyf4U8yQZ_TQ.png)

A la hora de hablar sobre webscraping, la primera herramienta que se nos viene a la cabeza suele ser Beautiful Soup 4, un paquete de Python que es de los más conocidos para realizar scraping en webs.

Es muy conocido por la facilidad que nos otorga, pero es cierto que hoy día lo tienen muy analizado, incluso nos hemos encontrado guiños a la hora de hacer scraping con esta herramienta, como por ejemplo cuando hacemos scraping a la web de Amazon. Por eso hoy voy a hablar de una herramienta que he usado mucho últimamente para crear distintas APIs.


## ¿Qué es Colly?
Colly es un paquete para realizar web scraping, programado en Go y pensado para ser usado en Go. Uno de los puntos fuertes de esta herramienta es su sencillez y la facilidad que nos otorga para recoger datos.

```go
func main() {
	c := colly.NewCollector()

	// Find and visit all links
	c.OnHTML("a", func(e *colly.HTMLElement) {
		e.Request.Visit(e.Attr("href"))
	})

	c.OnRequest(func(r *colly.Request) {
		fmt.Println("Visiting", r.URL)
	})

	c.Visit("http://go-colly.org/")
}
```

Con una simple función como la anterior, podemos recoger los datos de varias webs.


## Instalación de Colly
Como hemos mencionado anteriormente, Colly es un paquete de Golang. Por lo tanto, tenemos que instalarlo dentro de nuestro proyecto.

```go
module github.com/x/y

go 1.14

require (
        github.com/gocolly/colly/v2 latest
)
```

## Documentación
[Podemos encontrar la documentación en su web](https://go-colly.org/), a mi parecer es muy intuitiva y fácil de perfeccionar. También podemos encontrar varios ejemplos, para las personas que entiendan mejor observando casos prácticos.


## Conclusión
Despues de informarme sobre las herramientas de web scrapping que existen en el lenguaje Go, he llegado a la conclusión de que esta es la más cuidada. Y al ser un lenguaje no tan “mainstream”, no está lo suficiente baneada de las webs. No como ocurre con herramientas como BS4, que pueden llegar a sernos inútiles si no la usamos con mucha maña.

Además, tenemos el añadido de que Go es un lenguaje que permite realizar concurrencia de manera muy sencilla, por lo que esto nos abre un nuevo abanico de posibilidades a la hora de recoger datos.
