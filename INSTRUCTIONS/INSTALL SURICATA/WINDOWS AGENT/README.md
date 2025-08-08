1.- Instalar npcap en https://npcap.com
2.- Instalar suricata en https://suricata.io/download/
3.- Instalar reglas de suricata en https://rules.emergingthreats.net/open/suricata-7.0.3
- emerging-all.rules.tar.gz
4.- Instalar Notepad++
-Luego ir a C:\Program Files\Suricata\suricata.yaml (abrir con notepadplusplus en administrador)
dentro de address-group:
-Modificar el primer HOME_NET: "<IP-DISPOSITIVO>"
-Buscar con crtl+f "rule-files:" seleccionar todo lo de dentro de rule-files y comentar bloque seleccionado.
Poner dentro de "C:\Program Files\Suricata\rules" el archivo comprimido en emerging-all.rules.tar.gz
Luego en "rule-files:" escribir la nueva regla
- emerging-all.rules
5. Dentro de "C:\Program Files\Suricata" crear nueva carpeta con nombre filter y luego crear un archivo .bpf que dentro contenga "host <IP-DISPOSITIVO>"
6. Finalmente abrimos CMD en modo administrador y escribimos el codigo
"wmic nicconfig get ipaddress,SettingID" debemos guardar el SettingID que este al lado de nuestra IP
7. Dentro del mismo CMD (administrador) poner el siguiente comando:
"C:\Program Files\Suricata\suricata.exe" -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F C:\Program Files\Suricata\filter\filter.bpf

esto hara que se generen unos archivos dentro de "C:\Program Files\Suricata\log"
para ver el trafico que se va generando y suricata va analizando, se puede desde el eve.json como recomendacion puedes abrir el archivo ese con notepad++
8. Dentro de "C:\Program Files(x86)\ossec-agent\ossec.conf
bajamos hasta el final, antes de </ossec_conf> ponemos 
<localfile>
  <log_format>json</log_format>
  <location>C:\Program Files\Suricata\log\eve.json<\location>
</localfile>

9. Dejamos de correr suricata y wazuh
-> Suricata: Ctrl+C
-> Wazuh: net stop Wazuh y luego lo volvemos a hacer correr con net start Wazuh

10. Por ultimo en el archivo "C:\Program Files\Suricata\suricata.yaml"
decomentamos todo lo que habiamos comentado y para volver a correr suricata se debe poner nuevamente el codigo:
"C:\Program Files\Suricata\suricata.exe" -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F C:\Program Files\Suricata\filter\filter.bpf

///OPCIONAL para que este proceso de iniciar suricata sea automatico
1.- Abrir el programador de tareas
2.- Crear tarea básica
3.- Agregar nombre (por ejemplo: "Suricata IDs")
4.- Elige cuando se inicie el sistema como desencadenador
5.- En accion: Iniciar programa
-En programa o script poner la ruta del ejectuable de suricata ("C:\Program Files\Suricata\suricata.exe")
-En agregar argumentos: -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F C:\Program Files\Suricata\filter\filter.bpf
6.- Ejecutar la tarea

////EXISTEN AJUSTES ADICIONALES DENTRO DE SURICATA PARA QUE PUEDA CAPTURAR MAS TIPOS DE PAQUETES

estos ajustes estan en configuration dentro del repositorios
