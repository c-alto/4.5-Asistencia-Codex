cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led_controller C CXX)

# Documentation-first scaffold:
# The current firmware source is Arduino-style (setup/loop + Keypad library).
# Build with Arduino-Pico (or Wokwi Arduino) for behavior parity.
# This CMake file is intentionally minimal to provide a clean C/C++ repo layout.

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use Arduino-Pico toolchain to build src/main.cpp"
)
