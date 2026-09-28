# Day 9: Interrupts and ISR

## Project Description

This project introduces hardware interrupts in AVR Assembly using the ATmega32.

The main goal of this day was to understand the basic structure of an interrupt-driven program, including the interrupt vector, Interrupt Service Routine (ISR), global interrupt enable, and `RETI`.

The INT0 hardware implementation was intentionally not completed on this day because the register-access instructions required to configure the ATmega32 interrupt control registers had not yet been covered.

## Concepts Learned

- Interrupts
- Interrupt Service Routine (ISR)
- Interrupt vector
- `SEI`
- `RETI`
- Program flow during an interrupt
- Difference between normal program flow and interrupt-driven flow

## Program Flow

```text
Main program
     ↓
   SEI
     ↓
 Main loop
     ↓
Interrupt occurs
     ↓
 INT0 vector
     ↓
 INT0_ISR
     ↓
   RETI
     ↓
Main program continues
````

## Code

```asm
.include "m32def.inc"

.org 0x00
    RJMP MAIN

.org INT0addr
    RJMP INT0_ISR

MAIN:
    SEI

LOOP:
    RJMP LOOP

INT0_ISR:
    ; Interrupt code will be added later
    RETI
```

## What I Learned

* `SEI` enables global interrupts.
* The interrupt vector directs the processor to the corresponding ISR.
* An ISR contains the code executed when an interrupt occurs.
* `RETI` returns execution from the ISR to the main program.
* Unlike polling, interrupts allow the microcontroller to respond to an event without continuously checking the input in the main loop.

## Not Completed Yet

The actual INT0 button and LED implementation was not completed on this day.

The ATmega32 requires configuration of interrupt-related registers such as `MCUCR` and `GICR`.

The register-access instructions required to configure these registers had not yet been covered in the course. Rather than using instructions that had not been learned yet, the hardware implementation was intentionally postponed.

The complete INT0 hardware implementation will be added after learning the required register-access instructions.

## Embedded Systems Relevance

Interrupts are fundamental to embedded systems because they allow a microcontroller to respond to external and internal events without continuously polling inputs.

They are commonly used for:

* Buttons and external inputs
* Sensors
* Timers
* Alarms
* UART and other communication events
* Real-time system events

Understanding interrupts and ISRs is an important foundation for more advanced embedded topics such as timers, UART communication, RTOS task scheduling, and event-driven firmware.

```