<img width="2160" height="3840" alt="Setup2" src="https://github.com/user-attachments/assets/47201bd7-e1eb-4b12-9aaa-be7a0d976279" /># 🔥 Smart Heating IoT System

IoT-based smart heating control system designed to automate room temperature regulation using an ESP32 microcontroller, MQTT communication, FastAPI backend and Grafana visualization.

---

## 📌 Overview

This project was developed to automate room heating based on real-time temperature measurements while providing remote monitoring and control capabilities.

The system measures ambient temperature using a DS18B20 sensor and controls a 220V electric heater through a relay module. Current consumption is monitored using an ACS712 current sensor for monitoring and validation purposes.

Sensor data is transmitted securely through MQTT to a FastAPI backend, stored in PostgreSQL and visualized in Grafana dashboards.

---

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

---

## 🏗️ System Architecture

The system architecture is composed of four main layers:

1. ESP32 firmware layer
2. MQTT communication layer
3. Backend and database layer
4. Visualization and control layer

### Architecture Diagram

<img width="697" height="537" alt="Diagrama Calefacc" src="https://github.com/user-attachments/assets/2a930e48-c2ea-4901-ad4a-49725eef913d" />

---

## 🔌 Hardware

### Main Components

| Component | Purpose |
|---|---|
| ESP32 | Main controller |
| DS18B20 | Temperature sensing |
| ACS712 | Current measurement |
| SLA-05VDC-SL-A Relay | Heater switching |
| 220V Heater | Room heating |
| Mosquitto Broker | MQTT communication |

### Hardware Setup

<img width="3024" height="4032" alt="Setup1" src="https://github.com/user-attachments/assets/18263e1b-dfcc-4700-9d33-25e469fbe300" />
<img width="2160" height="3840" alt="Setup2" src="https://github.com/user-attachments/assets/b03f21b6-e094-4570-a598-f221195922e0" />

---

## ⚡ Electrical Diagram

The system uses an isolated relay module to safely switch a 220V heater while keeping the ESP32 low-voltage circuitry separated from the AC power stage.

<img width="1465" height="961" alt="Diagrama_conexion" src="https://github.com/user-attachments/assets/60a04189-7dd6-4e6d-a338-3ea8e00cc8ab" />

---

## 🖥️ Software Stack

### Backend
- Python
- FastAPI
- PostgreSQL

### Embedded
- ESP32
- ESP-IDF
- MQTT Client

### Monitoring
- Grafana
- Mosquitto MQTT Broker

### Infrastructure
- Ubuntu Server
- systemd services

---

## 📊 Grafana Dashboard

The Grafana dashboard provides:

- Real-time temperature monitoring
- Heater state visualization
- Current consumption monitoring
- Automatic mode configuration
- Remote heater control
- Historical data analysis

### Dashboard Examples

<img width="1752" height="928" alt="Grafana" src="https://github.com/user-attachments/assets/3ee50c90-0b2b-49ab-b914-817314147798" />

---

## 🤖 Automatic Control Logic

The automatic control system evaluates:

- Current room temperature
- Configured operating schedule
- Temperature thresholds
- Heater timeout limits

### Control Logic

```text
IF:
    Current time is inside allowed schedule
    AND
    Temperature < Minimum threshold

THEN:
    Heater ON

IF:
    Temperature > Maximum threshold
    OR
    Timeout exceeded

THEN:
    Heater OFF
