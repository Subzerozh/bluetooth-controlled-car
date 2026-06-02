# Bluetooth-Controlled Car (STM32)

![STM32](https://img.shields.io/badge/Microcontroller-STM32F4-blue)
![C/C++](https://img.shields.io/badge/Language-Bare--Metal%20C-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Abstract
This repository contains the bare-metal C source code and hardware documentation for a **Bluetooth-controlled car** based on the **STM32F4** microcontroller. Unlike standard Arduino-based projects, this system is built from scratch using **register-level programming** to ensure high performance, low latency, and robust hardware-software integration. 

The vehicle features a custom UART communication protocol, real-time motor control via PWM, and an autonomous obstacle-avoidance safety mechanism.

## Key Features & Technical Highlights
* **Bare-Metal Programming:** Direct register-level manipulation for GPIO, Timers, and UART without relying on high-level HAL libraries.
* **Custom UART Protocol:** Designed a robust 3-byte communication frame (`START` + `CMD` + `CHECKSUM`) to prevent data loss and ensure secure command execution.
* **State-Machine Parser:** Implemented a finite state machine (FSM) to efficiently parse incoming Bluetooth data streams.
* **BER Monitoring:** Integrated Bit Error Rate (BER) monitoring to evaluate wireless transmission quality in real-time.
* **PWM Motor Control:** Utilized `TIM3` hardware timers to generate precise PWM signals for the **L298N H-bridge**, ensuring smooth speed control and directional maneuvering.
* **Obstacle Detection:** Hardware interrupt-driven mechanism using an obstacle sensor (Ultrasonic/IR) to automatically halt the vehicle upon detecting barriers.

## Hardware Components
- **Microcontroller:** STM32F401RE (Nucleo Board / Custom PCB)
- **Motor Driver:** L298N Dual H-Bridge
- **Wireless Module:** HC-05 Bluetooth Module
- **Actuators:** 4x DC Gear Motors
- **Sensors:** HC-SR04 Ultrasonic Sensor / IR Obstacle Sensor
- **Power:** 2x 18650 Li-ion Batteries (7.4V)

## System Architecture

### 1. Custom Communication Frame
The Android controller app sends movement commands (Forward, Backward, Left, Right, Stop) via Bluetooth. The STM32 parses these commands using the following structure:
` ` `text
[ 0xAA (START) ] | [ COMMAND BYTE ] | [ CHECKSUM ]
` ` `

### 2. Block Diagram
![System Architecture](https://github.com/Subzerozh/bluetooth-controlled-car/blob/main/luongxuly.png?raw=true)

## Key Results & Demonstration

- **Hardware Setup:**
<img src="https://github.com/Subzerozh/bluetooth-controlled-car/blob/main/car.jpg?raw=true" width="600">

- **Live Demonstration:**
![Car Demo](https://github.com/Subzerozh/bluetooth-controlled-car/blob/main/CarDemo.gif?raw=true) 
---
*Developed by [Vu Ha](https://www.linkedin.com/in/vu-ha-63716a330/) as part of an Embedded Systems hardware project.*
