# AgroESC

### 12S–14S 60A Sensorless BLDC ESC for Agricultural Drones

<p align="center">
  <img src="images/esc_3d_render.png" width="700">
</p>

<p align="center">
  <b>STM32F051 · DRV8300 · IPT015N10N5 · DShot · Sensorless BEMF · AM32</b>
</p>

---

## Overview

**AgroESC** is a high-voltage, high-current sensorless BLDC Electronic Speed Controller designed for agricultural drones, heavy-lift multirotors, and other high-power UAV applications.

The ESC is designed for **12S–14S LiPo batteries** with a **60A continuous current target**.

The hardware is based on an **STM32F051** microcontroller, **DRV8300** three-phase gate driver, and six **IPT015N10N5** power MOSFETs.

The ESC uses **sensorless six-step BLDC commutation** with Back-EMF rotor-position detection and communicates with the flight controller using **DShot**.

The hardware is designed for compatibility with **AM32 firmware**.

---

## Features

- 12S–14S LiPo operation
- 60A continuous current design target
- Sensorless BLDC operation
- Six-step commutation
- Back-EMF rotor-position detection
- DShot flight-controller interface
- STM32F051 MCU
- DRV8300 three-phase gate driver
- 6 × IPT015N10N5 power MOSFETs
- Low-side current sensing
- Battery-voltage monitoring
- Temperature monitoring
- High-voltage buck power supply
- 12V gate-drive supply
- 3.3V logic supply
- AM32 firmware support
- Designed for forced-air / PCB thermal cooling

---

## Electrical Specifications

| Parameter | Specification |
|---|---|
| Battery | 12S–14S LiPo |
| 12S nominal voltage | 44.4 V |
| 14S nominal voltage | 51.8 V |
| Maximum battery voltage | 58.8 V |
| Continuous current target | 60 A |
| Motor | 3-phase BLDC |
| Commutation | Sensorless six-step |
| Rotor position | Back-EMF |
| MCU | STM32F051 |
| Gate driver | DRV8300 |
| Power MOSFET | IPT015N10N5 |
| MOSFET count | 6 |
| FC protocol | DShot |
| Firmware | AM32 |
| Logic voltage | 3.3 V |
| Gate-drive voltage | 12 V |

> 60A continuous and 12S–14S operation are design targets and require experimental validation on assembled hardware.

---

## System Architecture

```text
                    ┌────────────────────┐
                    │  Flight Controller │
                    └─────────┬──────────┘
                              │
                            DShot
                              │
                              ▼
                     ┌─────────────────┐
                     │   STM32F051     │
                     │                 │
                     │  AM32 Firmware  │
                     └───────┬─────────┘
                             │
                             │ PWM
                             ▼
                     ┌─────────────────┐
                     │     DRV8300    │
                     │   Gate Driver  │
                     └───────┬─────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │   3-Phase Power      │
                  │       Stage          │
                  │                      │
                  │  6 × IPT015N10N5     │
                  └──────────┬───────────┘
                             │
                        U / V / W
                             │
                             ▼
                        BLDC Motor
