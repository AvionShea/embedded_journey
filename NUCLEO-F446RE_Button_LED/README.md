# NUCLEO-F446RE Button LED

**Project #2 — Controlling an LED with a physical button.**

## Overview

A step up from Blinky, this project introduces GPIO input by reading the state of the onboard user button and using it to toggle the green LED. Instead of the microcontroller doing something on its own, it now responds to the physical world. That's a fundamental shift in thinking and a core concept in embedded development.

## What It Does

Press the onboard B1 button (PC13) and the green LED (LD2) toggles on or off, just like a light switch. Press it again and it switches back. The state persists until the button is pressed again.

## Hardware

- **Board:** STM32 NUCLEO-F446RE
- **MCU:** STM32F446RETx, Arm Cortex-M4, 512KB Flash, 128KB RAM
- **LED:** LD2 (Green) on pin PA5
- **Button:** B1 (Blue Push Button) on pin PC13

## Tools Used

- STM32CubeMX, board configuration and HAL code generation
- STM32CubeIDE 2.1.0, coding, compiling, and flashing
- ST-LINK (onboard), programming interface

## What I Learned

- How to read a GPIO input pin using the HAL library
- What "active low" means, the button reads LOW when pressed and HIGH when released, which is common in embedded hardware design
- What debouncing is and why it matters, mechanical buttons bounce electrically when pressed and can register multiple inputs in microseconds without a small delay to smooth it out
- The difference between reactive firmware and time-driven firmware
- How to use a conditional to make firmware respond to real-world input

## Concepts Covered

- GPIO input configuration
- Active low button logic
- Software debouncing
- HAL library usage (`HAL_GPIO_ReadPin`, `HAL_GPIO_TogglePin`, `HAL_Delay`)
- Reactive firmware design

## Notes

This project felt like a bigger leap than expected. Blinky runs on its own, but this one waits for something to happen in the real world before it responds. That reactive pattern is everywhere in embedded systems, from button presses to sensor thresholds to interrupt-driven events. Getting comfortable with input/output interaction here sets the foundation for everything more complex down the road.