# Day 4: Subroutines, CALL and RET

## Project Description

This project uses an ATmega32 in Proteus to learn subroutines using `RCALL` and `RET` in AVR Assembly.

The program controls three LEDs connected to PORTC and creates a RED, BLUE, and YELLOW light sequence.

Instead of writing the delay code separately for each light, one reusable `DELAY` subroutine is created and called using `RCALL`.

## Components Used

* ATmega32
* Proteus
* AVR Assembly
* 3 LEDs
* Resistors
* Virtual wires
* Ground

## Program Logic

The program uses three light states:

```text
RED    → 00000001
BLUE   → 00000010
YELLOW → 00000100
```

The sequence continuously repeats:

```text
RED → BLUE → YELLOW → RED
```

Each light calls the same `DELAY` subroutine.

## Concepts Learned

* `RCALL`
* `RET`
* Subroutines
* Reusable code
* `DEC`
* `BRNE`
* Nested loops
* `DDRC`
* `PORTC`
* `OUT`
* Labels
* Program flow

## Output

The LEDs continuously follow this sequence:

```text
RED → BLUE → YELLOW → RED → ...
```

Each LED remains ON for a short period because the `DELAY` subroutine uses nested loops.

## Mistakes Fixed

* I learned that `RCALL` is used to call a subroutine.
* I learned that `RET` returns execution from the subroutine.
* I learned that the same subroutine can be reused multiple times.
* I learned that the delay code does not need to be repeated for every LED state.
* I learned how `DEC` and `BRNE` create the nested-loop delay.
* I learned how `RJMP RED` sends the program back to the beginning of the light sequence.
* I learned how subroutines make Assembly code more organized and reusable.

## Embedded Systems Relevance

Subroutines are important in embedded systems because the same operation is often needed in multiple places.

Instead of repeating the same code, a microcontroller can use a reusable function or subroutine.

This project demonstrates the Assembly equivalent of using functions in C, where `RCALL` calls the function and `RET` returns from it.
