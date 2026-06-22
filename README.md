# X525-Quadcopter-Restoration

## 📌 Project Overview
This project documents the physical restoration and software configuration of a legacy X525 Quad-X drone. The primary objective was to troubleshoot a complete avionics failure after a decade of inactivity, successfully bridging older hardware (APM 2.8) with modern diagnostic practices.

## ⚙️ Hardware Architecture
* **Frame:** X525 Glass Fiber Quad-X
* **Flight Controller:** ArduPilot Mega (APM) 2.8
* **Motors:** Brushless A2212 1000KV
* **ESCs:** 30A SimonK Firmware
* **Radio System:** FlySky (PWM configuration)

## 🛠️ Engineering Milestones & Troubleshooting

Throughout the restoration process, several critical hardware and software conflicts were isolated and resolved:

### 1. Power Bus & Telemetry Isolation
* **Issue:** The flight controller would not boot when running exclusively on LiPo power, causing the ESCs to enter a silent failsafe mode.
* **Solution:** Diagnosed a 5V power routing failure. Integrated a dedicated Power Module to bypass the USB power line, successfully establishing a clean 5V supply and telemetry data link to the APM.

### 2. Signal Synchronization & PWM Calibration
* **Issue:** ESCs failed to register the throttle signal from the flight controller due to boot-time delays in the APM processor.
* **Solution:** Executed a direct hardware isolation test. Bypassed the flight controller to calibrate the ESCs directly through the receiver's CH3 (Throttle), mapping the absolute analog limits of the FlySky transmitter.

### 3. Phase Loss Diagnosis (Motor Cogging)
* **Issue:** Motor 2 exhibited severe stuttering ("cogging") and failed to complete a full rotation.
* **Solution:** Applied mechanical isolation. Swapped a known working motor into the suspected ESC channel, confirming a dead phase (burnt MOSFET) within the ESC itself rather than a stator winding failure. 

### 4. AHRS Matrix Realignment (Software Over Mechanical)
* **Issue:** The physical anti-vibration mount constrained the flight controller's orientation, pointing the internal gyroscopes away from the drone's true forward vector.
* **Solution:** Rather than compromising the mechanical dampening, the correction was handled in software. Modified the `AHRS_ORIENTATION` parameter in Mission Planner to offset the Yaw mathematically, perfectly realigning the IMU with the physical chassis.

### 5. Ground PID Saturation & Integral Windup
* **Issue:** Asymmetrical motor spool-up upon arming on the test bench, caused by the PID controller's Integral (I) term attempting to correct micro-inclinations on the ground.
* **Solution:** Mitigated by zeroing the `MOT_SPIN_ARMED` parameter to disable the safety idle, and executing a rigid 6-axis accelerometer calibration to establish a perfect absolute zero for the artificial horizon.

## 🚀 Current Status
The avionics system is currently fully operational, with perfect symmetry in motor response and active IMU stabilization. The next phase involves flight testing and dynamic PID tuning.
