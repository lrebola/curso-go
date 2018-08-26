# Métodos e interfaces

### Métodos
```go
package main

import (
    "fmt"
    "math"
)

type Vertex struct {
    X, Y float64
}

func (v *Vertex) Abs() float64 {
    return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
    v := &Vertex{3, 4}
    fmt.Println(v.Abs())
}
```
Go no tiene clases. De todas formas, puedes definir métodos para tipos struct.

El receptor del método aparece en su propia lista de argumentos entre la palabra reservada func y el nombre del método.


### Métodos (continuación)
```go
package main

import (
    "fmt"
    "math"
)

type MyFloat float64

func (f MyFloat) Abs() float64 {
    if f < 0 {
        return float64(-f)
    }
    return float64(f)
}

func main() {
    f := MyFloat(-math.Sqrt2)
    fmt.Println(f.Abs())
}
```
De hecho, puedes definir un método para cualquier tipo que definas en tu paquete, no sólamente para estructuras.

No puedes definir un método de un tipo de otro paquete o de un tipo básico.

### Métodos con punteros a receptores
```go
package main

import (
    "fmt"
    "math"
)

type Vertex struct {
    X, Y float64
}

func (v *Vertex) Scale(f float64) {
    v.X = v.X * f
    v.Y = v.Y * f
}

func (v *Vertex) Abs() float64 {
    return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
    v := &Vertex{3, 4}
    v.Scale(5)
    fmt.Println(v, v.Abs())
}
```
Los métodos pueden asociarse con un tipo o un puntero a un tipo declarado.

Acabamos de ver dos métodos Abs. Uno para el puntero a un vértice`*Vertex` y otro para el tipo MyFloat.

Hay dos razones para usar un receptor de tipo puntero. Primero, para evitar copiar el valor en cada llamada al método (más eficiente si el tipo usado es una estructura grande). Segundo, de tal forma que el método pueda modificar el valor a la que apunta el receptor.

Intenta cambiar las declaraciones de los métodos Abs y Scale para usar Vertex como el receptor, en lugar de *Vertex.

El método Scale no tiene efecto cuando v es un vértice`Vertex`. Scale cambia v. Cuando`v` es un tipo (no un puntero) el método ve una copia del vértice Vertex y no puede mutar el valor original.

Abs funciona de cualquier forma. Sólo lee v. No importa si está leyendo el valor original (a través del puntero) o una copia del valor.

### Interfaces
```go
package main

import (
    "fmt"
    "math"
)

type Abser interface {
    Abs() float64
}

func main() {
    var a Abser
    f := MyFloat(-math.Sqrt2)
    v := Vertex{3, 4}

    a = f  // a MyFloat implementa Abser
    a = &v // a *Vertex implementa Abser
    a = v  // a Vertex, NO implementa Abser

    fmt.Println(a.Abs())
}

type MyFloat float64

func (f MyFloat) Abs() float64 {
    if f < 0 {
        return float64(-f)
    }
    return float64(f)
}

type Vertex struct {
    X, Y float64
}

func (v *Vertex) Abs() float64 {
    return math.Sqrt(v.X*v.X + v.Y*v.Y)
}
```
Una interfaz es un tipo de datos definido como un conjunto de métodos.

Un tipo interface puede contener cualquier tipo que implemente esos métodos.

### Las interfaces se implementan implícitamente
```go
package main

import (
    "fmt"
    "os"
)

type Reader interface {
    Read(b []byte) (n int, err error)
}

type Writer interface {
    Write(b []byte) (n int, err error)
}

type ReadWriter interface {
    Reader
    Writer
}

func main() {
    var w Writer

    // os.Stdout implementa Writer
    w = os.Stdout

    fmt.Fprintf(w, "hola, writer\n")
}


```
Un tipo implementa una interfaz simplemente implementando los métodos.

No hay declaración explícita.

Las interfaces implícitas desacoplan la implementación de paquetes entre los paquetes que definen las interfaces: ninguno depende de otro.

También favorece la definición de interfaces precisas, porque no tienes que encontrar todas las implementaciones y etiquetarlas con el nuevo nombre de la interfaz.

El paquete io http://golang.org/pkg/io/ define Reader y Writer; Tú no tienes que hacerlo.

### Errores
```go
package main

import (
    "fmt"
    "time"
)

type MyError struct {
    When time.Time
    What string
}

func (e *MyError) Error() string {
    return fmt.Sprintf("A las %v, %s",
        e.When, e.What)
}

func run() error {
    return &MyError{
        time.Now(),
        "ha fallado",
    }
}

func main() {
    if err := run(); err != nil {
        fmt.Println(err)
    }
}
```
Un error es cualquier cosa que se defina así mismo como una cadena de error. La idea está en la interfaz predefinida error, con su único método, Error, que devuelve una cadena de caracteres:
```
type error interface {
    Error() string
}
```
Las funciones de impresión del paquete fmt sabe cómo llamar al método cuando se le pide imprimir un error.

