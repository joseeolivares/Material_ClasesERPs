# Introducción a las redes en Ubuntu

## Algunos comandos

## ifconfig

Muestra la configuración de la interfaz de red actual, incluyendo la dirección IP, la máscara de red y otros detalles.

## ip

Proporciona información detallada sobre la configuración de red, como interfaces, rutas y direcciones IP.

## ping

Envía paquetes ICMP a una dirección IP o nombre de dominio para verificar la conectividad de red y medir el tiempo de respuesta.

## Primeras configuraciones

1. Conectar o desconectar una interfaz de red:

Para conectar una interfaz de red (por ejemplo, eth0) usamos:

```
sudo ifconfig eth0 up
```

Para desconectar una interfaz de red (por ejemplo, eth0) usamos:

```
sudo ifconfig eth0 down
```

2. Asignar una dirección IP estática:

Si deseas asignar una dirección IP estática a una interfaz de red, puedes editar el archivo de configuración de la interfaz. Por ejemplo, si deseas configurar una dirección IP estática para eth0, puedes editar el archivo /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

Luego, agrega o modifica las líneas para configurar la dirección IP estática:

```
auto eth0
iface eth0 inet static
address 192.168.1.100  # Cambia la dirección IP deseada
netmask 255.255.255.0  # Cambia la máscara de red
gateway 192.168.1.1    # Cambia la puerta de enlace

```

Guarda el archivo y reinicia la interfaz o el sistema:

```
sudo ifdown eth0
sudo ifup eth0
```

3. Resolución de nombres DNS:

Puedes editar el archivo /etc/resolv.conf para configurar servidores DNS. Por ejemplo:

```
sudo nano /etc/resolv.conf
```

Agrega líneas como estas:

```
nameserver 8.8.8.8
nameserver 8.8.4.4

```

Guarda el archivo después de agregar los servidores DNS deseados.

Recuerda que estos son solo ejemplos y que la configuración de red puede variar según tu entorno y tus necesidades específicas. Asegúrate de comprender bien tu red antes de realizar cambios importantes en la configuración. Además, ten en cuenta que las configuraciones de red pueden variar según la versión de Ubuntu y las herramientas de red disponibles.



