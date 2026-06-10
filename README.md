# Introducción
 -Nmap viene de Network Mapper
 
 -Es una herramienta de código abierto para escaneo de redes y puertos para hacer auditorías de segridad.
 
 -Una de la más usadas lo que le da una ventaja operativa de documentación extra a la oficial.

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

 -Es más “seguro” para no romper nada, pero menos parecido a lo que haría un analista en un entorno profesional, si lo ejecutas en tu host es lo más seguro si estás empezando pero si lo ejecutas en VM no trendrías que tener miedo con sus respectivos respaldos.

 **Usuario root**

 -Nmap sí puede usar raw sockets y otras capacidades del kernel, así que se habilitan técnicas como -sS (SYN scan), muchos tipos de host discovery avanzados y scripts que tocan cosas más bajas de red lo cual nos abre un gran abanico de posibilidades.

 -Los resultados suelen ser más completos y fiables: mejor detección de servicios, SO, respuesta a firewalls, etc lo cual nos da mucha maá información que puede ser crucial.

 -Es el modo esperado en auditorías de seguridad reales, por eso en casi todos los ejemplos profesionales verás sudo nmap.

# flujo de trabajo básico

**1. Uso básico**

 En este caso usaremos la paguina del campus de ciberseguridad

No se puede usar ```https:// ni www``` ya que dara fallo

<img width="913" height="76" alt="image" src="https://github.com/user-attachments/assets/43005160-67ed-4307-b059-5b18228b16ff" />

Al usarse bien nos devuelve información básica como la ip ```(217.160.0.100)``` y los puertos abiertos

```text
PORT    STATE  SERVICE
21/tcp  closed ftp
22/tcp  closed ssh
80/tcp  open   http
443/tcp open   https
```

<img width="909" height="199" alt="image" src="https://github.com/user-attachments/assets/1d26433e-7734-4207-bb1a-dc323e4bdc19" />

A partir de ahora usaremos la ip como referencia en vez del enlace 

**2. Definir objetivos**

Podemos escanear la red en la que estamos conectados con:
```text
nmap -sn 192.168.1.0/24
```
<img width="920" height="213" alt="image" src="https://github.com/user-attachments/assets/4afc83f5-2951-42a1-ab06-340e99a367db" />

Para encerrarlo en un archivo para su posterior lectura automáticamente podemos ejecutar directamente:
```text
sudo nmap -sn 192.168.1.0/24 -oG scan.gnmap
grep "Up" scan.gnmap | awk '{print $2}' > ips-activas.txt
```
<img width="922" height="591" alt="image" src="https://github.com/user-attachments/assets/43d00ac0-3244-4940-8b3e-4fcf7485696f" />


Si desglosamos el comando sería así:
1. Primer comando: ```sudo nmap -sn 192.168.1.0/24 -oG scan.gnmap```

 -**sudo**
Ejecutas Nmap con privilegios elevados, lo que permite usar toda la potencia de nmap de sondeos (ICMP, ARP, etc.) y mejora la detección de hosts.

 -**nmap -sn**
 Con este comando especificamos que queremos solo los host encendidos ya que va preguntando "¿Quien esta vivo?" con ping scan.

 -**-oG scan.gnmap**
 Indicamos que lo queremos exportar a un formato grepeable en este caso scan.gnmap.

2. Segundo comando: ```grep "Up" scan.gnmap | awk '{print $2}' > ips-activas.txt```

Si usamos el archivo grepeable no se podía ejecutar ningun script de bash ya que nos sale demasiados datos que no nos importan.

<img width="922" height="221" alt="image" src="https://github.com/user-attachments/assets/3e6d1b0b-7c46-4537-97b2-c972731bb8c3" />

Así que lo debemos de filtrar con ```grep y awk```

 -**grep "Up" scan.gnmap**
Abre el archivo grepeable y se queda solo con las lineas que contienen "Up" por si se cuela alguno apagado

 -**awk '{print $2}'**
Aquí lo que hacemos es sacar el segundo campo que se dividen por espacios que en este caso es la ip ya que el contenido es ```Host: 192.168.1.1 (home.home)   Status: Up``` 

 -**> ips-activas.txt**
