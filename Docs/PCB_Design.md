# PCB Design Using KiCad

## Overview

To improve hardware integration and gain practical PCB design experience, a custom PCB was designed for the ESP32-based cattle rumination monitoring system using **KiCad**.

The design integrates:

- ESP32-WROOM-32
- MPU6050 Accelerometer
- DS18B20 Temperature Sensor
- NEO-6M GPS Module

> **Note:** The deployed cattle monitoring system was implemented using a perfboard prototype. The PCB presented here was developed as a fabrication-ready prototype design and was **not manufactured**.

---

# Schematic Design

The schematic was developed based on the firmware architecture and peripheral interface requirements.

## Hardware Interfaces

| Module | Interface | ESP32 Pins |
|----------|----------|----------|
| MPU6050 | I²C | GPIO21 (SDA), GPIO22 (SCL) |
| DS18B20 | One-Wire | GPIO2 |
| NEO-6M GPS | UART | GPIO16 (RX), GPIO17 (TX) |

<p align="center">
  <img src="Images/pcb/Schematics diagram.png" width="900">
</p>

The schematic defines the electrical connectivity between the ESP32 and peripheral modules while ensuring reliable communication through I²C, UART, and One-Wire interfaces.

---

# PCB Layout

The PCB layout was designed with emphasis on compact routing, signal integrity, and ease of hardware integration.

## PCB Specifications

| Parameter | Value |
|------------|------------|
| PCB Length | 55 mm |
| PCB Width | 85 mm |
| Design Software | KiCad |

## Design Considerations

- Central placement of the ESP32 for simplified routing
- Short I²C traces between ESP32 and MPU6050
- Dedicated ground plane for noise reduction
- GPS antenna clearance
- ESP32 antenna keep-out region

<p align="center">
  <img src="Images/pcb/PCB Design Layout.png" width="900">
</p>

### PCB Dimensions

<table align="center">
<tr>
<td align="center">

**Length (55 mm)**

<img src="Images/pcb/Designed PCB Dimensions , L=55mm.png" width="320">

</td>

<td align="center">

**Width (85 mm)**

<img src="Images/pcb/Designed PCB Dimenions , width = 85mm.png" width="320">

</td>
</tr>
</table>

---

# Custom Library Development

Since standard KiCad libraries did not include all required modules, custom symbols and footprints were created using component datasheets.

## Custom Symbols

### MPU6050 Symbol

<p align="center">
  <img src="Images/pcb/MPU6050 Custom Symbol Design.png" width="650">
</p>

### NEO-6M GPS Symbol

<p align="center">
  <img src="Images/pcb/NEO-6M Custom Symbol Design.png" width="650">
</p>

The custom symbols accurately define device pin assignments for schematic capture.

---

## Custom Footprints

### MPU6050 Footprint

<p align="center">
  <img src="Images/pcb/MPU6050 Custom Footprint .png" width="650">
</p>

### NEO-6M GPS Footprint

<p align="center">
  <img src="Images/pcb/NEO-6M Custom Footprint.png" width="650">
</p>

The footprints were created using the physical package dimensions provided in the respective component datasheets to ensure correct PCB placement.

---

# Design Outcomes

The following PCB design activities were successfully completed:

- Schematic Capture
- Custom Symbol Development
- Custom Footprint Development
- PCB Layout Design
- Component Placement
- Signal Trace Routing
- Ground Plane Implementation
- ESP32 Antenna Keep-Out Planning
- Design Rule Verification
- Gerber File Generation

---

# Tools and Components

## Software

- KiCad

## Hardware Components

- ESP32-WROOM-32
- MPU6050 Accelerometer
- DS18B20 Temperature Sensor
- NEO-6M GPS Module

---

# Future Work

- PCB Fabrication
- Component Assembly
- Hardware Validation
- Power Optimization
- Miniaturized Wearable Enclosure