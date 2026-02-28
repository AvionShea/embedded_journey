# NUCLEO-F446RE LED State Machine with UART Telemetry

**Project #4 — A finite state machine with real-time serial telemetry output.**

## Overview

This project combines everything learned so far into one cohesive embedded program. A button press cycles the onboard LED through three states, and each state continuously reports its status over UART serial in real time. This is real embedded systems thinking: interrupt-driven input, non-blocking timing, state machine logic, and live telemetry output all working together in one program.

## What It Does

Each press of the B1 button advances the LED through a three-state cycle. The UART terminal displays output continuously at the speed of each blink state until the next button press changes the state.

| State | LED Behavior | UART Output |
|-------|-------------|-------------|
| OFF | Off | `State: OFF` |
| SLOW BLINK | 500ms toggle | `You should hire me.` |
| FAST BLINK | 100ms toggle | `You should REALY hire me!` |

## Hardware

- **Board:** STM32 NUCLEO-F446RE
- **MCU:** STM32F446RETx, Arm Cortex-M4, 512KB Flash, 128KB RAM
- **LED:** LD2 (Green) on pin PA5
- **Button:** B1 (Blue Push Button) on pin PC13
- **Interface:** USART2, pre-wired through ST-LINK to USB, no extra hardware needed

## Tools Used

- STM32CubeMX, board configuration and HAL code generation
- STM32CubeIDE 2.1.0, coding, compiling, and flashing
- ST-LINK (onboard), programming interface
- PuTTY, serial terminal for reading UART telemetry output

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

- How to implement a Finite State Machine (FSM) in embedded C using an enum
- How non-blocking timing works using `HAL_GetTick()` for both blink timing and debounce logic
- Why `HAL_Delay()` is problematic in real firmware and how `HAL_GetTick()` solves it by never freezing the CPU
- How mechanical button bounce works and how a timestamp-based debounce filter eliminates false presses
- How to synchronize UART output to a timed event so telemetry messages transmit at the speed of the current state
- How to use a toggle flag to send one message per full blink cycle rather than twice per cycle

## Concepts Covered

- Finite State Machine (FSM) design
- Non-blocking firmware architecture using `HAL_GetTick()`
- Button debouncing with timestamp comparison
- GPIO input and output
- UART telemetry output synchronized to state behavior
- `typedef enum` for clean, readable state definitions
- UART helper function abstraction

## Why This Matters

This project demonstrates patterns used in real defense and aerospace firmware. State machines govern everything from flight mode transitions to fault response sequences. UART telemetry is how embedded systems report their internal state to ground systems or diagnostic tools. Non-blocking architecture is a hard requirement in safety-critical systems where a frozen CPU is not an option.

## Notes

The most interesting expansion in this project was moving the UART transmit calls from the button press handler into the blink logic itself. That change made the serial output dynamic, printing at the rhythm of each state rather than just once on transition. Small change in the code, big change in behavior. That kind of thinking, tracing data flow through a system and finding the right place to attach behavior, is core embedded engineering work.