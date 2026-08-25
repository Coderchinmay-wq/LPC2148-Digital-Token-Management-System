# Digital Token Management System using LPC2148

<p align="center">

  <img src="https://img.shields.io/badge/Microcontroller-LPC2148-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Architecture-ARM7-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Language-Embedded%20C-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/IDE-Keil%20%C2%B5Vision-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/Display-7--Segment-red?style=for-the-badge">

</p>

<p align="center">
  <b>An ARM7-based embedded digital token display system using LPC2148 and multiplexed seven-segment displays.</b>
</p>

---

## 📌 Overview

The **Digital Token Management System** is an embedded systems project developed using the **LPC2148 ARM7 microcontroller**.

The system is designed to display sequential token numbers from **00 to 99** using two multiplexed seven-segment displays.

The project demonstrates fundamental embedded-system concepts including:

- GPIO programming
- Seven-segment display interfacing
- Display multiplexing
- Token counting
- Digit separation
- Delay-based display refreshing
- Real-time embedded control

The project was developed as part of the **ARM Processor and Application Lab**.

---

## 🎯 Objectives

- Design a digital token display system using the LPC2148.
- Interface dual seven-segment displays with the microcontroller.
- Generate sequential token numbers.
- Implement multiplexed display control.
- Demonstrate GPIO-based peripheral interfacing.
- Understand basic real-time embedded display operation.

---

## ⚙️ System Concept

The system follows the sequence:

```text
        Token Counter
             │
             ▼
       LPC2148 ARM7
             │
       ┌─────┴─────┐
       │           │
       ▼           ▼
    Tens Digit  Units Digit
       │           │
       └─────┬─────┘
             ▼
   Multiplexed 7-Segment
        Display
             │
             ▼
        Token Number
          00 → 99
```

## 🔢 Token Range

| Parameter     | Value |
| ------------- | ----: |
| Minimum Token |  `00` |
| Maximum Token |  `99` |
| Total Tokens  | `100` |


## 🔌 Hardware Requirements

| Component                 |    Quantity |
| ------------------------- | ----------: |
| LPC2148 Development Board |           1 |
| Seven-Segment Display     |           2 |
| Resistors                 |          14 |
| Connecting Wires          | As required |

## 🖥️ Software Requirements

- Embedded C
- Keil µVision IDE
- LPC2148 development environment

## 🔧 Peripherals Used 

### On-Chip Peripherals
- GPIO
- Timer / delay generation
### Off-Chip Peripherals
- Seven-Segment Display 1
- Seven-Segment Display 2

## 🔌 GPIO Configuration

| Function           |       GPIO Usage |
| ------------------ | ---------------: |
| Segment Lines      |      8 GPIO pins |
| Digit Select Lines |      2 GPIO pins |
| **Total**          | **10 GPIO pins** |

The documented design uses:
```
Segment Lines : P0.16 – P0.23
Digit Select  : P0.28 – P0.29

```
``Note: Pin assignments should be verified against the specific LPC2148 development board before reproducing the hardware.
``
