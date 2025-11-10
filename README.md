# IoT-Based Environmental Monitoring Using ESP32, DHT11, MQTT Protocol

## Overview
This project monitors temperature and humidity using an **ESP32**, **DHT11 sensor**, and **NeoPixel LED**. The **MQTT** (`broker.hivemq.com`) protocol sends the data, which is displayed in charts and gauges created by **Node-RED**.

## Components
- **ESP32**: Wi-Fi-enabled microcontroller  
- **DHT11**: Temperature & humidity sensor  
- **NeoPixel LED**: Status indicator  
- **MQTT Protocol**: Lightweight IoT communication  
- **Node-RED**: Dashboard for real-time visualization  

## Architecture
1. **Sensing**: DHT11 reads temperature & humidity  
2. **Communication**: ESP32 publishes JSON data via MQTT  
3. **Visualization**: Node-RED updates charts and gauges in real-time  

## Features
- Real-time monitoring of temperature and humidity  
- Visual dashboards in Node-RED  
- NeoPixel LED for status/alerts  

## How It Works
1. ESP32 connects to Wi-Fi and the MQTT broker  
2. Sensor readings are obtained from DHT11  
3. Data is published as JSON:  
```json
{"d":{"temp":24.6,"humidity":58.2}}
```
4. Node-RED subscribes to the topic and displays the readings
5. NeoPixel LED can indicate thresholds or system status
