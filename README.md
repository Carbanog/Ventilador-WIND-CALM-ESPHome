# 🌀 Ventilador WIND CALM – Integración con ESPHome

Este proyecto contiene la configuración completa de ESPHome para controlar el ventilador de techo WIND CALM de la marca CREATE, el cual utiliza comunicación UART con un chip Tuya. Es totalmente compatible con Home Assistant.

---

## ✅ Funcionalidades

- Encendido y apagado del ventilador  
- Control de 6 velocidades (valores del 1 al 6 → 1 % a 100 %)  
- Cambio de sentido de giro del ventilador  
- Encendido y apagado de la luz integrada  
- Selección de temperatura de color de la luz (3 niveles: 0, 500, 1000)  
- Silenciar los pitidos del ventilador (beep)  
- Monitoreo de la señal Wi-Fi y del tiempo de actividad del ESP  
- Reinicio remoto del ESP32 desde Home Assistant  

---

## 🧰 Requisitos

- Un ESP32 (por ejemplo, placa `esp32dev`)  
- Ventilador WIND CALM con control UART basado en Tuya  

---

## 📡 Datapoints conocidos del ventilador WIND CALM

| DP  | Función                              | Tipo        | Valores conocidos               | Comentarios                                                                 |
|-----|--------------------------------------|-------------|----------------------------------|------------------------------------------------------------------------------|
| 20  | Luz ON/OFF                           | Boolean     | `true` / `false`                | Enciende o apaga la luz                                                     |
| 23  | Temperatura de color de la luz       | Número      | `0`, `500`, `1000`              | 3 tonos de blanco disponibles (no es RGB)                                   |
| 60  | Ventilador ON/OFF                    | Boolean     | `true` / `false`                | Enciende o apaga el motor del ventilador                                   |
| 62  | Velocidad del ventilador             | Número      | `1` a `6`                       | 6 velocidades (1 % a 100 %)                                                 |
| 63  | Dirección de giro                    | Enum        | `0`, `1`                        | 0: sentido normal, 1: sentido inverso                                       |
| 64  | Temporizador de apagado              | Número      | `1` a `N` (minutos)             | ⚠️ No recomendable: puede bloquear UART hasta reinicio manual               |
| 66  | Sonido / Beep                        | Boolean     | `true` / `false`                | Activa o silencia los pitidos al usar el mando o UART                      |

---

## ⚠️ Notas y recomendaciones

- La luz del ventilador es solo **blanca**, no RGB. La selección de temperatura de color funciona correctamente mediante el datapoint `23` (niveles: 0, 500, 1000).
- Las **velocidades** van del 1 al 6 (1 % → 100 %), y deben ser valores enteros.
- Para usar UART, es necesario **retirar el módulo Tuya original (CB3S)**.
- Algunos modelos de ESP32 requieren **cruzar los pines TX y RX**.
- Asegúrate de tener **buena cobertura Wi-Fi**. La carcasa metálica del ventilador reduce la señal y, además, cuando el motor se activa, la señal puede debilitarse aún más.
- El **beep** se activa automáticamente al encender. Puedes desactivarlo desde Home Assistant.

---

## 🔧 Consejos adicionales

- Si el ventilador no responde al cambiar la velocidad, revisa las conexiones UART y la señal Wi-Fi.
- **Evita usar el temporizador (datapoint 64)**: al agotarse, el ventilador se apaga y deja de responder a comandos UART hasta encenderlo manualmente con el mando RF.
- Si tienes problemas de cobertura, considera usar un **ESP32 con antena externa** o colocar el router más cerca del ventilador.
