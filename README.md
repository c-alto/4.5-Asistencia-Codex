# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W project that reads a 4x4 membrane keypad and controls 12 LEDs using GPIO outputs.

## Features

- 4x4 keypad scanning using Arduino `Keypad` library
- 12 independent LED outputs
- Group controls for blue LED bank (`9` ON, `0` OFF)
- Group controls for red LED bank (`*` ON, `#` OFF)
- Behavior preserved from provided source code

## Repository Structure

- `src/main.cpp` - firmware entry point and full control logic
- `include/` - reserved for future headers
- `docs/wiring.md` - hardware wiring and GPIO mapping
- `docs/architecture.md` - software architecture and execution flow
- `diagram.json` - Wokwi hardware diagram
- `CMakeLists.txt` - clean C/C++ scaffold marker

## Hardware Bill of Materials

- Raspberry Pi Pico W
- 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220 Ω resistors (LED current limiting)
- 4x 1 kΩ resistors (keypad row pull-ups)
- Jumper wires / breadboard

## GPIO Summary

See full table in `docs/wiring.md`.

- Keypad Columns: GP19, GP18, GP17, GP16
- Keypad Rows: GP26, GP22, GP21, GP20
- LEDs: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

## Running in Wokwi

1. Create/import a Raspberry Pi Pico project in Wokwi.
2. Copy `diagram.json` into the project as `diagram.json`.
3. Copy `src/main.cpp` as the sketch source (Arduino mode).
4. Add library dependency: `Keypad`.
5. Start simulation and use keypad keys to drive LEDs.

## Running on Real Hardware (Pico W)

This firmware uses Arduino-style APIs (`setup()` / `loop()`).

1. Install Arduino IDE 2.x.
2. Install board package: **Raspberry Pi Pico/RP2040 (Earle Philhower core)**.
3. Select board: **Raspberry Pi Pico W**.
4. Install library: **Keypad** (Library Manager).
5. Open `src/main.cpp` content in an `.ino` sketch (or equivalent project).
6. Build and upload to Pico W over USB.

## About Wi-Fi

- Pico W Wi-Fi is **not used** in this project.
- No credentials are required.
- Keep secrets (SSID/password/API keys) out of source control if Wi-Fi is added later.
