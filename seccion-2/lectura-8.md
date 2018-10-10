Your first library 
https://golang.org/doc/code.html#GOPATH




## Workspace


En Go se suele conservar todos los proyectos de código en un único espacio de trabajo. Esto difiere de otros entornos de programación donde cada workspace suele estar asociado a un repositorio de control de versiones. En Go, deberemos tener cada repositorio dentro de un mismo workspace. A menos que optemos por cambiar el path de GOPATH cada vez que queramos trabajar en otro directorio de workspace.


Workspaces

A workspace is a directory hierarchy with two directories at its root:

    src contains Go source files, and
    bin contains executable commands. 

Un espacio de trabajo es una jerarquía de directorios con dos directorios en su raíz:

src contiene archivos fuente Go, y
bin contiene comandos ejecutables.

La herramienta go crea e instala binarios en el directorio bin.