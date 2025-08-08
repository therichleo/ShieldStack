Edita el archivo "C:\Program Files(x86)\ossec-agent\ossec.conf dentro del apartado <syscheck> debemos poner esto:
<directories check_all="yes" report_changes="yes" realtime="yes">C:\Users\<Usuario>\Downloads</directories>
Luego reiniciamos Wazuh Agent con CMD administrador
net stop Wazuh
net start Wazuh
(pueden probar poniendo un archivo de texto dentro de la carpeta descargas)
///INSTALACION DE VIRUSTOTAL
1.- Estar registrado en virustotal con una API_KEY 
2.- Dentro de Wazuh Manager: "sudo nano /var/ossec/etc/ossec.conf"

agregar lo siguiente

<integration>
  <name>virustotal</name>
  <api_key>API_KEY</api_key>
  <group>syscheck</group>
  <alert_format>json</alert_format>
</integration>

3.- Reiniciamos Wazuh Manager con "sudo systemctl restart wazuh-manager"
4.- Luego creamos un archivo de texto con este texto dentro X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
y vamos a lograr visualizar dentro del dashboard que lanza de que efectivamente esta funcionando
