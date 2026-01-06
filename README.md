# arduino-based-line-follower
## Line Follower Robot using Arduino UNO & L298N

This project implements a **two-sensor line follower robot** using an **Arduino UNO**, **L298N motor driver**, **TT DC gear motors**, and **IR reflective sensors**.  
The robot follows a black line on a light surface using simple decision logic.

---

## 📌 Project Overview

The robot continuously reads two IR sensors:
- **Left IR Sensor**
- **Right IR Sensor**

Based on sensor input:
- No sensor detects line → move forward
- Right sensor detects line → turn right
- Left sensor detects line → turn left
- Both sensors detect line → stop

Motor speed is controlled using PWM, and motor direction is controlled using the L298N H-bridge driver.

---

## 🧰 Components Used

- Arduino UNO
- L298N Motor Driver Module
- 2 × TT DC Gear Motors
- 2 × IR Sensor Modules (Digital Output)
- Battery (7–12V DC)
- On/Off Switch
- Connecting wires
- Robot chassis

---

## 🔌 Power Connections

- Battery **+ve** → Switch → L298N `12V` and Arduino `VIN`
- Battery **-ve** → Common GND
- Arduino GND, L298N GND, IR Sensor GND must be **common**

⚠️ **Important:**  
Never connect motor supply directly to Arduino 5V pin.

---

## 🧭 Pin Connections (As per Code)

### IR Sensors
| Sensor | Arduino Pin |
|------|------------|
| Right IR | D11 |
| Left IR | D12 |

### L298N → Arduino
| Function | Arduino Pin |
|--------|-------------|
| ENA (Right motor PWM) | D6 |
| IN1 (Right motor) | D7 |
| IN2 (Right motor) | D8 |
| ENB (Left motor PWM) | D5 |
| IN3 (Left motor) | D9 |
| IN4 (Left motor) | D10 |

---

## ⚙️ Working Principle

1. IR sensors detect reflected IR light
2. Black surface absorbs IR → sensor output HIGH
3. Arduino reads sensor values
4. Arduino decides motor direction & speed
5. L298N drives motors accordingly

---

## 🧠 Control Logic

| Left Sensor | Right Sensor | Action |
|-----------|-------------|-------|
| LOW | LOW | Move Forward |
| LOW | HIGH | Turn Right |
| HIGH | LOW | Turn Left |
| HIGH | HIGH | Stop |

---

## 🎚 PWM Frequency Modification


```c
TCCR0B = TCCR0B & B11111000 | B00000010;


```c
TCCR0B = TCCR0B & B11111000 | B00000010;
