💧 Wi-Fi Water Level Monitor (ESP-12F)

This repository contains the KiCad design files for a low-cost, connected device designed to monitor liquid levels (e.g., in a rainwater barrel, sump, or tank) and trigger an alert (buzzer) when the level reaches a critical point. The use of the ESP-12F module allows for seamless integration with Wi-Fi, enabling notifications and data logging via MQTT, Home Assistant, or a custom server.

✨ Key Features

Wireless Connectivity: Uses the popular ESP-12F (ESP8266) module for Wi-Fi networking.

Simple Input: Single-pin input for a float switch or non-contact liquid sensor.

Acoustic Alarm: On-board buzzer driven by a transistor (S8050) for high-volume local alerts.

Stable Power: Dedicated AMS1117 3.3V Linear Regulator for clean power.

Easy Programming: Dedicated 4-pin UART header for quick firmware flashing.

Robust Design: Features thick power traces and a solid Ground Plane for reliable wireless operation.

🛠️ Hardware Overview

Power System

The board is designed to accept a standard $5\text{V}$ DC input via a screw terminal ($J2$). This power is filtered by capacitors and then regulated down to $3.3\text{V}$ by the AMS1117 linear regulator ($U2$) to safely power the ESP-12F module.

Core Components

Component

Function

Notes

U1: ESP-12F

Wi-Fi Microcontroller

Core logic and wireless communication.

U2: AMS1117-3.3

$5\text{V} \rightarrow 3.3\text{V}$ Regulator

Ensures stable voltage for the ESP8266.

Q1: S8050 NPN

Transistor Switch

Drives the high-current Buzzer using a low-current GPIO signal.

J1

Sensor Input (GPIO14)

Connects to the external float switch (Signal/GND).

Programming & Strapping

The board includes the necessary components for reliable flashing:

RST/EN Circuit: $R4$ and $SW1$ allow for manual reset.

FLASH Circuit: $R5$ and $SW2$ pull GPIO0 low, enabling the Flash Programming Mode.

UART Header (J3): Provides access to $TX$, $RX$, $GND$, and $3.3\text{V}$ for USB-to-UART adapters.

🖼️ Design Files

All design files are created in KiCad.

water_level.kicad_sch: The complete schematic diagram.

water_level.kicad_pcb: The fully routed PCB layout.

/gerber: Contains all files needed to manufacture the PCB ($F.Cu$, $B.Cu$, $Edge.Cuts$, etc.).

(Note: A high-resolution PDF of the schematic and an image of the final PCB layout should be included in the repository for quick viewing.)
