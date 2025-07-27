🌀 Ventilador WIND CALM – Integración con ESPHome
Este proyecto contiene la configuración completa de ESPHome para controlar el ventilador de techo WIND CALM de la marca CREATE, el cual utiliza comunicación UART con un chip Tuya. Es totalmente compatible con Home Assistant.

✅ Funcionalidades
Encendido y apagado del ventilador

Control de 6 velocidades (valores del 1 al 6 → 1% a 100%)

Cambio de sentido de giro del ventilador

Encendido y apagado de la luz integrada

Selección de temperatura de color de la luz (3 niveles: 0, 500, 1000)

Silenciar los pitidos del ventilador (beep)

Monitoreo de la señal Wi-Fi y del tiempo de actividad del ESP

Reinicio remoto del ESP32 desde Home Assistant

🧰 Requisitos
Un ESP32 (por ejemplo, placa esp32dev)

Ventilador WIND CALM con control UART basado en Tuya

⚠️ Notas y recomendaciones
La luz del ventilador es solo blanca, no RGB. La selección de temperatura de color funciona correctamente mediante el datapoint 23 (niveles: 0, 500, 1000).

Las velocidades del ventilador van del 1 al 6 (donde 1 es el 1 % y 6 el 100 %). Se deben usar valores enteros.

Para usar UART, es necesario retirar el módulo Tuya original (CB3S) del ventilador.

En algunos modelos de ESP32 es necesario cruzar los pines TX y RX.

Es muy importante una buena cobertura Wi-Fi, ya que el ventilador tiene una carcasa metálica que atenúa la señal. Además, cuando el ventilador comienza a girar, la señal puede debilitarse aún más.

El beep del ventilador se activa automáticamente al encender el dispositivo. Puede silenciarse desde Home Assistant usando el interruptor correspondiente.

🔧 Consejos adicionales
Si el ventilador no responde al cambiar la velocidad, verifica las conexiones UART y la calidad de la señal Wi-Fi.

Evita usar el temporizador (datapoint 64) del ventilador. Cuando se agota, el ventilador se apaga pero ya no responde a comandos UART hasta que se enciende manualmente con el mando RF. Es mejor controlar el apagado con automatizaciones desde Home Assistant.

Si tienes problemas de cobertura, considera usar un ESP32 con mejor antena externa o mover el router más cerca del ventilador.
