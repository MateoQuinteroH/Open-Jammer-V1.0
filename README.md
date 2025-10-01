# Open-Jammer-V1.0
This project is an ESP32 based WiFi/Bluetooth jammer device.

The project requirements are as follows:
  * Batteries driven device.
  * Screen and buttons for user interaction.
  * Bluetooth and WiFi jamming capabilities.
  * Electrical protections to ensure device safe operation.

## Block Diagram

The general block diagram of the system is shown below:

<img width="229" height="636" alt="imagen" src="https://github.com/user-attachments/assets/100e8dfc-eb57-4590-a7d7-c7e25eaa08e7" />

The system can be separated in 3 main stages:
* Power management
* Microcontroller
* User interface

### Power management
The system will be powered from a battery, this battery must be rechargeable and the system must be usable while recharging the battery. Before calculate the power management stage, the power consumption must be defined.

| Component | Notes | Power Consumption [mA] |
| :--- | :---: | :---: |
| ESP32-S3-WROOM-1-N16R2 | Active (RF working) TX 802.11b, 1 Mbps, @20.5 dBm  | 355 |   
| ESP32-S3-WROOM-1-N16R2 | Active (RF working) RX 802.11n, HT40 | 97 |
| ESP32-S3-WROOM-1-N16R2 | Modem-Sleep 40MHz Single core running 32-bit data access instructions, the other core in idle state | 21.8 |
| SSD1306 oled screen 0.96'' | 50% check board operating current | 20 |

The maximum current consumption is reached when the ESP32 is transmitting in RF and the OLED screen is at 50% check board operating current:

$355mA + 20mA = 375mA$

The chosen battery is a LiPo 3.7V 5000mAh

<img width="327" height="218" alt="imagen" src="https://github.com/user-attachments/assets/89f5ab3d-8b37-421e-a707-79ce8adb2ce0" />

The battery duration is:

$\frac{5000mAh}{375mA} = 13.3h$

The block diagram of the power management system is:

<img width="313" height="423" alt="imagen" src="https://github.com/user-attachments/assets/ad784686-7e1c-430b-b2fa-732228324f67" />

The battery charger chip used is the MCP73831T-2DCI/OT from microchip.

| MPN  | Manufacturer | Package | Charge Current - Max [A] | Charging Saturation Voltage [V] |
| :--- | :---: | :---: | :---: | :---: |
| MCP73831T-2DCI/OT | MICROCHIP | SOT-23-5 | 0.5 | 4.2 |

The typical application of the MCP73831T-2DCI/OT is the:

<img width="505" height="224" alt="imagen" src="https://github.com/user-attachments/assets/57d6cf3a-31b9-441c-8020-97ad8789fd37" />


The battery protection chipis the DW01.

| MPN  | Manufacturer | Package | End-Off Voltage | Voltage - Supply | Supply Current (Iq) | Type of Battery |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| DW01 | HXY MOSFET | SOT23-6 | 2.4V | 1V~5.5V | 1.5uA | Lithium-ion/Polymer |

The typical application of the DW01 is the:

<img width="632" height="271" alt="imagen" src="https://github.com/user-attachments/assets/283cd79a-c7d4-4b2d-bc98-37b2b4db7c5d" />



