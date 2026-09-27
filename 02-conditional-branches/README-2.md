# Day 2: Conditional Branches

## Project Description

This project uses an ATmega32 in Proteus to learn conditional branching in AVR Assembly.

The program compares a simulated temperature value and selects a LOW, NORMAL, or HIGH status using conditional branch instructions.

## Components Used

* ATmega32
* Proteus
* AVR Assembly
* Registers
* No external hardware required for the comparison logic

## Program Logic

The program starts with a simulated temperature value:

```text
Temperature = 25
```

It then checks the value using conditional branches.

```text
Temperature >= 31  → HIGH
Temperature >= 20  → NORMAL
Temperature < 20   → LOW
```

## Concepts Learned

* `CPI`
* `BRSH`
* `RJMP`
* Conditional branching
* Carry flag
* Comparing register values
* `if / else if / else` logic in Assembly
* Labels
* Program flow

## Code Flow

The program first checks whether the temperature is 31 or higher:

```asm
CPI R16,31
BRSH HIGHER
```

If that condition is false, it checks whether the temperature is 20 or higher:

```asm
CPI R16,20
BRSH NORMAL
```

If neither condition is true, the program reaches the LOW section.

## Output

For a temperature of:

```text
25
```

the program selects:

```text
NORMAL
```

The corresponding register value becomes:

```text
R16 = 16
```

For a temperature below 20:

```text
LOW
```

For a temperature of 31 or higher:

```text
HIGH
```

## Status Logic

```text
Temperature >= 31  → HIGH
Temperature >= 20  → NORMAL
Temperature < 20   → LOW
```

## Mistakes Fixed

* I learned how `CPI` compares a register with a constant value.
* I learned how `BRSH` can be used for unsigned greater-than-or-equal comparisons.
* I learned that each condition needs a branch to the correct label.
* I learned to use `RJMP STOP` after each condition so the program does not fall into the next section.
* I learned how Assembly conditional branches can be used to create `if / else if / else` logic.

## Embedded Systems Relevance

Conditional branching is an important part of embedded systems.

Microcontrollers constantly compare sensor values and make decisions based on those values.

This project demonstrates how Assembly can implement the same type of decision-making logic used in C `if / else` statements.
