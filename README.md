# FP65: 65C02-based experimental computer platform

FP65 is a modular (retro)computer project based on the WDC65C02s.
It is mainly a playground to play and experiments with old computer technology and chips.

The design is modular in the sense that it is based on a backplane that carries the 65C02 memory bus.

The `FP` of *FP65* stands for *Front Panel*.
The original idea of the project is to build a front-panel controlable computer based on the 65C02.
Something very similar to the Altair 8800 or the IMSAI 8080.
The project has been a little bit side-tracked so far, but this is still one of the goal.

## Project goals and limitations

The main goal is to have fun with old computer technologies, learning new skils in the process in a nice side-effect.
In order to keep things fun and interesting, there needs to be some (artificial) limitations.

The focus so far has been to make a retro-inspired computer platform only using through-hole components that are still readily available (as of late 2023) at regular electronic retailer.
I could have sourced cool parts from ebay (and I am entertaining the idea for doing a 68K-based project), but here I really wanted to stick with easily and safely sourcable parts.
The only exception to this rule is the [USBIO-A](usbio-a/) board that uses an Arduino board to essencially emulate an Apple I keyboard and screen to USB-serial.

Within this focus, the spread of chip and design vintage is quite big: the modular backbone design is inspired by the later 70s computer kit like the Altair 8800 and the IMSAI 8080.
The main CPU, the WDC65C02s, is an improved CMOS version of the MOS6502 from the 80s. Similarly the SCSI-A 53C80 SCSI chip has its roots in the mid-80s.

The latest technologies so far are found in the SIO-A board that uses a 16C550 UART tranceiver, this chips is a late-80s chip but is very much reminecent of the 90s and early 2000s PC technology.
chance are, your current PC-compatible computer still has a 16550-compatible UART somewhere in the chipset.

Of course the memory used, be it static RAM or ROM (actually a FLASH chip), are also 90s to 2000s technologies: they are the latest generation still available as through-hole components.

## Boards

The board made so far are:
 - [Backplane](backplane/): 50-pins 4 boards backplane with power supply and chaining connectors
 - [MCU-A](mcu-a/): wdc65C02s CPU board with clock
 - [RAM-A](ram-a/): 32KBytes static ram
 - [ROM-A](rom-a/): 4KBytes to 24KBytes ROM. Implemented in a 128KBytes FLASH with 8 static pages (dip-switch selectable).
 - [SCSI-A](scsi-a/): Asynchronous 8bit SCSI-SC interface. SCSI2 compatible with internal and external MAC-style connector.
 - [SIO-A](sio-a/): 16C550 UART with RS232-level and TTS-level connection plus 65C22 VIA for Timer and parallel (GP)I/O
 - [USBIO-A](usbio-a/): APPLE-I style emulated I/O to a USB-serial port.

# Software

FP65 has a memory map and I/O compatible with an apple-I (when using the USBIO-A board).
As such it can run WOZMON, the apple-I monitor, and any apple-I/replica-I software directly.
