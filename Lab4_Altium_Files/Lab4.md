# Tarjeta OBC + COMMS (PCB 2) — CubeSat UD34

Este directorio contiene el proyecto de diseño electrónico en **Altium Designer** correspondiente a la tarjeta integrada de **Computador de a Bordo y Comunicaciones (OBC + COMMS - PCB 2)** del nanosatélite académico tipo CubeSat 1U (UD34).

- **Autores:** Juan José Díaz, Kevin Echeverri
- **Institución:** Universidad de Antioquia
- **Curso:** Diseño de Productos Electrónicos
- **Documento de Referencia:** `Proyecto_Diseño_E2.pdf` (Especificación de la tarjeta OBC+COMMS)

---

## 1. Identificación de la Tarjeta

La **PCB 2** es la tarjeta central de la plataforma espacial UD34 y consolida las siguientes funciones:
- **Computador de a Bordo (OBC):** Procesador SoC Microchip SmartFusion2 (ARM Cortex-M3 + matriz FPGA Flash), encargado de la coordinación de la misión, gestión de telemetría/telecomando y compresión de datos.
- **Sistema de Almacenamiento Masivo:** Memorias MRAM (código seguro/RTOS), RAM DDR3L (buffer temporal de trabajo) y eMMC de 32 GB (almacenamiento de imágenes multiespectrales).
- **Comunicaciones UHF (TT&C):** Transceptor RFIC Si4468 y amplificador de potencia ADL5324 operando en 435–438 MHz a 9.6 kbps para comandos y telemetría.
- **Comunicaciones Banda S (Downlink):** Transceptor SDR AD9364 y amplificador de potencia operando en 2.2–2.4 GHz para descarga masiva de imágenes hacia la estación terrestre de Medellín (1–8 Mbps).
- **Regulación Local (POL):** Convertidores Buck TPS62130A y LDOs de ultra-bajo ruido LT3042/LT3045.

---

## 2. Software y Versión de Altium Utilizada

- **Herramienta CAD:** Altium Designer
- **Versión Recomendada:** **Altium Designer 24.0** (o superior)
- **Formato de Proyecto:** Proyecto de PCB multinivel con esquema jerárquico (`.PrjPcb`).
- **Librería de Componentes:** Librería local/integrada mantenida dentro del repositorio (`.SchLib`).

---

## 3. Estructura del Proyecto

```text
Lab4_Altium_Files/
├── Lab4_Altium_Files.PrjPcb            # Archivo principal del proyecto Altium
├── 02_Top_Board.SchDoc         # Esquemático raíz (Top-Level Sheet)
├── 03_SoC_SmartFusion2.SchDoc  # Sub-hoja SoC SmartFusion2
├── 04_Memory.SchDoc            # Sub-hoja Memorias (MRAM, DDR3L, eMMC)
├── 05_UHF.SchDoc               # Sub-hoja Transceptor UHF
├── 06_S_Band.SchDoc            # Sub-hoja Transceptor Banda S
├── 07_Power.SchDoc             # Sub-hoja Regulación de Potencia Local
├── 08_Interfaces.SchDoc        # Sub-hoja Bus PC/104 y conectores de debug
├── Libraries/                  # Librerías locales de componentes
│   ├── Lab4_Altium_Files.SchLib
└── README.md                   # Este archivo
```

---

## 4. Instrucciones para Abrir y Explorar el Proyecto

Sigue los siguientes pasos para clonar y abrir el proyecto de la tarjeta en **Altium Designer**:

### Requisitos Previos
1. Tener instalado **Altium Designer v24.0** o superior.
2. Tener instalado un cliente **Git** (Git CLI o GitHub Desktop).

### Paso 1: Clonar el Repositorio
Abre la terminal o cliente Git y clona el repositorio en tu máquina local:
```bash
git clone https://github.com/juanjodiaz04/Proyecto_Diseno_Productos.git
cd Lab4_Altium_Files
```

### Paso 2: Abrir el Proyecto en Altium Designer
1. Ejecuta **Altium Designer**.
2. Ve al menú superior y selecciona **File > Open Project...** (o presiona `Ctrl + O`).
3. Navega hasta la carpeta `Lab4_Altium_Files/` y selecciona el archivo de proyecto **`Lab4_Altium_Files.PrjPcb`**.
4. Haz clic en **Open**.

### Paso 3: Cargar y Verificar las Librerías Locales
Para garantizar que todos los símbolos esquemáticos y footprints se vinculen correctamente mediante rutas relativas:
1. En el panel **Projects** (panel lateral izquierdo), verifica que la carpeta `Libraries/` aparezca vinculada bajo el proyecto.
2. Si realizas cambios en los componentes locales (`.SchLib` o `.PcbLib`), haz clic derecho sobre el proyecto de librería integrada y selecciona **Compile Integrated Library**.

### Paso 4: Navegar la Jerarquía del Esquemático y Ejecutar ERC
1. Abre el archivo **`02_Top_Board.SchDoc`** para visualizar el diagrama jerárquico por bloques.
2. Para explorar cualquier sub-bloque, mantén presionada la tecla `Ctrl` y haz doble clic sobre la hoja de bloque correspondiente (*Sheet Symbol*).
3. Para validar la integridad del diseño, haz clic derecho sobre `Lab4_Altium_Files.PrjPcb` en el panel de proyectos y selecciona **Validate PCB Project Lab4_Altium_Files.PrjPcb** para ejecutar la comprobación de reglas eléctricas (ERC).