# More types: structs, slices, and maps.


### Estructuras y tipos
```go
package main

import "fmt"

type Vertex struct {
    X int
    Y int
}

func main() {
    fmt.Println(Vertex{1, 2})
}

```
Una estructura (struct) es un registro de variables dentro de un mismo tipo.

(Y una declaración type declara un nuevo tipo de datos.)

### Campos de una estructura
```go
package main

import "fmt"

type Vertex struct {
    X int
    Y int
}

func main() {
    v := Vertex{1, 2}
    v.X = 4
    fmt.Println(v.X)
}
```
Los campos de una estructura son accesibles mediante el operador . (punto).

### Punteros
```go
package main

import "fmt"

type Vertex struct {
    X int
    Y int
}

func main() {
    p := Vertex{1, 2}
    q := &p
    q.X = 1e9
    fmt.Println(p)
}
```
Go posee punteros, pero no tiene aritmética de punteros (como C).

Los campos de las estructuras pueden accederse a través de un puntero a una estructura.

La indirección del puntero es transparente al programador.

### Estructuras literales
```go
package main

import "fmt"

type Vertex struct {
    X, Y int
}

var (
    p = Vertex{1, 2}  // Tiene tipo Vertex
    q = &Vertex{1, 2} // Tiene tipo *Vertex
    r = Vertex{X: 1}  // Y:0 es implicito
    s = Vertex{}      // X:0 e Y:0
)

func main() {
    fmt.Println(p, q, r, s)
}

```
Una estructura literal denota una nueva instancia de la estructura que muestra los valores de sus campos.

Puedes mostrar sólo un subconjunto de los campos utilizando la sintaxis Name:. (Y el orden de los campos nombrados es irrelevante.)

El prefijo especial & construye un puntero al espacio donde la nueva estructura se aloja.



### La función `new`
```go
package main

import "fmt"

type Vertex struct {
    X, Y int
}

func main() {
    v := new(Vertex)
    fmt.Println(v)
    v.X, v.Y = 11, 9
    fmt.Println(v)
}
```
La expresión new(T) aloja en memoria un valor T inicializado a 0 y retorna un puntero al mismo.
```
var t *T = new(T)
```
o
```
t := new(T)
```
### Slices
```go
package main

import "fmt"

func main() {
    p := []int{2, 3, 5, 7, 11, 13}
    fmt.Println("p ==", p)

    for i := 0; i < len(p); i++ {
        fmt.Printf("p[%d] == %d\n",
            i, p[i])
    }
}

```
Un slice apunta a un array de valores y posee un tamaño.

[]T es un slice con elementos de tipo T.

### Slicing slices
```go
package main

import "fmt"

func main() {
    p := []int{2, 3, 5, 7, 11, 13}
    fmt.Println("p ==", p)
    fmt.Println("p[1:4] ==", p[1:4])

    // Un valor de inicio omitido implica 0
    fmt.Println("p[:3] ==", p[:3])

    // Un valor de fin omitido implica len(s)
    fmt.Println("p[4:] ==", p[4:])
}

```
Los slices pueden ser reasignados, creando un nuevo slice que apunte al mismo array.

La expresión
```
s[lo:hi]
```
es evaluada como un slice de elementos desde el elemento de índice lo hasta el elemento hi-1 inclusive. Por tanto
```
s[lo:lo]
```
es un slice vacío y
```
s[lo:lo+1]
```
tiene un elemento.

### Creando slices
```go
package main

import "fmt"

func main() {
    a := make([]int, 5)
    printSlice("a", a)
    b := make([]int, 0, 5)
    printSlice("b", b)
    c := b[:2]
    printSlice("c", c)
    d := c[2:5]
    printSlice("d", d)
}

func printSlice(s string, x []int) {
    fmt.Printf("%s len=%d cap=%d %v\n",
        s, len(x), cap(x), x)
}
```
Los slices son creados con la función make. Funciona alojando un array inicializado a 0 y retornando un slice que apunta a ese array:
```
a := make([]int, 5)  // len(a)=5
```
Los slices tienen un tamaño y una capacidad. La capacidad de un slice es el tamaño máximo que el slice puede crecer dentro del array al que apunta.

Para especificar una capacidad basta con pasar un tercer argumento a make:
```
b := make([]int, 0, 5)
// len(b)=0, cap(b)=5
```
Los slices pueden crecer reasignándose (por encima de su capacidad):
```
b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4
```

