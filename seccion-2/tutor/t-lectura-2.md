

Los pasos a seguir en cada instalación de sistema operativo siempre serán los mismos, en este orden:

- Descargar e instalar el binario
- Comprobar las variables de entorno
- Instalar un versionador de código
- Comprobar la instalación

----

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que veremos más adelante.

Su instalación es muy simple, y a partir de la version 1.8 ya no es necesario configurar manualmente alguna de sus variables de entorno como figura en muchos tutoriales que podemos encontrar por Internet.

Pero igualmente haremos un repaso de estas variables de entorno para saber como funcionan y como se configuran.

A saber, dichas variables son GOROOT y GOPATH.

Donde `GOROOT` indica donde se encuentra instalado Go. Y como podemos observar en esta tabla, su directorio de instalación predeterminado en Windows esta en la unidad C.

Mientras que en los sistemas operativos basados en Unix, como Linux y Mac, se instala en /usr/local/go.

En cuanto a la variable `GOPATH`, 

La variable de entorno GOPATH enumera lugares para buscar el código Go.

La ruta Go se usa para resolver las declaraciones de importación.

En Unix, el valor es una cadena separada por dos puntos.

En Windows, el valor es una cadena separada por punto y coma.

GOPATH debe configurarse para obtener, compilar e instalar paquetes fuera del árbol Go estándar.

Cada directorio listado en GOPATH debe tener una estructura prescrita:

Go busca en cada directorio listado en GOPATH para encontrar el código fuente, pero los paquetes nuevos siempre se descargan en el primer directorio de la lista.

Por lo tanto debemos ser organizados para trabajar de esta manera.

esta especifica la ubicación del workspace, es decir nuestro espacio de trabajo donde escribiremos el código de nuestros proyectos. Además GOPATH es usado para resolver las importaciones de paquetes y no puede coincidir con el directorio de instalación.

El valor predeterminado de esta variable en la instalación lo podemos ver en esta tabla. Para Windows será el directorio de tu usuario. Este se encuentra dentro de la carpeta "Users" que esta dentro de la unidad C. Que sería C:\Users\TU_USUARIO.

Para Linux y Max, también será en el directorio Home del usuario.

Solo a modo de comentario, decir que esta variable también soporta una lista de directorios si queremos tener varios workspace. Pero debemos tener en cuenta que la importación de paquetes y dependencias si las obtenemos con go get, estas se descargaran en el primer directorio de la lista.

Para mas informacion se puede ejecutar el comando: go help gopath

https://stackoverflow.com/questions/36017724/can-i-have-multiple-gopath-directories


---
#### Instalar un versionador de código

Y por ultimo, con respecto al versionador de código es un requisito para trabajar con Go tener instalado uno en el Sistema Operativo. Y se preguntaran ¿por qué?


Esto se debe que para descargar paquetes y dependencias Go lo realiza a través del comando `go get`. Este comando realiza la obtención del código fuente utilizando alguno de estos sistemas de versionamiento de código.




GoGetTools

El ir a buscar el código fuente se realiza usando una de las siguientes herramientas que se espera encontrar en su sistema:





`go get`

GO necesita tengamos instalado en nuestro sistema operativo un versionador de código.

La obtención de un código fuente se realiza utilizando una de las siguientes herramientas que se espera encontrar en su sistema:

https://github.com/golang/go/wiki/GoGetTools

Para descargar paquetes y dependencias Go utiliza uno de los siguientes versionadores de código

Obtenga descargas de los paquetes nombrados por las rutas de importación, junto con sus dependencias. 

Una ruta de importación puede describir cómo obtener el código fuente del paquete utilizando un sistema de control de revisión como Git o Mercurial.

La herramienta go utiliza esta propiedad para recuperar paquetes de repositorios remotos.

Si incluye la URL del repositorio en la ruta de importación del paquete, vaya a obtener, compilará e instálela automáticamente:

If you include the repository URL in the package's import path, go get will fetch, build, and install it automatically: 


Si el paquete especificado no está presente en un espacio de trabajo, go get lo colocará dentro del primer espacio de trabajo especificado por GOPATH.

---

Ahora pasemos a realizar las instalaciones en cada sistema operativo.



In $GOPATH, you must have three folders as follows:

    src for source files whose suffix is .go, .c, .g, .s.
    pkg for compiled files whose suffix is .a.
    bin for executable files
