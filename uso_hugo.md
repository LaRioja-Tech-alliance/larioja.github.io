### Trabajando con Hugo

Hugo**](https://gohugo.io/) es un software que permite crear sitios web  estáticos pero trabajando _casi_  como si fueran dinámicos.
 Para ello podremos usar diferentes plantillas que configuraremos, para luego añadir entradas y contenido dinámico fácilmente. 

 Hugo usa [markdown](https://es.wikipedia.org/wiki/Markdown) para añadir los contenidos pero también podremos usar HTML, CSS y JavaScript si fuera necesario.

 Para crear una pagina web lo primero que tenemos que hacer es bajarnos el programa, lo cual podemos hacer desde https://github.com/gohugoio/hugo/releases
 Una vez tengamos instalado **hugo** en nuestro ordenador, podremos empezar a crear nuestra propia pagina web.

Como primer paso abriremos un terminal y ejecutaremos la siguiente sentencia:

 ```
 > hugo new site mipagina
 ```

 Con esto **hugo** creara un directorio llamado 'mipagina' debajo del actual.  Nos moveremos a el directorio para poder instalar el tema con el que queremos que funcione nuestra página web.

```
> cd mipagina
```

En  https://themes.gohugo.io/ tenemos todas los temas (o plantillas) sobre las que basar nuestra página web. Estos temas están en su mayoría alojados en GitHub por lo cual lo más fácil para descargarlos es usar el comando **git** . De todos modos,  siempre tenemos la opción de descargar un fichero *zip* que después descomprimiremos en el directorio **themes**

Supongamos que queremos usar el tema **initio** que es el que usamos en la página  de [RiojaTech Alliance](http://lariojatech.org/) . Para ello iremos a su URL https://themes.gohugo.io/hugo-initio/ y pulsaremos sobre el botón '**Download**', lo cual nos llevara a **GitHub**, a la dirección https://github.com/miguelsimoni/hugo-initio. Allí descargaremos el fichero **ZIP**, dándole a l botón **Download ZIP**.

![github](.\github.png)



Después descomprimiremos el fichero ZIP dentro del directorio **themes** , de tal manera que la estructura de nuestros directorios será como la siguiente:

![directorios](.\directorios.png)

Suele ser una buena idea copiar el  contenido del directorio `example-site` dentro de nuestro directorio principal para tener una plantilla sobre la que empezar a trabajar.

* **Probando nuestra pagina web**

Ahora, para ver como va quedando nuestra página web, ejecutaremos este comando:

```
> hugo -F serve
```

De está manera se lanzara un pequeño servidor web el cual escuchara en el puerto 1313 .

Este servidor monitorizara los cambios en los ficheros de tal manera que si modificamos cualquier fichero, nuestra pagina web será recargada automáticamente.

En la dirección http://localhost:1313/ con nuestro navegador favorito podremos ver el resultado.

* **Añadiendo contenido**

Si queremos añadir una entrada en la pagina web usaremos este comando:

```bash
> hugo new post/post0.md
```

Esto nos generara el fichero 'post0.md' en el directorio **content/post/**

Este fichero tendrá el siguiente contenido.

```
---
title: "post0" # Nombre del post
date: 2018-11-01T11:21:58+01:00 ## fecha actual.
draft: true # Poner a false para que aparezca el evento
---

```

Debajo deberemos poner el contenido de nuestro articulo. Recordar que se puede usar el lenguaje **markdown** y también **HTML**.

Si ponemos la etiqueta `<!--more-->`  si nuestra plantilla lo soporta, separaremos el sumario de nuestro articulo, del articulo completo en si.



* **Configurando HUGO**

El fichero principal de Hugo esta en el directorio raíz y se llama `config.toml`

En este fichero configuraremos  el tema a usar , el titulo de nuestra pagina web y otra serie de parámetros.  Estos parámetros pueden variar de un tema a otro aunque siempre suele haber unos cuantos en común.

Esto es un extracto del fichero `config.toml` de la web www.lariojatech.org

```
baseURL = "http://lariojatech.org/"
languageCode = "es-es"
title = "La Rioja Tech Alliance"
theme = "hugo-initio"
publishDir = "docs"

[params]
    name = "La Rioja Tech Alliance"
    description = "Los grupos de tecnología de La Rioja hacemos piña para promover la tecnología "   
    favicon = "images/gt_favicon.png"
    DateForm = "2, January 2006"

    .....
    
```

Si queremos hacer algún cambio a la plantilla descargada deberemos cambiar los ficheros ubicados en `themes/NOMBRE_PLANTILLA/layouts/partials` . Ahí encontraremos una serie de ficheros donde se especifica el comportamiento de la plantilla.

En `themes/NOMBRE_PLANTILLA/_default` es probable que existan los ficheros list.html y single.html. En *single.html*  se definirá como se deben presentar una pagina de tipo lista, es decir cuando se deben mostrar diferentes artículos juntos. En _single.html_  se especifica como se debe presentar una pagina de un sola entrada.

* **Generando pagina web con HTML estático**

Para generar todos los ficheros que deberán ir en el servidor web, ejecutaremos el comando  

```
> hugo -F
```

Los ficheros, por defecto serán generados, en el directorio **public** . Ese comportamiento se puede cambiar añadiendo la directiva `publishDir`  en el fichero **config.toml**

El flag ""-F" es para obligar a Hugo a incluir los posts cuya fecha sea superior a la actual, pues por defecto no los incluye. Si no la pusiéramos todos los eventos futuros no aparecerían con lo cual como agenda pues seria un poco 'soso'  ;-) 





