# NUCLEO-F446RE Blinky

**Project #1 — My first embedded program running on real hardware.**

## Overview

This is the classic "Hello World" of embedded development — blinking an LED. Simple as it sounds, getting here required learning an entirely new toolchain, understanding how microcontrollers are configured, and successfully flashing code to physical hardware for the first time. It's a small win that represents a complete embedded workflow from start to finish.

## What It Does

Blinks the onboard green LED (LD2) on the NUCLEO-F446RE at a 1000ms interval — on for a second, off for a second, indefinitely.

## Hardware

- **Board:** STM32 NUCLEO-F446RE
- **MCU:** STM32F446RETx — Arm Cortex-M4, 512KB Flash, 128KB RAM
- **LED:** LD2 (Green) on pin PA5

## Tools Used

- STM32CubeMX — board configuration and HAL code generation
- STM32CubeIDE 2.1.0 — coding, compiling, and flashing
- ST-LINK (onboard) — programming interface

## What I Learned

- The difference between STM32CubeMX and STM32CubeIDE and why both are needed
- How to select a development board vs bare MCU in CubeMX
- What the .ioc file is and how it drives code generation
- How the HAL (Hardware Abstraction Layer) works and why it's used
- The importance of writing application code between `USER CODE BEGIN` and `USER CODE END` comment blocks so regenerating code doesn't overwrite your work
- How to build and flash firmware to a physical board via ST-LINK

## Concepts Covered

- GPIO output configuration
- HAL library usage (`HAL_GPIO_TogglePin`, `HAL_Delay`)
- STM32 project structure (Core, Drivers, .ioc, linker scripts)
- The full embedded development workflow: configure → generate → code → build → flash

## Notes

This project took longer than expected to set up due to the CubeMX/CubeIDE integration not being fully bundled in my installation. Had to install STM32CubeMX separately and learn the two-tool workflow. Once that was sorted, the actual code was two lines. Lesson learned: embedded development setup is half the battle.
