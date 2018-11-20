En esta clase previa a ejecutar la instalación en cada sistema operativo explicaré las cosas comunes con el objetivo de no repetir lo mismo en cada uno de ellos.

Entonces, los pasos que vamos a realizar en cada sistema operativo serán:

- Descargar e instalar el binario
- Comprobar las variables de entorno
- Instalar un versionador de código
- Comprobar la instalación

----
####  Descargar e instalar el binario

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos que los veremos más adelante.

Su instalación es muy simple, y a partir de la version 1.8 ya no es necesario configurar manualmente sus variables de entorno como figura en muchos tutoriales.

---
#### Comprobar las variables de entorno

Pero igualmente vamos a **comprobar las variables de entorno** para saber su utilidad y como se configuran.

A saber, dichas variables son GOROOT y GOPATH.

---

Donde `GOROOT` indica donde se encuentra instalado Go. Y como podemos observar en esta tabla, su directorio de instalación predeterminado en Windows esta en la unidad C.

Mientras que en los sistemas operativos basados en Unix, como Linux y Mac, se instala en /usr/local/.

Estos son directorios predeterminados y por supuesto podemos utilizar otros.

---

En cuanto a la variable `GOPATH`, básicamente enumera los lugares para buscar el código fuente, compilar e instalar los paquetes no estándares que importamos en nuestros proyectos.

Cuando digo enumera, me refiero a listar los directorios donde el compilador de Go debe buscar el código.

En otras palabras, GOPATH define cuales serán nuestros workspaces (o espacios de trabajo) y es importante aclarar que este no puede coincidir con el directorio de instalación.

Generalmente sería suficiente usar un solo directorio de trabajo para todos los códigos.

Les recomiendo, al menos en un principio trabajar con un solo workspace definido en la variable GOPATH, porque se pueden encontrar con algunos inconvenientes.

Porque GOPATH es usado por el compilador para resolver las declaraciones de importación de paquetes.

Go escanea cada directorio listado en GOPATH para encontrar el código fuente, pero para tener en cuenta, los paquetes que importamos siempre se descargaran en el primer directorio de la lista.

Por lo tanto debemos ser organizados para trabajar de esta manera con varios espacios de trabajos.

Podemos observar en esta tabla, que la variable tiene los siguientes valores predeterminados que apuntan a un subdirectorio llamado "go".

En Windows será dentro del directorio de tu usuario. Este se encuentra en la unidad C, y carpeta "Users".

Para Linux y Max, también será dentro del directorio Home del usuario.

Siempre y cuando, no hayamos instalado una distribución de Go justo en estos directorios. Recordemos que no pueden coincidir.

----
#### Configurar varios workspaces

En cuanto a configurar varios workspaces en la variable, esto depende del sistema operativo que usemos porque Windows y Unix definen distinto carácter de separación como podemos observar en esta tabla:

En Windows, los valores son separados por punto y coma.

En Unix, los valores son separados por dos puntos.

----

Por ultimo con respecto a GOPATH, cada directorio listado en la variable debe tener una estructura de carpetas:

La carpeta `src` que será como su nombre lo indica, donde debemos colocar el código fuente. Aquí adentro crearemos las subcarpetas de nuestros proyectos y repositorios de nuestro versionador de código.

Y la carpeta `bin` será donde la go tool compile e instale los binarios generados. Son los ejecutables.

---

#### Instalar un versionador de código

GO necesita tengamos instalado en nuestro Sistema Operativo un versionador de código, porque lo usa para descargar paquetes nombrados por las rutas de importación, junto con sus dependencias. 

Una ruta de importación describe cómo puede el comando `go get` obtener el código fuente del paquete utilizando un sistema de control de revisión como Git o SVN.

Entonces, este comando realiza la obtención del código fuente de repositorios remotos usando una de las siguientes herramientas que espera encontrar en el sistema:

- Git
- Subversion
- Mercurial
- Bazaar

Luego de obtener el código, lo compilará e instalará automáticamente dentro del primer o único directorio listado en GOPATH.

**go get**
Entonces, cada vez que hacemos un import de un paquete remoto se ejecutará el comando _go get_ para resolver las rutas de importación y realizar dicha descarga.

**gopath**
Y el directorio donde hayamos definido GOPATH se usará para resolver declaraciones de importación y descargar los paquetes remotos.

---

Llegó el momento de comenzar con las instalaciones. Nos vemos en el próximo video.

----

Refrencias de otra info para este video:

https://github.com/golang/go/wiki/GoGetTools
https://stackoverflow.com/questions/36017724/can-i-have-multiple-gopath-directories

Para más información se puede ejecutar el comando: go help gopath