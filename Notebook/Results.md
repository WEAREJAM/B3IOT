## Step 1: Hardware Setup
Connecting DHT11 sensor to ESP32

## Step 2: Arduino Code Overview
1. Connects to the hotspot  
2. Reads temperature and humidity from DHT11 sensor  

### A. MQTT Communication
The ESP32 successfully connects to the MQTT broker and continuously publishes environmental data. Each message follows the JSON format:

```json
{"d":{"temp":24.6,"humidity":58.2}}
```
![DHT11 Sensor Data2](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture2.png?raw=true)
Fig 1: Data received from DHT11

The DHT11 sensor makes continuous measurements of the temperature and humidity of the ambient air in real time. Acquired data is read by the ESP32, formatted as JSON messages, and sent to the MQTT broker for further processing. These are the bases for the dashboard visualization in Node-RED and, correspondingly, for the indication of LED colors, allowing direct and clear comprehension of the environmental conditions.[5]

### B. Data Visualization
Node-RED accurately displays live temperature and humidity readings through gauges and charts. The chart reflects real-time variations, allowing users to observe environmental trends. The system showed negligible delay in data transmission and smooth updates across the MQTT channel.

![DHT11 Sensor Data3](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture3.png?raw=true)
Fig 2: MQTT Data Flow in Node-Red

![DHT11 Sensor Data4](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture4.png?raw=true)

![DHT11 Sensor Data5](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture5.png?raw=true)
Fig 3: Node-Red temperature chart

### C. LED Color Response

| Temperature Range | LED Color | Status Description |
|------------------|-----------|------------------|
| Below 10°C       | Blue      | Cold             |
| 10–25°C          | Green     | Normal           |
| 25–30°C          | Yellow    | Warm             |
| Above 30°C       | Red       | Hot Alert        |

![DHT11 Sensor Data6](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture6.png?raw=true)

**Fig 4:** NeoPixel LED Color Response

The NeoPixel LED accurately reflected environmental changes and provided instant visual feedback without the need to view the dashboard.

---

### D. Discussion

The implemented IoT-based temperature and humidity monitoring system is used to demonstrate **real-time environmental tracking** along with visual feedback. The ESP32 integrated with the DHT11 sensor measures the continuous value of temperature and humidity and sends it to the MQTT broker via a Wi-Fi connection. Node-RED subscribed to the data publishing and showed it on dynamic gauges and charts, confirming seamless MQTT communication with minimal latency.[7]

Temperature changes were properly reflected by the color of the LED, which gave an instant visual indication of the state of the environment. For example:  
- Below 10°C – Blue LED for cold  
- 10–25°C – Green LED for normal  
- 25–30°C – Yellow LED for warm  
- Above 30°C – Red LED for hot alert  

The system showed a green light at around 21°C and a yellow light at around 26°C during tests, confirming that the thresholds are set up correctly and it behaves accordingly.

In general, the system performed well in sensing, processing, and transmitting data.[7] Minor mismatches in colors at the beginning were corrected by adjusting the NeoPixel color order configuration. The MQTT flow remained stable throughout, showing that this setup can be used as a **low-cost, efficient prototype** for smart home or environmental monitoring applications.[6]
