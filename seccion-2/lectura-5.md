## Instalación en Mac OS





#### Comprobar las variables

Se pueden comprobar ambas variables con el comando `go env`.

```sh
$ go env
...
GOPATH="/Users/leonardorebola/go"
GOROOT="/usr/local/go"
...
# Entre otras variables que se listarán.
```

#### Comprobar la instalación

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

