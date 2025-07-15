## Guía paso a paso para generar alertas a un correo electrónico
#### Aqui generare un tutorial paso a paso en donde explicare como generar alertas por email como estas:
<div style="display: flex;">
  <img width="459" height="194" alt="Imagen 1" src="https://github.com/user-attachments/assets/5fe60a10-7096-4979-bfbb-f936369ecc80" />
  <img width="496" height="267" alt="Imagen 2" src="https://github.com/user-attachments/assets/12117915-4f91-4b74-907e-862ff0fb96f0" />
</div>

###### Cosas a tener en cuenta:
- ###### Necesitaremos una app de contrasenhas, por lo cual para mi recomendacion es hacer que nuestra cuenta de correo electronico tenga 2FA y luego puedes generar la app password desde el menu de seguridad
##### Indice:
1. Creacion de SMTP Server (PostFix)
2. Creacion de contrasenha de APP
3. Modificacion Wazuh
4. Prueba y resultado

### Creacion de SMTP Server (PostFix)
Esta creacion y levantacion del servidor SMTP puede hacerse de diferentes maneras pero en mi caso utilizare sistema operativo Ubuntu (Linux)
