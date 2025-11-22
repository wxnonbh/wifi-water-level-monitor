🚀 Usage and Programming Guide

This document explains how to power, program, and connect the Wi-Fi Water Level Monitor board.

1. Wiring the Board

Power Input (J2)

The board accepts a stable $5\text{V}$ DC input.
| Pin | Label | Connection |
| :--- | :--- | :--- |
| Pin 1 | GND | Connect to the negative ($-$) pole of the $5\text{V}$ supply. |
| Pin 2 | $+5\text{V}$ | Connect to the positive ($+$) pole of the $5\text{V}$ supply. |

Sensor Input (J1)

The sensor input is designed for a simple, two-wire float switch (or similar liquid level sensor).
| Pin | Label | Connection |
| :--- | :--- | :--- |
| Pin 1 | GND | Connect to the common ground of the sensor. |
| Pin 2 | SIG | Connects to GPIO14 on the ESP8266. This is the signal line used to detect the liquid level. |

2. Programming the ESP-12F

Programming requires an external USB-to-UART adapter (e.g., FTDI or CP2102) connected to the $J3$ header.

Programming Header (J3) Connections

Pin

Function

Adapter Pin

Pin 1

$3.3\text{V}$

$3.3\text{V}$

Pin 2

TX

RX (on adapter)

Pin 3

RX

TX (on adapter)

Pin 4

GND

GND

Entering Flash Mode

To upload new firmware (e.g., using the Arduino IDE or PlatformIO):

Connect the UART adapter to your PC and the board's $J3$ header.

Hold down the FLASH button ($SW2$).

Momentarily press the RESET button ($SW1$) and release it.

Release the FLASH button.

The ESP8266 is now in bootloader mode. You can proceed with the firmware upload.

3. Recommended Firmware Logic

The board uses GPIO14 for the sensor input and GPIO13 for the buzzer output.

Input (GPIO14): Use the INPUT_PULLUP setting in your firmware. Since the hardware includes a $10\text{k}\Omega$ pull-up ($R1$), the sensor should pull the pin LOW when activated.

Level is detected: GPIO14 reads LOW ($0\text{V}$).

Level is NOT detected: GPIO14 reads HIGH ($3.3\text{V}$).

Output (GPIO13): This pin drives the transistor base.

To turn the buzzer ON: Set GPIO13 to HIGH ($3.3\text{V}$).

To turn the buzzer OFF: Set GPIO13 to LOW ($0\text{V}$).
