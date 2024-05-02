# Actividad 13
## Pregunta 1: Diseño de un sistema de entrega y recuperación de correo electrónico

**Contexto:** Una empresa necesita diseñar un sistema de correo electrónico robusto que utilice SMTP, IMAP, y SSL/TLS para la entrega y recuperación segura de correo electrónico.

**Algunos conceptos**
- **SMTP:** Protocolo que se usa para enviar correos electrónicos a través de internet.
- **IMAP:** Protocolo que se utilizada para recuperar correos electrónicos desde un servidor.
- **SSL/TLS:** Son protocolos que se utilizan para establecer una conexión segura a través de internet cifrando la información que se transmite de un cliente al servidor.
- **Certificados X.509:** estándar para vertificados de clave pública. Representan a un usuario, equipo, servicio o dispositivo.

* ### Diagrama de red
![Diagrama de red](img/Act13_diagrama.png)

* ### Escribir un pseudocódigo para la configuración del servidor SMTP y IMAP que también maneje conexiones SSL/TLS.
```
#Establecer conexión con el servidor
setup_smpt_server()
From
To
Content
Send
Quit() #fin de la comunicación con el servidor

# Verificar las credenciales del servidor
# Comunicación con el servidor del receptor
send_email(smtp_server)

# Proteger la comunicación con SSL/TLS
# El servidor del receptor recibe el mensaje
# Establecer conexión con IMAP
setup_imap_server()

# Se recupera el correo electrónico del servidor con IMAP, se identifica las partes del correo
fetch_emails()

# El receptor recibe el correo

```

* ### Explicar cómo se gestionarán los certificados X.509 en este sistema y la importancia de estos para SSL/TLS.
Los certificados X.509 son importantes porque permitir verificar que clientes y servidores, es decir que nos estamos comunicando con quien realmente queremos comunicarnos.

En nuestro contexto:
Cuando el cliente envia el correo electrónico a su servidor de correo, el servidor puede verificar al cliente y el cliente puede verificar al servidor.

* ### Discutir cómo se manejarán las direcciones IP dinámicas y estáticas dentro de esta red, especialmente en relación con DHCP y NAT.
