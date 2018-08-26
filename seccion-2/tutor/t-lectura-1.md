## Características de Go

**Open Source** OK
Sus creadores explican que la decisión de Google para que Go sea de código abierto, se debe a que esa es la única forma en que puede tener éxito.

Un lenguaje necesita de comunidades grandes y amplias. Sostienen que los lenguajes cerrados mueren.

Un lenguaje necesita muchas personas que escriban gran cantidad de software, de modo que cuando necesites una herramienta o librería en particular, exista una buena probabilidad de que alguien ya la hubiera escrito.

Go acepta y revisa contribuciones del código fuente, ideas o informes de errores de cualquier persona.

Referencia: https://blog.golang.org/open-source

---

**Tipado estático** OK
Go usa tipado estático. Esto es cuando un lenguaje realiza la comprobación de tipificación durante la compilación, y no durante la ejecución.

Lenguajes de tipado estático son C, C++ o Java.

---

**Punto y coma** OK
El uso del punto y coma al final de una instrucción es opcional.

---

**Aritmética de punteros** OK
Go permite trabajar con punteros, pero no tiene aritmética de punteros.

La razón es la seguridad. Sin aritmética de punteros es posible crear un lenguaje en el que no se puede obtener una dirección ilegal que sea usada de forma incorrecta.

Por defecto Go envía los argumentos como valor, si deseas que los argumentos sean enviados por referencia debes usar un puntero.

https://gustavopeiretti.com/go-punteros/
https://gist.github.com/juanamari94/a06fbcc59d646750301d98aa7ca36289

----

**Go no tiene excepciones.** OK
Según los creadores, las excepciones tienen que ser realmente excepcionales y el uso que se le da mayoritariamente no justifica su existencia porque al final se acaban usando como controladores del flujo de la aplicación.

El código Go usa valores de error para indicar un estado anormal a través de un valor de retorno en cada función.

De esta manera es más fácil ver cuales funciones regresan errores y manejarlos utilizando las mismas estructuras de control como lo hacemos con todas las demás tareas.

http://goconejemplos.com/errores
https://blog.golang.org/error-handling-and-go

----

**Compilado**
Go es un lenguaje compilado a código máquina y multiplataforma.

Soporta compilación cruzada, esto quiere decir que permite generar el binario para otra plataforma: Por ejemplo compilar sobre Windows el binario para ser desplegado en Linux.

No tiene dependencias con otros software que deban estar instalados. Por ejemplo Java requiere la JVM.

Además velocidad de compilación de Go es muy rápida en comparación a otros lenguajes.

https://golangpost.blogspot.com/
https://stackoverflow.com/questions/20829155/how-to-cross-compile-from-windows-to-linux
https://github.com/golang/go/wiki/WindowsCrossCompiling

----

**¿Orientado a objetos?**
Go tiene tipos y métodos, y permite un estilo de programación orientado a objetos, pero no admite construir jerarquías, es decir, no admite la herencia, q

Go admite el paradigma de programación orientada a objetos, pero a diferencia de los lenguajes de programación más populares no dispone de herencia de tipos y tampoco de palabras clave que denoten claramente que soporta este paradigma.

No cuenta con soporte para herencia (aspecto esencial que difiere de los lenguajes POO clásicos).

----

No hay que preocuparse sobre si los usuarios tienen Ruby o la JVM instalada o, si la tienen, qué versión tendrán.

---