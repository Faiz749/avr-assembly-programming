# Day 5: Stack, PUSH and POP

## Project Description

This project uses an ATmega32 in Proteus to learn the stack and `PUSH` / `POP` instructions in AVR Assembly.

The program controls four LEDs connected to PORTA and uses a reusable delay subroutine. The subroutine saves and restores register values using the stack.

## Components Used

* ATmega32
* Proteus
* AVR Assembly
* 4 LEDs
* Resistors
* Virtual wires
* Ground

## LED Pattern

The four LEDs are connected to PORTA:

```text
PA0 → RED
PA1 → BLUE
PA2 → GREEN
PA3 → YELLOW
```

The program follows this sequence:

```text
RED → BLUE → GREEN → YELLOW → RED → ...
```

## Concepts Learned

* Stack
* LIFO
* `PUSH`
* `POP`
* `SP` (Stack Pointer)
* `RCALL`
* `RET`
* Saving register values
* Restoring register values
* Reusable subroutines
* `DDRA`
* `PORTA`
* `OUT`
* Nested loops
* Program flow

## Stack Logic

The stack follows:

```text
Last In → First Out
```

For example:

```asm
PUSH R16
PUSH R17
PUSH R18
```

The values must be restored in reverse order:

```asm
POP R18
POP R17
POP R16
```

The last register pushed is therefore the first register popped.

## Mistakes Fixed

* I learned that the stack follows LIFO: Last In, First Out.
* I learned that the last value pushed must be the first value popped.
* I learned that `PUSH` saves a register value on the stack.
* I learned that `POP` restores a previously saved value.
* I learned that `PUSH` and `POP` should be used in reverse order.
* I learned that subroutines can protect registers by saving and restoring them.
* I learned that `RCALL` calls a subroutine and `RET` returns from it.
* I learned that the Stack Pointer is used by the stack even when it is not directly manipulated in the code.

## Embedded Systems Relevance

The stack is an important part of microcontroller operation.

It is used for subroutine calls, return addresses, temporary register storage, and nested function calls.

Understanding `PUSH`, `POP`, and LIFO behavior provides the foundation for understanding how AVR Assembly manages function calls and registers.

This concept will also be important when working with interrupts and more complex embedded systems.
