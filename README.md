# PRACTICA1-DHT22

**Objetivo de la práctica**
El propósito de esta actividad es aprender a trabajar con la placa ESP32 junto al sensor de temperatura y humedad DHT22, para leer y mostrar valores ambientales en el monitor serie. Este ejercicio facilita la comprensión de la interacción entre ambos componentes y la adquisición de datos ambientales mediante programación en Arduino.

______________________________________
**Material y equipo necesario**
•	Plataforma Wokwi: Simulador en línea que permite probar circuitos electrónicos y código sin hardware físico.
•	Placa ESP32: Microcontrolador económico con conectividad Wi-Fi y Bluetooth.
•	Sensor DHT22: Dispositivo digital para medir temperatura y humedad con alta precisión, cubriendo rangos de 0-100% de humedad y -40°C a 80°C de temperatura.

_______________________________________
**Modo de conexion**
El pin de señal del sensor DHT22 (DHT_PIN) está conectado al GPIO 15 de la ESP32. Además, se utiliza una resistencia de 10k ohmios entre el pin de señal del sensor y el GPIO de la ESP32.
![](https://github.com/marcorea97/PRACTICA1-DHT22/blob/main/Captura%20de%20pantalla%202024-12-17%20221000.png)
________________________________________
**Descripción del código**


El código está diseñado utilizando la librería DHTesp, que facilita la comunicación con el sensor DHT22. Su funcionamiento es el siguiente:
#include "DHTesp.h"

const int DHT_PIN = 15; // Pin conectado al sensor
DHTesp dhtSensor; // Instancia del sensor

void setup() {
  Serial.begin(115200); // Inicializar el puerto serie
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22); // Configurar el sensor DHT22
}

void loop() {
  TempAndHumidity data = dhtSensor.getTempAndHumidity(); // Leer datos del sensor
  Serial.println("Temp: " + String(data.temperature, 1) + "°C"); // Mostrar temperatura
  Serial.println("Humidity: " + String(data.humidity, 1) + "%"); // Mostrar humedad
  Serial.println("---"); // Separador
  delay(1000); // Pausa de 1 segundo entre lecturas
}


______________________________________________
**Explicación del código**


•	Librería DHTesp: Se utiliza para gestionar la comunicación con el DHT22.
•	Configuración inicial: En setup(), se define el pin del sensor y se inicializa.
•	Lectura de datos: En el ciclo loop(), se obtienen los valores de temperatura y humedad con getTempAndHumidity(), mostrándolos en el monitor serie mediante Serial.println().
•	Intervalo entre lecturas: Un retardo de 1 segundo (delay(1000)) garantiza que las lecturas no sean continuas.
________________________________________
Resultados esperados


Al ejecutar este código, ya sea en la plataforma Wokwi o con hardware físico, el monitor serie mostrará valores de temperatura y humedad actualizados cada segundo.
Ejemplo de salida en el monitor serie:
Temp: 25.6°C  
Humidity: 60%  
---  
Nota: Los valores variarán dependiendo de las condiciones ambientales reales o simuladas.
________________________________________
**Conclusión**

Esta práctica demuestra cómo integrar el sensor DHT22 con la ESP32 para monitorear temperatura y humedad. Además, la simulación en Wokwi permite verificar el código sin necesidad de hardware físico. Estas habilidades son esenciales en proyectos de monitoreo ambiental y en el desarrollo de aplicaciones del Internet de las Cosas (IoT).
