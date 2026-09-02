# Arduino Bluetooth-Controlled RC Robotic Car

An intelligent, wireless mobile robotic platform controlled via a smartphone Bluetooth connection. This project integrates an Arduino microcontroller, motor driver circuitry, DC motors, and an HC-05 Bluetooth module to enable responsive wireless navigation.

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Technical Specifications & Components](#technical-specifications--components)
- [Circuit Connections & Hardware Wiring](#circuit-connections--hardware-wiring)
- [Arduino Firmware & Control Logic](#arduino-firmware--control-logic)
- [Project Structure](#project-structure)
- [Authors & Acknowledgments](#authors--acknowledgments)

---

## 🔍 Project Overview

The **Bluetooth-Controlled RC Robotic Car** was designed as an interactive hardware and embedded software project. By utilizing an Arduino board paired with a wireless Bluetooth transceiver, users can stream real-time directional commands (Forward, Backward, Left, Right, Stop) from any standard Bluetooth-enabled mobile terminal or custom controller app.

### Key Features
* **Wireless Smartphone Control:** Communicates seamlessly with mobile devices via a serial Bluetooth interface (HC-05 / HC-06).
* **Bidirectional Motor Drive:** Utilizes an L298N (or equivalent) motor driver module to control speed and rotational direction for dual DC motors.
* **Modular Embedded Architecture:** Built on a clean, extensible Arduino C/C++ sketch structure for easy debugging and future sensor integration.

---

## ⚙️ Technical Specifications & Components

| Component | Function / Description |
| :--- | :--- |
| **Arduino Uno / Nano** | Microcontroller board handling serial communication and motor control logic |
| **HC-05 Bluetooth Module** | Enables wireless serial UART communication with smartphones |
| **L298N Motor Driver** | Manages high-current dual DC motor power distribution and directional control |
| **DC Gear Motors (x2 or x4)** | Drive motors providing locomotion to the chassis |
| **Chassis & Power Supply** | Akai/Acrylic robot chassis powered by an external battery pack |

---

## 🔌 Circuit Connections & Hardware Wiring

1. **Bluetooth Module (HC-05):** 
   - `VCC` $\rightarrow$ 5V (or 3.3V depending on module breakout)
   - `GND` $\rightarrow$ Ground
   - `TX` $\rightarrow$ Arduino Digital Pin (SoftwareSerial RX or Pin 0)
   - `RX` $\rightarrow$ Arduino Digital Pin (SoftwareSerial TX or Pin 1 through voltage divider)
2. **Motor Driver (L298N):**
   - Connected to Arduino digital and PWM pins for direction and speed control.
   - Powered by an independent external battery source with common ground.

---

## 💻 Arduino Firmware & Control Logic

```cpp
// Example Arduino snippet for parsing Bluetooth commands
char incomingCommand;

void setup() {
  Serial.begin(9600); // Initialize serial communication for Bluetooth
  // Configure motor control pins as OUTPUT
}

void loop() {
  if (Serial.available() > 0) {
    incomingCommand = Serial.read();
    
    // Execute movement based on command character
    switch (incomingCommand) {
      case 'F': moveForward(); break;
      case 'B': moveBackward(); break;
      case 'L': turnLeft(); break;
      case 'R': turnRight(); break;
      case 'S': stopCar(); break;
    }
  }
}

void moveForward() {
  // Logic for driving motors forward
}

void moveBackward() {
  // Logic for driving motors backward
}

void turnLeft() {
  // Logic for pivoting left
}

void turnRight() {
  // Logic for pivoting right
}

void stopCar() {
  // Logic for halting all motors
}
