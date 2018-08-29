
## Instalando Go

Para la instalación de *Go* descargaremos desde su página [golang.org/dl](https://golang.org/dl/) el instalador correspondiente a la plataforma de Sistema Operativo que vayamos a usar.

Este binario de *Go* nos permite compilar, descargar e instalar paquetes y ejecutar otros comandos útiles.

##### Variables de entorno

Luego de la instalación debemos tener en cuenta las siguientes dos variables de entorno.

##### `GOROOT`
El instalador binario de *Go* comúnmente se instala en:

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

Se pueden comprobar ambas variables con el comando `go env`. Ejemplo:

```sh
$ go env
...
GOPATH="/Users/leonardorebola/go"
GOROOT="/usr/local/go"
...
# Entre otras variables que se listaran.
```

## Comprobar la instalación

Verificarmos invocando al comando *go* para imprimir su versión:
```sh
$ go version
```
## Ejecutar código

Crearemos el fichero `hola-mundo.go`:

```go
package main

func main() {
	println("¡Hola Mundo!")
}
```

Compilamos y ejecutamos con:

```sh
$ go run hola-mundo.go
```

En este caso `println(string)` es una función predefinida, no requiere referenciar ningún paquete.

El código siempre debe estar dentro del **workspace** *(definido por GOPATH)*, salvo no utilices las librerías estándar de *Go* ni otras librerías de terceros como en el ejemplo anterior.

- `go run` compila y ejecuta el código.
- `go build` compila y genera un ejecutable binario.

## Go Tool

Comandos de Go provistos por la *Go Tool*.

```sh
$ go command [arguments]
```

### Comandos
| Comando | Descripción |
| ----- | ----- |
| `build` | Compilar paquetes y dependencias. |
| `clean` | Elimina archivos de la cache. |
| `doc` | Muestra la documentación de un paquete o símbolo. |
| `env` | Imprime las variables de entorno de *Go*. |
| `bug` | Iniciar un informe de error |
| `fix` | Actualiza paquetes. |
| `fmt` | *gofmt* formatea el código fuente. |
| `generate` | Generar archivos Go por fuente de procesamiento |
| `get` | Descargar e instalar paquetes y dependencias. |
| `install` | Compilar e instalar paquetes y dependencias. |
| `list` | Lista de paquetes. |
| `run` | Compilar y ejecutar el programa Go. |
| `test` | |
| `tool` |  |
| `version` | Imprimir la versión Go. |
| `vet` | Reportar posibles errores en los paquetes. |
| `help` | "go help [command]" para más información sobre un comando. |


### Ejemplos:

```sh
$
```

```sh
$
```

```sh
$
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
* https://golang.org/cmd/go/

___

###### Página: [1](./lectura-1.md), [2](./lectura-2.md), [3](./lectura-3.md), [4]
