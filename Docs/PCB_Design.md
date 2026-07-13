# PCB Design Using KiCad

## Overview

To improve hardware integration and gain practical PCB design experience, a custom PCB was designed for the ESP32-based cattle rumination monitoring system using KiCad.

The design integrates:

- ESP32-WROOM-32
- MPU6050 Accelerometer
- DS18B20 Temperature Sensor
- NEO-6M GPS Module

> Note: The deployed cattle monitoring system was implemented using a perfboard prototype. The PCB presented here was developed as a fabrication-ready prototype design and was not manufactured.

---

## Schematic Design

The schematic was developed based on the firmware architecture and peripheral interface requirements.

### Interfaces

| Module | Interface | ESP32 Pins |
|----------|----------|----------|
| MPU6050 | I²C | GPIO21 (SDA), GPIO22 (SCL) |
| DS18B20 | One-Wire | GPIO2 |
| NEO-6M GPS | UART | GPIO16 (RX), GPIO17 (TX) |

<p align="center">
  <img src="../hardware/schematic/schematic.png" width="850">
</p>

---

## PCB Layout

### PCB Specifications

| Parameter | Value |
|------------|------------|
| Length | 55 mm |
| Width | 85 mm |
| Design Tool | KiCad |

### Design Considerations

- Central placement of ESP32 for simplified routing
- Short I²C traces between ESP32 and MPU6050
- Ground plane for noise reduction
- GPS antenna clearance
- ESP32 antenna keep-out region

<p align="center">
  <img src="../hardware/pcb_layout/pcb_layout.png" width="850">
</p>

---

## Custom Library Development

Custom KiCad libraries were created for:

### Custom Symbols

- MPU6050
- NEO-6M GPS

### Custom Footprints

- MPU6050
- NEO-6M GPS

These libraries were developed using datasheet dimensions and pin mappings to ensure correct schematic representation and PCB placement.

<p align="center">
  <img src="../hardware/custom_symbols/neo6m_symbol.png" width="650">
</p>

<p align="center">
  <img src="../hardware/custom_footprints/neo6m_footprint.png" width="650">
</p>

---

## Design Outcomes

### PCB Design Activities Performed

- Schematic Capture
- PCB Layout Design
- Component Placement
- Trace Routing
- Ground Plane Implementation
- ESP32 Antenna Keep-Out Planning
- Custom Symbol Creation
- Custom Footprint Development
- Gerber File Generation

### Tools Used

- KiCad
- ESP32-WROOM-32
- MPU6050
- DS18B20
- NEO-6M GPS

---

## Future Work

- PCB Fabrication
- Hardware Assembly
- Prototype Validation
- Compact Wearable Enclosure Design