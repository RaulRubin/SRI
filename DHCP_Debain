# Practica de Instalacion del DHCP en un equipo Debian Server

## Preparamos el router
Primero prepararemos el router para la conectividad de la red interna de la estructura con el exterior

![Image]()

Como podemos ver la LAN de la red es la 10.0.218.1 que es la que asociamos en el VirtualBox para la red interna.

## Instalamos el servidor DHCP en Debian

Antes de hacerlo comprobamos la configuracion de red del Bebian 12, que seria una estatica, osea que tenemos que ponerle nosotros la Ip, en nuestro caso seria la 10.0.218.2

![Image]()

---

Para ello usare un Debian 12 de entorno grafico.

![Image]()

Como se puede apreciar primero hice un **apt update** para asegurarme de que esta actualizado y despues le hice un **apt-get install isc-dhcp-server** para instalar el servidor DHCP

## Configuramos el servidor DHCP

Deberemos de configurarlo desde el fichero **/etc/dhcp/dhcpd.conf** donde pondremos el rango de ips, los DNS que usaremos, el nombre del servidor DHCP y la ip del router, y despues de ello habra otra opcion que nos dejara poner en base de segundos el tiempo que tenemos para darle IP.

![Image]()

Tambien deberemos de asignar una ip fija para un equipo linux, entonces bajaremos en ese mismo fichero hacia una parte comentada donde pone **host tunombre**

Lo descomentamos y le ponemos un nombre para identificarlo, en mi caso Ubuntu-Cliente. Abajo habra mas contenido que pertenece a la direccion MAC del equipo linux y la ip que queremos asignarle

![Image]()

## Configuramos el servicio DHCP

Para configurarlo, deberemos de editar el fichero **/etc/default/isc-dhcp-server** y de lo que nos pone, bajaremos a "INTERFACESv4" y pondremos enp0s3 entre comillas despues del igual.
Esto lo haremos para identificar el interfaz ethernet usado

![Image]()

## Reiniciamos el servicio DHCP

Reiniciamos el servicio para que se guarden los cambios y se actualicen, para ello usaremos el **systemctl restart isc-dhcp-server.service** y luego de ello miraremos que no paso ningun tipo de inconveniente realizando un **systemctl status isc-dhcp-server.service**

![Image]()

aunque tambien para comprobar el servicio podemos poner **journalctl -f -u isc-dhcp-server** que nos informa sobre el DHCPOFFFER, DHCPREQUEST, DHCPPACK y DHCPDISCOVER

![Image]()

## Configuracion de red de los equipos clientes

Aqui iremos a los clientes y abriremos los distintos interfaces de red.

En Windows seria este:

![Image]()

Y en el equipo Linux seria este

![Image]()

## Conectividad entre equipos clientes con el servidor Debian

Para que pueda se pueda realizar todo, tendran todos los equipos que tener conectividad con el servidor, para ello los pondremos en la misma red interna y luego haremos un ping con cada uno hacia el servidor.

Este seria el de Linux 

![Image]()

y este seria el de Windows

![Image]()

## Comprobacion de las IP

Una vez hayamos reiniciamos el servicio y haya conectividad comprobaremos las ips en todos los clientes

Este seria en Windows

![Image]()

y este seria en Linux que como le pusimos una ip fija, se le asigna la que hayamos puesto.

![Image]()

Y asi tendriamos un servidor funcional de DHCP.
