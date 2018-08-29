¡Llegó la hora de instalar Go!

Veremos como hacerlo en Windows, Linux y Mac OS. Para que cada uno pueda hacerlo en su Sistema Operativo preferido.

El binario de Go que instalaremos nos permite compilar, descargar e instalar paquetes o librerías y ejecutar varios comandos útiles que pronto veremos.

Luego de su instalación, debemos configurar dos variables de entorno que Go necesita:

La primera es GOROOT, que indica el directorio donde se encuentra el binario de Go.

Y la segunda es GOPATH, esta representa la ubicación de nuestro Espacio de Trabajo. Es decir, cual será nuestra carpeta de workspace donde escribiremos el código de nuestros proyectos.

En Go se suele conservar todos los proyectos de código en un único espacio de trabajo. Esto difiere de otros entornos de programación donde cada workspace suele estar asociado a un repositorio de control de versiones. En Go, deberemos tener cada repositorio dentro de un mismo workspace. A menos que optemos por cambiar el path de GOPATH cada vez que queramos trabajar en otro directorio de workspace.

Además GOPATH es usado para resolver las importaciones de paquetes y no puede coincidir con el directorio de instalación.


Esto es básicamente lo que debemos tener en cuenta, ahora vamos a instalar Go, configurar la variables de entorno y ejecutar un Hola Mundo.

---



Workspaces

A workspace is a directory hierarchy with two directories at its root:

    src contains Go source files, and
    bin contains executable commands. 

Un espacio de trabajo es una jerarquía de directorios con dos directorios en su raíz:

src contiene archivos fuente Go, y
bin contiene comandos ejecutables.

La herramienta ir crea e instala binarios en el directorio bin.