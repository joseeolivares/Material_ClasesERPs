# Configuración de firewall

## Configuración con UFW:

Ubuntu utiliza iptables por defecto como herramienta para configurar firewall. Sin embargo, desde Ubuntu 18.04, se ha introducido ufw (Uncomplicated Firewall) como una interfaz fácil de usar para iptables.

Veamos ejemplos de configuraciones que podemos hacer usando ufw:

### 1: Instalar

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ufw

```

### 2: Habilitar el Firewall

```
sudo ufw enable

```

### 3: Configurar reglas

- Permitir una conexión específica:

```
sudo ufw allow 22  # Permitir SSH
```

- Permitir un rango de puertos:

```
sudo ufw allow 6000:6005/tcp
```

- Permitir tráfico desde una dirección IP específica:

```
sudo ufw allow from 192.168.1.2
```

- Permitir tráfico a una aplicación específica:

```
sudo ufw allow OpenSSH
```

- Denegar una conexión específica:

```
sudo ufw deny 80  # Denegar tráfico HTTP
```

- Denegar tráfico desde una dirección IP específica:

```
sudo ufw deny from 192.168.1.3
```

- Verificar el estado del firewall:

```
sudo ufw status
```

## Configuración con iptables:

Se puede utilizar iptables directamente, configurando reglas manualmente. Aunque iptables es más potente, su sintaxis puede ser más compleja.

Ejemplo:

```
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT  # Permitir SSH
sudo iptables -A INPUT -p tcp --dport 80 -j DROP    # Denegar tráfico HTTP

```

Recuerda que al configurar el firewall, es esencial tener cuidado para no bloquear el acceso a tu sistema. Siempre puedes probar las reglas en un entorno seguro antes de aplicarlas en producción.
