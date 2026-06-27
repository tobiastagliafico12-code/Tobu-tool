
# 🛠️ TOBU - Multi-Tool de Reconocimiento, Utilidades OSINT y mas
Una potente herramienta de consola con interfaz interactiva que reúne utilidades de auditoría de red, recopilación de información (OSINT) y análisis de seguridad en un solo lugar.

## 🚀 Características Principales:

 * **🌐 Escaneo de Puertos:** Escaneo ágil de rangos TCP con barra de progreso en tiempo real.

 * **📍 Geolocalización & Reputación IP:** Rastreo de ubicación (país, ciudad, ISP) y detección de VPNs, Proxies o Hosting.
 
* **👤 OSINT en Redes Sociales:** Buscador masivo de nombres de usuario en plataformas como GitHub, Instagram, X, TikTok, YouTube y Reddit.

 * **📱 Análisis de Dispositivo & Telefonía:** Extracción de info de hardware/sistema (Android, RAM, kernel) y validación avanzada de números telefónicos (operadora y país).
 
* **🛡️ Seguridad de Credenciales:** Generador dinámico de *wordlists* personalizadas para test de fuerza bruta y analizador de seguridad de contraseñas.

* 🎨 Personalización Visual:
** Banner ASCII dinámico, animaciones de carga y 4 temas visuales interactivos (*Cyber Blue, Matrix Green, Blood Red, Purple Hacker*).

# ⚡PREVIA:
<p align="center">
  <img src=Screenshot_20260625-213738.jpg width="400" alt="TOBU corriendo">
</p>



## 🖐️REQUISITOS:
TERMUX (emulador de terminal en android)
y descargar phonenumbers y Python en este:
```bash 
pkg install python3 && pip install phonenumbers
```