### Slices nil
```go
package main

import "fmt"

func main() {
    var z []int
    fmt.Println(z, len(z), cap(z))
    if z == nil {
        fmt.Println("¡nulo!")
    }
}

```
El valor por defecto de un slice es nil.

Un slice nil tiene un tamaño y una longitud de 0.

(Para más detalle por favor mira el artículo (en inglés) "Go Slices: usage and internals".) http://golang.org/doc/articles/slices_usage_and_internals.html

### Range
```go
package main

import "fmt"

var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

func main() {
    for i, v := range pow {
        fmt.Printf("2**%d = %d\n", i, v)
    }
}

```
La forma range de un bucle for itera sobre elementos de un slice o un map.

### Range (continuación)
```go
package main

import "fmt"

func main() {
    pow := make([]int, 10)
    for i := range pow {
        pow[i] = 1 << uint(i)
    }
    for _, value := range pow {
        fmt.Printf("%d\n", value)
    }
}
```
Puedes obviar la clave o el valor asignándoselo a _.

Si sólo quieres el índice, descarta el , value integramente.


### Ejercicio: Slices
```go
package main

import "code.google.com/p/go-tour/pic"

func Pic(dx, dy int) [][]uint8 {
}

func main() {
    pic.Show(Pic)
}
```
Implementa la función Pic. Debería devolver un slice de tamaño dy, siendo cada uno de los elementos un slice de dx enteros sin signo de 8 bits. Cuando ejecutes el programa, mostrará tu dibujo, interpretando los números enteros como una escala de grises (bueno, escala de azules).

La elección de la imagen es de tu elección. Algunas funciones interesantes pueden ser x^y, (x+y)/2, y x*y.

(Necesitas usar un bucle para reservar memoria para cada []uint8 dentro de la matriz [][]uint8.)

(Usa uint8(intValue) para covertir entre tipos.)


### Maps
```go
package main

import "fmt"

type Vertex struct {
    Lat, Long float64
}

var m map[string]Vertex

func main() {
    m = make(map[string]Vertex)
    m["Bell Labs"] = Vertex{
        40.68433, -74.39967,
    }
    fmt.Println(m["Bell Labs"])
}
```
Un map relaciona claves y valores.

Los Maps deben crearse con la función make (nunca con new) antes de su uso; el map nil está vacío y no puede ser asignado.



### Map literales
```go
package main

import "fmt"

type Vertex struct {
    Lat, Long float64
}

var m = map[string]Vertex{
    "Bell Labs": Vertex{
        40.68433, -74.39967,
    },
    "Google": Vertex{
        37.42202, -122.08408,
    },
}

func main() {
    fmt.Println(m)
}
```
Los map literales son como las estructuras literales, pero las claves son obligatorias.



### Map literales (continuación)
```go
package main

import "fmt"

type Vertex struct {
    Lat, Long float64
}

var m = map[string]Vertex{
    "Bell Labs": {40.68433, -74.39967},
    "Google":    {37.42202, -122.08408},
}

func main() {
    fmt.Println(m)
}
```
Si el tipo superior es un nombre de un tipo, puedes omitirlo de los elementos del literal.



### Operaciones con maps
```go
package main

import "fmt"

func main() {
    m := make(map[string]int)

    m["Respuesta"] = 42
    fmt.Println("Valor:", m["Respuesta"])

    m["Respuesta"] = 48
    fmt.Println("Valor:", m["Respuesta"])

    delete(m, "Respuesta")
    fmt.Println("Valor:", m["Respuesta"])

    v, ok := m["Respuesta"]
    fmt.Println("Valor:", v, "¿Existe?", ok)
}
```
Insertar o actualizar un elemento de un map m:
```
m[clave] = elem
```
Recuperar un elemento:
```
elem = m[clave]
```
Borrar un elemento:
```
delete(m, clave)
```
Comprobar si una clave está presente con una doble assignación:
```
elem, ok = m[clave]
```
Si clave existe en m, ok es true. De otro modo ok és false y elem tiene el valor inicial del tipo de los elementos del map.

De manera similar, cuando leemos de un map, si la clave no está el resultado es el valor inicial del tipo de los elementos del map.

### Ejercicio: Maps
```go
package main

import (
    "code.google.com/p/go-tour/wc"
)

func ContadorPalabras(s string) map[string]int {
    return map[string]int{"x": 1}
}

func main() {
    wc.Test(ContadorPalabras)
}
```
Implementa ContadorPalabras. Debería devolver un map con el número de veces que una "palabra" aparece en la cadena s. La función wc.Test ejecuta un caso de prueba ejecutando la función implementada e imprime éxito o fallo.

