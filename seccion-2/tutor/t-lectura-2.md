En esta clase previa a ejecutar la instalación en cada sistema operativo explicaré varias cosas a tener en cuenta durante la misma, para no ser repetitivo en los siguientes tres videos.

Entonces, los pasos que vamos a realizar en cada instalación de los sistemas operativos siempre serán los mismos:

- Descargar e instalar el binario
- Comprobar las variables de entorno
- Instalar un versionador de código
- Comprobar la instalación

----

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que veremos más adelante.

Su instalación es muy simple, y a partir de la version 1.8 ya no es necesario configurar manualmente alguna de sus variables de entorno como figura en muchos tutoriales que podemos encontrar por Internet.

Pero igualmente haremos un repaso de estas variables de entorno para saber como funcionan y como se configuran.

A saber, dichas variables son GOROOT y GOPATH.

---

Donde `GOROOT` indica donde se encuentra instalado Go. Y como podemos observar en esta tabla, su directorio de instalación predeterminado en Windows esta en la unidad C.

Mientras que en los sistemas operativos basados en Unix, como Linux y Mac, se instala en /usr/local/go.

---

En cuanto a la variable `GOPATH`, básicamente enumera los lugares para buscar el código, compilar e instalar los paquetes no estándares que importamos en nuestros proyectos.

Cuando digo enumera, me refiero a listar los directorios donde el compilador de Go debe buscar el código.

En otras palabras, GOPATH define cuales serán nuestros workspaces (o espacios de trabajo) y este no puede coincidir con el directorio de instalación.

Generalmente es suficiente usar un solo directorio de trabajo para todos los códigos.

Les recomiendo, al menos en un principio trabajar con un solo workspace definido en la variable GOPATH porque se pueden encontrar con algunos inconvenientes.

Porque GOPATH también es usado por el compilador para resolver las declaraciones de importación de paquetes.

Go busca en cada directorio listado en GOPATH para encontrar el código fuente, pero los paquetes que importamos, siempre se descargan en el primer directorio de la lista.

Por lo tanto debemos ser organizados para trabajar de esta manera con varios espacios de trabajos.

Como podemos observar en la tabla, el valor predeterminado de esta variable para Windows será el directorio de tu usuario. Este se encuentra dentro de la carpeta "Users" que esta dentro de la unidad C. Que sería C:\Users\TU_USUARIO.

Para Linux y Max, también será en el directorio Home del usuario.

En cuanto a como configurar varios espacios de trabajo en la variable, según el sistema operativo el separador de directorios será uno de los que figura en esta tabla.

En Windows, los valores son separados por punto y coma.

En Unix, los valores son separados por dos puntos.

Para más información se puede ejecutar el comando: go help gopath

----

Por ultimo con respecto a GOPATH, cada directorio listado en la variable debe tener una estructura de carpetas creada:

La carpeta `src` que será como su nombre lo indica, donde debemos colocar el código fuente.

Por lo tanto, aquí adentro crearemos las subcarpetas de nuestros proyectos y los repositorios de nuestro versionador de código.

Y la carpeta `bin` será donde la go tool compile e instale los binarios generados. Son los ejecutables.

---
#### Instalar un versionador de código

GO necesita tengamos instalado en nuestro Sistema Operativo un versionador de código para descargar paquetes nombrados por las rutas de importación, junto con sus dependencias. 

Una ruta de importación describe cómo puede el comando `go get` obtener el código fuente del paquete utilizando un sistema de control de revisión como Git o SVN.

Entonces, este comando realiza la obtención del código fuente de repositorios remotos usando una de las siguientes herramientas que espera encontrar en el sistema:

- Git
- Subversion
- Mercurial
- Bazaar

Luego de obtener el código, lo compilará e instalará automáticamente dentro del primer o único directorio listado de GOPATH.

---

Ahora pasemos a realizar las instalaciones en cada sistema operativo.





https://github.com/golang/go/wiki/GoGetTools

https://stackoverflow.com/questions/36017724/can-i-have-multiple-gopath-directories