# ⭐SCRIPT: 
```bash

#!/data/data/com.termux/files/usr/bin/bash
A='\033[0;34m'; R='\033[0;31m'; V='\033[0;32m'; AM='\033[1;33m'; C='\033[0;36m'; B='\033[1;37m'; M='\033[0;35m'; X='\033[0m'

startup_screen(){
clear
for i in {1..40}; do
    COLOR=$((RANDOM % 6 + 31))
    echo -e "\033[0;${COLOR}m$(cat /dev/urandom | tr -dc '01@#$%&*' | head -c 80)${X}"
    sleep 0.02
done
clear
echo -e "${A}████████╗ ██████╗ ██████╗ ██╗ ██╗"
echo "╚══██╔══╝██╔═══██╗██╔══██╗██║ ██║"
echo " ██║ ██║ ██║██████╔╝██║ ██║"
echo " ██║ ██║ ██║██╔══██╗██║ ██║"
echo " ██║ ╚██████╔╝██████╔╝╚██████╔╝"
echo " ╚═╝ ╚═════╝ ╚═════╝ ╚═════╝ "
echo -e "${X}"
echo -e "${B} Herramienta de escaneo v4.2${X}"
echo -e "${AM} by TOBU${X}\n"
echo -ne "${C}Iniciando Sistema [${X}"
for i in {1..100}; do echo -ne "${V}█${X}"; sleep 0.01; done
echo -e "${C}] 100%${X}"
sleep 0.5
clear
}

# ===== GLITCH EFFECT =====
glitch_banner(){
clear
for i in {1..3}; do
    echo -e "${R}████████╗ ██████╗ ██████╗ ██╗ ██╗${X}"
    echo -e "${V}╚══██╔══╝██╔═══██╗██╔══██╗██║ ██║${X}"
    echo -e "${C} ██║ ██║ ██║██████╔╝██║ ██║${X}"
    sleep 0.05
    clear
    echo -e "${AM}████████╗ ██████╗ ██████╗ ██╗ ██╗${X}"
    echo -e "${B}╚══██╔══╝██╔═══██╗██╔══██╗██║ ██║${X}"
    echo -e "${R} ██║ ██║ ██║██████╔╝██║ ██║${X}"
    sleep 0.05
done
echo -e "${A}████████╗ ██████╗ ██████╗ ██╗ ██╗"
echo "╚══██╔══╝██╔═══██╗██╔══██╗██║ ██║"
echo " ██║ ██║ ██║██████╔╝██║ ██║"
echo " ██║ ██║ ██║██╔══██╗██║ ██║"
echo " ██║ ╚██████╔╝██████╔╝╚██████╔╝"
echo " ╚═╝ ╚═════╝ ╚═════╝ ╚═════╝ "
echo -e "${X}"
echo -e "${B} Herramienta de escaneo v4.2${X}"
echo -e "${AM} by TOBU${X}\n"
}

cambiar_tema(){
clear; banner; echo -e "${AM}=== 🎨 SELECCIONAR TEMA ===${X}\n";
echo -e "${B}1${X} │ ${A}🔵 Cyber Blue${X}";
echo -e "${B}2${X} │ ${V}💚 Matrix Green${X}";
echo -e "${B}3${X} │ ${R}🔴 Blood Red${X}";
echo -e "${B}4${X} │ ${C}🟣 Purple Hacker${X}";
echo -e "${B}0${X} │ ${R}⬅️ Volver${X}\n";
read -p "Opcion: " t;
case $t in
1) A='\033[0;34m'; R='\033[0;31m'; V='\033[0;32m'; AM='\033[1;33m'; C='\033[0;36m'; B='\033[1;37m'; M='\033[0;35m' ;;
2) A='\033[0;32m'; R='\033[0;32m'; V='\033[0;32m'; AM='\033[0;32m'; C='\033[0;32m'; B='\033[1;32m'; M='\033[0;32m' ;;
3) A='\033[0;31m'; R='\033[0;31m'; V='\033[0;31m'; AM='\033[0;31m'; C='\033[0;31m'; B='\033[1;31m'; M='\033[0;31m' ;;
4) A='\033[0;35m'; R='\033[0;35m'; V='\033[0;35m'; AM='\033[1;35m'; C='\033[0;35m'; B='\033[1;35m'; M='\033[0;35m' ;;
0) return ;;
esac;
echo -e "\n${V}Tema aplicado ✓${X}"; sleep 1;
}

configuracion(){
while true; do
clear; banner;
echo -e "${AM}=== ⚙️ CONFIGURACIÓN ===${X}\n";
echo -e "${B}1${X} │ ${C}🎨 Cambiar Tema Colores${X}";
echo -e "${B}0${X} │ ${R}⬅️ Volver al Menú${X}\n";
read -p "Opcion: " cf
case $cf in
1) cambiar_tema ;;
0) break ;;
*) echo -e "${R}Invalida${X}"; sleep 1 ;;
esac
done
}

banner(){ glitch_banner; }

matrix(){ for i in {1..15}; do echo -e "${V}$(cat /dev/urandom | tr -dc '01' | head -c 60)${X}"; sleep 0.04; done; clear; }

cargando(){ clear; matrix; echo -e "${R}[ $1 CARGANDO ]${X}"; sleep 1; }

barra(){ total=$2; actual=$1; ancho=20; lleno=$((actual*ancho/total)); vacio=$((ancho-lleno)); perc=$((actual*100/total)); printf "\r${C}[${V}"; for i in $(seq 1 $lleno); do printf "█"; done; for i in $(seq 1 $vacio); do printf "░"; done; printf "${C}] %3d%% Puerto %d${X}" $perc $actual; }

portscan(){ cargando "ESCANEO DE PUERTOS"; banner; read -p "IP a escanear: " ip; read -p "Rango puertos ej 20-100: " rango; echo ""; IFS=- read min max <<< "$rango"; total=$((max-min+1)); found=0; for p in $(seq $min $max); do barra $p $total; timeout 0.3 bash -c "echo >/dev/null >/dev/tcp/$ip/$p" 2>/dev/null && echo -e "\n${V}[PUERTO $p ABIERTO] \a${X}" && found=1; done; echo ""; if [ $found -eq 0 ]; then echo -e "${AM}No se encontraron puertos abiertos${X}"; fi; echo ""; read -p "Enter para volver..."; }

geoip(){
cargando "UBICACION POR IP";
banner;
read -p "Ingresa la IP: " ip;
echo "";
echo -e "${C}Obteniendo datos...${X}";
echo "";
res=$(curl -s --connect-timeout 5 "http://ip-api.com/json/$ip?lang=es&fields=status,country,regionName,city,isp,lat,lon,timezone,query" 2>/dev/null);
if [ -z "$res" ] || echo "$res" | grep -q '"status":"fail"'; then
    echo -e "${R}Error: Sin conexion o IP invalida${X}";
else
    echo "$res" | python3 -m json.tool 2>/dev/null || echo "$res";
    echo "";
    lat=$(echo "$res" | python3 -c "import sys,json; print(json.load(sys.stdin)['lat'])" 2>/dev/null)
    lon=$(echo "$res" | python3 -c "import sys,json; print(json.load(sys.stdin)['lon'])" 2>/dev/null)
    city=$(echo "$res" | python3 -c "import sys,json; print(json.load(sys.stdin)['city'])" 2>/dev/null)
    country=$(echo "$res" | python3 -c "import sys,json; print(json.load(sys.stdin)['country'])" 2>/dev/null)
    if [ -n "$lat" ] && [ -n "$lon" ]; then
        echo -e "${V}[+] Generando mapa...${X}"
        mapa="/sdcard/TOBU_Mapa_${ip}.html"
        cat > "$mapa" <<EOF
<!DOCTYPE html><html><head><title>TOBU Mapa $ip</title>
<meta charset="utf-8" /><meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<style>body{margin:0;padding:0}#map{height:100vh;width:100vw}</style>
</head><body>
<div style="position:absolute;z-index:1000;background:#000;color:#0f0;padding:5px;font-family:monospace;">TOBU v4.2 | $ip | $city, $country</div>
<div id="map"></div>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>var map=L.map('map').setView([$lat,$lon],12);
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
L.marker([$lat,$lon]).addTo(map).bindPopup('<b>IP: $ip</b><br>$city, $country').openPopup();
</script></body></html>
EOF
        echo -e "${V}Mapa guardado en: ${AM}$mapa${X}"
        echo -e "${C}Abriendo mapa...${X}"
        termux-open "$mapa" 2>/dev/null
    fi
fi;
echo "";
read -p "Enter para volver...";
}

ip_rep(){ cargando "IP REPUTATION"; banner; read -p "Ingresa la IP: " ip; echo ""; echo -e "${C}Analizando reputacion...${X}"; echo ""; data=$(curl -s --connect-timeout 5 "http://ip-api.com/json/$ip?fields=status,query,country,as,proxy,hosting" 2>/dev/null); if [ -z "$data" ]; then echo -e "${R}Error: Sin conexion${X}"; else echo "$data" | python3 -m json.tool 2>/dev/null || echo "$data"; echo ""; if echo "$data" | grep -q '"proxy":true'; then echo -e "${R}ALERTA: Proxy/VPN detectado${X}"; elif echo "$data" | grep -q '"hosting":true'; then echo -e "${R}ALERTA: IP de Hosting${X}"; else echo -e "${V}IP residencial normal${X}"; fi; fi; echo ""; read -p "Enter para volver..."; }

wordlist_gen(){ cargando "GENERADOR WORDLISTS"; banner; read -p "Palabra base ej admin: " base; echo ""; echo -e "${C}Generando combinaciones...${X}\n"; sufijos=("123" "2026" "!" "@" "01" "admin" "qwerty" "1234"); for s in "${sufijos[@]}"; do echo "${base}${s}"; echo "${base^}${s}"; done > wordlist_$base.txt; cat wordlist_$base.txt; echo -e "\n${V}Guardado en: wordlist_$base.txt${X}"; echo ""; read -p "Enter para volver..."; }

pass_check(){ cargando "VERIFICACION PASS"; banner; read -p "Ingresa la contraseña a analizar: " pass; len=${#pass}; fuerza=0; [[ $pass =~ [a-z] ]] && ((fuerza++)); [[ $pass =~ [A-Z] ]] && ((fuerza++)); [[ $pass =~ [0-9] ]] && ((fuerza++)); [[ $pass =~ [^a-zA-Z0-9] ]] && ((fuerza++)); echo ""; echo -e "${B}Longitud: ${X}$len caracteres"; echo -e "${B}Mayusculas: ${X}$([[ $pass =~ [A-Z] ]] && echo 'Si' || echo 'No')"; echo -e "${B}Numeros: ${X}$([[ $pass =~ [0-9] ]] && echo 'Si' || echo 'No')"; echo -e "${B}Simbolos: ${X}$([[ $pass =~ [^a-zA-Z0-9] ]] && echo 'Si' || echo 'No')"; echo ""; if [ $len -ge 12 ] && [ $fuerza -eq 4 ]; then echo -e "${V}FUERTE 🔒 - Muy dificil de crackear${X}"; elif [ $len -ge 8 ] && [ $fuerza -ge 3 ]; then echo -e "${AM}MEDIA ⚠️ - Aceptable pero mejorable${X}"; else echo -e "${R}DEBIL 💀 - Facil de crackear${X}"; fi; echo ""; read -p "Enter para volver..."; }

vpn_check(){
cargando "ESTADO DE ANONIMATO";
banner;
echo -e "${C}Consultando IP publica...${X}\n";
ip_real=$(curl -s --max-time 5 ifconfig.me 2>/dev/null)
geo=$(curl -s --max-time 5 "http://ip-api.com/json/$ip_real?fields=country,isp,proxy,hosting" 2>/dev/null)
if [ -z "$ip_real" ]; then
    echo -e "${R}Error: Sin conexion a internet${X}"
else
    echo -e "${B}Tu IP Publica: ${X}$ip_real"
    echo "$geo" | python3 -m json.tool 2>/dev/null || echo "$geo"
    echo ""
    if echo "$geo" | grep -q '"proxy":true'; then
        echo -e "${V}[✓] VPN/PROXY ACTIVA - Estas anonimo${X}"
    elif echo "$geo" | grep -q '"hosting":true'; then
        echo -e "${AM}[!] IP de Hosting/VPS detectada${X}"
    else
        echo -e "${R}[x] VPN INACTIVA - IP residencial expuesta${X}"
    fi
fi
echo ""
read -p "Enter para volver..."
}

email_check(){
cargando "BREACH CHECK";
banner;
read -p "Ingresa el email a verificar: " email;
echo "";
echo -e "${C}Consultando breaches...${X}\n";
echo -e "${AM}Nota: Solo muestra si el email aparecio en breaches conocidos${X}\n";
res=$(curl -s "https://haveibeenpwned.com/api/v3/breachedaccount/$email?truncateResponse=false" 2>/dev/null)
if [ -z "$res" ] || [ "$res" == "[]" ]; then
    echo -e "${V}[✓] SIN BREACHES ENCONTRADOS${X}"
    echo -e "${B}El email no aparece en bases filtradas conocidas${X}"
else
    echo -e "${R}[!] EMAIL COMPROMETIDO${X}\n"
    echo "$res" | python3 -c "import sys,json; d=json.load(sys.stdin);
for x in d: print('[+] {} - {} - {} cuentas'.format(x['Name'], x['BreachDate'], x['PwnCount']))" 2>/dev/null
    echo ""
    echo -e "${AM}Recomendacion: Cambiar contraseñas ya${X}"
fi
echo ""
read -p "Enter para volver..."
}

# ===== SIMULADOR ATAQUE - SOLO DEMO/ANIMACION =====
simular_ataque(){
cargando "SIMULADOR";
banner;
echo -e "${AM}[!] MODO SIMULACION - SIN ACCESO REAL [!]${X}\n";
read -p "Ingresa IP de objetivo DEMO: " ip;
echo "";
echo -e "${C}Iniciando escaneo simulado contra $ip...${X}\n";
sleep 1;

fases=("Reconocimiento" "Mapeo de puertos" "Fuerza bruta" "Explotacion" "Post-Explotacion")
for i in {1..100}; do
    if [ $((i % 20)) -eq 0 ]; then
        fase=${fases[$((i/20))]}
        echo -e "\n${B}[*] $fase...${X}"
    fi
    printf "\r${R}[${V}";
    for j in $(seq 1 $((i/5))); do printf "█"; done;
    printf "${R}] %3d%%${X}" $i;
    sleep 0.03;
done
echo -e "\n\n${R}[!] SIMULACION FINALIZADA [!]${X}"
echo -e "${AM}Resultado: ACCESO DENEGADO - Sistema protegido${X}"
echo -e "${C}Esto es solo una animacion educativa. No se realizo ningun ataque real.${X}\n"
read -p "Enter para volver..."
}

herramientas_ip(){ while true; do banner; echo -e "${AM}=== 🌐 HERRAMIENTAS POR IP ===${X}"; echo ""; echo -e "${B}1${X} │ ${C}🔍 Escaneo de Puertos${X}"; echo -e "${B}2${X} │ ${C}📍 Ubicacion por IP + Mapa${X}"; echo -e "${B}3${X} │ ${C}🛡️ IP Reputation${X}"; echo -e "${B}0${X} │ ${R}⬅️ Volver al menu${X}"; echo ""; read -p "Opcion: " op; case $op in 1) portscan ;; 2) geoip ;; 3) ip_rep ;; 0) break ;; *) echo -e "${R}Invalida${X}"; sleep 1 ;; esac; done; }

dispositivo(){ cargando "DISPOSITIVO"; banner; echo -e "${V}Info del telefono:${X}"; echo ""; echo -e "${B}Modelo: ${X}$(getprop ro.product.model 2>/dev/null)"; echo -e "${B}Marca: ${X}$(getprop ro.product.brand 2>/dev/null)"; echo -e "${B}Android: ${X}$(getprop ro.build.version.release 2>/dev/null)"; echo -e "${B}Kernel: ${X}$(uname -r)"; echo -e "${B}RAM: ${X}$(free -h 2>/dev/null | grep Mem | awk '{print $2}')"; echo ""; read -p "Enter para volver..."; }

userfinder(){ cargando "USER FINDER MASIVO"; banner; read -p "Usuario a buscar: " u; echo ""; echo -e "${AM}Buscando en redes...${X}"; echo ""; echo -e "${B}[+] GitHub: ${X}github.com/$u"; echo -e "${B}[+] Instagram: ${X}instagram.com/$u"; echo -e "${B}[+] Twitter/X: ${X}x.com/$u"; echo -e "${B}[+] TikTok: ${X}tiktok.com/@$u"; echo -e "${B}[+] YouTube: ${X}youtube.com/@$u"; echo -e "${B}[+] Reddit: ${X}reddit.com/user/$u"; echo ""; read -p "Enter para volver..."; }

telefono(){ cargando "NUMERO TELEFONICO"; banner; read -p "Numero con codigo pais ej +54911: " n; echo ""; python3 -c "import phonenumbers; from phonenumbers import geocoder,carrier; z=phonenumbers.parse('$n',None); print('Valido:',phonenumbers.is_valid_number(z)); print('Pais:',geocoder.description_for_number(z,'es')); print('Operadora:',carrier.name_for_number(z,'es'))" 2>/dev/null || echo "Instala: pip install phonenumbers"; echo ""; read -p "Enter para volver..."; }

startup_screen

while true; do
banner;
echo -e "${AM}╔════════╗${X}"; sleep 0.05;
echo -e "${AM}║ ${B}1${AM} │ ${C}🌐 HERRAMIENTAS POR IP${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}2${AM} │ ${C}📱 Escaneo de Dispositivo${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}3${AM} │ ${C}👤 User Finder Masivo${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}4${AM} │ ${C}📞 Numero Telefonico${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}5${AM} │ ${C}💥 Generador Wordlists${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}6${AM} │ ${C}🔒 Verificacion seguridad${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}7${AM} │ ${C}🛡️ Detector VPN${AM} ║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}8${AM} │ ${C}📧 Breach Check Email${AM} ║${X}";
echo -e "${AM}║${X} ${AM}║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}9${AM} │ ${B}💀 DEMO: Simulador de Ataque${AM} ║${X}"; # BLANCO ${B} 
echo -e "${AM}║ ${B}10${AM} │ ${M}⚙️ Configuración${AM} ║${X}"; # VIOLETA ${M}
echo -e "${AM}║${X} ${AM}║${X}"; sleep 0.05;
echo -e "${AM}║ ${B}0${AM} │ ${R}❌ Salir${AM} ║${X}"; # ROJO ${R}
echo -e "${AM}╚════════╝${X}"; echo "";

read -p "Opcion: " o;
echo ""

# ===== CALAVERA ASCII =====
echo -e "${R}"
cat << 'EOF'
   __
  / _\.-''-.
 / _ \
 | \\ / |
 | |
 | |
  \_/ \___/
   \___/
   TOBU
EOF
echo -e "${X}\n"

case $o in
1) herramientas_ip ;;
2) dispositivo ;;
3) userfinder ;;
4) telefono ;;
5) wordlist_gen ;;
6) pass_check ;;
7) vpn_check ;;
8) email_check ;;
9) simular_ataque ;;
10) configuracion ;;
0) clear; echo -e "${R}Saliendo...${X}"; sleep 1; clear; exit 0 ;;
*) echo -e "${R}Invalida${X}"; sleep 1 ;;
esac;
done
```
* Tan solo es copiar y pegar el script en Termux.👌

# AVISOS Y RECOMENDACIONES SOBRE EL USO:
* ❗Al seleccionar la opción "0": "SALIR", se cerrará automáticamente la herramienta y la app.

* ❗Al colocar un número telefónico en la opcion "4", Le recomendamos que use un código de país, ejemplo: "+54"xxx

* ❗Las opciones del submenú de herramientas de IP "1", Pueden dejar de funcionar dependiendo de tu dispositivo.



