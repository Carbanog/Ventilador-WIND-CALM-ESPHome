# 🌀 Ventilador WIND CALM ESPHome

Este proyecto contiene la configuración completa de ESPHome para controlar el ventilador de techo **WIND CALM** de CREATE, que utiliza UART y el chip Tuya. Compatible con Home Assistant.

---

## ✅ Funcionalidades incluidas

- Encendido/apagado del ventilador
- Control de 6 velocidades (1% – 100%)
- Cambio de dirección del ventilador
- Encendido/apagado de luz integrada
- Selector de temperatura de luz (3 posiciones: 0, 500, 1000)
- Silenciar los pitidos del ventilador
- Medición de señal WiFi y uptime del ESP
- Reinicio remoto del ESP32

---

## 🧰 Requisitos

- Un ESP32 (modelo `esp32dev` u otro)
- Ventilador WIND CALM con control Tuya UART
- Cableado UART:
  - TX ESP32 → RX del ventilador
  - RX ESP32 → TX del ventilador

---

❗ Notas
El control de luz incluye selector de temperatura (no RGB).

El datapoint de velocidad va del 1 al 6, donde 1 representa el 1% y 6 el 100%.

Este dispositivo no necesita automatizaciones externas para funcionar completamente.