Redirigimos el archivo grepeable ya filtrado a un .txt en este caso con el nombre ips-activas.txt aunque se le puede llamar de cualquier manera y se nos quedaría de esta manera.

<img width="923" height="186" alt="image" src="https://github.com/user-attachments/assets/5f8c83e0-1f87-4727-9bd1-3410bed126b2" />

Este archivo ya sí lo podemos escanear en cadena para no perder el tiempo ya que en redes coorporativas más extensas habrá muchas más IPs activas.

Para escanear todos las IPs filtradas en el archivo anterior ejecutamos el siguente comando:
```text
sudo nmap -sS -sV -iL ips-activas.txt
```
Lo cual nos devuelve un escaneo completo de cada uno de las IPs

<img width="922" height="871" alt="image" src="https://github.com/user-attachments/assets/10b82c86-d2b9-4b9f-885e-256c800c0132" />


**Escaneo especial a IPs**

Para sacar las IPs, si es a una página web podemos o bien hacer un escaneo básico de nmap o usar la herramienta ping con un ```ping campusciberseguridad.com```o algo más silencioso como un ```ping -c 1 campusciberseguridad.com``` ya que el Target ```-c``` se usa para mandar unos paquetes en especifico y si mandamos uno es mucho más silencioso que si mandamos varios.

<img width="924" height="501" alt="image" src="https://github.com/user-attachments/assets/8449f38d-53c0-4c98-be04-55f689392175" />

# Uso de Target más usados

Ya hemos hablado de los Target que más vamos a usar pero vamos a ponerlas en uso, vamos a hacer un comando por cada una de ellas, uno que las englobe todas y por último un comando muy extenso que nos dará un archivo que se podra usar para auditorías de red.

```text
sudo nmap 217.160.0.0/24
```
  -Escanea toda la red usando la notación CIDR.

  -En este ejemplo recorremos la subred detrás de la ip del .1 al .254 te muetra que host nos responden y que puertos tiene abiertos

-Es útil si no sabes aún que ip te interesa en concreto y quieres descubrir más host.

  <img width="917" height="819" alt="image" src="https://github.com/user-attachments/assets/1d73ca78-fde6-4aab-9dd8-24d640e59355" />


```text
sudo nmap -sS -sV -iL objetivos.txt
```

 -Le estamos diciendo que lea una lista de IPs que previemente escaneamos y grepeamos (en este caso en la ip del campus del rango .0 al .03) y que mapee los puertos abiertos

<img width="918" height="411" alt="image" src="https://github.com/user-attachments/assets/798d99b3-1cde-4dc9-affa-bf88ef63b58d" />

```text
sudo nmap -iR 5 -Pn
```

 -Con -iR 5 le decimos que escane 5 host aleatorios en internet.

 -Lo acompañamos con -Pn para solo tratar con los host encendidos y no depender de ping.

 -Se usa, sobre todo más en laboratorio no en entornos coorporativos pero es una opción curiosa que quería recalcar como curiosidad mas que para uso real en una auditoría.

<img width="912" height="414" alt="image" src="https://github.com/user-attachments/assets/793deebd-7d83-4793-9e3a-97f15cc5f406" />

 ```text
sudo nmap -sS -sV 217.160.0.0/24 \
  --exclude 217.160.0.100
```
 -Escaneamos la subred pero respetando y sin tocar la ip atacada.

 - Usamos ```--exlude```para dejar fuera los host sensibles a los cuales podemos no tener permiso como es el caso de un escaneo por curiosidad.

 - Es útil para trabajar con grandes rangos pero respetando una black list crítica o prohibida

<img width="919" height="742" alt="image" src="https://github.com/user-attachments/assets/b609f919-c5c1-48f3-ae3c-9809f1c69815" />


**Comando extenso para una auditoría**

El siguiente comando, lo que hará será un escaneo TCP sobre la ip 217.160.0.100 que pertenece al campus que convinamos detección de de servicios, versiones, sistema operativo y scripts de detección de vulnerabilidades, utilizando una configuración de alto rendimiento con los targets que explicaré posteriormente:

