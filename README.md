# Introduccion
 -Nmap viene de Network Mapper
 
 -Es una herramienta de codigo abierto para escaneo de redes y puertos para hacer auditorias de segridad.
 
 -Una de la mas usadas lo que le da una ventaa operativa de documentacion extra a la oficial.

 # ¿Que podemos hacer con nmap?
 
1. Descubrimiento de hosts.
2. Escaneo de puertos y servicios.
3. Detección de versiones y sistemas operativos.
4. Uso de scripts NSE básicos.

# Target speceficacion en español

Puedes pasar nombres de host, direcciones IP, redes, etc.

```text
-iL <inputfilename>: lee una lista de hosts/redes desde un archivo.
-iR <num hosts>: elige objetivos aleatorios.
--exclude <host1,...>: excluye ciertos hosts o redes del escaneo.
--excludefile <exclude_file>: excluye usando una lista guardada en un archivo.

HOST DISCOVERY (descubrimiento de hosts)
-sL: solo lista los objetivos, no escanea puertos.
-sn: hace un “ping scan”, sin escaneo de puertos.
-Pn: trata todos los hosts como activos y salta la fase de descubrimiento.
-PS/PA/PU/PY[portlist]: usa distintos tipos de paquetes (TCP SYN, ACK, UDP, SCTP) para descubrir hosts.
-PE/PP/PM: usa distintos tipos de peticiones ICMP (eco, timestamp, netmask).
-PO[protocol list]: hace ping por protocolo IP.
-n/-R: nunca resolver DNS / resolver siempre.
--dns-servers ...: especifica servidores DNS propios.
--system-dns: usa el DNS del sistema.
--traceroute: traza la ruta (saltos) hasta cada host.

SCAN TECHNIQUES (técnicas de escaneo)
-sS/sT/sA/sW/sM: diferentes tipos de escaneo TCP (SYN, connect, ACK, Window, Maimon).
-sU: escaneo de puertos UDP.
-sN/sF/sX: escaneos TCP “raros” (Null, FIN, Xmas) para evasión.
--scanflags <flags>: personalizar los flags TCP.
-sI <zombie host>: idle scan usando un “zombie”.
-sY/sZ: escaneos SCTP.
-sO: escaneo de protocolos IP.
-b <FTP relay host>: escaneo usando un servidor FTP como rebote.

PORT SPECIFICATION AND SCAN ORDER (puertos y orden de escaneo)
-p <port ranges>: escanear solo ciertos puertos o rangos.
--exclude-ports <port ranges>: excluir puertos concretos.
-F: modo rápido, escanea menos puertos.
-r: escanear puertos en orden, sin aleatorizar.
--top-ports <number>: escanea los N puertos más comunes.
--port-ratio <ratio>: escanea puertos más comunes que ese ratio.

SERVICE/VERSION DETECTION (detección de servicio/versión)
-sV: sondea puertos abiertos para saber qué servicio/versión hay.
--version-intensity <level>: controla cuánto “insiste” Nmap (0 a 9).
--version-light: escaneo ligero de versiones.
--version-all: prueba todas las sondas posibles.
--version-trace: muestra detalle de lo que hace en el escaneo de versiones.

SCRIPT SCAN (escaneo con scripts)
-sC: equivalente a --script=default.
--script=<Lua scripts>: seleccionar scripts o categorías.
--script-args=...: pasar argumentos a los scripts.
--script-args-file=filename: argumentos desde archivo.
--script-trace: mostrar todo el tráfico de los scripts.
--script-updatedb: actualizar la base de datos de scripts.
--script-help=...: ayuda sobre scripts concretos.

OS DETECTION (detección de SO)
-O: activar detección de sistema operativo.
--osscan-limit: solo probar detección en hosts “prometedores”.
--osscan-guess: adivinar de forma más agresiva.

TIMING AND PERFORMANCE (tiempos y rendimiento)
-T0 a -T5: plantillas de velocidad (más alto = más rápido).
Resto de opciones (--min-hostgroup, --min-rate, etc.) afinan paralelismo, retrasos y límites de tiempo.

FIREWALL/IDS EVASION AND SPOOFING (evasión y suplantación)
-f / --mtu: fragmentar paquetes.
-D: usar IP falsas de señuelo (decoys).
-S: falsear la dirección IP origen.
-e: elegir interfaz de red.
-g/--source-port: fijar puerto origen.
Más opciones para proxies, datos personalizados, TTL, MAC falso, etc.

OUTPUT (salida de resultados)
-oN/-oX/-oS/-oG: guardar resultados en distintos formatos.
-oA <basename>: guardar en varios formatos a la vez.
-v y -d: subir detalle (verbosidad y depuración).
--open: mostrar solo puertos abiertos o posiblemente abiertos.
--resume: reanudar un escaneo interrumpido.

MISC (varios)
-6: activar escaneo IPv6.
-A: activar de golpe OS detection, version detection, scripts y traceroute.
--privileged / --unprivileged: forzar cómo se comporta respecto a permisos.
-V: versión de Nmap.
-h: mostrar la ayuda.
```
# Target speceficacion importantes
Estas son las que usarás el 90% del tiempo:

