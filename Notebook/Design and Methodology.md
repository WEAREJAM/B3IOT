## System Design and Methodology

### A. System Architecture
The system is divided into three layers:

1. **Sensing Layer:** The DHT11 sensor measures temperature and humidity from the environment.  
2. **Processing Layer:** The ESP32 microcontroller collects the sensor data, formats it in JSON, and publishes it to the MQTT broker.  
3. **Visualization Layer:** Node-RED subscribes to the MQTT topic and visualizes the data using interactive charts and gauges.[3]  

**MQTT Topics:**  
- Publish Topic: `H00508398/evt/status/fmt/json`  
- Subscribe Topic: `H00508398/cmd/display/fmt/json`  

**LED Color Thresholds:**  
- Below 10°C – Blue (Cold)  
- 10–25°C – Green (Comfortable)  
- 25–30°C – Yellow (Warm)  
- Above 30°C – Red (Hot)  

---

### B. Hardware Components
| Component | Description |
|-----------|-------------|
| ESP32 | Main controller with built-in Wi-Fi and processing capability |
| DHT11 Sensor | Measures temperature and humidity |
| NeoPixel RGB LED | Displays color-based environmental feedback |
| Breadboard and Wires | Used for secure connections among components |

---

### C. Software and Tools
1. **Arduino IDE** – For programming and uploading code to ESP32  
2. **HiveMQ Public Broker** – Facilitates MQTT communication  
3. **Node-RED** – For data visualization through dashboard nodes  
4. **Personal Hotspot** – Used to establish the Wi-Fi connection for ESP32  

---

### D. Implementation Overview
The ESP32 connects to the personal hotspot and establishes an MQTT connection with the HiveMQ broker. It reads data from the DHT11 sensor at regular intervals, converts the data into JSON format, and publishes it to the MQTT topic. The NeoPixel LED changes its color according to the temperature range to provide immediate environmental feedback. Node-RED subscribes to the topic, visualizes data in gauges and charts, and maintains live updates.[4]  

---

### E. Flow of Operation

![DHT11 Sensor Data](https://github.com/WEAREJAM/B3IOT/blob/main/Images/Picture1.png?raw=true)

Immediately after the ESP32 is powered on, it starts executing the program:  

1. Initializes a **serial monitor** for real-time testing and monitoring.  
2. Connects to a **Wi-Fi network** using a personal hotspot to communicate with the MQTT broker.  
3. Initializes the **DHT sensor** to measure temperature and humidity.  
4. Sets up the **NeoPixel RGB LED** for visual temperature feedback.  
5. Attempts to **connect to the MQTT broker**. If unsuccessful, it restarts and tries again.  
6. Enters the **main loop** indefinitely:
   - Reads current temperature and humidity from the DHT sensor. If a read fails, it skips the cycle.  
   - Changes the NeoPixel LED color based on temperature:
     - Blue for cold (<10°C)  
     - Green for normal (10–25°C)  
     - Yellow for warm (25–30°C)  
     - Red for hot (>30°C)  
   - Formats temperature and humidity values into a **JSON message** and transmits it to the MQTT broker.  
   - Delays briefly to listen for MQTT messages before repeating the loop.[5]  
