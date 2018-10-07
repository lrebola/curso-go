Los pasos a seguir en cada instalacion de sistema operativo siempre serán los mismos, en este orden:

- Descargar e instalar el binario
- Comprobar las variables de entorno
- Instalar un versionador de código
- Comprobar la instalación

----

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que veremos más adelante.

Su instalacion es muy simple, y a partir de la version 1.8 ya no es necesario configurar manualmente alguna de sus variables de entorno como figura en muchos tutoriales que podemos encontrar por Internet.

Pero igualmente haremos un repaso de estas variables de entorno para saber como funcionan y como se configuran.

A saber, dichas variables son GOROOT y GOPATH.

Donde `GOROOT` indica donde se encuentra instalado Go. Y como podemos observar en esta tabla, su directorio de instalacion predeterminado en Windows esta en la unidad C.

Mientras que en los sistemas operativos basados en Unix, como Linux y Mac, se instala en /usr/local/go.

En cuanto a la variable `GOPATH`, esta especifica la ubicación del workspace, es decir nuestro espacio de trabajo donde escribiremos el código de nuestros proyectos. Además GOPATH es usado para resolver las importaciones de paquetes y no puede coincidir con el directorio de instalación.

El valor predeterminado de esta variable en la instalacion lo podemos ver en esta tabla. Para Windows será el directorio de tu usuario. Este se encuentra dentro de la carpeta "Users" que esta dentro de la unidad C. Que sería C:\Users\TU_USUARIO.

Para Linux y Max, tambien será en el directorio Home del usuario.

---

Ahora pasemos a realizar las instalaciones en cada sistema operativo.