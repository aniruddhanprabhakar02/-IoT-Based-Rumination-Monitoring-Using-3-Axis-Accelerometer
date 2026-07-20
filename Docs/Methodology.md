# Methodology

## Project Title

**IoT-Based Cattle Rumination Monitoring and Health Analysis System**

---

# 1. Introduction

Rumination behavior is a key indicator of cattle health, digestive efficiency, and overall well-being. Changes in rumination patterns can provide early indications of stress, illness, reduced feed intake, and metabolic disorders.

This project implements an IoT-based rumination monitoring system using an ESP32 microcontroller, inertial sensing, temperature monitoring, and cloud connectivity. Jaw movement data is acquired using an accelerometer, processed using digital signal processing techniques, and analyzed to identify rumination behavior in real time.

---

# 2. System Overview

The developed system performs the following functions:

- Jaw movement sensing using an MPU6050 accelerometer
- Signal conditioning through digital filtering
- Chewing event detection using peak analysis
- Chews Per Minute (CPM) estimation
- Coefficient of Variation (CV) computation
- Rumination classification
- Body temperature monitoring
- GPS-based location tracking
- Cloud-based visualization and logging

---

# 3. Hardware Architecture

## 3.1 ESP32 Microcontroller

The ESP32 serves as the central processing unit of the system.

### Responsibilities

- Sensor data acquisition
- Signal processing
- Feature extraction
- Rumination classification
- Wi-Fi communication
- Cloud data transmission

### Features

- Built-in Wi-Fi
- Dual-core architecture
- Multiple GPIO interfaces
- I²C and UART support
- Low power consumption

---

## 3.2 MPU6050 Accelerometer

The MPU6050 is used to capture jaw movement associated with chewing activity.

### Configuration

| Parameter | Value |
|------------|------------|
| Accelerometer Range | ±8 g |
| Sampling Frequency | 25 Hz |
| Interface | I²C |
| I²C Address | 0x68 |

### Acceleration Magnitude

To reduce sensitivity to sensor orientation, acceleration magnitude is calculated using:

```math
|a| = \sqrt{a_x^2 + a_y^2 + a_z^2}
```

Where:

- ax = Acceleration along X-axis
- ay = Acceleration along Y-axis
- az = Acceleration along Z-axis

The magnitude signal is used for subsequent processing.

---

## 3.3 DS18B20 Temperature Sensor

The DS18B20 sensor measures cattle body temperature.

### Features

- Digital output
- One-Wire communication
- High measurement accuracy
- Low power consumption

Temperature data is transmitted alongside rumination information for health monitoring.

---

## 3.4 NEO-6M GPS Module

The GPS module provides real-time location tracking.

### Information Captured

- Latitude
- Longitude

Location information can be used for animal tracking and grazing behavior analysis.

---

# 4. Data Acquisition

Accelerometer data is continuously sampled at:

```text
Sampling Frequency = 25 Hz
```

### Analysis Window

```text
Window Duration = 4 Seconds
```

### Samples Per Window

```text
N = FS × Window Duration

N = 25 × 4

N = 100 Samples
```

For each sample:

1. Read accelerometer values
2. Compute acceleration magnitude
3. Apply filtering
4. Store filtered value in buffer
5. Analyze when the window is complete

---

# 5. Signal Processing

Raw accelerometer measurements contain:

- Gravity components
- Body movement artifacts
- Environmental disturbances
- Sensor noise

To isolate jaw movement associated with rumination, a two-stage filtering process is used.

---

## 5.1 High-Pass Filter

The high-pass filter removes low-frequency body movement and gravity effects.

### Equation

```math
y[n] = \alpha \left( y[n-1] + x[n] - x[n-1] \right)
```

Where:

```text
α = 0.88
```

### Purpose

- Remove slow body motion
- Remove posture changes
- Suppress gravity effects

---

## 5.2 Low-Pass Filter

The low-pass filter removes high-frequency noise.

### Equation

```math
y[n] = y[n-1] + \beta \left( x[n] - y[n-1] \right)
```

Where:

```text
β = 0.70
```

### Purpose

- Reduce sensor noise
- Smooth signal fluctuations
- Preserve chewing-related motion

---

## 5.3 Band-Limited Chewing Signal

The combined filtering stages produce a signal dominated by chewing activity while suppressing unwanted motion and noise.

```text
Acceleration Magnitude
        │
        ▼
High-Pass Filter
        │
        ▼
Low-Pass Filter
        │
        ▼
Filtered Signal
```

---

# 6. Peak Detection

Chewing activity produces periodic peaks in the filtered signal.

A chewing event is detected when:

```text
x[i] > x[i-1]
x[i] > x[i+1]
x[i] > 0.03
```

