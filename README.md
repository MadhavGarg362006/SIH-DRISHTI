# DRISHTI

Drone-based Risk Intelligence & Surveillance Technology Initiative

> A modular Edge-AI environmental intelligence payload that retrofits
> compatible survey UAVs into automated disaster verification units.
> DRISHTI combines RGB, thermal, environmental, GPS/IMU sensing, onboard
> edge processing, local storage, and a live dashboard to detect,
> verify, localize, assess risk, and support faster response.

[![License:
MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP32--S3-blue.svg)](https://www.espressif.com/en/products/socs/esp32-s3)
[![AI](https://img.shields.io/badge/AI-Edge%20AI-green.svg)](#9-edge-ai--dashboard)
[![Dashboard](https://img.shields.io/badge/Dashboard-Live%20Telemetry-brightgreen.svg)](#9-edge-ai--dashboard)

------------------------------------------------------------------------

## 📑 1. Table of Contents

-   [2. Executive Summary](#2-executive-summary)
-   [3. Problem Statement](#3-problem-statement)
-   [4. System Architecture](#4-system-architecture)
-   [5. Hardware Specifications](#5-hardware-specifications)
-   [6. Circuit & Prototype
    Explanation](#6-circuit--prototype-explanation)
-   [7. Hardware Integration & Pin
    Connections](#7-hardware-integration--pin-connections)
-   [8. Main System Modules](#8-main-system-modules)
-   [9. Edge-AI & Dashboard](#9-edge-ai--dashboard)
-   [10. Real-Life Applications](#10-real-life-applications)
-   [11. Future Upgrades](#11-future-upgrades)
-   [12. Project Status](#12-project-status)
-   [13. Conclusion](#13-conclusion)
-   [14. References](#14-references)

------------------------------------------------------------------------

## 2. Executive Summary

DRISHTI is a modular environmental intelligence payload designed to
mount on compatible existing survey UAVs.

The system is intended to close the gap between a broad environmental
alert and on-ground confirmation. Instead of requiring a new dedicated
disaster-monitoring UAV, DRISHTI uses a **retrofit-first architecture**
that adds sensing and intelligence capabilities to compatible
agency-owned drones.

The platform combines RGB imaging, thermal sensing, environmental
sensors, GPS/GNSS and IMU data with edge processing. Critical
information can be processed locally and stored during connectivity
loss, while available telemetry is transmitted to a centralized web
dashboard.

The complete operational pipeline is:

**Detect → Verify → Localize → Assess Risk → Act**

For the SIH 2026 project:

-   **Problem Statement ID:** 26178
-   **Problem Statement:** A Resilient AI-Powered Environmental
    monitoring network for early detection of environmental hazards.
-   **Theme:** Disaster Management
-   **Category:** Hardware
-   **Team ID:** 320
-   **Team Name:** Team Hexagon

------------------------------------------------------------------------

## 3. Problem Statement

### ⚠️ The Challenge

Large forest and remote environmental regions are difficult to
continuously monitor using ground teams alone.

Satellite systems provide wide-area environmental monitoring, but the
resulting alert does not itself provide detailed, immediate, on-site
confirmation.

The project identifies three major gaps:

-   **Coarse aerial visibility:** FSI MODIS/VIIRS alerts provide broad
    coverage but have approximately 1 km resolution and limited revisit
    frequency for a specific location.
-   **Verification gap:** A detected hotspot still needs confirmation
    before resources can be appropriately directed.
-   **Remote terrain:** Physically reaching difficult forest terrain for
    every potential event can delay assessment and consume manpower.

### 💼 Operational Impact

Emergency and forest-management teams need information that is:

-   Rapid
-   Geo-tagged
-   Evidence-backed
-   Multisensor
-   Usable in difficult terrain
-   Available even when connectivity is unreliable

### 🎯 Project Objective

-   Retrofit compatible existing UAVs instead of requiring new UAV
    procurement.
-   Capture RGB, thermal and environmental information.
-   Process critical information near the source using edge computing.
-   Verify potential hazards using multiple sensing modalities.
-   Generate geo-tagged evidence, confidence and risk information.
-   Preserve critical event data during connectivity loss.
-   Provide live telemetry and visualization through a centralized
    dashboard.
-   Build an architecture that can scale from one UAV to fleets, regions
    and multiple hazard types.

------------------------------------------------------------------------

## 4. System Architecture




<p align="center">
  <img src="Images/DRISHTI_Architecture.png" alt="DRISHTI System Architecture" width="90%">
  <br>
  <em>Figure: DRISHTI end-to-end architecture</em>
</p>
The project follows a sequential sensing-to-intelligence pipeline:

-   **Step 1: Existing UAV / Retrofit Platform**\
    A compatible survey UAV acts as the aerial platform. DRISHTI is
    designed as a modular payload so the existing aircraft can be
    reused.

-   **Step 2: Multimodal Sensing**\
    The payload collects RGB imagery, thermal information,
    temperature/humidity, flame/environmental signals, GPS/GNSS and IMU
    data.

-   **Step 3: Edge Processing**\
    Sensor data and imagery are processed close to the source.
    Pre-processing includes image enhancement, sensor synchronization
    and event preparation.

-   **Step 4: AI/CV Verification**\
    The AI/CV layer identifies anomalies and combines information from
    multiple sensors to support event verification and confidence
    estimation.

-   **Step 5: Local Storage & Communication**\
    Critical data can be buffered locally. When connectivity is
    available, event telemetry can be transmitted through the
    communication layer.

-   **Step 6: Dashboard / GIS**\
    Geo-tagged events, telemetry, risk information and evidence are
    presented through the monitoring dashboard.

-   **Step 7: Actionable Intelligence**\
    The final output is intended to provide authorities with location,
    evidence, confidence and risk information for faster
    decision-making.

------------------------------------------------------------------------

## 5. Hardware Specifications

  -----------------------------------------------------------------------
  Component               Part / Technology       Role in the Project
  ----------------------- ----------------------- -----------------------
  Edge Controller         ESP32 / ESP32-S3        Sensor processing,
                                                  communication and
                                                  system control

  Camera                  ESP32-CAM + OV2640      RGB visual evidence and
                                                  image capture

  Thermal                 Thermal camera / future Heat-signature and
                          thermal module          thermal anomaly
                                                  detection

  Environmental Sensor    DHT11                   Temperature and
                                                  humidity

  Flame Sensor            Flame detection module  Local flame indication

  Gas Sensor              MQ-3                    Environmental / gas
                                                  sensing for prototype
                                                  verification

  IMU                     MPU6500                 Motion and orientation
                                                  data

  GPS                     NEO-6M GNSS             Geo-tagging and
                                                  localization

  Display                 OLED                    Local system / risk
                                                  status

  Storage                 Local storage /         Event retention during
                          buffering               connectivity loss

  UAV Platform            Compatible survey UAV   Aerial sensing platform
  -----------------------------------------------------------------------

### 🧰 Current Prototype Sensors

The present prototype focuses on the embedded sensing and telemetry
foundation:

-   DHT11 for temperature and humidity
-   Flame sensor for flame indication
-   MQ-3 for gas/environmental sensing
-   MPU6500 for IMU data
-   NEO-6M for GPS
-   ESP32-CAM / OV2640 for RGB imagery
-   OLED for local status display

Thermal sensing and dedicated onboard AI hardware are part of the
planned system expansion.

------------------------------------------------------------------------

## 6. Circuit & Prototype Explanation

The prototype is divided into sensing, processing, communication and
display modules.

``` text
Environmental Sensors
       │
       ├── DHT11
       ├── Flame Sensor
       └── MQ-3
       │
       ▼
     ESP32
       │
       ├── MPU6500
       ├── GPS
       ├── OLED
       └── Wi-Fi
       │
       ▼
   Telemetry Server
       │
       ▼
 DRISHTI Dashboard
```

The camera subsystem operates as a complementary visual sensing unit:

``` text
OV2640
   ↓
ESP32-CAM
   ↓
Image Capture
   ↓
Camera Communication
   ↓
Dashboard / Evidence Layer
```

### Current Prototype Flow

1.  Sensors collect environmental and motion information.
2.  ESP32 reads and formats the sensor values.
3.  GPS provides geographic information.
4.  Camera captures RGB evidence.
5.  Telemetry is transmitted to the server when connectivity is
    available.
6.  The dashboard presents the incoming information in real time.
7.  Local displays provide immediate system status.

------------------------------------------------------------------------

## 7. Hardware Integration & Pin Connections

### 🔌 Sensor Hub Pin Configuration

  Device           ESP32 GPIO Function
  -------------- ------------ ----------------------------------
  OLED SDA            GPIO 18 I²C data
  OLED SCL             GPIO 4 I²C clock
  MPU6500 SDA         GPIO 14 I²C data
  MPU6500 SCL         GPIO 13 I²C clock
  DHT11               GPIO 19 Temperature / humidity
  MQ-3                GPIO 35 Analog gas/environmental sensing
  Flame Sensor        GPIO 34 Flame input
  GPS RX              GPIO 16 GPS serial receive
  GPS TX              GPIO 17 GPS serial transmit

### 📷 ESP32-CAM Communication

The prototype camera subsystem uses an AI-Thinker / compatible ESP32-CAM
with OV2640.

The camera can provide RGB frames that complement environmental and
sensor telemetry.

------------------------------------------------------------------------

## 8. Main System Modules

### 🚁 1. Retrofit UAV Platform

The UAV is the carrier rather than the main intelligence layer.

The core design principle is:

**Existing compatible UAV + DRISHTI payload → Intelligent environmental
sensing node**

This allows the sensing system to be added to compatible existing UAV
infrastructure.

### 📷 2. RGB Imaging

The RGB camera provides visual context for an event.

It can help identify:

-   Smoke
-   Visible fire
-   Scene conditions
-   Vegetation
-   Infrastructure
-   Surrounding terrain

### 🌡️ 3. Thermal Sensing

Thermal sensing is intended to detect heat signatures that may not be
obvious from visible imagery.

This becomes particularly useful for:

-   Hotspots
-   Smouldering regions
-   Night-time monitoring
-   Areas partially obscured by smoke

### 🌦️ 4. Environmental Sensing

Environmental measurements provide additional context around a suspected
event.

Current prototype sensing includes:

-   Temperature
-   Humidity
-   Flame indication
-   Gas/environmental readings

### 📍 5. GPS / GNSS + IMU

GPS provides event coordinates while the IMU provides motion/orientation
information.

Together they support:

-   Geo-tagging
-   Location tracking
-   UAV state information
-   Event localization

### 🧠 6. Edge Intelligence

The edge layer is intended to perform processing close to the UAV rather
than sending every raw data stream to the cloud.

This reduces dependency on continuous connectivity and enables local
event processing.

### 💾 7. Local Storage & Communication

Critical information can be retained locally when communication is
unavailable.

The intended strategy is:

``` text
Sensor / Camera Data
        ↓
Local Processing
        ↓
Critical Event?
   ┌────┴────┐
  YES       NO
   ↓         ↓
Store      Process
   ↓
Connection Available?
   ├── YES → Transmit
   └── NO  → Retain
```

### 🖥️ 8. Dashboard / GIS

The dashboard provides a centralized interface for viewing:

-   Live telemetry
-   Sensor readings
-   Camera information
-   GPS location
-   Risk information
-   Event status
-   Alerts

------------------------------------------------------------------------

## 9. Edge-AI & Dashboard

### 🤖 Edge-AI Approach

The intended AI/CV pipeline is:

``` text
RGB + Thermal + Sensor Data
            ↓
       Pre-processing
            ↓
       Sensor Sync
            ↓
    Feature Extraction
            ↓
     Anomaly Detection
            ↓
      Sensor Fusion
            ↓
 Confidence / Risk Score
            ↓
   Geo-tagged Event
```

The key idea is not to depend on a single sensor.

For example:

``` text
Visual Anomaly
      +
Thermal Signature
      +
Temperature / Humidity
      +
Flame / Environmental Signal
      ↓
Event Verification
      ↓
Confidence + Risk
```

### 🌐 Live Dashboard

The software stack is designed around:

-   Node.js
-   Express.js
-   Socket.IO
-   HTML
-   CSS
-   JavaScript
-   REST-style telemetry endpoints
-   Real-time dashboard updates

### Typical Data Flow

``` text
ESP32 Sensor Hub
       ↓
HTTP Telemetry
       ↓
Node.js Server
       ↓
Socket.IO
       ↓
Live Web Dashboard
```

### Deployment

The dashboard can be deployed as a Node.js web service on Render.

Typical commands:

``` bash
npm install
npm start
```

After deployment:

``` text
ESP32
  ↓
Internet
  ↓
Render Server
  ↓
Socket.IO
  ↓
DRISHTI Dashboard
```

------------------------------------------------------------------------

## 10. Real-Life Applications

### 🔥 Forest & Wildlife Monitoring

-   Early verification of potential forest-fire events
-   Monitoring of difficult-to-access forest regions
-   Geo-tagged evidence for response teams
-   Repeated aerial surveys

### 🚑 Emergency Response

-   Rapid aerial assessment
-   Event verification before physical deployment
-   Risk-based prioritization
-   Situational awareness during response operations

### 🌊 Flood Monitoring

The same modular architecture can be adapted for:

-   Flooded regions
-   Water-level monitoring
-   Dam / embankment inspection
-   Post-flood assessment

### 🌱 Vegetation Monitoring

The payload can support:

-   Vegetation health monitoring
-   Environmental changes
-   Remote-area surveys
-   Agricultural/environmental inspection

### 🏭 Pollution & Infrastructure

Future sensing modules can support:

-   Air-quality monitoring
-   Industrial inspection
-   Infrastructure assessment
-   Environmental compliance monitoring

------------------------------------------------------------------------

## 11. Future Upgrades

-   **Thermal Camera Integration:** Add dedicated thermal imaging for
    heat-signature verification.
-   **Dedicated Edge-AI Computer:** Move heavier computer-vision
    inference to a more capable onboard compute platform.
-   **Multimodal Sensor Fusion:** Combine RGB, thermal and environmental
    features into a unified event-confidence model.
-   **Automated Risk Classification:** Generate structured risk levels
    from detected evidence.
-   **Offline-First Storage:** Expand event buffering and
    store-and-forward communication.
-   **GIS Integration:** Display geo-referenced incidents on a map-based
    command interface.
-   **Multi-UAV Coordination:** Support multiple DRISHTI-equipped UAVs
    from a centralized dashboard.
-   **LoRa / Long-Range Communication:** Add long-range telemetry for
    areas with limited cellular connectivity.
-   **Multi-Hazard Models:** Extend the same payload/software
    architecture to fire, flood, vegetation, pollution and
    infrastructure monitoring.
-   **Fleet Management:** Manage multiple payload-equipped agency UAVs
    from one operational interface.

### Scalability Roadmap

``` text
RETROFIT
   ↓
FLEET
   ↓
REGION
   ↓
MULTI-HAZARD
```

**RETROFIT:** Plug-and-deploy payload for compatible existing UAVs.

**FLEET:** Equip multiple agency-owned UAVs with the same modular
payload.

**REGION:** Scale across multiple sites with centralized aerial and
ground sensing.

**MULTI-HAZARD:** Reconfigure sensing and software for fire, flood,
vegetation, pollution and infrastructure monitoring.

------------------------------------------------------------------------

## 12. Project Status

  ----------------------------------------------------------------------------------
  Category           Task / Milestone          Status           Details
  ------------------ ---------------- ------------------------- --------------------
  **System**         DRISHTI                ✅ Completed        Modular
                     Architecture                               retrofit-based
                                                                environmental
                                                                intelligence
                                                                architecture defined

  **Embedded**       Sensor Hub             ✅ Completed        ESP32-based
                                                                environmental and
                                                                motion sensing
                                                                prototype

  **Embedded**       GPS Integration        ✅ Completed        NEO-6M used for
                                                                geo-tagging

  **Embedded**       IMU Integration        ✅ Completed        MPU6500 used for
                                                                motion/orientation
                                                                data

  **Embedded**       OLED Interface         ✅ Completed        Local status and
                                                                telemetry display

  **Camera**         ESP32-CAM +            ✅ Completed        RGB image capture
                     OV2640                                     prototype

  **Telemetry**      Sensor Data            ✅ Completed        Prototype telemetry
                     Transmission                               sent to server

  **Frontend**       Live Dashboard         ✅ Completed        Real-time telemetry
                                                                visualization

  **Deployment**     Cloud Dashboard        🔵 Deployment       Node.js dashboard
                                                                prepared for Render
                                                                deployment

  **AI/CV**          Anomaly               🟡 In Progress       AI/CV pipeline under
                     Detection                                  development

  **AI/CV**          Multimodal              🔵 Planned         Combine visual,
                     Sensor Fusion                              thermal and
                                                                environmental
                                                                evidence

  **Hardware**       Thermal                 🔵 Planned         Dedicated thermal
                     Integration                                sensing

  **Edge AI**        Dedicated Edge          🔵 Planned         Onboard inference
                     Compute                                    for heavier AI
                                                                workloads

  **GIS**            Geo-referenced          🔵 Planned         Map-based incident
                     Risk Map                                   visualization

  **Scalability**    Multi-UAV Fleet         🔵 Planned         Centralized fleet
                                                                monitoring

  **Multi-Hazard**   Fire / Flood /          🔵 Planned         Expandable
                     Pollution /                                hazard-specific
                     Infrastructure                             modules
  ----------------------------------------------------------------------------------

> **Legend:**\
> ✅ **Completed** --- Implemented and tested in the current prototype\
> 🟡 **In Progress** --- Active development\
> 🔵 **Planned** --- Staged for a future iteration

------------------------------------------------------------------------

## 13. Conclusion

DRISHTI establishes an end-to-end foundation for converting compatible
existing survey UAVs into intelligent environmental sensing platforms.

The central design principle is **RETROFIT, NOT REPLACE**.

The current prototype establishes the sensing, embedded processing,
GPS/IMU integration, camera subsystem and live telemetry/dashboard
foundation.

The planned Edge-AI layer extends this foundation by combining
multimodal observations to detect and verify environmental anomalies,
generate confidence and risk information, and provide geo-tagged
evidence.

The overall system is designed to progress from:

**Retrofit → Fleet → Region → Multi-Hazard**

The long-term objective is to provide authorities with a reusable aerial
intelligence layer that complements broad-area detection systems with
localized, evidence-backed verification.

------------------------------------------------------------------------

## 14. References

### 📄 Project / SIH Information

-   **Smart India Hackathon 2026:** Problem Statement ID 26178
-   **Problem Statement:** A Resilient AI-Powered Environmental
    monitoring network for early detection of environmental hazards.
-   **Theme:** Disaster Management
-   **Category:** Hardware
-   **Team:** Team Hexagon
-   **Team ID:** 320

### 💻 Embedded & Hardware

-   **ESP32-S3:** [Espressif Systems
    ESP32-S3](https://www.espressif.com/en/products/socs/esp32-s3)
-   **ESP32 Arduino Core:** [Espressif
    Arduino-ESP32](https://github.com/espressif/arduino-esp32)
-   **ESP32-CAM:** AI-Thinker / compatible ESP32-CAM platform
-   **OV2640:** Camera sensor used with the ESP32-CAM
-   **MPU6500:** 6-axis motion sensor
-   **NEO-6M:** GNSS receiver
-   **DHT11:** Temperature and humidity sensor

### 🌐 Software

-   **Node.js:** [Node.js](https://nodejs.org/)
-   **Express.js:** [Express](https://expressjs.com/)
-   **Socket.IO:** [Socket.IO](https://socket.io/)
-   **Render:** [Render](https://render.com/)

### 🛰️ Environmental Monitoring

-   **Forest Survey of India:** [Forest Survey of
    India](https://fsi.nic.in/)
-   **FSI Forest Fire Monitoring:** Near-real-time forest fire
    monitoring resources

------------------------------------------------------------------------

```{=html}
<p align="center">
```
`<strong>`{=html}DRISHTI`</strong>`{=html}`<br>`{=html} Detect • Verify
• Localize • Assess Risk • Act
```{=html}
</p>
```
```{=html}
<p align="center">
```
`<strong>`{=html}Team Hexagon • SIH 2026 • Team ID 320 • PS
26178`</strong>`{=html}
```{=html}
</p>
```
