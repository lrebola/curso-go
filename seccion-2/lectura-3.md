# Parte I

Conceptos básicos

## Paquetes, variables, y funciones

### Paquetes
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println("Feliz día", math.Pi)
}
```
- Todo programa en Go contiene paquetes.
- Los programas comienzan su ejecución en el paquete **main**.
- *En Go, el punto de entrada de un programa es una función llamada main ubicada en el paquete main.*
- Este programa usa los paquetes con rutas de importación "fmt" y "math".

Por convención, el nombre del paquete es el mismo que el último elemento de la ruta de importación.


### Importación
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Printf("Ahora tienes %g problemas.",
        math.Nextafter(2, 3))
}
```
Éste código agrupa las importaciones entre paréntesis de forma "factorizada". Tambien puedes realizar multiples importaciones de la siguiente forma:

```
import "fmt"
import "math"
```
pero es común usar la forma factorizada para eliminar código innecesario.


### Identificadores exportados
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(math.pi)
}
```
Tras importar un paquete, puedes hacer referencia a los identificadores que exporta.

En Go, un identificador es exportado si empieza por una mayúscula.

Foo es un identificador exportado, al igual que FOO. El identificador foo no es exportado.

Ejecuta el código. Después sustituye math.pi por math.Pi e intentalo de nuevo.


### Funciones
```go
package main

import "fmt"

func add(x int, y int) int {
    return x + y
}

func main() {
    fmt.Println(add(42, 13))
}

```
Una función puede tener cero o más argumentos.

En este ejemplo, add posee dos parámetros de tipo int.

Observa que el tipo de indica después del nombre de la variable.

(Para más información acerca de por qué los tipos se miestran así, échale un vistazo a ésta entrada en inglés.)


### Funciones (continuación)
```go
package main

import "fmt"

func add(x, y int) int {
    return x + y
}

func main() {
    fmt.Println(add(42, 13))
}

```
Cuando dos o más parámetros consecutivos de la función son del mismo tipo, puedes omitir el tipo de todos menos del último.

En el ejemplo, acortamos
```
x int, y int
```
a
```
x, y int
```



### Múltiples resultados
```go
package main

import "fmt"

func swap(x, y string) (string, string) {
    return y, x
}

func main() {
    a, b := swap("hola", "mundo")
    fmt.Println(a, b)
}

```
Una función puede devolver varios resultados.

Esta función devuelve dos cadenas.

### Resultados nombrados
```go
package main

import "fmt"

func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}

func main() {
    fmt.Println(split(17))
}

```
Las funciones tienen parametros; en Go los resultados pueden ser nombrados y actuar como variables; se les denomina "variables de retorno"

Si las variables de retorno tienen un nombre, una sentencia return sin argumentos devuelve el valor actual de dichas variables.

### Variables
```go
package main

import "fmt"

var x, y, z int
var c, python, java bool

func main() {
    fmt.Println(x, y, z, c, python, java)
}
```
La sentencia var declara una lista de variables; como en la lista de argumentos de las funciones, el tipo se indica al final.

### Variables inicializadas
```go
package main

import "fmt"

var x, y, z int = 1, 2, 3
var c, python, java = true, false, "¡no!"

func main() {
    fmt.Println(x, y, z, c, python, java)
}

```
La declaracion de variables permite inicializaciones, una por variable.

Si se inicializa una variable, el tipo puede omitirse; la variable adoptará el tipo del valor con el que ha sido inicializada.


### Declaración implícita de Variables
```go
package main

import "fmt"

func main() {
    var x, y, z int = 1, 2, 3
    c, python, java := true, false, "¡no!"

    fmt.Println(x, y, z, c, python, java)
}
```
Dentro de una función, puede utilizarse la sentencia de asignación := en lugar de la declaración var.

(Fuera de una función, todas las declaraciones de variables comienzan con la palabra clave var y el operando := no está disponible.)


### Tipos básicos
```go
package main

import (
    "fmt"
    "math/cmplx"
)

var (
    ToBe   bool       = false
    MaxInt uint64     = 1<<64 - 1
    z      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
    const f = "%T(%v)\n"
    fmt.Printf(f, ToBe, ToBe)
    fmt.Printf(f, MaxInt, MaxInt)
    fmt.Printf(f, z, z)
}
```
Los tipos básicos en Go son:
```
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte //alias para uint8

rune // alias para int32
     // Representa un punto Unicode

float32 float64

complex64 complex128
```


### Constantes
```go
package main

import "fmt"

const Pi = 3.14

func main() {
    const World = "世界"
    fmt.Println("Hola", World)
    fmt.Println("Feliz día de", Pi)

    const Truth = true
    fmt.Println("¿Go mola?", Truth)
}

```
Las constantes se declaran como las variables, pero con la palabra reservada const.

Las constantes pueden ser cadenas, booleanas, o numéricas.

### Constantes Numéricas
```go
package main

import "fmt"

const (
    Big   = 1 << 100
    Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
    return x * 0.1
}

func main() {
    fmt.Println(needInt(Small))
    fmt.Println(needFloat(Small))
    fmt.Println(needFloat(Big))
}

```
Las constantes numéricas son valores de alta precisión.

Una constante sin un tipo definido tiene el tipo necesitado según el contexto en el que se declara.

Intenta también imprimir el valor needInt(Big).

(An int can store at maximum a 64-bit integer, and sometimes less.)

## Referencias

* https://tour.golang.org

___

###### Página: [1] - [Siguiente >>](./lectura-2.md)
