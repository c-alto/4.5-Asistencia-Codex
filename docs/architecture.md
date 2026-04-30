# Firmware Architecture

## Overview
This project controls **12 LEDs** using a **4x4 membrane keypad** connected to a **Raspberry Pi Pico W (RP2040)**.

The firmware is written in Arduino-style C++ and centers around two lifecycle functions:

- `setup()`: configures all LED GPIOs as outputs and initializes them LOW.
- `loop()`: scans the keypad and applies LED actions according to the pressed key.

Core application logic was preserved as provided.

## Source Layout

- `src/main.cpp`: original firmware logic (keypad scanning and LED control).
- `docs/wiring.md`: pin mapping and electrical connections.
- `docs/architecture.md`: this document.
- `diagram.json`: Wokwi hardware definition used to derive wiring/docs.

## Runtime Flow

1. **Boot / init**
   - Configure 12 GPIO pins as digital outputs.
   - Turn all LEDs OFF.

2. **Main loop (every ~10 ms)**
   - Read keypad key (`keypad.getKey()`).
   - If key is valid, run `switch` case:
     - Numeric keys control blue LED bank (`1..8`) and group on/off (`9`, `0`).
     - Alpha keys control red LED bank (`A..D`) and group on/off (`*`, `#`).

## Module Dependencies

- `Keypad.h` (Arduino Keypad library)
- Arduino GPIO APIs: `pinMode`, `digitalWrite`, `delay`

## Notes for Pico W

- No Wi-Fi APIs are used in this firmware.
- Pico W behaves here purely as an RP2040 GPIO controller.
- GPIO assignments avoid changing behavior from the provided source.
