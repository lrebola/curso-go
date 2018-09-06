## Instalación en Windows

#### Descarga e instalación

Voy a describir el paso a paso de la instalación que consistirá en lo siguiente:

- La descarga e instalación del binario
- Configurar y comprobar las variables de entorno.
- Instalar un versionador de código (Go necesita de uno, ya lo veremos).
- Ejecutar un "Hola Mundo".

---

Entonces lo primero que debemos realizar es descargar el binario de Go en esta pagina: [https://golang.org/dl](https://golang.org/dl/).

Aquí elegimos la opción Windows. Como podemos observar, es compatible con todas las versiones de Windows desde el XP SP 3 en adelante.

Ya ha finalizada la descarga, ahora solo debemos ejecutar el instalador.

Este wizard es el típico de cualquier instalación en Windows, le damos clic a siguiente.

Aceptamos los términos y condiciones.

Acá podemos elegir el directorio de instalación para Go, vamos a dejarlo en este path estándar y le damos a siguiente.

En instalar.

Windows nos pregunta si permitimos realizar la instalación. Ponemos si.

Ha comenzado el proceso de instalación en el sistema operativo, esperamos un momento a que finalice.

Nos avisa que la instalación a terminado, le damos a finalizar.

---

Ahora desde el explorador de archivos vamos a ver el directorio donde instalamos Go. Si no hemos cambiado el path de instalación, lo tenemos en la raíz del disco C, adentro de esta carpeta Go.

Podemos ver que aquí tenemos todos los archivos y carpetas de la instalación. No tocaremos nada.

---

Como hemos usamos el instalador automático, este ya se encargó de agregar las variables de entorno en Windows.

Por lo tanto, antes de pasar a comprobar y configurar las variables de entorno, podemos chequear que Go ya funciona.

Abrimos el CMD de Windows y escribimos "go". 

Podemos observar que ya se reconoce el comando, esto significa que la variable de entorno GOROOT se configuró correctamente, y ademas también se modificó la variable PATH del sistema operativo con el directorio binario de Go. Ya veremos esto ultimo.

En caso que GOROOT o PATH no hayan sido configuradas por el instalador, cuando ejecuten el comando go en el CMD de Windows les debería mostrar un mensaje que dice: "Go" no se reconoce como un comando interno o externo.

Esto se debería solucionar configurando las variables como lo veremos a continuación.

---

Entonces, si todo salió bien, solo nos resta configurar la variable GOPATH.

Pero de paso también revisaremos las variables GOROOT y PATH por si alguien tuvo problemas y no funciona el comando Go, deberá agregarlas si no están.

Antes de seguir, vamos a crear una carpeta que será nuestro espacio de trabajo, y este directorio se lo asignaremos a la variable GOPATH para configurar nuestro workspace.

Vamos de nuevo al explorador de archivos, yo la voy a crear dentro de Documentos. Uds pueden crearla donde gusten, pero excepto en el mismo directorio donde esta instalado Go.

Listo, ahora voy a copiar el path y dentro de esta carpeta debemos crear las siguientes sub-carpetas:

###TODO: chequear esto
- src: donde crearemos nuestros proyectos de código.
- bin: en este directorio se generan los binarios ejecutables de los proyectos cuando los compilemos.
- y pkg: 


---

#### Configurar y comprobar las variables de entorno

Ahora si vamos a revisar las variables de entorno, para ello acá en Windows 10 podemos escribir directamente "variables de entorno".

Para otras versiones de Windows, la forma mas estándar de llegar hasta aquí es ir a Equipo, botón derecho en Propiedades, Configuración avanzada del sistema y por ultimo en Variables de Entorno.

Algo a tener en cuenta en este punto, es que tenemos dos tipos de variables de entorno en Windows.

Una global que corresponde al sistema, y otra de usuario. Es decir, las variables globales de sistema serán compartidas entre todos los usuarios del equipo, si tienen mas de un usuario. En cambio las variables de usuario solo la ve ese usuario en particular.

Nosotros vamos a configurar directamente todo en las variables de entorno del sistema.

Podemos observar que efectivamente tenemos GOROOT con el path de instalación. Si no lo tenemos, debemos añadirlo.

Ahora debemos buscar la variable PATH, y verificamos que exista el valor: C:\Go\bin.

En bin se encuentran los binarios de Go.

Bien, ahora vamos a agregar el path de nuestro workspace, es decir, el directorio que usaremos como espacio de trabajo para todos nuestros proyectos escritos en Go.

Para agregar GOPATH vamos a Nueva, escribimos GOPATH en nombre de variable y luego en Valor de la variable pegamos el path que copiamos hace un momento.

Ahora solo nos queda modificar la variable PATH agregando la sub-carpeta bin de nuestro workspace. Esto nos sirve para ejecutar nuestros proyectos compilados. 

Bien, para eso ubicamos esta variable “PATH” y damos clic en el botón “Editar”, ahora pegamos la dirección de nuestro workspace aquí, agregamos /bin y guardamos.

Listo, ya tenemos las variables de entorno configuradas. GOROOT, GOPATH y PATH.

Repasando, estas variables de entorno son:

GOROOT: El directorio donde instalamos Go, y donde se encuentran los binarios de la Go Tool que nos permitirá compilar entre otras cosas.

GOPATH: Es nuestro directorio de trabajo, aquí adentro vamos a crear todas las carpetas de proyectos Go.

PATH: Le indicamos a Windows donde se encuentran los binarios, para así poner ejecutarlos desde la linea de comandos, el CMD en Windows.

Le damos clic en Aceptar, aceptar.

Ya tenemos Go instalado y configurado. Así que vamos a probar si funciona.

---

#### Instalando un versionador de código.

Go necesita alguno 

#### Git
Instalar Git.
Go utiliza Git para descargar las librerías.









---
#### Instalar un versionador de código

`go get`

GO necesita tengamos instalado en nuestro sistema operativo un versionador de código.

La obtención de un código fuente se realiza utilizando una de las siguientes herramientas que se espera encontrar en su sistema:

https://github.com/golang/go/wiki/GoGetTools

Para descargar paquetes y dependencias Go utiliza uno de los siguientes versionadores de código

Obtenga descargas de los paquetes nombrados por las rutas de importación, junto con sus dependencias. 



#### Comprobar la instalación

```sh
$ go version
```


-> Ver variable gopath
gopath  se usa para resolver las declaraciones de importación.

La variable de entorno GOPATH enumera lugares para buscar el código Go.

Si la variable de entorno no está configurada, GOPATH adopta de manera predeterminada un subdirectorio llamado "ir" en el directorio de inicio del usuario ($HOME/go on Unix, %USERPROFILE%\go on Windows), a menos que ese directorio tenga una distribución Go. Ejecute "go env GOPATH" para ver el GOPATH actual.

The GOPATH environment variable specifies the location of your workspace. If no GOPATH is set, it is assumed to be $HOME/go on Unix systems and %USERPROFILE%\go on Windows. If you want to use a custom location as your workspace, you can set the GOPATH environment variable. 

https://github.com/golang/go/wiki/SettingGOPATH

Es posible tener un listado de directorios en GOPATH