### Ejercicio: Errores
```go
package main

import (
    "fmt"
)

func Sqrt(f float64) (float64, error) {
    return 0, nil
}

func main() {
    fmt.Println(Sqrt(2))
    fmt.Println(Sqrt(-2))
}
```
Copia tu función Sqrt de ejercicios anteriores y modifícala para que devuelva un valor de tipo error.

Sqrt debe devolver un error no nulo cuando se le pasa un número negativo, dado que no soporta números complejos.

Crea un nuevo tipo
```
type ErrNegativeSqrt float64
```
y hazlo del tipo error implementando un método
```
func (e ErrNegativeSqrt) Error() string
```
de forma que ErrNegativeSqrt(-2).String() devuelva "no se puede calcular la raíz de un número negativo: -2".

Nota: una llamada a fmt.Sprint(e) dentro del método Error hará que el programa entre en un bucle infinito. Puedes evitarlo convirtiendo e: fmt.Sprint(float64(e)). ¿Por qué?

Cambia tu función Sqrt para devolver un valor ErrNegativeSqrt cuando se le pase un número negativo.



### Servidores Web
```go
package main

import (
    "fmt"
    "net/http"
)

type Hello struct{}

func (h Hello) ServeHTTP(
    w http.ResponseWriter,
    r *http.Request) {
    fmt.Fprint(w, "¡Hola!")
}

func main() {
    var h Hello
    http.ListenAndServe("localhost:4000", h)
}
```
El paquete http http://golang.org/pkg/http/ sirve peticiones HTTP usando cualquier valor que implemente http.Handler:
```
package http

type Handler interface {
ServeHTTP(
    w ResponseWriter, r *Request)
}
```
n este ejemplo, el tipo Hello implementa http.Handler.

Visita http://localhost:4000/ para ver la bienvenida.

Nota: Este ejemplo sólo se puede ejecutar a través del tour web local. Para intentar implementar servidores web puedes Instalar Go.


### Ejercicio: Manejadores HTTP
```go
package main

import (
    "net/http"
)

func main() {
    // Tu http.Handle llama aquí
    http.ListenAndServe("localhost:4000", nil)
}
```
Implementa los siguientes tipos y define métodos ServeHTTP para ellos. Asígnalos distintas rutas de tu servidor web.
```
type String string

type Struct struct {
    Greeting string
    Punct    string
    Who      string
}
```
Por ejemplo, deberías poder asignárselas usando:
```
http.Handle("/string", String("I'm a frayed knot."))
http.Handle("/struct", &Struct{"Hola", ":", "Gophers!"})
```

### Imágenes
```go
package main

import (
    "fmt"
    "image"
)

func main() {
    m := image.NewRGBA(image.Rect(0, 0, 100, 100))
    fmt.Println(m.Bounds())
    fmt.Println(m.At(0, 0).RGBA())
}
```
El paquete image http://golang.org/pkg/image/#Image define la interfaz Image:


```
package image

type Image interface {
    ColorModel() color.Model
    Bounds() Rectangle
    At(x, y int) color.Color
}
```
(Mira la documentación http://golang.org/pkg/image/#Image para más detalles.)

color.Color y color.Model también son interfaces, pero las ignoraremos usando las implementaciones predefinidas image.RGBA y image.RGBAModel.


### Ejercicio: Imágenes
```go
package main

import (
    "code.google.com/p/go-tour/pic"
    "image"
)

type Image struct{}

func main() {
    m := Image{}
    pic.ShowImage(m)
}
```
¿Recuerdas el generador de imágenes que escribiste antes? Vamos a escribir otro, pero esta vez devolverá una implementación de image.Image en lugar de un slice.

Define tu propio tipo Image, implementa los métodos necesarios http://golang.org/pkg/image/#Image, y llama a pic.ShowImage.

Bounds deberían devolver un image.Rectangle, como `image.Rect(0, 0, w, h)`.

ColorModel debería devolver color.RGBAModel.

At debería devolver un color; el valor v del último generador corresponde a `color.RGBA{v, v, 255, 255}`.

### Ejercicio: Lector Rot13
```go
package main

import (
    "io"
    "os"
    "strings"
)

type rot13Reader struct {
    r io.Reader
}

func main() {
    s := strings.NewReader(
        "¡Unf qrfpvsenqb ry póqvtb!")
        //"Lbh penpxrq gur pbqr!")
    r := rot13Reader{s}
    io.Copy(os.Stdout, &r)
}
```
Un patrón común es un io.Reader http://golang.org/pkg/io/#Reader que encapsula otro io.Reader, modificando el flujo de datos de alguna forma.

Por ejemplo, la función gzip.NewReader http://golang.org/pkg/compress/gzip/#Decompressor.NewReader recibe un io.Reader (un flujo de datos en formato gzip) y devuelve un *gzip.Decompressor que también implementa io.Reader (un flujo de datos descomprimidos).

Implementa un rot13Reader que implemente io.Reader y lea de un io.Reader, modificando el flujo de datos aplicándole el algoritmo de cifrado ROT13 http://es.wikipedia.org/wiki/ROT13 a todos los caracteres alfabéticos.

El tipo rot13Reader está completo. Implementa su método Read para que implemente la interfaz io.Reader.
