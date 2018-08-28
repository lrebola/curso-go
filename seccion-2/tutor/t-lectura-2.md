¡Llegó la hora de instalar Go!

Veremos como hacerlo en Windows, Linux y Mac OS. Para que cada uno pueda hacerlo en su Sistema Operativo preferido.

Antes de proceder a descargar el instalador vamos a ver de que se trata la instalación y como la vamos a hacer.

Luego aplicaremos lo aquí visto para realizar la instalación en cada plataforma.

---

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que veremos pronto.

Además Go necesita dos variables de entorno para funcionar.

La primera es GOROOT, que indica el directorio donde se encuentra el binario de Go.

Y la segunda es GOPATH, y representa la ubicación de nuestro workspace. Es decir, cual será nuestra carpeta donde escribiremos el código de nuestros proyectos.

Además GOPATH es usado para resolver las importaciones de paquetes y no puede coincidir con el directorio de instalación.


Esto es básicamente lo que debemos tener en cuenta, ahora vamos a hacerlo.


Ahora vamos a instalar Go, configurar la variables de entorno y ejecutar un Hola Mundo.

---
Los programadores Go suelen conservar todos sus códigos Go en un único espacio de trabajo.

Tenga en cuenta que esto difiere de otros entornos de programación en los que cada proyecto tiene un espacio de trabajo separado y los espacios de trabajo están estrechamente vinculados a los repositorios de control de versiones.


Workspaces

A workspace is a directory hierarchy with two directories at its root:

    src contains Go source files, and
    bin contains executable commands. 

Un espacio de trabajo es una jerarquía de directorios con dos directorios en su raíz:

src contiene archivos fuente Go, y
bin contiene comandos ejecutables.

La herramienta ir crea e instala binarios en el directorio bin.

