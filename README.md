# FCFZ-FullLCD

Full-featured DIY Flipper Zero clone with an LCD display.

## 📸 Hardware Overview

### PCB Top View
![](https://github.com/alexonwheels644/FCFZ-FullLCD-PCB/blob/main/img/UP.jpg)

### PCB Bottom View
![](https://github.com/alexonwheels644/FCFZ-FullLCD-PCB/blob/main/img/DOWN.jpg)

---



## 💾 Firmware & Software
> 🚀 **Looking for the code?** You can find the compiled binaries, source code, and flashing instructions in my github:
> 👉 **[Download Firmware Here](https://github.com/alexonwheels644/FCFZ-FullLCD)
)**

---

## 📋 Bill of Materials (BOM)

### 🧠 Core Controller & Wireless Modules
* **STM32WB55CGU6 (WeAct Studio Dev Board)**
  * The main brain of the device, handling processing, Bluetooth capabilities, and system logic.
* **E07-400MM10S**
  * High-performance 10mW RF radio module operating in the sub-GHz spectrum.
* **ANT (Spring Antenna)**
  * Dedicated helical spring antenna fine-tuned for the E07 wireless transceiver module.

### 📺 Display & User Interface
* **LCD 1.4" ST7567**
  * Central graphical display unit with a crisp 128x64 resolution for real-time menu navigation.
* **4x4x0.5mm Tactile Buttons** (6 pieces)
  * Low-profile SMD input switches mapped to hardware navigation (UP, DOWN, LEFT, RIGHT, OK, BACK).
* **5050 RGB LED**
  * Multi-color status indicator for background notifications, system logs, and operation status.

### 🔌 Power Management & Logic ICs
* **MCP23017**
  * 16-bit I2C I/O port expander dedicated to driving tactile buttons, the RGB LED, and the haptic motor.
* **TP4056**
  * Linear Li-Ion battery charger IC configured to safely manage internal battery replenishment.
* **MT3608**
  * High-efficiency step-up (boost) DC-DC converter regulating stable voltage overheads directly from the Li-Po battery.
* **MAX16054**
  * Pushbutton on/off controller featuring debounce circuitry, mapped directly to the BACK button for power states.
* **SN74LVC1G32DBVR**
  * 2-input positive-OR gate, engineered to handle hardware system resets upon holding down the LEFT + BACK keys simultaneously.
* **MCP6002**
  * Low-noise operational amplifier driving signal filtration for the integrated 125kHz RFID module.

### 🛠️ Hardware Interfaces & Peripherals
* **USB Type-C 16-Pin**
  * Modern, heavy-duty surface mount receptacle facilitating wired data transfer, flashing, and device charging.
* **Micro SD Card Reader (SMD)**
  * Compact surface-mount flash memory socket used for reading/writing local system assets, logs, and dumps.
* **Buzzer 9032 (Passive)**
  * Piezoelectric passive sounder responsible for delivering audible signals, sound effects, and UI chirps.
* **IR LED & IR Receiver**
  * Dedicated optical pairing for capturing, capturing dumps, and playing back Infrared remote control protocols.
* **2.54mm Pin Headers (1x10 & 1x8)**
  * External GPIO breaking-out terminal rails allowing effortless hardware hacking and modular expansion.

### 🔌 Active Semiconductors (Transistors)
*⚠️ **Note:** All transistors listed below must use the standard **SOT-23 package**.*

| Component Type | Part Number | Component Designators | Quantity | Technical Notes / Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **NPN Transistor** | J3Y | Q1 | 1 | High-current switch for the Infrared (IR) transmitter circuit |
| **NPN Transistor** | 2TY | Q2 | 1 | Low-side driver for the passive audio buzzer gating |
| **NPN Transistor** | S8050 | Q3 | 1 | High-speed switching transistor for 125kHz RFID tag emulation |
| **P-Ch MOSFET** | A19T | Q4, Q5 | 2 | Power path routing for the 125kHz RFID module and MAX16054 power switch |
| **N-Ch MOSFET** | A2SHB | Q6 | 1 | Low-side enhancement-mode driver for the haptic vibration motor |

### 🛑 Active Semiconductors (Diodes)

| Component Type | Part Number | Component Designators | Quantity | Technical Notes / Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **Switching Diode** | 1N4148 SMD | U7, U9 | 2 | High-speed isolation; one for 125kHz RFID, one protecting BACK key line to MCP23017 |
| **Protection Diode** | S4 | D1, D2 | 2 | High-current reverse protection for the Li-Po battery and USB Type-C rails |
| **Schottky Diode** | SS34 | U11 | 1 | High-speed barrier rectifier matched for the MT3608 boost converter feedback loop |

### 📉 Passive Components (Resistors)
*⚠️ **Note:** All resistors listed below must use the standard **0805 SMD package**.*

| Component Type | Value / Rating | Component Designators | Quantity | Technical Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Power Inductor** | 22 uH | L1 | 1 | Power-optimized storage choke matched for the MT3608 boost circuit |
| **0805 Resistor** | 0.1 Ohm | R23 | 1 | High-precision current-sensing shunt resistor |
| **0805 Resistor** | 100 Ohm | R3 | 1 | Current limiting resistor |
| **0805 Resistor** | 1 kOhm | R1, R2, R17, R24 | 4 | Pull-up / general signal limiting |
| **0805 Resistor** | 2.2 kOhm | R8, R19 | 2 | Specialized signal conditioning bias |
| **0805 Resistor** | 5.1 kOhm | R6, R7 | 2 | Configured for proper USB-C CC line detection |
| **0805 Resistor** | 10 kOhm | R4, R9, R10, R14, R15, R16, R22, R25, R28, U19 | 10 | Universal digital pull-up/pull-down array |
| **0805 Resistor** | 15 kOhm | R20 | 1 | Analog voltage divider / reference step |
| **0805 Resistor** | 18 kOhm | R21 | 1 | System voltage sensing network bias |
| **0805 Resistor** | 50 kOhm | R5 | 1 | High-ohm control loop biasing resistor |
| **0805 Resistor** | 100 kOhm | R11, R12, R13 | 3 | High-impedance reference pull-down network |

### 🔋 Passive Components (Capacitors)
*⚠️ **Note:** All capacitors listed below must use the standard **0805 SMD package**.*

| Component Type | Value / Rating | Component Designators | Quantity | Dielectric / Technical Requirements |
| :--- | :--- | :--- | :--- | :--- |
| **0805 Capacitor** | 1 nF | C3 | 1 | Standard filtering ceramic capacitor |
| **0805 Capacitor** | 3.3 nF | C1 | 1 | **CRITICAL: Must strictly use C0G/NP0 ultra-stable dielectric!** |
| **0805 Capacitor** | 22 nF | C2 | 1 | Signal smoothing capacitor |
| **0805 Capacitor** | 100 nF | C4, C5, C6 | 3 | Local high-frequency IC decoupling capacitors |
| **0805 Capacitor** | 22 uF | C10, C11 | 2 | Main power rail bulk smoothing capacitors |

---

## 🛠️ Step-by-Step PCBA Assembly Manual

For a flawless manual assembly, it is highly recommended to use premium flux, thin solder wire (or solder paste with a hot air rework station), and a pair of fine tweezers. Assemble components sequentially based on their physical profile **from lowest to highest** to avoid access blockages during soldering.

### Phase 1: Micro SMD Passives (0805 Form Factor)
* **Step 1:** Populate and reflow all **0805 SMD Resistors** across the board. Double-check small values like the R23 (0.1 Ohm shunt) to ensure accuracy.
* **Step 2:** Populate all **0805 SMD Capacitors**. 
  * ⚠️ **CRITICAL WARNING:** **C1 (3.3nF)** dictates the stability of your 125khz. You **must** utilize a high-quality **0805 C0G/NP0** rated capacitor here. Regular X7R/Y5V dielectrics will drift with temperature fluctuations and completely break radio communication reliability.

### Phase 2: Structural Connector Breakouts
* **Step 3:** Mount the **2.54mm Pin Headers (1x10 and 1x8)**. Use a breadboard as a leveling jig during soldering to ensure the pins remain perpendicular to the PCB surface.

### Phase 3: Discrete Semiconductors
* **Step 4:** Carefully solder all small-outline package transistors (**Q1–Q6** in SOT-23) and SMD diodes (**U7, U9, D1, D2, U11**). Always verify correct cathode orientation utilizing the line marks indicated on the PCB silkscreen layout.

### Phase 4: Core Interfacing Integrated Circuits
* **Step 5:** Position and solder the **MCP6002** operational amplifier and the **MCP23017** port expander.
  * ⚠️ **HARDWARE MODIFICATION REQUIRED:** To match the firmware routing and correct port expander mapping, you **must solder a physical wire jumper** on the designated MCP23017 pins exactly as highlighted in the hardware reference photograph below:
![](https://github.com/alexonwheels644/FCFZ-FullLCD-PCB/blob/main/img/CONNECT.jpg)

### Phase 5: High-Density External Interface Sockets
* **Step 6:** Align and solder the **16-pin USB Type-C socket** and the **Micro SD Card Reader slot**. Use plenty of flux on the Type-C signal pins to prevent bridging underneath the housing. Inspect the ground pads thoroughly for solid structural anchoring to the PCB.

### Phase 6: Bulky Peripherals & Inductors
* **Step 7:** Solder the large power **Inductor (22uH)** and the **Passive Buzzer 9032**. Ensure the buzzer sits flush against the board to prevent acoustic rattling inside the final enclosure shell.

### Phase 7: Integrated Power & Logic Matrix
* **Step 8:** Carefully solder the power management array and supporting logic units: **TP4056** (charging), **MT3608** (boost), **SN74** (reset gate), **INA219** (power monitor), and the **MAX16054** (pushbutton module). Check for solder bridges between adjacent pins.

### Phase 8: Optoelectronics & Infrared Network
* **Step 9:** Fit the **IR LED** and the **IR Receiver** into their respective pins.
  * ⚠️ **POST-SOLDER TRIMMING:** Once the IR transmitter leads are successfully soldered, use flush cutters to trim the excess pins completely flush (under 0mm clearance) on the opposite side of the PCB. This step is necessary to clear out the mechanical footprint space for items mounted directly behind it.

### Phase 9: Radio Communications Node
* **Step 10:** Drop the **E07-400MM10S Sub-GHz module** onto its surface-mount castellated pads. Pre-tinning the PCB pads with solder before placing the module makes it much easier to bridge the connection cleanly. Finish by soldering the **ANT spring antenna** directly to its output pad.

### Phase 10: Core Processing Brain Injection
* **Step 11:** Align the **WeAct STM32WB55CGU6 Development Board** onto its pin rows. Solder all anchoring lines securely.
  * ⚠️ **POST-SOLDER TRIMMING:** Just like the IR transmitter node, use high-precision flush cutters to crop the remaining through-hole pins on the opposite side of the PCB completely flat against the solder joints. If these pins project outward, they will cause a physical collision and puncture the display panel.

### Phase 11: Display Panel Integration
* **Step 12:** Gently route and solder the **1.4-inch ST7567 LCD Display** directly over the flat-trimmed base of the board. Remove the protective plastic film only after your final enclosure assembly is complete to avoid scratching the display surface.
