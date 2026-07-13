# Experimental Results

## Overview

The developed cattle monitoring system was experimentally evaluated under real-world farm conditions. The system was deployed on cattle and successfully monitored jaw movement, estimated chewing activity, classified rumination behavior, and transmitted data to cloud platforms for visualization and logging.

---

## Hardware Prototype

The complete system was assembled using a perfboard-based prototype integrating the ESP32, MPU6050 accelerometer, DS18B20 temperature sensor, and NEO-6M GPS module.

<p align="center">
  <img src="../images/hardware/prototype_board.jpg" width="700">
</p>

### Prototype Features

- ESP32-based data acquisition
- Wireless cloud connectivity
- Accelerometer-based jaw motion sensing
- Temperature monitoring
- GPS tracking capability
- Battery-powered operation

---

## Field Deployment

The system was deployed on live cattle to evaluate rumination monitoring performance under actual farm conditions.

<p align="center">
  <img src="../images/field_testing/cow_deployment_1.jpg" width="700">
</p>

### Deployment Objectives

- Validate jaw motion sensing
- Evaluate rumination detection
- Test wireless connectivity
- Verify cloud data logging
- Assess real-time dashboard visualization

---

## Blynk Dashboard Visualization

The processed sensor data was transmitted to the Blynk IoT platform for real-time monitoring.

<p align="center">
  <img src="../images/dashboard/blynk_dashboard_1.jpg" width="750">
</p>

### Dashboard Parameters

- Chews Per Minute (CPM)
- Coefficient of Variation (CV)
- Rumination Status
- Total Chew Count
- Temperature
- GPS Location

---

## Cloud Data Logging

Sensor data was uploaded to Google Sheets using HTTP POST requests.

### Logged Parameters

| Parameter | Description |
|------------|------------|
| CPM | Chews Per Minute |
| CV | Coefficient of Variation |
| Rumination Label | Activity Classification |
| Rumination Count | Detected Rumination Events |
| Total Chews | Cumulative Chew Count |
| Peak Amplitude | Peak Signal Magnitude |
| Temperature | Body Temperature |

<p align="center">
  <img src="../images/results/google_sheets_logging.png" width="850">
</p>

---

## Sample Logged Data

| CPM | CV | Label |
|------|------|------|
| 120 | 0.753 | Rumination |
| 135 | 0.640 | Rumination |
| 60 | 0.328 | Rumination |
| 15 | 1.000 | Other |
| 90 | 0.560 | Rumination |

These observations demonstrate the system's ability to differentiate rhythmic chewing activity from non-rumination behaviors.

---

## Experimental Observations

### Successful Outcomes

- Continuous IMU data acquisition achieved
- Real-time chewing event detection implemented
- Rumination classification performed on-device
- Temperature monitoring integrated successfully
- Cloud telemetry established through Wi-Fi
- Data visualization achieved using Blynk
- Long-term logging implemented using Google Sheets
- Successful field deployment on cattle

---

## System Validation

The project successfully demonstrated:

### Embedded System Integration

- ESP32 firmware development
- Multi-sensor integration
- Real-time signal processing

### IoT Connectivity

- Wireless data transmission
- Cloud-based visualization
- Remote monitoring

### Livestock Monitoring

- Rumination behavior tracking
- Temperature monitoring
- Location tracking

---

## Limitations

- Rule-based classification using fixed thresholds
- GPS accuracy dependent on satellite visibility
- Battery life optimization not extensively studied
- PCB design was not fabricated and validated

---

## Future Improvements

- Machine Learning-based behavior classification
- Automated health anomaly detection
- LoRa-based long-range communication
- Solar-powered operation
- Fabricated custom PCB implementation
- Mobile alert generation

---

## Demonstration Media

Additional project demonstrations are available in:

```text
/videos/
```

Including:

- Hardware Demonstration
- Field Testing
- Dashboard Monitoring
- Cloud Data Logging

---

## Conclusion

The developed IoT-based cattle monitoring system successfully demonstrated real-time rumination monitoring, temperature sensing, cloud connectivity, and field deployment. The results validate the feasibility of using low-cost embedded sensing and signal processing techniques for livestock health monitoring applications.