Each valid peak corresponds to a chewing cycle.

### Measurements Recorded

- Peak count
- Peak amplitude
- Peak intervals
- Total chew count

---

# 7. Feature Extraction

Two primary features are extracted from every analysis window.

---

## 7.1 Chews Per Minute (CPM)

CPM represents chewing frequency.

### Calculation

```math
CPM =
\frac{\text{Number of Peaks}}
{\text{Window Duration (Minutes)}}
```

### Interpretation

| CPM Value | Interpretation |
|------------|------------|
| Low | Minimal chewing activity |
| Moderate | Possible rumination |
| High | Active chewing behavior |

---

## 7.2 Coefficient of Variation (CV)

CV measures the regularity of chewing intervals.

### Calculation

```math
CV = \frac{\sigma}{\mu}
```

Where:

- σ = Standard deviation of peak intervals
- μ = Mean peak interval

### Interpretation

| CV Value | Interpretation |
|------------|------------|
| Low | Rhythmic chewing |
| High | Irregular movement |

---

# 8. Rumination Classification

Rumination is identified using frequency and rhythmic consistency.

A window is classified as rumination when:

```text
30 ≤ CPM ≤ 140
```

AND

```text
CV < 1.35
```

If both conditions are satisfied:

```text
Label = Rumination
```

Otherwise:

```text
Label = Other Activity
```

---

# 9. Temperature Monitoring

At the end of each analysis window:

1. Read DS18B20 temperature
2. Convert to Celsius
3. Convert to Fahrenheit
4. Upload to cloud platform

Temperature measurements are correlated with rumination activity for health assessment.

---

# 10. Cloud Data Transmission

Data is transmitted using Wi-Fi connectivity provided by the ESP32.

## Blynk Dashboard

The following parameters are visualized:

- CPM
- CV
- Rumination Status
- Total Chew Count
- Temperature
- GPS Data

---

## Google Sheets Logging

Data is uploaded using HTTP POST requests.

### Logged Parameters

- CPM
- CV
- Rumination Label
- Rumination Count
- Total Chews
- Peak Amplitude
- Temperature

This enables long-term behavioral analysis and record keeping.

---

# 11. System Workflow

The following workflow illustrates the complete data acquisition, signal processing, rumination classification, and cloud communication pipeline implemented in the developed system.

<p align="center">
  <img src="Images/workflow/System Workflow_Cattle.png" 
  alt="System Workflow" width="850">
</p>

### Workflow Description

1. The ESP32 initializes the sensors and establishes a Wi-Fi connection.
2. The MPU6050 continuously acquires jaw movement acceleration data at 25 Hz.
3. The acceleration magnitude is computed from the three-axis measurements.
4. High-pass and low-pass digital filters remove unwanted motion artifacts and sensor noise.
5. The filtered signal is stored in a 4-second analysis window.
6. Peak detection identifies individual chewing events.
7. Chews Per Minute (CPM) and Coefficient of Variation (CV) are computed.
8. Rumination behavior is classified using the predefined CPM and CV thresholds.
9. Body temperature is measured using the DS18B20 sensor.
10. GPS coordinates are acquired from the NEO-6M module.
11. All processed information is transmitted to the Blynk dashboard and logged to Google Sheets for remote monitoring and long-term analysis.

### Processing Pipeline

```text
System Power ON
       │
       ▼
Connect to Wi-Fi
       │
       ▼
Initialize Sensors
       │
       ▼
Acquire IMU Data
       │
       ▼
Compute Magnitude
       │
       ▼
High-Pass Filtering
       │
       ▼
Low-Pass Filtering
       │
       ▼
Fill Analysis Window
       │
       ▼
Peak Detection
       │
       ▼
Compute CPM & CV
       │
       ▼
Rumination Classification
       │
       ▼
Read Temperature
       │
       ▼
Read GPS Data
       │
       ▼
Upload to Cloud
       │
       ▼
Repeat
```

# 12. System Innovations

Compared to basic threshold-counting approaches, the proposed system introduces:

- Acceleration magnitude-based analysis
- Two-stage digital filtering
- Statistical CV-based rhythm validation
- Combined frequency and regularity classification
- Cloud-based telemetry and logging
- Integrated temperature monitoring
- Real-time dashboard visualization

---

# 13. Outcome

The developed system successfully:

- Detected chewing events in real time
- Estimated chewing frequency
- Measured chewing regularity
- Classified rumination behavior
- Monitored body temperature
- Logged cloud telemetry
- Visualized data remotely through Blynk

The architecture provides a foundation for future livestock health monitoring applications, including:

- Early disease detection
- Heat stress monitoring
- Automated alert generation
- Machine learning-based health prediction
- Precision livestock farming
