# ⚙️ STM32_baremetal_Project - Reliable background task management for microcontrollers

[![](https://img.shields.io/badge/Download-Release-blue.svg)](https://github.com/yopa1947/STM32_baremetal_Project/releases)

This project provides a clean system to run multiple tasks on the STM32F407 processor. It manages task switching without complex external libraries. You gain full control over how the processor handles your code.

## 🛠 Project Overview

Most software relies on extra layers of code to handle tasks. This project removes those layers. It uses the internal clock of the processor to switch between tasks at fixed intervals. This approach ensures your code runs exactly as you intend. We use the ARM Cortex-M4 hardware to manage these transitions.

The scheduler keeps your system organized. It assigns "time slices" to different functions. If one task finishes its work, the processor moves to the next task. This ensures the system remains responsive.

## 📋 System Requirements

To run this project, you need:
- A Windows computer (Windows 10 or 11).
- An STM32F407 discovery board or equivalent hardware.
- A USB cable to connect your board to the computer.
- Basic familiarity with connecting hardware devices to USB ports.

## 📥 Downloading the Software

You must download the firmware files to your computer before you can load them onto your hardware.

1. Go to the [Project Release Page](https://github.com/yopa1947/STM32_baremetal_Project/releases).
2. Look for the most recent version at the top of the list.
3. Click the link that ends in ".bin" or ".hex" to save the file to your computer.
4. Save this file in a folder you can find later, like your Downloads folder.

## 🔌 Connecting Your Hardware

1. Take your STM32F407 board.
2. Connect the mini-USB cable to the port labeled "ST-LINK" on the board.
3. Plug the other end of the USB cable into a free port on your computer.
4. Wait for Windows to detect the board. Your computer should recognize it as a new storage drive or a debug interface.

## 🚀 Running the Project

You need a small utility program to copy the downloaded file onto your board. We suggest using the ST-LINK Utility or the STM32CubeProgrammer software.

1. Install the utility software according to the instructions provided by the manufacturer.
2. Open the utility program.
3. Click on the "Connect" button to link your computer to the board.
4. Open the file you downloaded earlier.
5. Select the "Program" or "Write" button in the utility.
6. The software will transfer the data to your board.
7. Once the transfer finishes, the board will restart and begin running the code.

## 🧩 How the Scheduler Works

The software operates through a process called context switching. When the processor clock triggers a signal, the current task pauses. The system saves the state of the registers. It then loads the state for the next task. 

This happens thousands of times each second. Because this project avoids extra layers like HAL or RTOS, the system overhead remains low. The CPU spends more time running your specific logic and less time managing itself. 

The linker script controls where the instructions reside in the memory. By using a custom script, we ensure the code fits the specific map of the STM32F407 chip. This manual setup gives you a lean environment.

## 🔧 Troubleshooting Common Issues

If the board does not respond, check these items:
- Ensure the USB cable provides both power and data. Some cables act as power-only cords.
- Check that the LED indicators on your board glow after you connect the device.
- Verify that your utility software sees the board. If the software says "No target found," remove the cable and push it back in firmly.
- Confirm you downloaded the correct file version for your specific board model.

## 📅 Maintenance

This project functions as a static core. It does not require frequent background updates. If you modify your code, simply re-compile and repeat the transfer process. Always keep a backup of your previous working version before you load a new build onto the chip.

Keywords: arm, arm-none-eabi-gcc, baremetal, context-switching, cortex-m4, embedded-c, embedded-systems, rtos, scheduler, schedulers