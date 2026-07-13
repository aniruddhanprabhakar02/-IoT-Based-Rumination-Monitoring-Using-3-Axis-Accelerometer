# References

The design of the rumination monitoring algorithm, sensor placement strategy, and behavioral analysis methodology was inspired by prior research on accelerometer-based livestock monitoring systems.

---

## Research Papers

### [1] Iqbal et al., 2021

**Validation of an Accelerometer Sensor-Based Collar for Monitoring Grazing and Rumination Behaviours in Dairy Cows**

Key Contributions:

- Accelerometer-based rumination monitoring
- Chewing activity analysis
- Behavioral classification using motion data
- Validation of wearable sensing approaches

Influenced:

- CPM (Chews Per Minute) analysis
- Rumination detection methodology
- Wearable sensor deployment strategy

---

### [2] Riaboff et al., 2020

**Monitoring Pasture-Based Dairy Cow Behaviour Using Accelerometer-Based Sensors**

Key Contributions:

- Activity recognition using inertial sensors
- Grazing and rumination behavior analysis
- Sensor placement considerations

Influenced:

- Accelerometer placement methodology
- Motion signal interpretation
- Livestock behavior monitoring concepts

---

### [3] Mauny et al., 2019

**Automatic Classification of Rumination and Ingestive Behaviors in Cattle Using Machine Learning Techniques**

## Supporting Literature

The research papers referenced during development are available in:

docs/papers/

Key Contributions:

- Rumination classification approaches
- Behavioral feature extraction
- Automated livestock monitoring

Influenced:

- Feature engineering concepts
- Rumination classification framework
- Future machine learning enhancements

---

## Technical References

### ESP32 Documentation

- ESP32-WROOM-32 Technical Reference Manual
- ESP32 Datasheet
- Espressif Systems Documentation

Used For:

- GPIO configuration
- Wi-Fi communication
- Peripheral interfacing

---

### MPU6050 Documentation

- MPU6050 Product Specification
- MPU6050 Register Map Documentation

Used For:

- Accelerometer configuration
- Motion sensing implementation
- Sampling rate configuration

---

### DS18B20 Documentation

- DS18B20 Digital Temperature Sensor Datasheet

Used For:

- One-Wire communication
- Temperature acquisition

---

### NEO-6M Documentation

- u-blox NEO-6M GPS Module Documentation

Used For:

- GPS interfacing
- Location acquisition

---

### KiCad Documentation

- KiCad Official Documentation

Used For:

- Schematic capture
- PCB layout design
- Custom symbol creation
- Custom footprint development

---

## Software Libraries

### Arduino Framework

Used for:

- ESP32 firmware development
- Peripheral integration
- Real-time data acquisition

### Blynk IoT Platform

Used for:

- Cloud connectivity
- Dashboard visualization
- Remote monitoring

### Google Sheets Web App

Used for:

- Cloud-based data logging
- Long-term data storage

---

## Disclaimer

This project implements a lightweight rule-based rumination detection approach optimized for real-time execution on ESP32 hardware. The methodology was inspired by published research on livestock behavior monitoring but was independently implemented, tuned, and experimentally validated as part of this project.