# Day 3: Light Logic

## Project Description

This project uses an ATmega32 in Proteus to learn program flow using `JMP` and `RJMP` in AVR Assembly.

The program controls three LEDs connected to PORTD and creates a simple light sequence using RED, BLUE, and GREEN states.

## Components Used

* ATmega32
* Proteus
* AVR Assembly
* 3 LEDs
* Resistors
* Virtual wires
* Ground

## Program Logic

The program creates three light states:

```text
RED   → 00000001
BLUE  → 00000010
GREEN → 00000100
```

The sequence continuously repeats:

```text
RED → BLUE → GREEN → RED
```

## Concepts Learned

* `JMP`
* `RJMP`
* Unconditional jumps
* Program flow
* Labels
* `BRNE`
* `DEC`
* Nested loops
* Creating delays
* `DDRD`
* `PORTD`
* `OUT`
* Binary bit patterns
* State-based logic

## Code Flow

The program first configures PORTD as an output:

```asm
LDI R16,0xFF
OUT DDRD,R16
```

The RED state turns on PD0:

```asm
LDI R16,0b00000001
OUT PORTD,R16
```

After the delay, the BLUE state turns on PD1:

```asm
LDI R16,0b00000010
OUT PORTD,R16
```

After another delay, the GREEN state turns on PD2:

```asm
LDI R16,0b00000100
OUT PORTD,R16
```

Finally, `JMP RED` sends the program back to the RED state:

```asm
JMP RED
```

## Output

The LEDs continuously follow this sequence:

```text
RED → BLUE → GREEN → RED → ...
```

Each state remains active for a short time because nested `DEC` and `BRNE` loops are used to create a delay.

## Mistakes Fixed

* I learned that `JMP` and `RJMP` are unconditional jumps.
* I learned how jumps change the normal program flow.
* I learned how labels such as `RED`, `BLUE`, and `GREEN` can represent different program states.
* I learned how `JMP RED` can return the program to an earlier section.
* I learned how `BRNE` and `DEC` can be used together to create delays.
* I learned how nested loops can create longer delays.
* I learned how binary values can control individual PORTD pins.

## Embedded Systems Relevance

Program flow is an important part of embedded systems.

Microcontrollers often move between different states depending on what the system needs to do.

This project demonstrates how Assembly can create simple state-based logic using jumps and loops.

The same concept can later be used for systems such as traffic lights, cooling systems, alarms, and machine control.
