# 🔐 Sistema de Detección de Intrusiones en Tiempo Real para Redes Linux

Este proyecto presenta un **sistema de detección de intrusiones (IDS)** desarrollado en **C++**, diseñado para monitorear y analizar el tráfico de red en sistemas basados en **Linux**. Utiliza la biblioteca **libpcap** para capturar y examinar paquetes de red en tiempo real, con el objetivo de identificar intentos de intrusión como **escaneos de puertos realizados con Nmap** y **ataques generados mediante hping3**.

## 🛠️ Características Principales

- 📡 **Captura de paquetes** utilizando `libpcap`
- 🔍 **Inspección profunda de paquetes** IP y TCP
- 🚨 **Detección de técnicas comunes de reconocimiento**:
  - Escaneos con Nmap (SYN, FIN, NULL, XMAS, etc.)
  - Patrones de tráfico anómalos generados con hping3
- 📈 **Alertas en tiempo real** mediante consola o archivo de logs
- 🐧 Compatible con sistemas operativos Linux (probado en Ubuntu)

## ⚙️ Tecnologías Utilizadas

- **C++**
- **libpcap** – para captura y filtrado de paquetes
- **Sockets POSIX** – para el manejo de red a bajo nivel
- **Makefile** – para automatizar la compilación

## 📂 Estructura del Proyecto

```
📁 intrusion-detection/
├── src/
│   ├── main.cpp             # Punto de entrada del sistema
│   ├── packet_analyzer.cpp  # Lógica de análisis de paquetes
│   └── utils.cpp            # Funciones auxiliares
├── include/
│   ├── packet_analyzer.h
│   └── utils.h
├── logs/
│   └── alerts.log           # (Opcional) Registro de intrusiones detectadas
├── Makefile                 # Configuración de compilación
└── README.md
```

## 🚀 Cómo Ejecutarlo

### Requisitos Previos

- Sistema operativo basado en Linux
- Compilador `g++`
- Biblioteca `libpcap-dev` instalada:
  ```bash
  sudo apt install libpcap-dev
  ```

### Compilación del Proyecto

```bash
make
```

### Ejecución del Sistema

```bash
sudo ./intrusion_detector eth0
```

Reemplaza `eth0` con el nombre de tu interfaz de red activa (por ejemplo: `wlan0`).

## 🧪 Lógica de Detección

El sistema inspecciona cada paquete capturado y aplica reglas basadas en firmas para identificar:

- **Escaneos de puertos con Nmap**: combinaciones inusuales de flags TCP.
- **Tráfico generado con hping3**: patrones de paquetes y frecuencias anómalas.

## 📌 Mejoras Futuras

- 📄 Soporte para archivos de configuración personalizables
- 🧠 Integración de técnicas de aprendizaje automático para detección de anomalías
- 🌐 Panel web para monitoreo en tiempo real
- 🗂 Exportación de logs para integración con herramientas SIEM

## 📄 Licencia

Este proyecto se distribuye bajo la licencia MIT.
