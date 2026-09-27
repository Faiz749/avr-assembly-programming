# Day 1: BRNE LED Loop

## Project Description

This project uses an ATmega32 in Proteus to understand `DEC` and `BRNE` instructions.

The program uses nested loops to create a delay and repeatedly turns eight LEDs connected to PORTB ON and OFF.

## Components Used

* ATmega32
* 8 LEDs
* Proteus
* Virtual wires
* Ground

## Wiring Flow

The eight LEDs are connected to PORTB:

```text
PB0 → LED 1
PB1 → LED 2
PB2 → LED 3
PB3 → LED 4
PB4 → LED 5
PB5 → LED 6
PB6 → LED 7
PB7 → LED 8
```

The LED outputs are connected to ground.

## Concepts Learned

* `DEC`
* `BRNE`
* Z flag
* Assembly loops
* Nested loops
* `DDRB`
* `PORTB`
* `OUT`
* `LDI`
* `JMP`
* Creating delays using instruction loops

## How It Works

First, all PORTB pins are configured as outputs:

```asm
LDI R16,0xFF
OUT DDRB,R16
```

The program then uses `R17` and `R18` as loop counters.

The inner loop uses:

```asm
DEC R17
BRNE L_2
```

The outer loop uses:

```asm
DEC R18
BRNE L_1
```

The same nested-loop structure is used again for the LED OFF delay.

Finally, the program jumps back to the beginning:

```asm
JMP L_1
```

This creates a continuous ON and OFF cycle.

## Output

When the program turns PORTB ON:

```text
All 8 LEDs ON
```

When the program turns PORTB OFF:

```text
All 8 LEDs OFF
```

The LEDs continuously switch between ON and OFF with a delay created using nested `BRNE` loops.

## Mistakes Fixed

* I learned that `BRNE` depends on the Zero flag.
* I learned that `DEC` changes the Zero flag when the counter reaches zero.
* I learned how to use two registers as nested loop counters.
* I learned that the inner loop must finish before the outer loop counter is decremented.
* I learned how nested loops can be used to create a longer delay.
* I learned how `DDRB` configures PORTB as output pins.
* I learned how `PORTB` controls all eight LED outputs.

## Demo

A Proteus screenshot showing the ATmega32 and eight LEDs is included in this folder.

Proteus screenshot:

```text
brne-led-demo.mp4
brne-led-circut.png
```

## Embedded Systems Relevance

Loops are one of the most important control-flow concepts in embedded systems.

Microcontrollers often repeat tasks such as checking inputs, updating outputs, reading sensors, and creating timing delays.

Understanding `DEC` and `BRNE` provides the foundation for more advanced Assembly control flow and timing.
