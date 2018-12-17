# Pagina web de riojatech.org

### Pagina web de Riojatech alliance creada con [HUGO](https://gohugo.io/) [![Build Status](https://travis-ci.org/LaRioja-Tech-alliance/www.lariojatech.org.svg?branch=source)](https://travis-ci.org/LaRioja-Tech-alliance/www.lariojatech.org)

[**Hugo**](https://gohugo.io/) es un software que permite crear sitios web  estáticos pero trabajando _casi_  como si fueran dinámicos.
 Para ello podremos usar diferentes plantillas que configuraremos, para luego añadir entradas y contenido dinámico fácilmente. 

Hugo usa [markdown](https://es.wikipedia.org/wiki/Markdown) para añadir los contenidos pero también podremos usar HTML, CSS y JavaScript si fuera necesario.

El programa, lo cual podemos hacer desde https://github.com/gohugoio/hugo/releases

Para hacer cualquier modificación  en la web deberemos realizar un clone de la rama 'source' y posicionarnos sobre el directorio `www.lariojatech.org`

El tema utilizado es **INITIO** 

https://github.com/miguelsimoni/hugo-initio

- **Probando la pagina web**

Ahora, para ver como va quedando nuestra página web, ejecutaremos este comando:

```
> hugo -F serve
```

De está manera se lanzara un pequeño servidor web el cual escuchara en el puerto 1313 .

Este servidor monitorizara los cambios en los ficheros de tal manera que si modificamos cualquier fichero, nuestra pagina web será recargada automáticamente.

En la dirección http://localhost:1313/ con nuestro navegador favorito podremos ver el resultado.

* **Añadir Eventos**

Para añadir eventos usar el comando: 

```
 > hugo new post/AÑO_MES_DIA.md
```

Esto nos creara un fichero bajo `content/post/` 

En la cabecera debe aparecer algo como esto:

~~~
---
title: "TITULO A PONER"
date: date: 2018-11-28T18:00:00+01:00 # Sera la fecha en que sera  el evento
draft: false ## Por defecto es true. Cambiarlo.
---
~~~
Debajo deberemos poner el contenido de nuestro articulo. Recordar que se puede usar el lenguaje **markdown** y también **HTML**.

Si ponemos la etiqueta `<!--more-->`  si nuestra plantilla lo soporta, separaremos el sumario de nuestro articulo, del articulo completo en si.

+ **Añadir Grupos**

Para añadir nuevos grupos se debe usar el comando: 

```
hugo new service/NOMBRE_GRUPO.md
```

Esto creara un fichero en `content/service/`

Deberemos modificarlo para que sea algo parecido a esto:

```
---
title: "GDG - LA RIOJA"
date: 2018-11-26T10:28:22+01:00
draft: false # Si es true no aparecera. Cambiarlo
weight: 1 # Orden en que aparecera en la pagina web
---
<a href="https://gdglarioja.blogspot.com/">![GDG LA RIOJA](/img/gdg_larioja.jpeg)</a>

<div class="social">
	<a href="https://gdglarioja.blogspot.com/">
		<i class="fa fa-globe"></i>
	</a>
	<a href="https://twitter.com/GDGLaRioja">
		<i class="fa fa-twitter"></i>
	</a>
	<a href="https://www.meetup.com/es-ES/GDG-La-Rioja/">
		<i class="fa fa-meetup"></i>
	</a>
	<a href="https://github.com/LaRioja-Tech-alliance/">
		<i class="fa fa-github"></i>
	</a>
</div>
```

* **Terminando cambios**

Una vez tenemos la página web como queremos, simplemente subiremos los ficheros a GitHub con 

```
> git add .
> git commit -a -m "CAMBIOS_REALIZADOS"
> git push
```

La pagina esta monitorizada por **travis.org** el cual generara automáticamente la pagina estática en la rama **master**  , que es lo que se presenta en la dirección http://lariojatech.org/

Tenéis un pequeño manual que complementa a este en  **uso_hugo.md**

Para dudas o comentarios mandar un correo a chuchip@gmail.com . También me tenéis en **slack** en  https://spaincommunity.slack.com en el canal **larioja-tech-alliance**





