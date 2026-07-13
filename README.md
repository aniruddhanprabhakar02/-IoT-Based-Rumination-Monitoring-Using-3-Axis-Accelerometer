# IoT-Based Cattle Rumination Monitoring and Health Analysis System

<p align="center">
  <img src="images/field_testing/cow_deployment_1.jpg" alt="Cattle Monitoring System" width="750">
</p>

## Project Overview

This project presents an IoT-based cattle monitoring system designed to monitor rumination behavior, body temperature, and location of cattle in real time.

The system uses an ESP32 microcontroller integrated with an MPU6050 accelerometer, DS18B20 temperature sensor, and NEO-6M GPS module. Accelerometer signals are processed using digital signal processing techniques to estimate chewing activity and classify rumination behavior. Data is visualized through a Blynk IoT dashboard and logged to Google Sheets for long-term analysis.

### Applications

- Livestock Health Monitoring
- Early Disease Detection
- Heat Stress Monitoring
- Precision Livestock Farming
- Behavioral Analytics

---

## Key Features

- Real-time rumination monitoring
- Jaw movement sensing using MPU6050
- Signal filtering and peak detection
- Chews Per Minute (CPM) estimation
- Coefficient of Variation (CV) analysis
- Rule-based rumination classification
- Temperature monitoring using DS18B20
- GPS-based cattle tracking
- Blynk IoT dashboard integration
- Google Sheets cloud logging
- Custom PCB design using KiCad
- Field-tested on live cattle

---

## System Architecture

<p align="center">
  <img src="images/workflow/system_architecture.png" width="800">
</p>

### Data Flow

```text
MPU6050
   │
   ▼
Acceleration Magnitude
   │
   ▼
Signal Filtering
   │
   ▼
Peak Detection
   │
   ▼
CPM + CV Analysis
   │
   ▼
Rumination Classification
   │
   ▼
ESP32
   │
   ├── Blynk Dashboard
   ├── Google Sheets Logging
   ├── Temperature Monitoring
   └── GPS Tracking
```

---

## Hardware Components

| Component | Purpose |
|------------|----------|
| ESP32-WROOM-32 | Main Controller |
| MPU6050 | Jaw Motion Detection |
| DS18B20 | Temperature Monitoring |
| NEO-6M GPS | Location Tracking |
| 18650 Battery | Portable Power Supply |
| Perfboard Prototype | Hardware Integration |

---

## Field Deployment

The developed system was deployed and tested on live cattle under farm conditions.

<p align="center">
  <img src="images/field_testing/cow_deployment_1.jpg" width="700">
</p>

### Validation Performed

- Real-time chewing detection
- Rumination classification
- Cloud logging
- Dashboard visualization
- End-to-end system testing

---

## Hardware Prototype

<p align="center">
  <img src="images/hardware/prototype_board.jpg" width="700">
</p>

The prototype integrates:

- ESP32
- MPU6050
- DS18B20
- NEO-6M GPS
- Battery Power Supply

---

## Dashboard Screenshots

### Blynk IoT Dashboard

<p align="center">
  <img src="images/dashboard/blynk_dashboard_1.jpg" width="750">
</p>

The dashboard displays:

- Chews Per Minute (CPM)
- Coefficient of Variation (CV)
- Rumination Status
- Temperature
- Total Chew Count
- GPS Data

---

## Results Summary

The developed system successfully:

- Detected chewing events
- Estimated chewing frequency
- Computed chewing regularity
- Classified rumination behavior
- Logged sensor data to cloud platforms
- Visualized real-time animal activity
- Demonstrated successful field deployment

---

## Repository Structure

```text
ESP32-Cattle-Rumination-Monitoring
│
├── README.md
│
├── docs
│   ├── Methodology.md
│   ├── PCB_Design.md
│   ├── Results.md
│   └── References.md
|   └── papers/
|      ├── paper_1.pdf
|      ├── paper_2.pdf
|      └── paper_3.pdf
|
│
├── firmware
│   └── rumination_monitoring.ino
│
├── hardware
│   ├── schematic
│   ├── pcb_layout
│   ├── custom_symbols
│   ├── custom_footprints
│   └── gerber_files
│
├── images
│
├── videos
│
├── data
│
└── LICENSE
```

---

## Documentation

Detailed project documentation is available below:

### Technical Documentation

- 📖 [Methodology](Docs/Methodology.md)
- 🔧 [PCB Design Report](Docs/PCB_Design.md)
- 📊 [Experimental Results](Docs/Results.md)
- 📚 [Research References](Docs/References.md)

---

## Technologies Used

### Hardware

- ESP32-WROOM-32
- MPU6050
- DS18B20
- NEO-6M GPS

### Software

- Arduino IDE
- KiCad
- Blynk IoT
- Google Sheets API

### Concepts

- Embedded Systems
- Internet of Things (IoT)
- Digital Signal Processing
- Peak Detection
- Statistical Feature Extraction
- Cloud Telemetry
- PCB Design

---

## Future Enhancements

- Machine Learning Based Rumination Detection
- Health Anomaly Detection
- Heat Stress Monitoring
- LoRa-Based Communication
- Solar-Powered Sensor Node
- PCB Fabrication and Miniaturization

---

## Author

**Aniruddhan P**

M.E. Embedded Systems and Technologies

Embedded Systems | Embedded Linux | IoT | Edge AI