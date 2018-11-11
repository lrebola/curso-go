## Instalación en Windows

- Descarga e instalación del binario.
- Comprobar las variables de entorno.
- Instalar un versionador de código.
- Ejecutar un "Hola Mundo".

#### Descarga e instalación del binario
Instalador: [https://golang.org/dl](https://golang.org/dl/)

#### Comprobar la instalación

```sh
$ go version
go version go1.XX.X X/X
```

#### Comprobar las variables de entorno

```sh
$ go env
...
GOPATH="C:\Users\<TU_USUARIO>\Documents\Go"
GOROOT="C:\Go"
...
# Entre otras variables que se listarán.
```

#### Instalar un versionador de código

Utilizaremos Git: https://git-scm.com/downloads


#### Ejecutar un "Hola Mundo".

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
