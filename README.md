# 🔥 Smart Heating IoT System
IoT-based smart heating control system designed to automate room temperature regulation using a mini ESP32C3 microcontroller, MQTT communication, FastAPI backend and Grafana visualization.

## 📌 Overview

This project was developed to automate room heating based on real-time temperature measurements while providing remote monitoring and control capabilities.

The system measures ambient temperature using a DS18B20 sensor and controls a 220V electric heater through a relay module. Current consumption is monitored using an ACS712 current sensor for monitoring and validation purposes.

Sensor data is transmitted securely through MQTT to a FastAPI backend, stored in PostgreSQL and visualized in Grafana dashboards.

## ✨ Features

- Real-time temperature monitoring
- Automatic heater control
- Manual ON/OFF remote control
- MQTT secure communication (TLS)
- Current sensing and monitoring
- FastAPI backend
- PostgreSQL database integration
- Grafana dashboard visualization
- Configurable temperature thresholds
- Configurable automatic schedules
- Remote configuration through Grafana
- Automatic timeout protection

## 🏗️ System Architecture

The system architecture is composed of four main layers:

1. ESP32 firmware layer
2. MQTT communication layer
3. Backend and database layer
4. Visualization and control layer

### Architecture Diagram

<p align="center"><img width="500" height="400" alt="Diagrama Calefacc" src="https://github.com/user-attachments/assets/024316c2-2868-40de-b776-dacc2467da92" /></p>

## 🔌 Hardware

### Main Components
| Component | Purpose |
|---|---|
| mini ESP32C3 | Main controller |
| DS18B20 | Temperature sensing |
| ACS712 | Current measurement |
| SLA-05VDC-SL-A Relay | Heater switching |
| 220V Heater | Room heating |
| Mosquitto Broker | MQTT communication |

### Hardware Setup


<p align="center"><img width="300" height="400" alt="Setup 3" src="https://github.com/user-attachments/assets/3e310902-496f-4c3c-89c8-5c5c44788561"/>
<img width="300" height="400" alt="Setup1" src="https://github.com/user-attachments/assets/18263e1b-dfcc-4700-9d33-25e469fbe300"/>
<img width="250" height="400" alt="Setup2" src="https://github.com/user-attachments/assets/b03f21b6-e094-4570-a598-f221195922e0" /></p>


## ⚡ Electrical Diagram

The system uses an isolated relay module to safely switch a 220V heater while keeping the mini ESP32C3 low-voltage circuitry separated from the AC power stage.

<p align="center"><img width="865" height="600" alt="Diagrama_conexion" src="https://github.com/user-attachments/assets/60a04189-7dd6-4e6d-a338-3ea8e00cc8ab" /></p>


## 🖥️ Software Stack

### Backend
- Python
- FastAPI
- PostgreSQL

### Embedded
- mini ESP32C3
- ESP-IDF
- MQTT Client

### Monitoring
- Grafana
- Mosquitto MQTT Broker

### Infrastructure
- Ubuntu Server
- systemd services

## 📡 MQTT Communication

The system uses MQTT over TLS for secure bidirectional communication between the ESP32 and the backend.

### MQTT Topics

| Topic | Purpose |
|---|---|
| `calefactor/sensores` | Sensor telemetry |
| `calefactor/heater/cmd` | Heater control commands |

### Telemetry Data

The ESP32 periodically publishes:

- Temperature
- Current consumption
- Heater state
- WiFi RSSI
- Device IP
- Event type

## 📊 Grafana Dashboard

The Grafana dashboard provides:

- Real-time temperature monitoring
- Heater state visualization
- Current consumption monitoring
- Automatic mode configuration
- Remote heater control
- Historical data analysis

### Dashboard Examples


<img width="2186" height="865" alt="Grafana1" src="https://github.com/user-attachments/assets/85928950-a82c-41a0-8f97-8716d82643a5" />
<img width="2163" height="759" alt="Grafana2" src="https://github.com/user-attachments/assets/05e53e98-b488-4db1-b898-ed19ba7692a0" />
<img width="2164" height="375" alt="Grafana3" src="https://github.com/user-attachments/assets/5209a84b-18cd-4bbd-8303-740ec9e2055a" />

## 🧠 Intelligent Control Logic

The heating system implements multiple protection and automation layers to improve safety, stability and operational reliability.

### Automatic Control Features

- Temperature threshold control
- Configurable operating schedules
- Heater timeout protection
- Cooldown protection between cycles
- Manual override mode
- Forced automatic activation
- Automatic recovery after backend restart

## 🛡️ Reliability & Safety Features

Several protection mechanisms were implemented to improve operational safety and fault tolerance:

- Automatic heater timeout shutdown
- Cooldown delay between automatic cycles
- Relay/current cross-validation
- Backend recovery after restart
- ESP32 offline monitoring
- Event and alarm historical logging
- Safe heater shutdown during backend restart

### Fault Detection

The backend continuously validates heater behavior using current sensing and MQTT telemetry.

Implemented alarms include:

- Heater ON with no current detected
- Current detected while relay is OFF
- ESP32 offline detection
- ESP32 unexpected reboot detection
- Backend restart detection
- ESP32 timeout protection events
