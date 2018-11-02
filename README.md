[![Build Status](https://travis-ci.org/VigoTech/vigotech.github.io.svg?branch=source)](https://travis-ci.org/VigoTech/vigotech.github.io)

# Introducción

Este repositorio contiene  a página web de La Rioja Tech Alliance.

## Trabajar en la WEB

A web está hecho usando [Hugo](https://gohugo.io/). Hay que trabajar conb markdown en la carpeta `content` o el  tema en la carpeta `themes` y genera una web estatica en `docs`.

### SETUP básica

Se quieres contribuir:

- Instala Hugo: https://gohugo.io/overview/installing/
- Se vas hacer una Pull Request, realiza un Fork del repositorio: https://help.github.com/articles/fork-a-repo/
- Clona el repositorio GitHub: https://help.github.com/articles/cloning-a-repository/
- siempre trabaja en branch `source`, el master se reserva para o contido final.

La carpeta del repositorio ejecuta:

```bash
git checkout source
git update-index --assume-unchanged content/page/proxectos.md
git update-index --assume-unchanged content/page/videos.md
git update-index --assume-unchanged content/post/vigotech-proxectos.md
git update-index --assume-unchanged content/post/vigotech-charlas.md
hugo server
```

Directamente pudes abrir la URL en el navegador. Según realices cambios, actualizanse el navegador de forma automática (al realizar los commits).


## Generación automatica de contenidos

A parte dos videos xenérase automáticamente (fan falta credenciais propias de Google Cloud, ver o link de enrriba). Tamén a parte dos proxectos.

A configuración está na carpeta scripts (channels.json e projects.json) e o script que teñe toda a lóxica é `vigotech.go`.

### Añadir un video

Os vídeos de YouTube se xeneran automáticamente con frecuencia diaria. Se o teu canal non está dado de alta, fai unha PR añadindo o novo canal o ficheiro `scripts/channels.json`.

Se non é un canal de YouTube, terás que añadilo cada vez creando una PR o ficheiro `scripts/scripts/videosNoYoutube.txt`

### Añadir un proyecto

Os proxectos se xeneran automáticamente a partir dun arquivo JSON. Desta forma, é doado mostrar aleatoriamente (frecuencia diaria) proxectos aleatorios na páxina principal.

Se queres añadir algún, fai un PR añadindo o proxecto o ficheiro `scripts/projects.json`.

### SETUP generación automática

Hai unha serie de requisitos extra para poder traballar localmente coa xeración automática de contidos 

- Ter [go](https://github.com/golang/go) instalado.
- Ter [gjson](https://github.com/tidwall/gjson) instalado.
- Dispor dunha API KEY de Google e ter a [API de Youtube habilitada](https://developers.google.com/youtube/v3/getting-started).

Hai incluido un script para Linux/MAC que pode ser de utilidade para aqueles que non traballaron nunca con Go:

```bash
# VERSION - OS - ARCH are optional
# Default: 1.8.1 - linux - amd64
bash scripts/quick_go_setup.sh VERSION OS ARCH
```

Isto instalará e/ou testeará Go no teu sistema ademáis de engadir as dependecias.

Unha vez instalados Go e as dependencias, crea unha variable de entorno coa túa API KEY de Google:

```bash
export YOUTUBE_TOKEN=123caramba
```

E finalmente executa o script `vigotech.go`:

```bash
go run scripts/vigotech.go
```

## Despliegue Automático

Unha vez o cambio súbese a `source`, [Travis](https://travis-ci.org/VigoTech/vigotech.github.io) encárgase de desplegalo. Non hai nada que facer nesa parte.

Ver [rcoedo web](http://rcoedo.com/post/hugo-static-site-generator/) para máis información.
