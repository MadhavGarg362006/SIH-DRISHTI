# DRISHTI

## Drone-based Risk Intelligence & Surveillance Technology Initiative

> **A modular Edge-AI retrofit payload that transforms compatible
> agency-owned UAVs into automated environmental hazard verification
> units.**

[![Platform](https://img.shields.io/badge/Platform-ESP32--S3-blue)](#technology-stack)
[![Edge
AI](https://img.shields.io/badge/AI-Edge%20Inference-green)](#edge-intelligence)
[![Dashboard](https://img.shields.io/badge/Dashboard-Live%20Telemetry-orange)](#real-time-dashboard)
[![Deployment](https://img.shields.io/badge/Deployment-Render-purple)](#deployment-on-render)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

------------------------------------------------------------------------

## 🚨 The Problem

Large-scale environmental hazards such as forest fires require rapid
**verification after an initial alert**.

Satellite-based systems provide wide-area detection, but an alert alone
cannot provide:

-   Immediate local verification
-   High-resolution aerial evidence
-   Continuous event monitoring
-   Multi-sensor confirmation
-   Real-time risk assessment
-   Direct geo-tagged field intelligence

This creates a critical gap:

**Detection → Verification → Decision → Action**

DRISHTI is designed to close that gap.

------------------------------------------------------------------------

# 🎯 Our Solution

**DRISHTI** is a modular drone-mounted sensing and Edge-AI platform
designed to retrofit **compatible existing UAVs**.

Instead of requiring agencies to procure dedicated disaster-monitoring
drones, DRISHTI aims to convert compatible survey UAVs into intelligent
environmental sensing nodes.

### Core Pipeline

``` text
Satellite / Ground Alert
          ↓
   UAV Deployment
          ↓
 Multimodal Sensing
          ↓
 Edge Pre-processing
          ↓
 Edge-AI Verification
          ↓
 Risk & Location Assessment
          ↓
 Geo-tagged Evidence
          ↓
 Dashboard / GIS / Alerts
```

------------------------------------------------------------------------

# 🛰️ DRISHTI Architecture

``` text
                  ┌─────────────────────────┐
                  │ Satellite / Ground Alert │
                  └────────────┬────────────┘
                               │
                               ▼
                    ┌────────────────────┐
                    │ Compatible UAV     │
                    │ Existing Fleet     │
                    └─────────┬──────────┘
                              │
                              ▼
              ┌─────────────────────────────┐
              │       DRISHTI PAYLOAD       │
              │                             │
              │ RGB Camera                  │
              │ Thermal Sensing             │
              │ Temperature / Humidity      │
              │ Flame / Gas Sensing         │
              │ GPS + IMU                   │
              │ Edge Processing              │
              └──────────────┬──────────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Edge Intelligence   │
                  │                     │
                  │ Detection           │
                  │ Sensor Fusion       │
                  │ Classification      │
                  │ Confidence           │
                  │ Risk Assessment      │
                  └──────────┬──────────┘
                             │
                  ┌──────────┴──────────┐
                  │                     │
                  ▼                     ▼
        ┌─────────────────┐   ┌─────────────────┐
        │ Local Storage   │   │ Connectivity    │
        │ Event Evidence  │   │ Wi-Fi / 4G      │
        └────────┬────────┘   └────────┬────────┘
                 │                     │
                 └──────────┬──────────┘
                            ▼
                 ┌──────────────────────┐
                 │ DRISHTI Dashboard    │
                 │                      │
                 │ Live Telemetry       │
                 │ Camera Feed          │
                 │ GPS / Location       │
                 │ Risk Status          │
                 │ Alerts               │
                 └──────────────────────┘
```

------------------------------------------------------------------------

# 🔍 Key Capabilities

### 1. Multimodal Sensing

DRISHTI combines multiple data sources rather than relying on a single
sensor.

-   RGB visual imaging
-   Thermal anomaly detection
-   Temperature
-   Humidity
-   Flame detection
-   Gas / environmental sensing
-   GPS
-   IMU / motion data

### 2. Edge Intelligence

Critical processing is intended to occur close to the source rather than
continuously depending on cloud connectivity.

This enables:

-   Local event processing
-   Faster anomaly detection
-   Reduced communication dependency
-   Sensor verification
-   Confidence-based event assessment

### 3. Geo-tagged Intelligence

Detected events can be associated with:

-   GPS coordinates
-   Timestamp
-   Sensor measurements
-   Visual evidence
-   Risk level
-   Detection confidence

### 4. Connectivity-Resilient Operation

DRISHTI is designed to handle intermittent connectivity.

``` text
Sensor Data
    ↓
Local Processing
    ↓
Local Buffer / Storage
    ↓
Connection Available?
    ├── YES → Transmit
    └── NO  → Retain Critical Evidence
```

------------------------------------------------------------------------

# 🧠 Edge Intelligence

The intended AI/CV pipeline is:

``` text
RGB / Thermal / Sensor Inputs
            ↓
      Pre-processing
            ↓
      Feature Extraction
            ↓
      Anomaly Detection
            ↓
      Sensor Verification
            ↓
    Confidence Estimation
            ↓
       Risk Assessment
```

Visual and environmental observations can complement each other:

``` text
Visual Anomaly
      +
Thermal Signature
      +
Temperature / Humidity
      +
Flame / Gas Signal
      ↓
Event Verification
      ↓
Confidence + Risk
```

------------------------------------------------------------------------

# 📡 Current Hardware Prototype

The current prototype uses an ESP32-based sensor hub and ESP32-CAM
subsystem.

### Sensor Hub

  Component      Function
  -------------- -----------------------------------
  ESP32          Sensor processing & communication
  DHT11          Temperature & humidity
  MQ-3           Gas / environmental sensing
  Flame Sensor   Flame detection
  MPU6500        Motion / IMU data
  NEO-6M GPS     Geo-tagging
  OLED           Local status / risk display

### Camera Subsystem

  Component   Function
  ----------- ---------------------------------
  ESP32-CAM   RGB image capture
  OV2640      Visual imaging
  OLED        Local risk/status display
  Wi-Fi       Image / telemetry communication

------------------------------------------------------------------------

# 🔌 Sensor Hub Pin Configuration

Current prototype configuration:

  Device           ESP32 GPIO
  -------------- ------------
  OLED SDA            GPIO 18
  OLED SCL             GPIO 4
  MPU6500 SDA         GPIO 14
  MPU6500 SCL         GPIO 13
  DHT11               GPIO 19
  MQ-3                GPIO 35
  Flame Sensor        GPIO 34
  GPS RX              GPIO 16
  GPS TX              GPIO 17

See the hardware documentation in `esp32/` for detailed wiring
information.

------------------------------------------------------------------------

# 💻 Technology Stack

## Hardware

-   ESP32 / ESP32-S3
-   ESP32-CAM
-   OV2640 camera
-   DHT11
-   MPU6500
-   MQ-3
-   Flame sensor
-   NEO-6M GPS
-   OLED display

## Embedded

-   Arduino IDE
-   C/C++
-   ESP32 Arduino Core
-   Wi-Fi
-   HTTP
-   JSON telemetry

## Backend

-   Node.js
-   Express.js
-   Socket.IO
-   CORS

## Frontend

-   HTML
-   CSS
-   JavaScript
-   Real-time Socket.IO communication
-   Live telemetry visualization

## Deployment

-   GitHub
-   Render
-   Node.js Web Service

------------------------------------------------------------------------

# 📊 Real-Time Dashboard

DRISHTI includes a web-based monitoring dashboard for centralized
visualization of incoming telemetry and camera information.

### Dashboard capabilities

-   Live sensor telemetry
-   Temperature
-   Humidity
-   Gas readings
-   Flame status
-   GPS information
-   IMU information
-   Camera status
-   Camera frames
-   Historical telemetry
-   System status
-   Reset controls
-   Real-time Socket.IO updates

------------------------------------------------------------------------

# 🔗 Backend API

  Endpoint               Method   Purpose
  ---------------------- -------- ------------------------------
  `/health`              GET      Server health check
  `/api/sensor-data`     POST     Receive ESP32 telemetry
  `/api/camera-frame`    POST     Receive camera frame
  `/api/camera-frame`    GET      Retrieve latest camera frame
  `/api/camera-status`   GET      Camera status
  `/api/history`         GET      Retrieve telemetry history
  `/api/status`          GET      Current system status
  `/api/reset-history`   POST     Reset stored telemetry

### Real-time communication

Socket.IO pushes incoming telemetry to connected dashboard clients.

``` text
ESP32
  ↓
HTTP POST
  ↓
Node.js / Express
  ↓
Socket.IO
  ↓
Live Dashboard
```

------------------------------------------------------------------------

# 🧪 Run Locally

## Requirements

-   Node.js 18+
-   npm
-   Arduino IDE for hardware deployment

Check your installation:

``` bash
node --version
npm --version
```

## Install Dependencies

``` bash
npm install
```

## Start the Dashboard

``` bash
npm start
```

Then open:

``` text
http://localhost:3000
```

------------------------------------------------------------------------

# 🧪 Test Without Hardware

The project includes mock telemetry tools for dashboard/backend testing.

Use the available mock tool in `tools/` to generate simulated ESP32
readings.

This is useful for:

-   Development
-   Dashboard testing
-   Demonstrations
-   Backend validation
-   SIH judging

------------------------------------------------------------------------

# 🚁 ESP32 Deployment

Open the relevant Arduino sketch from `esp32/`.

Configure the required network and server parameters:

``` cpp
WIFI_SSID
WIFI_PASSWORD
SERVER_URL
```

The sensor hub sends telemetry to:

``` text
/api/sensor-data
```

For a local server:

``` text
http://<PC-IP>:3000/api/sensor-data
```

For a deployed server:

``` text
https://<YOUR-RENDER-DOMAIN>/api/sensor-data
```

------------------------------------------------------------------------

# 📷 ESP32-CAM

The ESP32-CAM subsystem provides visual evidence from the UAV.

``` text
OV2640
   ↓
ESP32-CAM
   ↓
JPEG Frame
   ↓
HTTP Upload
   ↓
DRISHTI Server
   ↓
Dashboard
```

Camera data is handled through:

``` text
/api/camera-frame
```

------------------------------------------------------------------------

# ☁️ Deployment on Render

The repository includes:

``` text
render.yaml
```

The expected Node.js deployment configuration is:

``` yaml
services:
  - type: web
    name: drishti-dashboard
    runtime: node
    plan: free
    buildCommand: npm install
    startCommand: npm start
    healthCheckPath: /health
```

### Manual deployment

1.  Connect the GitHub repository to Render.
2.  Create a new **Web Service**.
3.  Select the DRISHTI repository.
4.  Set:

``` text
Build Command:
npm install
```

``` text
Start Command:
npm start
```

5.  Deploy.
6.  Verify:

``` text
https://<YOUR-RENDER-DOMAIN>/health
```

Expected response:

``` json
{
  "status": "ok"
}
```

The dashboard is then available at:

``` text
https://<YOUR-RENDER-DOMAIN>/
```

------------------------------------------------------------------------

# 🌐 End-to-End Data Flow

``` text
              ┌──────────────┐
              │    UAV       │
              └──────┬───────┘
                     │
                     ▼
          ┌─────────────────────┐
          │ DRISHTI Payload     │
          │                     │
          │ RGB / Thermal       │
          │ Sensors             │
          │ GPS / IMU           │
          │ Edge Processing     │
          └──────────┬──────────┘
                     │
                     ▼
              Local Processing
                     │
              ┌──────┴──────┐
              │             │
        Connectivity    No Network
              │             │
              ▼             ▼
         Cloud Server    Local Storage
              │
              ▼
        Socket.IO Stream
              │
              ▼
        Web Dashboard
```

------------------------------------------------------------------------

# ♻️ Retrofit & Scalability

DRISHTI is built around a **modular retrofit architecture**.

Instead of replacing existing UAV fleets:

``` text
Existing Compatible UAV
          +
    DRISHTI Payload
          ↓
Intelligent Environmental
     Sensing Node
```

## Scalability Roadmap

``` text
RETROFIT
   ↓
FLEET
   ↓
REGION
   ↓
MULTI-HAZARD
```

### Retrofit

Deploy the payload on compatible existing agency-owned UAVs.

### Fleet

Equip multiple compatible UAVs with the same sensing architecture.

### Region

Expand across multiple locations with centralized monitoring.

### Multi-Hazard

Adapt the platform for:

-   Forest fires
-   Floods
-   Vegetation monitoring
-   Pollution
-   Infrastructure inspection
-   Other environmental hazards

------------------------------------------------------------------------

# 💰 Retrofit-First Deployment Model

DRISHTI is designed to reuse compatible UAV infrastructure rather than
requiring a dedicated UAV for every application.

``` text
Existing UAV
     ↓
DRISHTI Retrofit Payload
     ↓
Multimodal Sensing
     ↓
Edge Intelligence
     ↓
Actionable Intelligence
```

> **Upgrade the sensing capability --- not the entire UAV fleet.**

------------------------------------------------------------------------

# 📈 Validation Metrics

The prototype can be evaluated using measurable system-level metrics.

### Detection

-   Detection accuracy
-   Precision
-   Recall
-   False-positive rate

### System

-   End-to-end latency
-   Sensor update rate
-   Camera frame latency
-   Processing time

### Localization

-   GPS localization error
-   Event coordinate accuracy

### Coverage

-   Area monitored per flight
-   Flight duration
-   Sensor coverage

### Reliability

-   Connectivity-loss handling
-   Data retention
-   Recovery after reconnection

------------------------------------------------------------------------

# 🧪 Current Prototype vs Future Development

## Current Prototype

-   Multisensor ESP32 telemetry
-   GPS geo-tagging
-   IMU monitoring
-   Flame sensing
-   Environmental sensing
-   ESP32-CAM visual capture
-   Real-time dashboard
-   Local OLED status display
-   HTTP telemetry
-   Socket.IO visualization
-   Render deployment support
-   Mock telemetry for demonstrations

## Planned Extensions

-   Thermal camera integration
-   Dedicated Edge-AI inference hardware
-   Computer-vision anomaly detection
-   Multimodal sensor fusion
-   Confidence scoring
-   Automated risk classification
-   GIS integration
-   Offline-first evidence storage
-   Multi-UAV fleet coordination
-   Multi-hazard models

------------------------------------------------------------------------

# 📁 Repository Structure

``` text
DRISHTI/
│
├── README.md
├── package.json
├── render.yaml
├── .gitignore
│
├── public/
│   ├── index.html
│   ├── DRISHTI_6_Dashboard.js
│   └── DRISHTI_7_Dashboard_Styles.css
│
├── server/
│   └── server.js
│
├── esp32/
│   ├── sensor-hub/
│   ├── esp32-cam/
│   └── WIRING_GUIDE.md
│
├── ai/
├── tools/
├── docs/
└── assets/
```

------------------------------------------------------------------------

# 🔐 Security & Prototype Notes

This repository is intended for a **prototype / hackathon
demonstration**.

Before production deployment:

-   Move Wi-Fi credentials to secure configuration.
-   Never commit API keys or passwords.
-   Use authenticated API endpoints.
-   Use HTTPS communication.
-   Validate incoming sensor data.
-   Add persistent database storage.
-   Implement device authentication.
-   Encrypt sensitive stored evidence.
-   Add role-based dashboard access.

------------------------------------------------------------------------

# ⚠️ Current Limitations

The current prototype has several intentional limitations:

1.  AI inference is under active development.
2.  Thermal sensing requires dedicated thermal hardware.
3.  The current backend primarily uses in-memory state.
4.  Connectivity resilience requires further field validation.
5.  Production UAV integration requires platform-specific mechanical and
    electrical validation.
6.  Detection performance requires validation using representative field
    datasets.

These limitations are part of the development roadmap and are not
presented as completed capabilities.

------------------------------------------------------------------------

# 🛣️ Development Roadmap

``` text
PHASE 1
Multisensor Prototype
        ↓
PHASE 2
Live UAV Telemetry + Camera
        ↓
PHASE 3
Edge-AI Detection
        ↓
PHASE 4
Multimodal Sensor Fusion
        ↓
PHASE 5
Risk & Confidence Engine
        ↓
PHASE 6
GIS + Multi-UAV Deployment
        ↓
PHASE 7
Multi-Hazard Platform
```

------------------------------------------------------------------------

# 👥 Team

## Team Hexagon

### Project

**DRISHTI --- Drone-based Risk Intelligence & Surveillance Technology
Initiative**

### Smart India Hackathon 2026

-   **Problem Statement ID:** 26178
-   **Theme:** Disaster Management
-   **Category:** Hardware
-   **Team ID:** 320

------------------------------------------------------------------------

# 📜 License

This project is released under the MIT License.

See [`LICENSE`](LICENSE) for details.

------------------------------------------------------------------------

# ⭐ DRISHTI in One Line

> **DRISHTI retrofits compatible UAVs with multimodal sensing and
> Edge-AI to bridge the gap between environmental alerts and real-time
> aerial verification.**
