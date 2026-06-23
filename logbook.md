## 📘 Day 1: System Bring-Up & Ground Station Configuration

### 1. Hardware Inspection & Telemetry Connection
The first objective was establishing communication between the legacy APM 2.8 flight controller and the Mission Planner Ground Control Station (GCS).
* **Physical Connection:** Connected the APM 2.8 via the lateral USB port. Onboard LEDs initialized, indicating board boot-up.
* **GCS Configuration:** Selected the active `COM` port (e.g., COM3 / Arduino Mega 2560) and set the baud rate strictly to `115200`. Clicked "CONNECT" to download the board's parameters.

> **🛠️ Troubleshooting: USB Cable Power vs. Data**
> * **Issue:** No connection or USB recognition chime from the computer.
> * **Root Cause:** Standard consumer micro-USB cables are often "charge-only" to save costs (containing only the 5V Positive and Negative wires).
> * **Fix:** Ensured the use of a fully pinned data cable containing the internal D+ and D- data transmission lines.

### 2. GCS Dashboard Fundamentals
Understanding the raw data feeds on the Mission Planner dashboard is critical before physical operation.
* **HUD (Head-Up Display):** Displays the Artificial Horizon.
    * *DISARMED:* Hardware safety lock is active. Motors will not spin.
    * *Bad Compass Health:* Magnetometer requires calibration (expected after 10 years of inactivity).
    * *No GPS:* Expected behavior indoors due to lack of satellite visibility through the roof.
* **Telemetry Panel:** Raw sensor data.
    * *Altitude:* Derived from the onboard barometer. Minor drifting indoors is normal due to ambient atmospheric pressure changes.
    * *Yaw:* Heading relative to magnetic north.
* **Dynamic IMU Test:** Manually pitched and rolled the airframe on the bench. The HUD horizon responded fluidly, confirming the Inertial Measurement Unit (IMU) gyroscopes and accelerometers survived storage intact.

### 3. Power Management: LiPo Revitalization & iMAX B6 Protocol
Proper battery management is paramount for safety and avionics stability. 
* **Diagnostics:** Checked the 3S (11.1V) LiPo health using the iMAX B6 `BATT METER`.
    * *Target Voltages:* 4.20V/cell (Full), ~3.80V/cell (Storage), <3.20V/cell (Critical/Dead).
    * *Workaround:* If `BATT METER` is missing on older charger firmware, start a brief charge cycle and press `INC` to view individual cell voltages on the fly.
* **Charging Parameters:** Configured for `LiPo BALANCE` mode. Set voltage to `11.1V (3S)` and target charge rate to `5.0A` (1C rate for a 5000mAh battery).

> **🛠️ Troubleshooting: iMAX B6 "INPUT VOL ERR"**
> * **Issue:** Charger crashes and displays an input voltage error immediately upon holding START.
> * **Root Cause:** The external generic 12V 5A power supply collapses under maximum load due to overrated factory specifications.
> * **Fix:** Manually derated the charging current from 5.0A down to 1.5A. This prevents the PSU from tripping, allowing a stable, albeit slower, charge.

* **Charge Completion Protocol:** * As cells approach 4.10V, the charger automatically enters a "Constant Voltage" phase, dropping the current near zero to balance the three cells with millivolt precision.
    * Upon the "FULL" acoustic alarm, the safety disconnect sequence is: press STOP, disconnect the main XT60 power lead first, followed by the white balance plug.