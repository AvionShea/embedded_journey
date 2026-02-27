# NUCLEO-F446RE UART Hello World

**Project #3 — Sending data from the microcontroller to a PC over UART serial communication.**

## Overview

This project takes a big step beyond blinking LEDs. For the first time, the STM32 is talking to a PC, transmitting a message over UART that shows up in a serial terminal. This is the foundation for debugging, sensor data readouts, telemetry, and status logging in real embedded systems.

## What It Does

Transmits "Hello World!" over USART2 to a connected PC every second. The message is visible in a serial terminal (PuTTY) running at 115200 baud.

## Hardware

- **Board:** STM32 NUCLEO-F446RE
- **MCU:** STM32F446RETx, Arm Cortex-M4, 512KB Flash, 128KB RAM
- **Interface:** USART2, wired through the onboard ST-LINK to the PC via USB (no extra wiring needed)

## Tools Used

- STM32CubeMX, board configuration and HAL code generation
- STM32CubeIDE 2.1.0, coding, compiling, and flashing
- ST-LINK (onboard), programming interface
- PuTTY, serial terminal for reading UART output on PC

## Serial Terminal Settings

| Setting | Value |
|---------|-------|
| Port | COM3 |
| Baud Rate | 115200 |
| Data Bits | 8 |
| Stop Bits | 1 |
| Parity | None |
| Flow Control | None |

## What I Learned

- How UART serial communication works at a basic level
- Why USART2 is used on the NUCLEO-F446RE specifically, it is pre-wired through the ST-LINK to the USB connection so no extra hardware is needed
- How to use `HAL_UART_Transmit()` to send data from the microcontroller
- What baud rate is and why the firmware, Windows COM port, and terminal must all match
- How to configure PuTTY for serial communication
- That Windows COM port default settings (9600 baud) do not automatically sync to firmware settings, this must be set manually

## Concepts Covered

- UART/USART serial communication
- HAL UART transmit (`HAL_UART_Transmit`)
- Baud rate configuration
- Serial terminal setup and usage
- Data type casting in C (`uint8_t`)

## Notes

The trickiest part of this project was not the code itself, it was the serial terminal setup. PuTTY requires the Connection -> Serial settings to be configured before opening from the Session screen. Also, Windows sets COM port baud rate to 9600 by default, which does not match the firmware's 115200 setting. Changing the Windows COM port speed in Device Manager resolved the issue. Always verify that firmware baud rate, Windows COM port settings, and terminal settings all match.