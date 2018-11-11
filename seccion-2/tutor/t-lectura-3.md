## Instalación en Windows

Bueno, vamos a instalar Go en Windows siguiendo los pasos descriptos en el video anterior. El primero es:

#### Descarga e instalación del binario

Entonces lo primero que debemos realizar es descargar el binario en esta pagina: [https://golang.org/dl](https://golang.org/dl/).

Veamos...

Aquí elegimos la opción Windows. Como podemos observar, es compatible con todas las versiones de Windows desde el XP SP 3 en adelante.

Esperamos a que finalice la descarga, y ahora solo debemos ejecutar el instalador.

Este wizard es el típico de cualquier instalación en Windows, le damos clic a siguiente.

Aceptamos los términos y condiciones.

Acá podemos elegir el directorio de instalación para Go, vamos a dejarlo en este path predeterminado y le damos clic a siguiente.

Ahora en instalar.

Windows nos pregunta si permitimos realizar la instalación. Ponemos si.

Ha comenzado el proceso de instalación en el sistema operativo, esperamos un momento a que finalice.

Nos avisa que la instalación a terminado, le damos a finalizar.

---

Ahora desde el explorador de archivos vamos a ver el directorio donde instalamos Go. Si no hemos cambiado el path de instalación, lo tenemos en la raíz del disco C, adentro de esta carpeta Go.

Podemos ver que aquí tenemos todos los archivos y carpetas de la instalación. Dejamos todo como está.

---


#### Comprobar la instalación

- Comprobar la instalación

La verificáramos ejecutando el comando *go version* para imprimir su versión.

```sh
$ go version
```
Vamos a la terminal, en este caso el CMD de Windows, y ejecutamos. Bien, Go esta funcionando.

Podemos observar que ya se reconoce el comando, esto significa que la variable de entorno GOROOT se configuró correctamente, y ademas que también se modificó la variable PATH del sistema operativo con el directorio binario de Go, porque fue reconocido el comando en el CMD.

Podemos ver, que se reconoce ejecutándolo en cualquier directorio.

#### Comprobar las variables de entorno

Ahora vamos a comprobar las variables de entorno, aunque ya hemos verificado que Go esta funcionando, es importante conocer cuales son, para que sirven y poder resolver problemas en diferentes ambientes.

En este caso como hemos usado el instalador automático, este ya se encargó de agregar las variables de entorno en Windows.

Las variables de entorno son estas dos: GOROOT y GOPATH.

Podemos revisar los valores configurados por el instalador como se muestra acá ejecutando el comando: go env.

El resultado que nos imprima la terminal será algo parecido a los valores de esta tabla.

Vamos a ver. Ejecutamos el comando.

Acá esta una, y acá la otra. Cada una con sus paths configurados.

También podemos consultar directamente el valor de una variable en particular agregando al comando el nombre de dicha variable: "go env GOPATH"

---

En caso que GOROOT o PATH no hayan sido configuradas por el instalador, cuando ejecuten el comando en el CMD de Windows les deberá mostrar un mensaje que dice: "Go" no se reconoce como un comando interno o externo.

Esto se puede solucionar agregando las variables manualmente, por eso vamos a revisar como las configuró el instalador.

Además será util comprender esto, porque en caso de necesitar trabajar con versiones más antiguas de Go deberán realizar manualmente este proceso de configuración.

---

Para ello acá en Windows 10 podemos escribir directamente "variables de entorno".

Para otras versiones de Windows, la forma mas estándar de llegar hasta aquí es ir a Equipo, botón derecho en Propiedades, "Configuración avanzada del sistema" y por ultimo en "Variables de Entorno".

Algo a tener en cuenta en este punto, es que tenemos dos tipos de variables de entorno en Windows.

Una global que corresponde al sistema, y otra de usuario. Es decir, las variables globales de sistema serán compartidas entre todos los usuarios del equipo -si tienen mas de un usuario-. En cambio las variables de usuario, solo la verá el usuario que estan utilizando.

Nosotros vamos a configurar directamente todo en las variables de entorno del sistema.

Podemos observar que efectivamente tenemos GOROOT con el path de instalación. Si no lo tenemos, debemos añadirlo.

Ahora debemos buscar la variable PATH, y verificamos que exista el valor: C:\Go\bin.

En bin se encuentran los binarios de Go.

Bien, ahora vamos a agregar el path de nuestro workspace, es decir, el directorio que usaremos como espacio de trabajo para todos nuestros proyectos escritos en Go.

--TODO: Verificar esto:

Para agregar GOPATH vamos a Nueva, escribimos GOPATH en nombre de variable y luego en Valor de la variable pegamos el path que copiamos hace un momento.

Ahora solo nos queda modificar la variable PATH agregando la sub-carpeta bin de nuestro workspace. Esto nos sirve para ejecutar nuestros proyectos compilados. 

Bien, para eso ubicamos esta variable “PATH” y damos clic en el botón “Editar”, ahora pegamos la dirección de nuestro workspace aquí, agregamos /bin y guardamos.

Listo, ya tenemos las variables de entorno configuradas. GOROOT, GOPATH y PATH.

Repasando, estas variables de entorno son:

GOROOT: El directorio donde instalamos Go, y donde se encuentran los binarios de la Go Tool que nos permitirá compilar entre otras cosas.

GOPATH: Es nuestro directorio de trabajo, aquí adentro vamos a crear todas las carpetas de proyectos Go.

PATH: Le indicamos a Windows donde se encuentran los binarios, para así poner ejecutarlos desde la linea de comandos, el CMD en Windows.

Le damos clic en Aceptar, Aceptar.

Ya tenemos Go instalado y configurado. Así que vamos a probar si funciona.

---

#### Instalar un versionador de código













---







Antes de seguir, vamos a crear una carpeta que será nuestro espacio de trabajo, y este directorio se lo asignaremos a la variable GOPATH para configurar nuestro workspace.

Vamos de nuevo al explorador de archivos, yo la voy a crear dentro de Documentos. Uds pueden crearla donde gusten, pero excepto en el mismo directorio donde esta instalado Go.

Listo, ahora voy a copiar el path y dentro de esta carpeta debemos crear las siguientes sub-carpetas:
