# Introducción

## Características

Algunas de sus características principales son:

* Open Source
* Tipado estático
* Compila a código máquina
* Multiplataforma
* Concurrente
* Garbage collector
* Orientado a objetos, "si y no"

## Instalando Go

Para la instalación de *Go* descargaremos desde su [página](https://golang.org/dl/) el instalador correspondiente al Sistema Operativo que vayamos a usar.

Este binario de *Go* nos permite compilar, descargar e instalar paquetes y ejecutar otros comandos útiles.

##### Variables de entorno

Luego de la instalación debemos tener en cuenta las siguientes dos variables de entorno.

##### `GOROOT`
El instalador binario de *Go* comunmente se instala en:

| OS | PATH |
| ------ | ------ |
| Linux y Mac OS | /usr/local/go |
| Windows | C:\Go |

Y este path queda definido en la variable de entorno `GOROOT`.

GOROOT siempre se escanea antes de GOPATH.

##### `GOPATH`

* Este path es usado para resolver importaciones de paquetes.
* Enumera lugares para buscar el código.
* Especifica la ubicación del workspace.
* Este path no puede coincidir con el directorio de instalación.

Se pueden comprobar ambas varibles con el comando `go env`. Ejemplo:

```sh
$ go env
...
GOPATH="/Users/leonardorebola/go"
GOROOT="/usr/local/go"
...
# Entre otras variables que se listaran.
```

## Comprobar la instalación

Verificarmos invocando al comando *go* para imprimir su versin:
```sh
$ go version
```

Crearemos el fichero `hola-mundo.go`:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hola Mundo")
}
```

Compilamos y ejecutamos:

```sh
$ go run hola-mundo.go
```

## Editores y plugins

Tenemos una amplia variedad de opciones para desarrollar en *Go* que podremos ver  [acá](https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins) y seguramente elegir nuestro editor favorito.

Algunas opciones recomendables son:

| IDE | Plugin |
| ------ | ------ |
| [Atom](http://atom.io) | [go-plus](https://github.com/joefitzgerald/go-plus) |
| [Sublime Text](https://www.sublimetext.com/3) | [Golang Build](https://github.com/golang/sublime-build) |
| [Visual Studio Code](https://code.visualstudio.com) | [Go Language Support](https://visualstudiogallery.msdn.microsoft.com/bd7675ba-1bf5-4395-8c5a-4fc19dfc0d76) |

## Referencias

* https://golang.org/doc/install

___

###### Página: [1](./lectura-1.md), [2](./lectura-2.md), [3](./lectura-3.md), [4]