```nmap <ip>```
Escanea una IP concreta, por ejemplo nmap 192.168.1.10.

```nmap <red/mascara>```
Escanea toda una red en notación CIDR, por ejemplo nmap 192.168.1.0/24.

```-iL <inputfilename>```
Lee una lista de hosts o redes desde un archivo de texto (una IP o red por línea). Es ideal cuando el analista ya tiene un inventario de objetivos.

```-iR <num hosts>```
Selecciona objetivos aleatorios en Internet. Se usa más en pruebas de laboratorio o investigación, no en entornos corporativos.

```--exclude <host1,host2,...>```
Permite excluir algunos hosts o rangos del escaneo, por ejemplo equipos sensibles o que no deben tocarse.

```--excludefile <exclude_file>```
Igual que --exclude, pero leyendo la lista de exclusiones desde un archivo (útil en empresas donde hay una lista oficial de IP que no se escanean)

# Guia de instalacion

**Debian / Ubuntu / Kali / Linux Mint**
```text
sudo apt update
sudo apt install nmap
nmap --version
```

**Fedora / CentOS / RHEL (versiones nuevas con dnf)**
```text
sudo dnf check-update
sudo dnf install nmap
nmap --version
```
**Arch Linux y derivadas (Manjaro, EndeavourOS, etc.)**
```text
sudo pacman -Syu
sudo pacman -S nmap
nmap --version
```
**macOS (con Homebrew)**
```text
# Primero instala Homebrew si no lo tienes (desde https://brew.sh)
brew install nmap
nmap --version
```
**Para Windows**
```text
En Windows, Nmap se instala descargando el instalador oficial desde https://nmap.org/download.html,
ejecutando el .exe como administrador y siguiendo el asistente. Una vez instalado, puede usarse desde la consola
(cmd o PowerShell) ejecutando nmap igual que en Linux o macOS.
```
# Diferencias entre $USER o root al ejecutarlo

**Usuario normal**

 -Nmap no puede crear sockets crudos, así que algunas de las técnicas de escaneo no están disponibles.

 -Suele usar métodos más “limitados”, por ejemplo llamadas connect() normales al sistema en lugar de SYN scan puro, y algunas detecciones de SO o scripts avanzados pueden no funcionar al no tener capacidad de permisos o dar menos información lo cual es critico para un analista de seguridad.

 -Es más “seguro” para no romper nada, pero menos parecido a lo que haría un analista en un entorno profesional, si lo ejectas en tu host es lo mas seguro si estas empezando pero si lo ejecutas en VM no trendrias que tener miedo con sus respectivos respaldos.

 **Usuario root**

 -Nmap sí puede usar raw sockets y otras capacidades del kernel, así que se habilitan técnicas como -sS (SYN scan), muchos tipos de host discovery avanzados y scripts que tocan cosas más bajas de red lo cual nos abre un gran abanico de posibilidades.

 -Los resultados suelen ser más completos y fiables: mejor detección de servicios, SO, respuesta a firewalls, etc lo cual nos da mucha mas informacion que puede ser crucual.

 -Es el modo esperado en auditorías de seguridad reales, por eso en casi todos los ejemplos profesionales verás sudo nmap.

