# X525-Quadcopter-Restoration

## 📌 Project Overview
This project documents the physical restoration and software configuration of a legacy X525 Quad-X drone. The primary objective was to troubleshoot a complete avionics failure after a decade of inactivity, successfully bridging older hardware (APM 2.8) with modern diagnostic practices.

## ⚙️ Hardware Architecture

### Airframe & Propulsion
* **Chassis:** X525 Glass Fiber Quad-X configuration (folding frame design).
* **Motors:** 4x Brushless Outrunner A2212/13T 1000KV.
* **Propellers:** 10x4.5 standard composite plastic propellers.
* **ESCs:** 4x HobbySky 30A with SimonK firmware (Supported input: 5-12S NiMH / 2-4S LiPo).
* **Power Distribution:** Integrated Quadcopter ESC Connection Board (PDB) featuring XT60 input for high-current distribution.

### Avionics & Flight Control
* **Flight Controller (FC):** APM 2.8 (ArduPilot Mega) running legacy ArduCopter firmware.
* **Power Management:** APM Power Module v1.0 (5.3V output for telemetry and FC power).
* **Receiver (RX):** FlySky FS-R9B 8-Channel 2.4GHz Digital Receiver System.

### Navigation
* **GPS Module:** External Ublox-style GPS module with integrated magnetometer (compass).
* **Design:** High-gain ceramic patch antenna mounted on a foldable mast for improved signal acquisition and electromagnetic interference (EMI) isolation.
* **Cabling:** Shielded Zhengwei E326510 28 AWG cabling for reliable MAVLink/I2C communication.

### Power Supply & Ground Support
* **Flight Battery:** HRB 3S (11.1V) 5000mAh 50C LiPo with XT60 connector.
* **Battery Maintenance:** iMAX B6 Digital Balance Charger & Discharger.
* **Telemetry & Configuration:** Mission Planner (utilizing both modern releases for diagnostics and legacy v1.3.56 for EEPROM writing overrides).