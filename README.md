# IMUMaster-PCB

## Project Overview
IMUMaster is a hardware circuit board project based on the **ICM-42688-P** (a high-precision 6-axis motion tracking/Inertial Measurement Unit). The schematic and PCB layout for this project are designed using **KiCad 9.0 (and above)**.
The board is equipped with an **ESP32-C3-WROOM-02** module for processing and communication, an **SY8120B** high-efficiency synchronous buck converter to provide stable power, and integrates an **MLT-9032** SMD buzzer for status indications or alarms. Power and programming can be achieved via the onboard USB-C receptacle or the JST single-row connector.

## Key Components
* **MCU/Wireless Module**: `ESP32-C3-WROOM-02` (Espressif) - Provides Wi-Fi & Bluetooth LE connectivity and acts as the main controller.
* **IMU Sensor**: `ICM-42688-P` (TDK InvenSense) - 6-axis motion tracking device (3-axis gyroscope + 3-axis accelerometer).
* **Power Management**: `SY8120B` (Silergy) - High-efficiency 2A, 18V input synchronous step-down regulator.
* **Audio Feedback**: `MLT-9032` - SMD passive/active buzzer.
* **Connectors**: 16-pin USB Type-C receptacle, JST XH 2.50mm 1x02 for external power input.

## Pin Configurations
Depending on the schematic routing, the key pinouts and interfaces are typically summarized as follows:
* **IMU (ICM-42688-P) Interface**: Connects to the ESP32-C3 via the SPI or I2C bus (Check the schematic for exact `SCL/SCLK`, `SDA/SDI`, `SDO`, `CS` pin mappings).
* **Buzzer (MLT-9032)**: Driven by an ESP32-C3 GPIO via a PWM signal to generate tones.
* **USB-C (16-Pin)**: Used for `VBUS` (Power input) and `D+/D-` for USB Serial / JTAG flashing for the ESP32-C3.
* **JST-XH (1x02)**: Used for external power supply input (e.g. Battery `VCC` and `GND`).

## Directory Structure
- `IMUMaster.kicad_sch` / `.kicad_pcb`: Core KiCad schematic and PCB design files. *(Requires KiCad 9.0 or later)*
- `kicad_api_libs/`: Contains project-specific component symbols (`.kicad_sym`), footprints (`.pretty`/`.kicad_mod`), and 3D models.
- `bom/`: Contains the interactive BOM file (`ibom.html`), which is highly recommended for manual soldering and debugging.
- `production/`: Manufacturing & fabrication files ready to be sent to PCBA manufacturers (like JLCPCB), including the production BOM (`bom.csv`) and component placement coordinates (`positions.csv`).

## Fabrication and PCBA Instructions
All necessary files for fabrication and PCB Assembly (PCBA) are located in the `production/` directory.
You can directly use the provided Bill of Materials (BOM) and CPL/POS data for manufacturing submission.

## Local Viewing and Editing
1. Please install [KiCad EDA](https://www.kicad.org/) **version 9.0 or newer**.
2. Double-click the `IMUMaster.kicad_pro` file to open the entire project, schematic, and PCB layout.
3. Open `bom/ibom.html` in your web browser to preview the Interactive BOM, which clearly highlights the exact position of each component on the PCB.
# IMU-ESPC3-Board
