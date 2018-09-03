- Descargar binario

Vamos a ver en que consiste la instalación de Go, para luego hacerlo en Windows, Linux y Mac OS. Para que cada uno pueda hacerlo en su Sistema Operativo preferido.

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que pronto veremos.

---

- Configurar variables de entorno

Luego de su instalación, debemos configurar dos variables de entorno que Go necesita:

La primera es GOROOT, que indica el directorio donde se encuentra instalado el binario de Go.

###TODO: variable path

Y la segunda es GOPATH, esta representa la ubicación de nuestro Espacio de Trabajo. Es decir, cual será nuestra carpeta de workspace donde escribiremos el código de nuestros proyectos.

En Go se suele conservar todos los proyectos de código en un único espacio de trabajo. Esto difiere de otros entornos de programación donde cada workspace suele estar asociado a un repositorio de control de versiones. En Go, deberemos tener cada repositorio dentro de un mismo workspace. A menos que optemos por cambiar el path de GOPATH cada vez que queramos trabajar en otro directorio de workspace.

Además GOPATH es usado para resolver las importaciones de paquetes y no puede coincidir con el directorio de instalación.

---

- Comprobar la instalación

La verificáramos ejecutando el comando *go version* para imprimir su versión.

Se pueden comprobar ambas variables con el comando *go env*.

---

Esto es básicamente lo que debemos tener en cuenta, ahora vamos a instalar Go, configurar las variables de entorno y ejecutar un Hola Mundo.

---

por mas que no vayan a instalar go en windows, recomiendo que todos vean el video de la instalacion de windows donde explicare mas en detalle.

Workspaces

A workspace is a directory hierarchy with two directories at its root:

    src contains Go source files, and
    bin contains executable commands. 

Un espacio de trabajo es una jerarquía de directorios con dos directorios en su raíz:

src contiene archivos fuente Go, y
bin contiene comandos ejecutables.

La herramienta go crea e instala binarios en el directorio bin.