# LINUX-Handheld-Console

Overview

This repository contains the KiCad schematics and PCB design files for a custom handheld gaming console. The board acts as a dedicated motherboard, providing power management, audio amplification, and gamepad input processing to a host Raspberry Pi via its 40-pin GPIO header.
Hardware Features

    System Power & Battery Management:

       - The system receives power and charges via a standard USB-C PORT.

       - A TP4056 linear charging IC handles the charging cycle for the internal battery.

       - A TP561089 converter regulates the battery voltage to supply a stable +5V rail for the host and peripherals.

      - The battery voltage is also divided and monitored by the ADC to allow the operating system to track remaining charge.

    Gamepad Inputs:

       - Standard digital face buttons, a D-Pad, and shoulder buttons are multiplexed using two 74HC165 shift registers.

       -  This shift register implementation significantly reduces the number of GPIO pins required by sending button states over a serial data line.

       - Analog signals from the left and right joysticks are processed by an onboard MCP3008 10-bit ADC.

       - The ADC transmits the digitized joystick positions back to the host processor over the SPI bus.

    Audio Subsystem:

       - Digital audio is transmitted directly from the host processor via the I2S interface (using DIN, BCLK, and LRCLK lines).

       - Dedicated left and right audio ICs decode and amplify the signal to drive the stereo speakers.
