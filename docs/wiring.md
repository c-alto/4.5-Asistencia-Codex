# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Components (from `diagram.json`)

- 1x Raspberry Pi Pico / Pico W compatible board
- 1x 4x4 membrane keypad
- 12x LEDs
  - 8x blue LEDs for keys `1..8`
  - 4x red LEDs for keys `A..D`
- 12x series resistors for LEDs (220 Ω)
- 4x pull-up resistors for keypad rows (1 kΩ to 3V3)

## Keypad Connections

| Keypad line | Pico W GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

Additional row pull-ups (from diagram):
- R1, R2, R3, R4 are each tied to **3V3** through **1 kΩ** resistors.

## LED Connections

All LED cathodes are connected to GND. Each anode is driven from a GPIO through a 220 Ω resistor.

| Logical LED | Trigger key(s) | Pico W GPIO |
|---|---|---|
| LED1 | `1` | GP11 |
| LED2 | `2` | GP10 |
| LED3 | `3` | GP9 |
| LED4 | `4` | GP8 |
| LED5 | `5` | GP7 |
| LED6 | `6` | GP6 |
| LED7 | `7` | GP5 |
| LED8 | `8` | GP4 |
| LED9 | `A` | GP3 |
| LED10 | `B` | GP2 |
| LED11 | `C` | GP28 |
| LED12 | `D` | GP27 |

## Behavioral Key Map

- `1..8`: turn ON corresponding blue LED.
- `9`: turn ON blue LED bank (`1..8`).
- `0`: turn OFF blue LED bank (`1..8`).
- `A..D`: turn ON corresponding red LED.
- `*`: turn ON red LED bank (`A..D`).
- `#`: turn OFF red LED bank (`A..D`).

## Assumptions

- The Wokwi part is `wokwi-pi-pico`; this mapping is electrically compatible with Pico W GPIO pinout for the pins used.
- Existing logic intentionally does not auto-clear individual LEDs when another key is pressed.
