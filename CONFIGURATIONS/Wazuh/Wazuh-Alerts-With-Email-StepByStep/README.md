## Step-by-Step Guide to Sending Alerts via Email
#### In this tutorial, I’ll walk you through the process of configuring email alerts, like the ones shown below:
<div style="display: flex;">
  <img width="459" height="194" alt="Imagen 1" src="https://github.com/user-attachments/assets/5fe60a10-7096-4979-bfbb-f936369ecc80" />
  <img width="496" height="267" alt="Imagen 2" src="https://github.com/user-attachments/assets/12117915-4f91-4b74-907e-862ff0fb96f0" />
</div>

###### Things to Keep in Mind:
- ###### You'll need an app password. I highly recommend enabling 2FA (Two-Factor Authentication) on your email account. After that, you can generate an App Password from your account’s security settings.
##### Table of Contents:
1. Creating the SMTP Server (Postfix)
2. Generating the App Password
3. Modifying Wazuh Configuration
4. Testing and Results

### Creating the SMTP Server (Postfix)
Esta creacion y levantacion del servidor SMTP puede hacerse de diferentes maneras pero en mi caso utilizare sistema operativo Ubuntu (Linux)
- Primero debemos correr el siguiente codigo
```
apt-get update && apt-get install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules
```
- Lo que hace es actualizar la dependecia de paquetes disponibles
- Instala PostFix el cual es un servidor de correos
- Instala MailUtils herramienta para enviar correos
- Y finalmente librerias necesarias para autenticacion y certificacion
Luego de esto, se debe ir a la ruta: ``` /etc/postfix/main.cf ``` y tenemos que poner lo siguiente:
```
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_use_tls = yes
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
```
Luego seguimos esta linea de comandos
- Pero antes de iniciar con los comandos ya debemos contar con un correo electronico el cual usara Wazuh para notificarte y una App password, en mi caso utilice la de google y para generarr la app password es directamente con este link ```https://myaccount.google.com/apppasswords``` Ya una vez teniendo todo esto en mano podemos avanzar directamente a los comandos:
