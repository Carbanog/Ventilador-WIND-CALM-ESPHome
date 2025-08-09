[🇪🇸 Read this in Spanish](README.es.md)

# 🌀 WIND CALM Ceiling Fan – ESPHome Integration

This project contains the complete ESPHome configuration to control the **WIND CALM** ceiling fan from the brand **CREATE**, which uses UART communication with a Tuya chip. It is fully compatible with Home Assistant.

---

## ✅ Features

- Turn the fan on and off  
- Control 6 speed levels (values from 1 to 6 → 1 % to 100 %)  
- Change the fan rotation direction  
- Turn the integrated light on and off  
- Select light color temperature (3 levels: 0, 500, 1000)  
- Mute the fan beeps  
- Monitor Wi-Fi signal strength and ESP uptime  
- Remotely restart the ESP32 from Home Assistant  

---

## 🧰 Requirements

- An **ESP32 C3 SuperMini** with an external antenna (recommended for better Wi-Fi range in installations with a metal housing or interference).  
- WIND CALM ceiling fan with Tuya-based UART control  

<img src="https://github.com/user-attachments/assets/c6f3eaaa-74be-4a08-b94f-f7bb6d09eda1" alt="WIND CALM Ceiling Fan" width="400">  
<img src="https://github.com/user-attachments/assets/b01adcb4-3eca-4b46-a009-985697ffa359" alt="ESP32 C3 SuperMini" width="400">

---

## 📡 Known Datapoints for WIND CALM Fan

| DP  | Function                             | Type        | Known values                     | Notes                                                                       |
|-----|--------------------------------------|-------------|-----------------------------------|------------------------------------------------------------------------------|
| 20  | Light ON/OFF                         | Boolean     | `true` / `false`                  | Turns the light on or off                                                   |
| 23  | Light color temperature              | Number      | `0`, `500`, `1000`                | 3 shades of white available (not RGB)                                       |
| 60  | Fan ON/OFF                           | Boolean     | `true` / `false`                  | Turns the fan motor on or off                                               |
| 62  | Fan speed                            | Number      | `1` to `6`                        | 6 speeds (1 % to 100 %)                                                      |
| 63  | Rotation direction                   | Enum        | `0`, `1`                          | 0: normal direction, 1: reverse direction                                   |
| 64  | Shutdown timer                       | Number      | `1` to `N` (minutes)              | ⚠️ Not recommended: may block UART until manual restart                     |
| 66  | Sound / Beep                         | Boolean     | `true` / `false`                  | Enables or disables the beeps when using the remote or UART                 |

---

## ⚠️ Notes & Recommendations

- This project was tested with an **ESP32 C3 SuperMini** with an external antenna due to Wi-Fi signal issues caused by the fan's metal housing and the motor's electromagnetic noise. Models without an external antenna showed unstable connections, especially when the fan was running.  
- The fan's light is **white only**, not RGB. Color temperature selection works correctly via datapoint `23` (levels: 0, 500, 1000).  
- **Speeds** range from 1 to 6 (1 % → 100 %), and must be integer values.  
- To use UART, you must **remove the original Tuya module (CB3S)**.  
- Some ESP32 models require **crossing TX and RX pins**.  
- Make sure you have **good Wi-Fi coverage**. The fan's metal housing reduces signal strength, and when the motor is running, the signal may drop even further.  
- The **beep** is automatically disabled on startup.  

---

## 🔧 Additional Tips

- If the fan does not respond when changing speed, check the UART connections and Wi-Fi signal.  
- **Avoid using the timer (datapoint 64)**: once it expires, the fan turns off and stops responding to UART commands until turned on manually with the RF remote.  
- If you have coverage issues, consider using an **ESP32 with an external antenna** or moving your router closer to the fan.  
