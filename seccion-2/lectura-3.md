# Flow control statements: for, if, else, switch and defer

### For
```go
package main

import "fmt"

func main() {
    sum := 0
    for i := 0; i < 10; i++ {
        sum += i
    }
    fmt.Println(sum)
}

```
Go tiene sólo un operando para definir los bucles, los bucles for.

El bucle for básico es muy parecido al que se utiliza en C o Java, salvo que los ( ) desaparecen (ni siquiera son opcionales) y las llaves { } son obligatorias.


### For (continuación)
```go
package main

import "fmt"

func main() {
    sum := 1
    for ;sum < 1000; {
        sum += sum
    }
    fmt.Println(sum)
}

```
Como en C o Java, puedes dejar las instrucciones de inicialización e incremento vacías.



### For es el "while" de Go
```go
package main

import "fmt"

func main() {
    sum := 1
    for sum < 1000 {
        sum += sum
    }
    fmt.Println(sum)
}

```
En este paso, puedes eliminar los puntos y coma ;: Un bucle while de C se transforma en un bucle for en Go.

### Eterno
```go
package main

func main() {
    for {
    }
}

```
Si omites la condición del bucle, es un bucle infinito de manera que un bucle infinito se escribe de manera compacta.

### If
```go
package main

import (
    "fmt"
    "math"
)

func sqrt(x float64) string {
    if x < 0 {
        return sqrt(-x) + "i"
    }
    return fmt.Sprint(math.Sqrt(x))
}

func main() {
    fmt.Println(sqrt(2), sqrt(-4))
}

```
La instrucción if es similar a la sentencia en C o Java, salvo que los paréntesis ( ) desaparecen (ni siquiera son opcionales) y las llaves { } son obligatorias.

(¿Te suena de algo?)


### If con instrucción inicial
```go
package main

import (
    "fmt"
    "math"
)

func pow(x, n, lim float64) float64 {
    if v := math.Pow(x, n); v < lim {
        return v
    }
    return lim
}

func main() {
    fmt.Println(
        pow(3, 2, 10),
        pow(3, 3, 20),
    )
}
```
Al igual que en la sentencia for, la sentencia if puede empezar con una instrucción de inicialización que se ejecutará antes de evaluar la condición.

Las variables declaradas por la instrucción de inicialización son únicamente visibles en el ámbito del if.

(Intenta usar v en la última sentencia return.)

### If y else
```go
package main

import (
    "fmt"
    "math"
)

func pow(x, n, lim float64) float64 {
    if v := math.Pow(x, n); v < lim {
        return v
    } else {
        fmt.Printf("%g >= %g\n", v, lim)
    }
    // No se puede usar v aquí
    return lim
}

func main() {
    fmt.Println(
        pow(3, 2, 10),
        pow(3, 3, 20),
    )
}

```
Las variables declaradas dentro de la instrucción de inicialización de un if son también visibles dentro de los bloques else.

### Ejercicio: Bucles y Funciones
```go
package main

import (
    "fmt"
)

func Sqrt(x float64) float64 {
}

func main() {
    fmt.Println(Sqrt(2))
}
```
Una forma sencilla de jugar con funciones y bucles es implementar la funcionalidad de la raíz cuadrada utilizando el método de Newton.

En este caso el método de Newton aproxima Sqrt(x) tomando un punto inicial z y repitiendo:

[Acá falta una imagen]

Para empezar, simplemente repite el cálculo 10 veces y mira cómo de cerca estás de la solución para distintos valores (1, 2, 3, ...).

Después cambia la condición del bucle para parar cuando el valor deje de cambiar (o solo cambie con un delta muy pequeño). Mira si esto ocurre con más o menos iteraciones. ¿Cómo estás de cerca comparado con math.Sqrt?

Pista: para declarar e inicializar un valor decimal dale un valor decimal o utiliza la conversión:
```
z := float64(0)
z := 0.0
```