**Comando**

```text
sudo nmap \
  -sS -sV -O -A \
  -p- \
  --open \
  --min-rate 5000 \
  --max-rate 20000 \
  --min-parallelism 50 \
  --max-retries 1 \
  -T5 -vvv -n -Pn \
  --reason \
  --script='default,vuln,http-*' \
  -oN auditoria_217.160.0.100_extenso.txt \
  217.160.0.100
```
**Targets usados uno a uno**

```-sS```
Escaneo TCP SYN (rápido y típico en auditoría).

```--sV```

Detección de versiones de servicios en los puertos abiertos.

```-O```
Intenta identificar el sistema operativo del host.

```-A```
Activa modo “agresivo”: OS detección, versión detección, scripts por defecto y traceroute.

```-p-```
Escanea todos los puertos TCP (1–65535).

```--open```
Solo muestra puertos abiertos (o posiblemente abiertos), lo que deja la salida más limpia para el informe.

**Parte de rendimiento / timing / rate**
```--min-rate 5000```
Envía como mínimo 5000 paquetes por segundo; fuerza un escaneo rápido.

```--max-rate 20000```
Pone un techo de velocidad para no sobrepasar los 20 000 paquetes por segundo.

```--min-parallelism 50```
Mínimo 50 sondeos en paralelo; aumenta la concurrencia y acelera el escaneo.

```--max-retries 1```
Solo reintenta una vez los paquetes que fallan; reduce el tiempo total, a costa de poder perder algún puerto si la red es inestable.

```-T5```
Plantilla de temporizado más agresiva (“insane”), máxima velocidad posible.

```-vvv```
Verbosidad máxima: Nmap imprime todo lo que va haciendo, útil para entender y documentar cada fase.

```-n```
No resuelve DNS (no intenta convertir IP a nombres), ahorra tiempo.

```-Pn```
No hace host discovery; asume que la IP está activa (útil cuando ya sabes que responde o cuando los pings pueden estar filtrados).

**Parte de scripts y razones**
```--reason```
Muestra el “motivo” por el que Nmap considera un puerto abierto/cerrado/filtrado (por ejemplo, tipo de respuesta recibida). Esto te da más contexto para tu informe técnico.

**--script='default,vuln,http-***

```default:``` scripts NSE básicos (información general, banners, etc.)

```vuln:``` scripts de detección de vulnerabilidades conocidas.

```http-*:``` scripts específicos de HTTP (cabeceras, métodos, info de servidor, etc.), muy útiles en una auditoría web.

**Parte de salida**
```-oN auditoria_217.160.0.100_extenso.txt```
Guarda toda la salida en un archivo de texto legible que puedes adjuntar directamente como anexo técnico de la auditoría.

```217.160.0.100```
IP objetivo.

El resultado del comando es:

