# 📝 Taller 1 - Comunicaciones Industriales

**Universidad Santo Tomás**  
**Autores:** David Esteban Díaz Castro, Ferney Arturo Amaya Gómez, Jhonny Alejandro Mejía  
**Fecha:** Septiembre 1, 2025  

---

## 📑 Contenido
1. [Diferentes tipos de detectores de errores](#-1-diferentes-tipos-de-detectores-de-errores)  
2. [Tecnologías actuales con RS232](#-2-tecnologías-actuales-con-rs232)  
3. [Exploración de la Raspberry Pi 3 Modelo B](#-3-exploración-de-la-raspberry-pi-3-modelo-b)  
   - Instalación de Raspbian  
   - Instalación de Grafana  
   - Instalación de Streamlit  
4. [Referencias](#-referencias)  

---

## 🔍 1. Diferentes tipos de detectores de errores
En transmisión de datos es fundamental garantizar la integridad. Se estudiaron los siguientes métodos:  

- **Bit de Paridad:** añade un bit extra para detectar errores simples de 1 bit.  
- **VRC (Vertical Redundancy Check):** genera un byte de control por carácter, más eficiente que la paridad simple.  
- **LRC (Longitudinal Redundancy Check):** analiza bits a lo largo de bloques de datos, más robusto en grandes volúmenes.  
- **CRC (Cyclic Redundancy Check):** usa polinomios para detectar errores de ráfaga, ampliamente usado en **Ethernet, USB, CAN**.  

📌 **Conclusión:** la **paridad** es el método más simple, mientras que el **CRC** es el más completo y confiable.  

---

## 🔌 2. Tecnologías actuales con RS232
Aunque RS232 es un estándar antiguo, sigue siendo útil en aplicaciones modernas:  

- **Conversión RS232 ↔ USB:** con chips como **FTDI FT232** o **Prolific PL2303**.  
- **Aislamiento galvánico:** uso de **optoacopladores** para proteger equipos sensibles.  
- **Integración con IoT:** gateways convierten **RS232 ↔ TCP/IP**, habilitando control remoto y supervisión industrial.  

---

## 🍓 3. Exploración de la Raspberry Pi 3 Modelo B
Se exploraron los pines de la **Raspberry Pi 3B** (alimentación, TX, RX, GPIO) y se realizaron pruebas prácticas.  

### 🖥️ Instalación de Raspbian
1. Descargar imagen oficial de **Raspberry Pi OS (32 bits)**.  
2. Instalar en tarjeta microSD (32 GB).  
3. Configuración inicial: idioma, contraseña, red.  
4. Debido a limitaciones de WiFi (solo 2.4 GHz), se optó por **Ethernet** para mayor estabilidad.  
5. Ajustes finales: instalación de paquetes, configuración de usuario y resolución de problemas de energía con un cargador adecuado.  

### 📊 Instalación de Grafana
Comandos utilizados:  

```bash
sudo apt-get install -y apt-transport-https software-properties-common wget gnupg
wget -q -O - https://packages.grafana.com/gpg.key | sudo gpg --dearmor -o /usr/share/keyrings/grafana.gpg
echo "deb [signed-by=/usr/share/keyrings/grafana.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt-get update
sudo apt-get install grafana -y
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
