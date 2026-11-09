# AI-Driven Real-Time Fire Detection and Tracking System

## Project Overview

An autonomous fire detection and tracking system developed as a graduation project at Al-Balqa Applied University (BAU). The project integrates computer vision, artificial intelligence, and mechatronic hardware control to detect fire in real time and orient a 2-DOF Pan-Tilt mechanism toward the detected source.

The system combines a custom-trained YOLO deep learning model with an HSV color-space validation layer to reduce false detections caused by environmental noise. Target coordinates are transmitted through serial communication (UART) from Python to an Arduino Uno, which controls two metal-gear servo motors using a PCA9685 16-channel PWM driver.

## Key Performance Metrics

Based on system evaluation and experimental results:

- Precision: 91.9%
- System Detection Accuracy: 91.1%
- Recall: 83.0%
- mAP@0.5 IoU: 90.5%
- Inference Time: Approximately 42 ms per frame
- End-to-End Latency: 60–80 ms
- Frame Rate: 22–24 FPS during real-time tracking

## System Architecture and Workflow

1. Perception Layer:
A 720P USB webcam captures real-time video frames. The frames are processed using the YOLO model and an HSV color masking layer targeting yellow, orange, and red tones to validate potential fire detections.

2. Logic Layer:
The system calculates the centroid coordinates (X, Y) of the detected bounding box and determines the positional error relative to the center of the image.

3. Execution Layer:
The calculated coordinates are transmitted through a serial connection at 115200 baud rate to the Arduino Uno, which controls the Pan-Tilt mechanism through the PCA9685 PWM driver.

## Hardware Components

- Microcontroller: Arduino Uno Rev3 (ATmega328P)
- Actuation: 2-DOF Pan-Tilt Bracket
- Servo Motors: MG996R Metal Gear Servo Motors
- PWM Driver: PCA9685 16-Channel 12-bit Servo Driver
- Vision Sensor: Elinz HD 720P USB Webcam
- Indicator Module: KY-008 Laser Transmitter (650 nm)
- Alert System: 5V Passive Buzzer Module

## Engineering Solutions Implemented

1. Mechanical Jitter Mitigation:
Implemented software-based hysteresis using a dead-zone mechanism and smoothing algorithms to reduce servo micro-oscillations when tracking stationary or slowly moving targets.

2. Power Stability:
Used a dedicated external 5V power supply connected to the PCA9685 driver's V+ terminal with a common ground to reduce voltage drops and prevent microcontroller resets during high-torque servo movements.

3. Buffer Optimization:
Configured frame-grabbing protocols to skip outdated frames and reduce processing delays, improving real-time system responsiveness.

## Project Team

- Mohammad Ali Mazen Ali Ismael
- Hamdi Riyad Hamdi Aldeeb
- Abdallah Mohammad Salleh Abedalaziz Khalfah

## Project Supervisor

Mr. Mohammad Al-Khawaldeh

## Institution

Al-Balqa Applied University (BAU)
Faculty of Engineering
Mechatronics Engineering Department
