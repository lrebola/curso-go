
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




## Referencias

* https://golang.org/doc/install

___

###### Página: [1](./lectura-1.md), [2](./lectura-2.md), [3](./lectura-3.md), [4]