```text
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.99 ( https://nmap.org ) at 2026-06-10 13:47 +0200
NSE: Loaded 321 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 13:47
Completed NSE at 13:48, 10.01s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 13:48
Completed NSE at 13:48, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 13:48
Completed NSE at 13:48, 0.00s elapsed
Pre-scan script results:
|_http-robtex-shared-ns: *TEMPORARILY DISABLED* due to changes in Robtex's API. See https://www.robtex.com/api/
Initiating SYN Stealth Scan at 13:48
Scanning 217.160.0.100 [65535 ports]
Discovered open port 80/tcp on 217.160.0.100
Discovered open port 443/tcp on 217.160.0.100
Completed SYN Stealth Scan at 13:48, 26.30s elapsed (65535 total ports)
Initiating Service scan at 13:48
Scanning 2 services on 217.160.0.100
Completed Service scan at 13:48, 6.19s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 217.160.0.100
Retrying OS detection (try #2) against 217.160.0.100
Initiating Traceroute at 13:48
Completed Traceroute at 13:48, 2.02s elapsed
NSE: Script scanning 217.160.0.100.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 13:48
NSE Timing: About 21.07% done; ETC: 13:51 (0:01:56 remaining)
NSE Timing: About 21.07% done; ETC: 13:53 (0:03:48 remaining)
NSE Timing: About 21.07% done; ETC: 13:56 (0:05:41 remaining)
NSE Timing: About 21.07% done; ETC: 13:58 (0:07:33 remaining)
NSE Timing: About 21.07% done; ETC: 14:00 (0:09:26 remaining)
NSE Timing: About 21.07% done; ETC: 14:03 (0:11:18 remaining)
NSE Timing: About 22.24% done; ETC: 14:04 (0:12:18 remaining)
NSE Timing: About 22.24% done; ETC: 14:06 (0:14:03 remaining)
NSE Timing: About 22.24% done; ETC: 14:09 (0:15:48 remaining)
NSE Timing: About 22.24% done; ETC: 14:11 (0:17:32 remaining)
NSE Timing: About 22.24% done; ETC: 14:13 (0:19:17 remaining)
NSE Timing: About 22.24% done; ETC: 14:15 (0:21:02 remaining)
NSE Timing: About 22.24% done; ETC: 14:18 (0:22:47 remaining)
NSE Timing: About 23.41% done; ETC: 14:18 (0:22:58 remaining)
NSE Timing: About 23.41% done; ETC: 14:20 (0:24:36 remaining)
NSE Timing: About 23.41% done; ETC: 14:23 (0:26:14 remaining)
NSE Timing: About 23.41% done; ETC: 14:25 (0:27:52 remaining)
NSE Timing: About 23.41% done; ETC: 14:27 (0:29:30 remaining)
NSE Timing: About 23.41% done; ETC: 14:29 (0:31:09 remaining)
NSE Timing: About 23.41% done; ETC: 14:31 (0:32:47 remaining)
Completed NSE at 13:58, 601.04s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 13:58
NSE Timing: About 88.37% done; ETC: 13:59 (0:00:04 remaining)
NSE Timing: About 88.37% done; ETC: 13:59 (0:00:08 remaining)
NSE Timing: About 88.37% done; ETC: 14:00 (0:00:12 remaining)
NSE Timing: About 88.37% done; ETC: 14:01 (0:00:16 remaining)
NSE Timing: About 88.37% done; ETC: 14:01 (0:00:20 remaining)
NSE Timing: About 88.37% done; ETC: 14:02 (0:00:24 remaining)
NSE Timing: About 88.37% done; ETC: 14:02 (0:00:28 remaining)
NSE Timing: About 88.37% done; ETC: 14:03 (0:00:32 remaining)
Completed NSE at 14:03, 262.62s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
Nmap scan report for 217.160.0.100
Host is up, received user-set (0.048s latency).
Skipping host 217.160.0.100 due to host timeout
NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 912.60 seconds
           Raw packets sent: 131186 (5.777MB) | Rcvd: 65 (4.866KB)
```

Y el archivo generado es:

<img width="920" height="229" alt="image" src="https://github.com/user-attachments/assets/be30e8c6-2090-45a7-a8ce-df7068cc2b81" />

En este caso, como era de esperar en una página de un campus de ciberseguridad no se ha encontrado nada.

# Final

Pues con este trabajo, no hemos llegado a ver toda la herramienta pero sí hemos aprendido a usar lo mas importante y básico y sobretodo para los más nuevos es una manera de quitarse el miedo a trabajar con la terminal, ya que parece muy difícil pero con los años me he dado cuenta que no quiero usar otra cosa si es posible ya que es más rápido aunque por supuesto hay que aprender a usarla, creo que nmap es una de las herramientas más importantes puesto que es por donde empieza todo, por un simple escaneo tanto una auditoría como la primera vez que virtualizamos un Kali o un Parrot motivados por una película o un vídeo y nos ponemos un tutorial, normalmente es la primera o de las primeras herramientas que solemos tocar, eso le da un magia especial y cuando se integra en nuestro día a día es algo que damos por hecho siempre pero ¿Qué auditor, hacker, pentester o curioso no lo usa en su día a día? hasta el punto de que cuesta imaginar un trabajo de reconocimiento sin ella.
