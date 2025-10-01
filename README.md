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
| ESP32-S3-WROOM-1-N16R2 | Dato 2a | Dato 2a |
| SSD1306 oled screen 0.96'' | Dato 2b | Dato 2b |


