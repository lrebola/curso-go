## Características de Go

**Open Source** OK
Sus creadores explican que la decisión de Google para que Go sea de código abierto, se debe a que esa es la única forma en que puede tener éxito.

Un lenguaje necesita de comunidades grandes y amplias. Sostienen que los lenguajes cerrados mueren.

Un lenguaje necesita muchas personas que escriban gran cantidad de software, de modo que cuando necesites una herramienta o librería en particular, exista una buena probabilidad de que alguien ya la hubiera escrito.

Go acepta y revisa contribuciones del código fuente, ideas o informes de errores de cualquier persona.

[//]: # (https://blog.golang.org/open-source)

---

**Tipado estático** OK
Go usa tipado estático. Esto implica que las variables deben ser de un tipo específico como string, int, bool, etc.

En Go se indica el tipo a la hora de definir la variable o también es posible dejar al compilador que infiera el tipo.

Se realiza la comprobación de tipificación durante la compilación, y no durante la ejecución como en lenguajes dinámicamente tipados.

Lenguajes de tipado estático son C, C++ o Java.

---

**El punto y coma** OK
El uso del punto y coma al final de una instrucción es opcional.

---

**Aritmética de punteros** OK
Go permite trabajar con punteros, pero no tiene aritmética de punteros.

La razón es la seguridad. Sin aritmética de punteros es posible crear un lenguaje en el que no se puede obtener una dirección ilegal que sea usada de forma incorrecta.

Por defecto Go envía los argumentos como valor, si deseas que los argumentos sean enviados por referencia debes usar un puntero.

[//]: # (https://gustavopeiretti.com/go-punteros/
https://gist.github.com/juanamari94/a06fbcc59d646750301d98aa7ca36289)

----

**Go no tiene excepciones.** OK
Según los creadores, las excepciones tienen que ser realmente excepcionales y el uso que se le da mayoritariamente no justifica su existencia porque al final se acaban usando como controladores del flujo de la aplicación.

El código Go usa valores de error para indicar un estado anormal a través de un valor de retorno en cada función.

De esta manera es más fácil ver cuales funciones regresan errores y manejarlos utilizando las mismas estructuras de control como lo hacemos con todas las demás tareas.

[//]: # (http://goconejemplos.com/errores
https://blog.golang.org/error-handling-and-go)

----

**Compilado** OK
Go es un lenguaje compilado a código máquina y multiplataforma.

Soporta compilación cruzada, esto quiere decir que permite generar el binario para otra plataforma: Por ejemplo compilar sobre Windows el binario para ser desplegado en Linux.

No tiene dependencias con otros software que deban estar instalados. Por ejemplo Java requiere la JVM.

Además la velocidad de compilación de Go es muy rápida en comparación a otros lenguajes.

[//]: # (https://golangpost.blogspot.com/
https://stackoverflow.com/questions/20829155/how-to-cross-compile-from-windows-to-linux
https://github.com/golang/go/wiki/WindowsCrossCompiling)

---

**Multiplataforma** OK
Como lo mencione recién, Go fue diseñado para ser un lenguaje utilizable en múltiples sistemas operativos como Linux, Mac OS, Windows, etc.

Go permite compilar la aplicación para múltiples sistemas operativos con facilidad.

No requiere de una maquina virtual o ser compilado directamente en el sistema operativo destino.

[//]: # (https://blog.gopheracademy.com/advent-2013/day-23-multi-platform-applications/
https://www.digitalocean.com/community/tutorials/how-to-build-go-executables-for-multiple-platforms-on-ubuntu-16-04
https://medium.com/@matiasbaruch/un-curso-de-go-4f07f3db3c0c)


---

**Garbage collector** OK
Go implementa un recolector de basura como la mayoría de los lenguajes modernos. 

Los lenguajes con recolectores de basura son capaces de realizar un seguimiento de las variables y liberarlas cuando no se utilicen más.

Sin el recolector de basura es tarea de los desarrolladores el liberar la memoria asociada a estas variables cuando va a dejar de ser utilizada.

---

**Imperativo** OK
Go es lenguaje imperativo. En este tipo de lenguajes, las instrucciones se ejecutan unas tras otras, de manera secuencial salvo cuando se encuentran estructuras de control condicionales o bucles.

[//]: # ( https://www.genbeta.com/desarrollo/diferencias-entre-paradigmas-de-programacion)

---

**Estructurado** OK
Go también es un lenguaje estructurado. Este paradigma de programación esta orientado a mejorar la claridad, calidad y tiempo de desarrollo.

Para ello se utilizan únicamente tres estructuras: secuencia, selección (if y switch) e iteración (bucles for y while).

---

**¿Orientado a objetos?**
Go no es un lenguaje orientado a objetos aunque si nos permite trabajar con cierta metodología de la programación orientada a objetos.

Por ejemplo, Go tiene tipos y métodos, y permite un estilo de programación orientado a objetos pero no existe la jerarquía de objetos, por lo tanto, no existe la herencia.

No utiliza clases, todo se maneja en paquetes y lo que tenemos son estructuras que pueden ser asociadas con métodos.

Go incluye el concepto de composición, que consiste en incluir una estructura dentro de otra.

---

**Concurrente**
Go está pensado para ejecutar procesos concurrentes. Para esto tiene dos poderosos mecanismos: las go-rutinas y los canales.

La concurrencia en Go es diferente: Una **go-rutina** es similar a un hilo sólo que es gestionada por Go, no por el sistema operativo y tienen muy poca sobrecarga.

En Go no existen los Threads, sino procesos independientes y concurrentes, que no necesariamente se ejecutaran en paralelo.

El proceso independiente puede que se ejecute en paralelo a otros procesos, pero esto dependerá de los procesadores asignados.

[//]: # (Pero de todos modos, se ejecutará sin parar el proceso actual.)

En resumen, la ejecución independiente es concurrente si se puede.


También tenemos los **canales** que son un medio de comunicación entre go-rutinas que se utiliza para enviar datos entre ellas.

Una go-rutina que quiera enviar datos a otra debe hacerlo mediante un canal.

Los canales también tienen tipos y serán del mismo tipo que los datos que se van a mandar a través de ellos.