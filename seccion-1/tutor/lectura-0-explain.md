Markdown
https://guides.github.com/features/mastering-markdown/
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

Intro Go
https://www.genbetadev.com/herramientas/introduccion-al-lenguaje-de-programacion-go
https://www.genbetadev.com/lenguajes-y-plataformas/empezar-a-aprender-go-golang




https://ed.team/blog/golang-el-lenguaje-de-programacion-creado-por-google
https://ed.team/cursos/go


https://golangcookbook.com/chapters/running/cross-compiling/
https://www.digitalocean.com/community/tutorials/how-to-build-go-executables-for-multiple-platforms-on-ubuntu-16-04


La notación de los comentarios es exactamente la misma que la de C++:
```go
/* ...
   ...
   ... */

// ...
```
Bibliografia

'The Little Go Book' en Castellano
https://raulexposito.com/documentos/go/
Go eficiente
https://nachopacheco.gitbooks.io/go-es/content/doc/go-eficiente/index.html
Go Books
https://github.com/dariubs/GoBooks



JEDI GO

Curso de maestro Jedi en Go

Este curso esta pensado para que aprendas todo lo necesario para iniciarte en *Go* desde **cero a experto.**

Dirigido a estudiantes, profesionales y aficionados de la programación.

Comenzaremos desde los conceptos basicos siguiendo la documentación oficial y llegaremos a construir ejemplos utiles.




Hay una buena cantidad de documentacion oficial de Go, y nos basaremos en ella para el desarrollo del curso y para que tambien una vez finalziado el curso tengan los recursos para quienes quiran profundizar más.

Luego que avancemos con lo fundamental de Go siguiendo la documentacion oficial procederemos a trabajar con ejemplos de acceso a base de datos Oracle, MySQL y MongoDB.

Crear un servicio REST con JSON y consumirlo utilizando Postman.

Le añadiremos seguridad con un sistemma de web tokens y login de usuario.




Ver: https://tour.golang.org/concurrency/11
https://golang.org/doc/articles/wiki/
https://talks.golang.org/2012/simple.slide#16
https://talks.golang.org/2012/concurrency.slide#18

https://github.com/a8m/go-lang-cheat-sheet#basic-syntax

Compiles to native code (no JVM)

Credits
Most example code taken from A Tour of Go, which is an excellent introduction to Go. If you're new to Go, do that tour. Seriously.

https://golangbot.com/functions/

https://learnxinyminutes.com/docs/go/

https://github.com/golang/go/wiki/Mobile

https://golang.org/pkg/net/http/

https://hackernoon.com/how-to-create-a-web-server-in-go-a064277287c9
https://github.com/golang/go/wiki/CodeReviewComments



https://www.aerofs.com/introducing-gockerize-md/
https://jm33.me/parsing-large-xml-with-go.html
https://blog.cloudboost.io/reading-humongous-files-in-go-c894b05ac020









lectura 4:


https://making.pusher.com/golangs-real-time-gc-in-theory-and-practice/

https://golang.org/doc/faq#Is_Go_an_object-oriented_language


- Es un lenguaje tipado estáticamente y compilado
- Es un lenguaje de programación concurrente y compilado
- Desarrollado por Google
- Disponible en formato binario para los sistemas operativos Windows, GNU/Linux, FreeBSD y Mac OS X
- Go es un lenguaje de programación compilado, concurrente, imperativo, estructurado, orientado a objetos —de una manera bastante especial—
- Go usa tipado estático
- Go admite el paradigma de programación orientada a objetos, pero a diferencia de los lenguajes de programación más populares no dispone de herencia de tipos y tampoco de palabras clave que denoten claramente que soporta este paradigma.
- Otro detalle que puede resultar confuso es que la definición de un tipo ("clase") se realiza por medio de declaraciones separadas (interfaces, structs, embedded values).
- Go no tiene excepciones.
- En Go el uso del carácter punto y coma “;“ al final de una instrucción es opcional..
- Go tiene tipos y métodos, y permite un estilo de programación orientado a objetos, pero no admite construir jerarquías, es decir, no admite la herencia, q




instalacion:
https://zainul.gitbooks.io/learn-go/content/gopath-vs-goroot.html

https://github.com/golang/go/wiki/SettingGOPATH

The Go path is used to resolve import statements.

The GOPATH environment variable lists places to look for Go code.

 If the environment variable is unset, GOPATH defaults to a subdirectory named "go" in the user's home directory ($HOME/go on Unix, %USERPROFILE%\go on Windows), unless that directory holds a Go distribution. Run "go env GOPATH" to see the current GOPATH.

 The GOPATH environment variable specifies the location of your workspace.

 Note that GOPATH must not be the same path as your Go installation.

 The GOROOT tree is always scanned in its entirety before GOPATH.




 ----


 https://raulexposito.com/documentos/go/
 https://groups.google.com/forum/#!forum/golang-nuts

 es un lenguaje relativamente sencillo con una librería estandar relativamente simple.

 Go tiene la naturaleza de simplificar la complejidad que hemos visto incluida en los lenguajes de programación en el último par de décadas mediante el uso de varios mecanismos.

 nos ha cubierto la necesidad de disponer de algo que nos permita desarrollar aplicaciones de bajo y de alto nivel.

 No hay que preocuparse sobre si los usuarios tienen Ruby o la JVM instalada o, si la tienen, qué versión tendrán.

 la propia documentación de Go, en particular Effective Go, es buena.

 Si buscas jugar un poco con Go deberías probar el Go Playground, el cual te permite ejecutar código en el navegador sin tener que instalar nada.


 Excepto para los ejemplos sencillos, Go ha sido diseñado para funcionar siempre que tu código esté dentro de un workspace. El workspace es un directorio formado por los subdirectorios bin, pkg y src.

}

Guarda el fichero con el nombre main.go. De momento, puedes guardarlo donde quieras, los ejemplos triviales no necesitan estar dentro del workspace de Go.

go run es un comando muy práctico que compila y ejecuta tu código.
