# Day 6: ATmega32 GPIO

## Project Description

This project uses an ATmega32 in Proteus to learn GPIO input and output in AVR Assembly.

The program uses two push buttons connected to PORTB and eight LEDs connected to PORTD.

Each button controls a different group of four LEDs.

## Components Used

* ATmega32
* Proteus
* 8 LEDs
* 2 Push Buttons
* Resistors
* AVR Assembly
* Virtual wires
* Ground

## Circuit Connections

### LEDs

The eight LEDs are connected to PORTD:

```text
PD0 → LED 1
PD1 → LED 2
PD2 → LED 3
PD3 → LED 4

PD4 → LED 5
PD5 → LED 6
PD6 → LED 7
PD7 → LED 8
```

### Push Buttons

```text
PB0 → Button 1
PB1 → Button 2
```

The buttons use the ATmega32 internal pull-up resistors.

## GPIO Configuration

PORTD is configured as output:

```asm
LDI R16,0xFF
OUT DDRD,R16
```

This makes all eight PORTD pins outputs.

PB0 is configured as an input:

```asm
CBI DDRB,0
SBI PORTB,0
```

PB1 is also configured as an input:

```asm
CBI DDRB,1
SBI PORTB,1
```

`SBI PORTB,0` and `SBI PORTB,1` enable the internal pull-up resistors.

## Concepts Learned

* GPIO
* Input and output configuration
* `DDRD`
* `PORTD`
* `DDRB`
* `PORTB`
* `PINB`
* `IN`
* `SBI`
* `CBI`
* `SBIS`
* Internal pull-up resistors
* Active-low inputs
* Bit testing
* Binary bit patterns
* Conditional program flow
* Controlling multiple LEDs

## Output

The program produces three possible output states:

```text
PB0 pressed → 00001111 → First 4 LEDs ON

PB1 pressed → 11110000 → Last 4 LEDs ON

No button   → 00000000 → All LEDs OFF
```

## Mistakes Fixed

* I learned that `DDRx` controls whether a pin is an input or output.
* I learned that a `1` in `DDRx` configures a pin as an output.
* I learned that a `0` in `DDRx` configures a pin as an input.
* I learned that `PORTx` controls output values and can enable internal pull-ups for inputs.
* I learned that `PINx` is used to read the state of the physical pins.
* I learned that internal pull-ups make the button input HIGH when released.
* I learned that pressing the button connects the input to GND, making it LOW.
* I learned how `SBIS` can be used to test an individual input bit.
* I learned how binary values such as `0x0F` and `0xF0` can control groups of LEDs.
* I learned how a microcontroller can read inputs and control outputs based on those inputs.

## Embedded Systems Relevance

GPIO is one of the most fundamental parts of embedded systems.

Microcontrollers constantly read inputs from buttons, switches, sensors, and other devices and then control outputs such as LEDs, motors, relays, and displays.
