# ESC Bicycle Model

This repository presents a nonlinear vehicle dynamics project implementing an **Electronic Stability Control (ESC)** system using a **bicycle model** and **yaw-moment control via differential braking**.

The objective of the project is to model, simulate, and validate how ESC stabilizes vehicle yaw dynamics during aggressive steering maneuvers by selectively applying brake forces.

---

## Project Overview

The model includes:
- Nonlinear bicycle vehicle model
- Front and rear lateral tire force modeling with saturation
- Yaw-rate reference generation
- ESC ON / OFF logic
- Yaw moment generation using differential braking
- Sideslip angle estimation using lateral acceleration
- Saturation, hysteresis, and filtering for realistic actuator behavior

Simulation results clearly show yaw instability in ESC-OFF conditions and stabilized behavior when ESC is active.

---

## Model Structure

The project is structured as follows:

