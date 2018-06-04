# Concurrencia

### Gorutinas
```go
package main

import (
    "fmt"
    "time"
)

func say(s string) {
    for i := 0; i < 5; i++ {
        time.Sleep(100 * time.Millisecond)
        fmt.Println(s)
    }
}

func main() {
    go say("mundo")
    say("hola")
}
```
Una gorutina es un hilo ligero manejado por el runtime de Go.
```go
go f(x, y, z)
```
comienza una nueva gorutina ejecutando
```go
f(x, y, z)
```
La evaluación de f, x, y, y z ocurre en la gorutina actual y la ejecución de f sucede en una nueva gorutina.

Las gorutinas ejecutan dentro del mismo espacio de direcciones, así que el acceso a memoria compartida debe ser síncronizado. El paquete sync http://golang.org/pkg/sync/ provee de llamadas útiles, aunque no las necesitarás demasiado ya que Go provee otro tipo de primitivas. (Mira la siguiente transparencia.)

[//]: #########################################

### Canales
```go
package main

import "fmt"

func sum(a []int, c chan int) {
    sum := 0
    for _, v := range a {
        sum += v
    }
    c <- sum // envía sum a c
}

func main() {
    a := []int{7, 2, 8, -9, 4, 0}

    c := make(chan int)
    go sum(a[:len(a)/2], c)
    go sum(a[len(a)/2:], c)
    x, y := <-c, <-c // recibe de c

    fmt.Println(x, y, x+y)
}
```
Los canales son un tipo de datos a través de los cuales puedes enviar o recibir valores con el operador <-.

```
ch <- v    // Envía v al canal ch.
v := <-ch  // Recibe del canal ch y
           // asigna el valor a v.
```
(Los datos fluyen en la dirección de la "flecha".)

De la misma forma que los maps y slices, los canales deben crearse antes de usarlos:
```
ch := make(chan int)
```
Por defecto, los envíos y recepciones se bloquean hasta que el otro extremo está listo. Esto permite que las gorutinas se sincronicen sin cerrojos explícitos o variables condicionales.

[//]: #########################################


### Canales con buffer
```go
package main

import "fmt"

func main() {
    c := make(chan int, 2)
    c <- 1
    c <- 2
    fmt.Println(<-c)
    fmt.Println(<-c)
}
```
Los canales pueden tener un buffer. Se puede indicar el tamaño del buffer pasando un segundo argumento a make para inicializar un canal con buffer de recepción:
```go
ch := make(chan int, 100)
```
Los envíos a un canal con buffer se bloquean sólo si el buffer está lleno. Las recepciones se bloquean si el buffer está vacío.

Modifica el ejemplo para llenar el buffer y observa qué ocurre.

[//]: #########################################


### Range y Close
```go
package main

import (
    "fmt"
)

func fibonacci(n int, c chan int) {
    x, y := 0, 1
    for i := 0; i < n; i++ {
        c <- x
        x, y = y, x+y
    }
    close(c)
}

func main() {
    c := make(chan int, 10)
    go fibonacci(cap(c), c)
    for i := range c {
        fmt.Println(i)
    }
}
```
Un hilo que envía datos puede cerrar un canal para indicar que ya no se van a enviar más datos. Los receptores pueden comprobar si un canal ha sido cerrado asignando un segundo parámetro en la expresión de recepción:
```
v, ok := <-ch
```
ok es false si no hay más valores que recibir y el canal está cerrado.

El bucle `for i := range c` recibe valores de un canal de forma repetida hasta que éste es cerrado.

Nota: Sólo el hilo que envía datos debería cerrar un canal, nunca el receptor. Los envíos a un canal cerrado generarán una excepción.

Otra nota: Los canales no son como ficheros; normalmente no necesitas cerrarlos. Cerrar un canal sólo es necesario cuando el receptor debe ser avisado que no va a recibir más datos.

[//]: #########################################


### Select
```go
package main

import "fmt"

func fibonacci(c, quit chan int) {
    x, y := 0, 1
    for {
        select {
        case c <- x:
            x, y = y, x+y
        case <-quit:
            fmt.Println("sale")
            return
        }
    }
}

func main() {
    c := make(chan int)
    quit := make(chan int)
    go func() {
        for i := 0; i < 10; i++ {
            fmt.Println(<-c)
        }
        quit <- 0
    }()
    fibonacci(c, quit)
}
```
La cláusula `select` permite a una gorutina esperar diversas operaciones de comunicación.

Un `select` se bloquea hasta que uno de sus casos puede ser ejecutado, ejecutando el caso que ha satisfecho su condición. Elige uno al azar si hay varios listos.

[//]: #########################################


### Select por defecto
```go
package main

import (
    "fmt"
    "time"
)

func main() {
    tick := time.Tick(1e8)
    boom := time.After(5e8)
    for {
        select {
        case <-tick:
            fmt.Println("tick.")
        case <-boom:
            fmt.Println("BOOM!")
            return
        default:
            fmt.Println("    .")
            time.Sleep(5e7)
        }
    }
}
```
El caso default en una cláusula select ejecuta si no hay otro caso listo.

Utiliza un caso default para intentar enviar o recibir de forma no bloqueante:
```go
select {
case i := <-c:
    // use i
default:
    // receiving from c would block
}
```
**Nota:** Este ejemplo no ejecutará en la versión web porque el [entorno posee una sandbox](http://golang.org/doc/play/) que no tiene el concepto de tiempo. Quizá quieras instalar Go para ver este ejemplo en acción.

[//]: #########################################

### Range
```go

```

[//]: #########################################

### Range
```go

```
