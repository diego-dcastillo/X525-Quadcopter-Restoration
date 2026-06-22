# X525 Legacy Quadcopter: Avionics Restoration & UAS Flight Operations

## 🚀 Project Overview
This repository documents the complete engineering restoration, avionics configuration, and flight testing of a legacy X525 Quad-X Unmanned Aerial System (UAS). Originally decommissioned and stored for over a decade, this airframe was systematically overhauled to serve as a practical testbed for studying low-level flight controller architectures, PID loop tuning, and autonomous navigation protocols. 

The primary objective of this project is to bridge older legacy hardware with modern diagnostic practices, demonstrating a hands-on understanding of rotorcraft aerodynamics, power distribution, and electronic troubleshooting from the ground up.

## ⚙️ Hardware Architecture

### Airframe & Propulsion
* **Chassis:** X525 Glass Fiber Quad-X configuration (folding frame design).
* **Motors:** 4x Brushless Outrunner A2212/13T 1000KV.
* **ESCs:** 4x HobbySky 30A with SimonK firmware (Supported input: 5-12S NiMH / 2-4S LiPo).
* **Power Distribution:** Centralized standard Power Distribution Board (PDB) directly soldered to ESC power leads.

### Avionics & Flight Control
* **Flight Controller (FC):** APM 2.8 (ArduPilot Mega) running legacy ArduCopter firmware.
* **Power Management:** APM Power Module v1.0 (Providing steady 5.3V and voltage/current telemetry to the FC).
* **Receiver (RX):** FlySky FS-R9B 8-Channel 2.4GHz Digital Receiver System.
* **Navigation:** GPS Module [MODEL_PENDING] with integrated external compass.

### Ground Support Equipment (GSE)
* **Battery Maintenance:** iMAX B6 Digital Balance Charger & Discharger with dedicated DC Power Supply.
* **Telemetry & Configuration:** Mission Planner (utilizing both modern releases for diagnostics and legacy v1.3.56 for EEPROM writing overrides).
