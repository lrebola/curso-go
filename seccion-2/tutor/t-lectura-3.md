## Instalación en Windows

#### Descarga e instalación

Voy a describir el paso a paso de la instalación que consistirá en los siguientes ítems:

- Descarga e instalación del binario
- Configurar y comprobar las variables de entorno
- Comprobar la instalación
- Ejecutar un "Hola Mundo"

Entonces lo primero que debemos realizar es descargar el binario de Go en esta pagina: [https://golang.org/dl](https://golang.org/dl/).

Aquí elegimos la opción Windows. Como podes observar, es compatible con todas las versiones de Windows desde el XP SP 3 en adelante.

Ya ha finalizado la descarga, y ahora solo debemos ejecutar el instalador.

Este Widzar es el típico de cualquier instalación en Windows, le daremos clic a siguiente.

Aceptamos los términos y condiciones.

Acá podemos escoger el directorio de instalación de Go, vamos a dejarlo en este path estándar y le damos a siguiente.

Ahora clic en instalar.

Nos pregunta Windows si permitimos realizar la instalación. Ponemos si.

Ha comenzado el proceso de instalación en el sistema operativo, esperamos un rato a que finalice.

Nos avisa que la instalación a terminado, le damos a finalizar.

---

Ahora desde el explorador de archivos vamos al directorio donde instalamos Go. Si no hemos cambiado el path en el widzar de instalación, lo encontraremos en C:\Go

Aquí vemos que tenemos todos los archivos y carpetas de la instalación de Go.

---

#### Configurar y comprobar las variables de entorno

El siguiente paso es revisar las variables de entorno, para ello acá en Windows 10 podemos escribir directamente "variables de entorno" y nos aparecerá esta pantalla.

Para otras versiones de Windows, la forma mas estándar de llegar hasta aquí es ir a Equipo, botón derecho en Propiedades, Configuración avanzada del sistema y por ultimo Variables de Entorno.

Podemos observar que efectivamente tenemos GOROOT con el path de instalación. Si no lo tenemos, debemos añadirlo.

Ahora debemos buscar la variable PATH, y verificamos que exista el parámetro: C:\Go\bin, esto también podría aparecer así: %GOROOT%\bin

En bin se encuentran los binarios de Go.

Bien, ahora vamos a agregar el path de nuestro workspace, es decir el directorio que usaremos como espacio de trabajo y que contendrá todos nuestros proyectos escritos en Go.

Volvamos al explorador de archivos, y veremos que dentro de nuestro usuario se a creado una carpeta de nombre Go.

Nos interesa la subcarpeta bin, que contendrá los binarios compilados de nuestros proyectos Go.

Bien, ahora copiamos este path y vamos a pegarlo en la variable de entorno PATH y guardamos.

Ahora solo nos queda agregar una ultima variable de entorno. La GOPATH.
Vamos a Nueva, escribimos GOPATH en nombre de variable y luego en Valor de la variable pegamos nuevamente el path que copiamos hace un momento.

Recordemos que GOPATH representa nuestro espacio de trabajo.

Listo, ya tenemos las variables de entorno configuradas. GOROOT, GOPATH y PATH.

Repasando, estas variables de entorno son:

GOROOT: EL directorio donde instalamos Go, y donde se encuentran los binarios de la Go Tool que nos permitirá compilar entre otras cosas.

GOPATH: Es nuestro directorio de trabajo, aquí adentro vamos a crear todas las carpetas de proyectos Go.

PATH: Le indicamos a Windows donde se encuentran los binarios, para así poner ejecutarlos desde la linea de comandos, el CMD en Windows.

Le damos clic en Aceptar, aceptar.

Ya tenemos Go instalado y configurado. Así que vamos a probar si funciona.

#### Comprobar la instalación







