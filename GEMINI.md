# Project Overview

This project is an example for the Espressif USB Host Library on the ESP32-S2/S3. It demonstrates how to interact with the USB Host Library API by implementing a pseudo class driver. The application initializes the USB host, waits for a device to connect, prints the device's information, and then waits for it to disconnect.

The main technologies used are:
- **Framework:** ESP-IDF
- **Language:** C
- **Toolchain:** xtensa-esp32-elf-gcc / riscv32-esp-elf-gcc

The project is structured as follows:
- `main/`: Contains the main application logic.
  - `usb_host_lib_main.c`: The main entry point of the application. It initializes the USB host library and the class driver.
  - `class_driver.c`: Implements a pseudo class driver that handles USB device events.
- `CMakeLists.txt`: The main build script for the project.
- `sdkconfig.defaults`: Default configuration for the project.

# Building and Running

To build, flash, and monitor the project, use the following command:

```bash
idf.py -p <PORT> flash monitor
```

Replace `<PORT>` with the serial port of your device.

To configure the project, use the following command:

```bash
idf.py menuconfig
```

# Troubleshooting

- **Device not detected:** If the device is not detected when connected to the USB OTG port, make sure that the jumper for the OTG port is closed on the board.

# MIDI Handling

The application is configured to handle MIDI messages from a connected USB MIDI device. It can parse and interpret the following messages:
-   **Note On:** When a key is pressed, the application will print the note number and velocity.
-   **Note Off:** When a key is released, the application will print the note number and a velocity of 0. A "Note On" message with a velocity of 0 is also interpreted as a "Note Off" message.

# Development Conventions

- The code follows the ESP-IDF C coding style.
- The project uses FreeRTOS for task management.
- Logging is done using the ESP-LOG library.