Puedes encontrar ayuda en strings.Fields. http://golang.org/pkg/strings/#Fields


### Funciones son valores
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    hypot := func(x, y float64) float64 {
        return math.Sqrt(x*x + y*y)
    }

    fmt.Println(hypot(3, 4))
}
```
Las funciones también son valores.


### Funciones son clausuras
```go
package main

import "fmt"

func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}

func main() {
    pos, neg := adder(), adder()
    for i := 0; i < 10; i++ {
        fmt.Println(
            pos(i),
            neg(-2*i),
        )
    }
}
```
Y las funciones son clausuras completas.

La función adder retorna una clausura (o función anónima). Cada clausura está vinculada a su variable sum correspondiente.



### Ejercicio: La clausura de Fibonacci
```go
package main

import "fmt"

// fibonacci es una función que devuelve
// una función que devuelve un int.
func fibonacci() func() int {
}

func main() {
    f := fibonacci()
    for i := 0; i < 10; i++ {
        fmt.Println(f())
    }
}
```
Vamos a divertirnos un poco con las funciones.

Implementa una función de fibonacci que devuelva una función (o clausura) que devuelva los sucesivos números de fibonacci.


### Switch
```go
package main

import (
    "fmt"
    "runtime"
)

func main() {
    fmt.Print("Go runs on ")
    switch os := runtime.GOOS; os {
    case "darwin":
        fmt.Println("OS X.")
    case "linux":
        fmt.Println("Linux.")
    default:
        // freebsd, openbsd,
        // plan9, windows...
        fmt.Printf("%s.", os)
    }
}
```
Probablemente ya sabes cómo iba a ser la cláusula switch.

El cuerpo de un caso sale automáticamente de la cláusula switch, a menos que termine con una sentencia fallthrough, que provocaría que siguiera ejecutando el siguiente caso contemplado.

### Orden de evaluación de un switch
```go
package main

import (
    "fmt"
    "time"
)

func main() {
    fmt.Println("¿Cuándo es Sábado?")
    today := time.Now().Weekday()
    switch time.Saturday {
    case today + 0:
        fmt.Println("Hoy.")
    case today + 1:
        fmt.Println("Mañana.")
    case today + 2:
        fmt.Println("Pasado mañana.")
    default:
        fmt.Println("Demasiado tarde.")
    }
}
```
Los casos de un Switch evaluan los casos de arriba a abajo, parando cuando se encuentra un caso satisfactorio.

(Por ejemplo,
```
switch i {
case 0:
case f():
}
```
no ejecuta f si i==0.)

Nota: El temps a Go playground sempre comença el dimarts 2009-11-10 23:00:00 UTC, un valor amb significat es deixa com a exercici per al lector.

### Switch sin condición
```go
package main

import (
    "fmt"
    "time"
)

func main() {
    t := time.Now()
    switch {
    case t.Hour() < 12:
        fmt.Println("¡Buenos días!")
    case t.Hour() < 17:
        fmt.Println("Buenas tardes.")
    default:
        fmt.Println("Buenas noches.")
    }
}
```
Un switch sin condición es lo mismo que switch true.

Esta construcción puede ser una manera clara de escribir cadenas largas if-then-else.


### Ejercicio avanzado: Raices cúbicas complejas
```go
package main

import "fmt"

func Cbrt(x complex128) complex128 {
}

func main() {
    fmt.Println(Cbrt(2))
}
```
Veamos cuál es el soporte de Go para números complejos mediante los tipos complex64 y complex128. Para raíces cuadradas el método de Newton se basa en repeticiones:

TODO: Falta IMAGEN

Busca la raíz cúbica de 2, para asegurarte que el algoritmo funciona. Existe una función Pow http://golang.org/pkg/cmath/#Pow en el paquete math/cmplx.

### Ejercicio avanzado: Raices cúbicas complejas
```go
package main

import "fmt"

func Cbrt(x complex128) complex128 {
}

func main() {
    fmt.Println(Cbrt(2))
}
```
Veamos cuál es el soporte de Go para números complejos mediante los tipos complex64 y complex128. Para raíces cuadradas el método de Newton se basa en repeticiones:

TODO: falta imagen

Busca la raíz cúbica de 2, para asegurarte que el algoritmo funciona. Existe una función Pow en el paquete math/cmplx.