# flujo de trabajo basico

**1. Uso basico**

 En este caso usaremos la paguina del campus de ciberseguridad

No se puede usar ```https:// ni www``` ya que dara fallo

<img width="913" height="76" alt="image" src="https://github.com/user-attachments/assets/43005160-67ed-4307-b059-5b18228b16ff" />

Al usarse bien nos devuelve informacion basica como la ip ```(217.160.0.100)``` y los puertos abiertos

```text
PORT    STATE  SERVICE
21/tcp  closed ftp
22/tcp  closed ssh
80/tcp  open   http
443/tcp open   https
```

<img width="909" height="199" alt="image" src="https://github.com/user-attachments/assets/1d26433e-7734-4207-bb1a-dc323e4bdc19" />

Apartir de ahora usaremos la ip como referencia en vez del enlace 

**2. Definir objetivo**

Podemos escanear la red en la que estamos conectados con:
```text
nmap -sn 192.168.1.0/24
```
<img width="920" height="213" alt="image" src="https://github.com/user-attachments/assets/4afc83f5-2951-42a1-ab06-340e99a367db" />

Para encerrarlo en un archivo para su posteriro lectura automaticamente podemos ejecutar directamente:
```text
sudo nmap -sn 192.168.1.0/24 -oG scan.gnmap
grep "Up" scan.gnmap | awk '{print $2}' > ips-activas.txt
```
<img width="922" height="591" alt="image" src="https://github.com/user-attachments/assets/43d00ac0-3244-4940-8b3e-4fcf7485696f" />


Si desglosamos el comando seria asi:
1. Primer comando: ```sudo nmap -sn 192.168.1.0/24 -oG scan.gnmap```

 -**sudo**
Ejecutas Nmap con privilegios elevados, lo que permite usar toda la potencia de nmap de sondeos (ICMP, ARP, etc.) y mejora la detección de hosts.

 -**nmap -sn**
 Con este comando especificamos que queremos solo los host encendidos ya que va preguntando "¿Quien esta vivo?" con ping scan.

 -**-oG scan.gnmap**
 Indicamos que lo queremos exportar a un formato grepeable en este caso scan.gnmap.

2. Segundo comando: ```grep "Up" scan.gnmap | awk '{print $2}' > ips-activas.txt```

Si usamos el archivo grepeable no se podia ejecitar ningun script de bash ya que nos sale demasiados datos que no nos importan

<img width="922" height="221" alt="image" src="https://github.com/user-attachments/assets/3e6d1b0b-7c46-4537-97b2-c972731bb8c3" />

Asi que lo debemos de filtrar con ```grep y awk```

 -**grep "Up" scan.gnmap**
Abre el archivo grepeable y se queda solo con las lineas que contienen "Up" por si se cuela alguno apagado

 -**awk '{print $2}'**
Aqui lo que hacemos es sacar el segundo campo que se dividen por espacion que en este caso es la ip ya que el contenido es ```Host: 192.168.1.1 (home.home)   Status: Up``` 

 -**> ips-activas.txt**
Rederigimos el archivo grepleable ya filtrado a un .txt en este caso con el nombre ips-activas.txt aunque se le puede llamar de cualquier manera y se nos quedaria de esta manera.

<img width="923" height="186" alt="image" src="https://github.com/user-attachments/assets/5f8c83e0-1f87-4727-9bd1-3410bed126b2" />

Este archivo ya si lo podemos escanear en cadena para no perder el tiempo ya que en redes coorporativas mas extensas abra muchas mas IPs activas.
