## Instalación de Go

![alt text](../resources/imgs/go_dl.png "The_Gopher")

#### Pasos a seguir

- Descargar binario
- Configurar variables de entorno
- Comprobar la instalación

#### Variables de entorno

##### `GOROOT`

- Indica donde se encuentra instalado Go.

| OS | PATH |
| ------ | ------ |
| Linux y Mac OS | /usr/local/go |
| Windows | C:\Go |

##### `GOPATH`
* Especifica la ubicación del workspace.
* Este path es usado para resolver importaciones de paquetes.

#### Comprobar la instalación

```sh
$ go version
go version go1.XX.X X/X
```

#### Comprobar las variables

```sh
$ go env
...
GOPATH="/Users/leonardorebola/go"
GOROOT="/usr/local/go"
...
# Entre otras variables que se listarán.
```

#### Referencias

* https://golang.org/doc/install
___

###### Página: [1](./lectura-1.md), [2](./lectura-2.md), [3](./lectura-3.md), [4]
