<p align="center">
  <img src="https://img.shields.io/badge/Estado-DEMO-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Módulos-0%2F10%20Libres-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Licencia-Proprietary-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Telegram-@Tobix_Ventas0-0088cc?style=for-the-badge&logo=telegram" />
</p>

# 💀 TOBU - Multi-Tool v4.2 

> Herramienta de consola estilo Matrix para Termux. 10 Módulos de Escaneo, OSINT y Utilidades.

---

### 🔥 PREVIA DE LA INTERFAZ
<p align="center">
  <img src="Screenshot_20260627-025600.jpg" width="400"/>
</p>


---

### 📊 DEMO vs PRO: COMPARATIVA REAL

| Característica | **DEMO GRATIS** | **PRO COMPLETA** |
| --- | --- | --- |
| **Precio** | Gratis | De pago por DM |
| **Módulos Visibles** | 10 | 10 |
| **Módulos Funcionales** | 0 | 10 |
| **Animaciones Glitch** | ✅ Sí | ✅ Sí, Full Speed |
| **Banner ASCII** | ✅ Sí | ✅ Sí |
| **Calavera ASCII** | ✅ Sí | ✅ Sí |
| **Efecto Matrix** | ✅ Sí | ✅ Sí |
| **Uso de Módulos** | 🔒 Bloqueado | ✅ Ilimitado |
| **Banner "Comprar PRO"** | ✅ Sí | ❌ No |
| **Updates Gratis** | ❌ No | ✅ Por 1 mes|
| **Soporte** | ❌ No | ✅ Por Telegram |

---

### 📦 LISTA DE FUNCIONES INCLUIDAS EN LA PRO

La DEMO te muestra el menú, pero todos los módulos están bloqueados.

**1. 🌐 HERRAMIENTAS POR IP** 
   Escaneo de Puertos TCP/UDP, GeoIP con mapa

**2. 📱 Escaneo de Dispositivo** 
   Puertos locales, info del sistema

**3. 👤 User Finder Masivo** 
   Busca un usuario en 100+ redes sociales al instante

**4. 📞 Numero Telefonico** 
   Info de país, operadora y tipo de línea

**5. 💥 Generador Wordlists** 
   Crea diccionarios personalizados

**6. 🔒 Verificacion seguridad** 
   Test de fuerza de contraseñas

**7. 🛡️ Detector VPN** 
   Detecta si una IP usa VPN/Proxy

**8. 📧 Breach Check Email** 
   Revisa si un email fue filtrado

**9. 💀 Simulador de Ataque** 
   Simulación visual para demos/educación

**10. ⚙️ Configuración** 
   Temas, velocidad, etc.

---

### 💎 PASAR A LA VERSIÓN PRO

La DEMO es solo para ver la estética. Si querés usarla de verdad:

1.  **10/10 Módulos 100% Funcionales** Sin bloqueos.
2.  **Sin el cartel de "COMPRAR PRO"** en cada opción.
3.  **Updates** v4.3, v5.0, etc gratis.
4.  **Soporte Directo** Te ayudo a instalarla.

**Precio: Consultar por DM**

👉 **[HABLAR POR TELEGRAM AHORA](https://t.me/Tobix_Ventas0)** 👈

---

### 📲 CÓMO PROBAR LA DEMO

1.  `pkg update && pkg upgrade -y`
2.  `pkg install bash`
3.  Copiá el código del script de abajo en un archivo: `nano tobu_demo.sh`
 ```bash
#!/data/data/com.termux/files/usr/bin/bash
A='\033[0;34m'; R='\033[0;31m'; V='\033[0;32m'; AM='\033[1;33m'; C='\033[0;36m'; B='\033[1;37m'; M='\033[0;35m'; X='\033[0m'

startup_screen(){
clear
for i in {1..30}; do
    COLOR=$((RANDOM % 6 + 31))
    echo -e "\033[0;${COLOR}m$(cat /dev/urandom | tr -dc '01@#$%&*' | head -c 70)${X}"
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
sleep 1
clear
}

glitch_banner(){
clear
for i in {1..2}; do
    echo -e "${R}████████╗ ██████╗ ██████╗ ██╗ ██╗${X}"
    sleep 0.05
    clear
    echo -e "${B}████████╗ ██████╗ ██████╗ ██╗ ██╗${X}"
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

banner(){ glitch_banner; }

matrix(){ for i in {1..8}; do echo -e "${V}$(cat /dev/urandom | tr -dc '01' | head -c 50)${X}"; sleep 0.05; done; clear; }
cargando(){ clear; matrix; echo -e "${R}[ CARGANDO ]${X}"; sleep 0.7; }

pro_lock(){
cargando
echo -e "${AM}╔══════════════╗${X}"
echo -e "${AM}║  ${R}[🔒 DISPONIBLE EN LA VERSIÓN PRO]${AM}  ║${X}"
echo -e "${AM}╚══════════════╝${X}\n"
read -p "Enter para volver..."
}

startup_screen

while true; do
banner;
echo -e "${AM}╔════════╗${X}"; sleep 0.03;
echo -e "${AM}║ ${B}1${AM} │ ${C}🌐 HERRAMIENTAS POR IP${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}2${AM} │ ${C}📱 Escaneo de Dispositivo${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}3${AM} │ ${C}👤 User Finder Masivo${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}4${AM} │ ${C}📞 Numero Telefonico${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}5${AM} │ ${C}💥 Generador Wordlists${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}6${AM} │ ${C}🔒 Verificacion seguridad${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}7${AM} │ ${C}🛡️ Detector VPN${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}8${AM} │ ${C}📧 Breach Check Email${AM} ║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}9${AM} │ ${B}💀 DEMO: Simulador de Ataque${AM} ║${X}";
echo -e "${AM}║ ${B}10${AM} │ ${M}⚙️ Configuración${AM} ║${X}";
echo -e "${AM}║${X} ${AM}║${X}"; sleep 0.03;
echo -e "${AM}║ ${B}0${AM} │ ${R}❌ Salir${AM} ║${X}";
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
1|2|3|4|5|6|7|8|9|10) pro_lock ;; # TODAS BLOQUEADAS
0) clear; echo -e "${R}Saliendo...${X}"; sleep 1; clear; exit 0 ;;
*) echo -e "${R}Invalida${X}"; sleep 1 ;;
esac;
done
```

5.  Dale permisos: `chmod +x tobu_demo.sh`
6.  Ejecuta: `bash tobu_demo.sh`

Podrás ver el menú, las animaciones y el banner. Al tocar cualquier opción te saldrá `[🔒 DISPONIBLE EN LA VERSIÓN PRO]`.

---

### 📜 LICENCIA - LEER ANTES DE USAR

TOBU Multi-Tool v4.2 - Copyright (c) 2026 Tobix. All Rights Reserved.

Esta es una DEMO con fines de exhibición y no comercial 
