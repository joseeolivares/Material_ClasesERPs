# Configuración del servicio de email

## Pasos a seguir:

### Paso 1: Actualizar el sistema

Asegúrate de que tu sistema esté actualizado para obtener las últimas actualizaciones y mejoras de seguridad.

```
sudo apt-get update
sudo apt-get upgrade
```

### Paso 2: Instalar Postfix

Instala el servidor de correo Postfix. Durante la instalación, se te pedirá que elijas un tipo de configuración; elige "Sitio de Internet".

```
sudo apt-get install postfix
```

### Paso 3: Configurar Postfix

Edita el archivo de configuración principal de Postfix.

```
sudo nano /etc/postfix/main.cf
```

Asegúrate de configurar las siguientes líneas, remplazando tu-dominio.com con tu dominio real:

Ejemplo:

```
myhostname = tu-dominio.com
myorigin = /etc/mailname
mydestination = tu-dominio.com, localhost.com, , localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

```

1. myhostname = tu-dominio.com:

Define el nombre de host (hostname) completamente cualificado del servidor de correo. Este valor debe ser el nombre de dominio completo asociado con tu servidor.

Ejemplo: Si tu servidor tiene el nombre de dominio mail.example.com, entonces myhostname = mail.example.com.

2. myorigin = /etc/mailname:

Especifica el archivo que contiene el nombre de dominio que Postfix utiliza como origen del correo electrónico. En muchos sistemas, /etc/mailname se utiliza para almacenar este valor.

Ejemplo: Si /etc/mailname contiene el valor example.com, entonces myorigin = /etc/mailname.

3. mydestination = tu-dominio.com, localhost.com, , localhost:

Indica los destinos para los cuales este servidor de correo aceptará correos. En este caso, tu-dominio.com es el dominio principal para el cual aceptará correos. También incluye localhost.com y localhost como destinos válidos.

Ejemplo: Si tu servidor de correo debe aceptar correos para los usuarios en user@tu-dominio.com, entonces mydestination debe incluir tu-dominio.com.

4. mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128:

Define las direcciones IP o rangos de IP que se consideran parte de la red interna del servidor de correo. En este caso, se incluyen las direcciones IPv4 127.0.0.0/8 y las direcciones IPv6 ::ffff:127.0.0.0/104 y ::1/128.
Ejemplo: Esto permite que el servidor de correo acepte conexiones desde localhost, lo que es necesario para el funcionamiento interno del servidor de correo.

Estas configuraciones son solo ejemplos y deben ajustarse según las necesidades específicas de tu entorno. Asegúrate de reemplazar tu-dominio.com y otros valores con los correspondientes a tu configuración. Además, después de realizar cambios en el archivo de configuración, es importante reiniciar el servicio de Postfix para aplicar las modificaciones:

```
sudo service postfix restart
```

### Paso 4: Reiniciar Postfix

Reinicia el servicio de Postfix para aplicar los cambios.

```
sudo service postfix restart
```

### Paso 5: Instalar Dovecot

Instala Dovecot, que proporciona servicios de acceso a correos electrónicos.

```
sudo apt-get install dovecot-imapd dovecot-pop3d
```

### Paso 6: Configurar Dovecot

Edita el archivo de configuración de Dovecot.

```
sudo nano /etc/dovecot/dovecot.conf
```

Asegúrate de configurar las siguientes líneas:

```
disable_plaintext_auth = no
mail_location = maildir:/var/mail/vhosts/%d/%n

```

1. disable_plaintext_auth = no:

Esta configuración permite la autenticación en texto plano, lo cual es necesario para permitir que clientes de correo se autentiquen utilizando métodos como PLAIN o LOGIN. Estos métodos pueden ser seguros cuando se utilizan junto con conexiones seguras como SSL/TLS.

Nota: Aunque permite la autenticación en texto plano, es crucial implementar conexiones seguras para proteger las credenciales de usuario durante el proceso de autenticación.

2. mail_location = maildir:/var/mail/vhosts/%d/%n:

Esta línea especifica la ubicación en el sistema de archivos donde se almacenarán los correos electrónicos. En este caso, se utiliza el formato maildir, que es un formato de almacenamiento de correos electrónicos en directorios.

%d se sustituirá por el dominio del usuario y %n por el nombre de usuario. Entonces, los correos electrónicos del usuario john en el dominio example.com se almacenarán en /var/mail/vhosts/example.com/john.
Nota: Asegúrate de que el directorio especificado tenga los permisos adecuados para que Dovecot pueda acceder y escribir en él.

Estas configuraciones son fundamentales para el funcionamiento básico de Dovecot como servidor IMAP y POP3. Dovecot es comúnmente utilizado para proporcionar acceso seguro y eficiente a los correos electrónicos almacenados en el servidor. Al igual que con cualquier servidor de correo, es crucial implementar prácticas de seguridad adecuadas, como el uso de conexiones seguras (SSL/TLS), autenticación fuerte, y la protección contra ataques de fuerza bruta.

### Paso 7: Reiniciar Dovecot

Reinicia el servicio de Dovecot.

```
sudo service dovecot restart
```

### Paso 8: Crear usuarios

Crea un usuario que se utilizará para iniciar sesión en el correo electrónico.

```
sudo useradd -m usuario
sudo passwd usuario

```

### Paso 9: Configurar cortafuegos (ufw)

Configura el cortafuegos Uncomplicated Firewall (ufw) para permitir el tráfico necesario para el correo electrónico.

```
sudo ufw allow 25  # SMTP
sudo ufw allow 587 # Submission
sudo ufw allow 110 # POP3
sudo ufw allow 143 # IMAP
sudo ufw enable
```

### Paso 10: Prueba

Envía un correo electrónico de prueba desde la línea de comandos.

```
echo "Este es el cuerpo del correo" | mail -s "Asunto del correo" destinatario@example.com
```

Puedes revisar los registros en /var/log/mail.log para verificar si hay problemas y solucionarlos si es necesario.

Ten en cuenta que esta guía es básica y hay muchos otros aspectos que debes considerar, como la configuración de seguridad adicional, la prevención de spam, la configuración de registros SPF/DKIM/DMARC, y la configuración de SSL/TLS para cifrar las conexiones de correo electrónico. Además, siempre es esencial comprender las implicaciones de seguridad al configurar un servidor de correo.

[EJEMPLO](https://www.lynksthings.com/posts/sysadmin/mailserver-postfix-gmail-relay/)
[VIDEO_EJEMPLO](https://www.youtube.com/watch?v=-3TR4pU3YiU)
[EJEMPLO_DOVECOT](https://www.youtube.com/watch?v=sW9gD_qLBcM)

## Ejemplo fichero para hotmail.es

```
# main.cf - Configuración principal de Postfix

# Nombre del host y dominio
myhostname = tu_servidor.com
mydomain = tu_servidor.com

# Configuración de red
inet_interfaces = all
inet_protocols = ipv4

# Configuración de entrega
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks = 127.0.0.0/8

# Configuración de relay (enviar correo a través de Hotmail)
relayhost = [smtp.live.com]:587
smtp_use_tls = yes
smtp_tls_security_level = encrypt
smtp_tls_note_starttls_offer = yes
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

# Autenticación para el servidor de correo saliente de Hotmail
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_sasl_mechanism_filter = plain

# Activar la entrega local para el correo saliente
local_transport = error:local mail delivery is disabled

# Reglas de filtrado (pueden variar según las necesidades)
smtpd_recipient_restrictions =
    permit_mynetworks,
    permit_sasl_authenticated,
    reject_unauth_destination

```