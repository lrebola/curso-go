## Instalación en Windows

- Descarga e instalación del binario
- Configurar y comprobar las variables de entorno
- Comprobar la instalación
- Ejecutar un "Hola Mundo"


#### Descarga e instalación
Link de descarga: [https://golang.org/dl](https://golang.org/dl/)

#### Configurar y comprobar las variables de entorno

```sh
$ go env
...
GOPATH="C:\Go"
GOROOT="C:\Go"
...
# Entre otras variables que se listarán.
```

#### Comprobar la instalación

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

