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

## 💡 Seven-Segment Display

A seven-segment display consists of LED segments arranged to represent numerical digits.

The project uses a common-cathode seven-segment display according to the segment-code implementation documented in the project.

The display segments are represented as: 

```
       a
      ---
   f |   | b
      -g-
   e |   | c
      ---
       d
```

An additional segment line is also included in the documented interface.

## 🔄 Display Multiplexing

Two seven-segment displays share the segment data lines.

Instead of continuously driving both displays independently, the LPC2148 rapidly switches between them.

Multiplexing Sequence
1. Generate units-digit segment pattern
2. Enable units display
3. Apply short delay
4. Clear display lines
5. Generate tens-digit segment pattern
6. Enable tens display
7. Apply short delay
8. Repeat continuously

Because the switching occurs rapidly, persistence of vision makes the two displays appear continuously illuminated.

Display Refresh

The documented implementation uses a delay-based refresh mechanism.

Each digit delay ≈ delay(5000)

Two displays:
2 × delay(5000)

## 🧠 Program Logic

The implementation uses an array containing segment codes for the required digits.

The display routine:

Receives the token value.

Separates the token into tens and units.

Selects the corresponding segment codes.

Enables each display alternately.

Uses delay to maintain the multiplexing sequence.

The main control loop continuously handles the token display and counter operation.

## 🧪 Implementation

### Main Technologies

Microcontroller : LPC2148
CPU Architecture: ARM7
Programming      : Embedded C
IDE              : Keil µVision
Display          : Dual 7-Segment
Control          : GPIO
Display Method   : Multiplexing
Token Range      : 00–99

## 📊 Expected Output

The system generates the following sequence:

```
00
01
02
03
04
05
...
95
96
97
98
99
00
01
...

```

## Observed Results

✅ Stable display obtained 

✅ Proper multiplexing achieved

✅ Token count increments correctly

✅ No visible flickering

✅ Correct two-digit token display

## 📸 Hardware Implementation

Add photographs of your actual hardware here.

<p align="center">
  <img src="images/hardware_setup.jpg" width="750">
</p>

### Example

LPC2148 Development Board
        │
        ├── GPIO Segment Lines
        │
        ▼
┌─────────────────────┐
│  7-Segment Display  │
│        4 7          │
└─────────────────────┘

📁 Repository Structure
LPC2148-Digital-Token-Management-System/
│
├── README.md
│
├── src/
│   └── main.c
│
├── docs/
│   └── ARM_Project_Report.pdf
│
├── images/
│   ├── hardware_setup.jpg
│   ├── seven_segment_display.jpg
│   └── block_diagram.png
│
├── Keil_Project/
│   ├── *.uvprojx
│   ├── *.uvoptx
│   └── source files
│
├── .gitignore
└── LICENSE

## 🚀 Applications

### The basic token-management concept can be adapted for:

🏦 Banks

🏥 Hospitals

🏢 Government service centers

🛒 Customer service counters

🏪 Retail service centers

🎫 Queue management systems

🏫 Institutional reception systems

🔮 Future Scope

The current system can be extended with additional hardware and communication features.

## Planned Improvements

 Push-button token increment
 Keypad-based token generation
 LCD display integration
 Wireless token display
 Voice announcement of token numbers
 UART communication with a central server
 Multiple counter management
 Centralized queue-management system

These extensions would transform the current sequential display prototype into a more complete queue-management system.

## 📚Concepts Demonstrated

                Embedded Systems
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
      ARM7           GPIO        Seven-Segment
   LPC2148            │             Display
        │             │              │
        └─────────────┼──────────────┘
                      │
                      ▼
                 Multiplexing
                      │
                      ▼
                Token Counter
                      │
                      ▼
                 00 → 99

---

## 🛠️ Skills Demonstrated

Embedded Systems
ARM7 microcontroller programming
Embedded C
GPIO configuration
Peripheral interfacing
Real-time control
Digital Electronics
Seven-segment display
Multiplexing
Digit encoding
Counter implementation
Display refreshing
Development
Keil µVision
Microcontroller debugging
Hardware-software integration
Embedded project documentation

---

## 📖 Project Workflow

Problem Definition
       │
       ▼
System Design
       │
       ▼
LPC2148 GPIO Configuration
       │
       ▼
Seven-Segment Interfacing
       │
       ▼
Display Multiplexing
       │
       ▼
Token Counter Implementation
       │
       ▼
Embedded C Compilation
       │
       ▼
Hardware Implementation
       │
       ▼
Testing & Verification
       │
       ▼
00 → 99 Token Display

## 📄 Documentation

The complete project report is available in:

docs/ARM_Project_Report.pdf

### The report contains:

Project abstract
Introduction
Objectives
Problem statement
System overview
Working principle
Hardware description
GPIO configuration
Seven-segment interfacing
Calculations
Implementation
Results
Conclusion
Future scope
References

## ✅ Project Status

Hardware Design       : Completed
Embedded C Program    : Completed
GPIO Interfacing      : Completed
7-Segment Display     : Completed
Multiplexing          : Completed
Token Counter         : Completed
Testing               : Completed
Documentation         : Completed

Status: 🟢 Completed

## 👨‍💻 Author:

Chinmay N. Yalawatti

Electronics & Communication Engineering

KLE Technological University – BVB Campus

Year	2026

## 📚 References

LPC2148 User Manual
ARM7TDMI-S Technical Reference Manual
Keil µVision Documentation
NXP LPC2148 Datasheet
Seven-Segment Display Datasheet

### ⭐ If You Find This Project Useful

If this project helps you understand ARM7, LPC2148, GPIO interfacing, or seven-segment multiplexing, consider giving the repository a ⭐.

<p align="center">

<b>Built with Embedded C • LPC2148 • ARM7 • GPIO • Seven-Segment Display</b>

</p> ```
