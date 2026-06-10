# Introduccion
 -Nmap viene de Network Mapper
 -Es una herramienta de codigo abierto para escaneo de redes y puertos para hacer auditorias de segridad.
 -Una de la mas usadas lo que le da una ventaa operativa de documentacion extra a la oficial.
 -

 # ¿Que podemos hacer con nmap?
 
1. Descubrimiento de hosts.
2. Escaneo de puertos y servicios.
3. Detección de versiones y sistemas operativos.
4. Uso de scripts NSE básicos.

# Target speceficacion en español

Puedes pasar nombres de host, direcciones IP, redes, etc.

```-iL <inputfilename>: lee una lista de hosts/redes desde un archivo.

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

-h: mostrar la ayuda.``` 

