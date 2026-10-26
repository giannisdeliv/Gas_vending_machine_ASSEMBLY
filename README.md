# Gas Vending Machine – ARM Cortex-M0+ (FRDM-KL25Z)

This repository contains an implementation of a **natural gas vending machine** on the **NXP FRDM-KL25Z** development board (MCU: **MKL25Z128VLK4**, ARM Cortex-M0+).

The project was developed as a **microprocessor / embedded systems assignment** and focuses on:

- Low-level programming in **ARM assembly** and **C**
- Integration of assembly routines with C code
- Basic modeling of a **vending machine** that converts money into gas volume and controls a pump

---

## 1. Project Overview

The gas vending machine simulates the behavior of a simple fuel/gas pump:

1. The **user activates the machine**.
2. The **user activates the pump**.
3. The user **inserts money**.
4. The firmware **converts the money into a gas quantity**.
5. The pump runs for the required time to deliver the gas volume.

Core logic is implemented in **two main functions**:

- `machine` – Handles machine activation, user activation, pump activation, and high-level state flow.
- `user` – Provides the user-specific inputs, such as activation commands and the amount of money.

These functions exchange data through registers and memory, enforcing simple rules:

- The machine is activated only if the correct **activation code** is given.
- The pump is activated only if the correct **pump code** is given.
- The amount of money must be within a valid range.
- If any check fails, **no gas** is produced.

---

## 2. Hardware & Tools

- **Board:** NXP **FRDM-KL25Z**
- **Microcontroller:** MKL25Z128VLK4 (ARM Cortex-M0+)
- **Language:**
  - C (initialization and high-level control)
  - ARM assembly (core vending machine logic)
- **IDE / Toolchain:** Keil µVision (ARM Compiler)
- **Debug / Programming:** OpenSDA / CMSIS-DAP (depending on your board configuration)

---

## 3. Repository Structure


Typical layout:

```text
Gas_vending_machine_ASSEMBLY/
├─ Project/
│  ├─ BasicUI.uvprojx          # Keil µVision project file
│  ├─ src/
│  │  ├─ main.c                # Main C source file
│  │  ├─ machine.s             # ARM assembly for vending machine logic (example name)
│  │  └─ user.c / user.s       # User-related code (example name)
│  ├─ system_MKL25Z4.c         # System initialization for KL25Z
│  ├─ startup_MKL25Z4.s        # Startup code & vector table
│  ├─ RTE/
│  │  └─ RTE_Components.h      # RTE configuration header
│  └─ ...                      # Other project support files
│
├─ docs/
│  └─ Gas_vending_machine_report_EN.docx   # English project report (theory & details)
│
└─ README.md                   # This file


POSSIBLE EXTENSIONS

This project can be extended in several ways:

1.Add a user interface (buttons, LEDs, LCD, UART menu, etc.).
2.Implement error codes or status messages.
3.Store transaction history in non-volatile memory.
4.Implement more complex price schemes (different fuel types, discounts, etc.).
5.Replace simulated timing with real-time timers (using the MCU’s timer peripherals)
