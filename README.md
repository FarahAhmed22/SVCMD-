# SVCMD: ESP32 S3 Based Vibration Monitoring System Using a Luenberger Observer and Physics-Informed ML

A graduation project on an embedded condition monitoring device that detects bearing faults in industrial machinery by combining a physics based state observer with a physics informed machine learning model.

## Overview

SVCMD (Smart Vibration Based Condition Monitoring Device) is an ESP32 S3 based system built to catch early stage bearing faults from vibration data before they turn into costly unplanned downtime. It combines a Luenberger observer for physics based state estimation with a Physics Informed Random Forest classifier, aiming for something more robust than either a purely data driven or purely physics based approach on its own.

The project was developed in partnership with UnipakNile, an industrial packaging manufacturer, so the work is grounded in a real maintenance use case rather than a purely academic one.

## Motivation

Unplanned bearing failure is one of the most common causes of industrial machine downtime, and one of the more preventable ones. Most condition monitoring approaches lean either purely data driven (accurate, but a black box, and data hungry) or purely physics based (interpretable, but brittle to real world noise). SVCMD tries to combine both. The observer supplies a physically grounded state estimate, which then feeds into the ML classifier's features, so the goal is a system that stays both accurate and explainable.

## Technical Approach

**Hardware**
- ESP32 S3 microcontroller
- ADXL355 accelerometer for vibration sensing
- I2C/SPI sensor interfacing

**Algorithm**
- Luenberger observer: estimates internal system states from available sensor measurements, grounded in the physical dynamics of the monitored machine
- Physics Informed Random Forest: a fault classification approach built on physically meaningful features rather than raw signal statistics alone

## Results

As an early benchmark, a Physics Informed Random Forest model was tested against the public CWRU Bearing Dataset to validate the overall modeling approach before building the full pipeline:

| Model | Dataset | Accuracy |
|-------|---------|----------|
| Physics Informed Random Forest | CWRU Bearing Dataset (benchmark) | 98.5% |

This is a preliminary result on public benchmark data, not the project's final output. The full pipeline, including live ADXL355 sensor integration, is still in progress.

## Repository Structure

```
/firmware   ESP32 S3 embedded code
/docs       technical report, Luenberger observer design, similitude analysis
/data       CWRU dataset references, sample sensor readings
/images     hardware photos, circuit diagrams, result plots
```

## Status

- [x] Luenberger observer designed
- [x] Early benchmark test on CWRU dataset (98.5% accuracy)
- [ ] Full RF pipeline built for live sensor data
- [ ] Full integration with live ADXL355 sensor data
- [ ] Field validation on UnipakNile production equipment

## Team

Farah Ahmed Ibrahim, Mechatronics Engineering, MSA University

Jana Saleh, graduation project partner

Supervised by Dr. Mohamed Ali Abdelnaby

Industrial partner: UnipakNile (Eng. Vincent Kassis, Eng. Antoine Zeidan)
