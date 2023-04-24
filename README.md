## Adafruit Feather RP2040 with USB Host PCB

<a href="http://www.adafruit.com/products/5723"><img src="assets/5723.jpg?raw=true" width="500px"><br/>
Click here to purchase one from the Adafruit shop</a>

PCB files for the Adafruit Feather RP2040 with USB Host. 

Format is EagleCAD schematic and board layout
* https://www.adafruit.com/product/5723

### Description

You're probably really used to microcontroller boards with USB, but what about a dev board with two? Two is more than one, so that makes it twice as good! And the Adafruit Feather RP2040 with USB Host is definitely double-the-fun of our other Feather RP2040 boards, with a USB Type A port on the end for connecting USB devices to. 

Now you might be thinking "hey waitaminute, the RP2040 doesn't have two USB port peripherals???" and you'd be correct! But what it does have is a nifty PIO peripheral that can be (ab)used to emulate a USB host peripheral. You get to keep the main USB port for uploading, debugging, and data communication, while at the same time sending and receiving data to just-about-any USB device. [This work is originally by sekigon on GitHub](https://github.com/sekigon-gonnoc/Pico-PIO-USB), and if you're using Pico SDK that's still the recommended library to use.

Currently, support for the USB Host peripheral is only in Arduino. So check out the [TinyUSB 'dual role' examples](https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole) for some things you can do! For example, [datalogging to a USB Key](https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole/MassStorage/msc_data_logger). Or [reading from another device/microcontroller that has USB CDC serial interface](https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole/CDC/serial_host_bridge). Or [creating an HID re-mapper](https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole/HID/hid_remapper). Or [connecting to weird devices that require firmware-updates like the Cypress EZ-USB based Intellikeys](https://github.com/adafruit/Adafruit_IntelliKeys) communications board.

Note that this is definitely a firmware hack: you will need to dedicate the second ARM core and both PIO peripherals to just handling the USB messages, but we find that it does work fairly well, or at least as well as most microcontroller's USB Host peripherals!

We also include a 1 Amp boost converter based on the TPS61023 so you can run from Lipo battery and get a nice clean 5V output for the USB devices. The booster has the enable pin tied to one of the extra GPIO on the RP2040 so power can be manually turned on and off to hard-reset whatever is connected.

At the Feather's heart is an RP2040 chip, clocked at 133 MHz and at 3.3V logic, the same one used in the Raspberry Pi Pico. This chip has a whopping 8MB of onboard QSPI FLASH and 264K of RAM!  There's even room left over for a STEMMA QT connector for plug-and-play of I2C devices!

To make it easy to use for portable projects, we added a connector for any of our 3.7V Lithium polymer batteries and built-in battery charging. You don't need a battery, it will run just fine straight from the USB Type C connector. But, if you do have a battery, you can take it on the go, then plug in the USB to recharge. The Feather will automatically switch over to USB power when it's available.

Here're some handy specs! You get:

* Measures 2.0" x 0.9" x 0.28" (50.8mm x 22.8mm x 7mm) without headers soldered in
* Light as a (large?) feather - 6.3 grams
* RP2040 32-bit Cortex M0+ dual core running at ~133 MHz @ 3.3V logic and power
* 264 KB RAM
* 8 MB SPI FLASH chip for storing files and CircuitPython/MicroPython code storage. No EEPROM
* Tons of GPIO! 21 x GPIO pins with following capabilities:
* Four 12-bit ADCs (one more than Pico)
* Two I2C, Two SPI, and two UART peripherals, we label one for the 'main' interface in standard Feather locations
* 16 x PWM outputs - for servos, LEDs, etc
* Built-in 200mA+ lipoly charger with charging status indicator LED
* Pin #13 red LED for general purpose blinking
* RGB NeoPixel for full-color indication.
* On-board STEMMA QT connector that lets you quickly connect any Qwiic, STEMMA QT or Grove I2C devices with no soldering!
* Both Reset button and Bootloader select button for quick restarts (no unplugging-replugging to relaunch code)
* USB Type C connector lets you access built-in ROM USB bootloader and serial port debugging
* USB Type A connector for USB host capability. D+ on GPIO 16, D- on GPIO 17
* 5V Boost converter, up to 1 Amp peak output for USB peripheral power, with 500mA resettable fuse. Enable on GPIO 18. 
* 3.3V Power/enable pin
* 4 mounting holes
* 12 MHz crystal for perfect timing.
* 3.3V regulator with 500mA peak current output

### License

Adafruit invests time and resources providing this open source design, please support Adafruit and open-source hardware by purchasing products from [Adafruit](https://www.adafruit.com)!

Designed by Limor Fried/Ladyada for Adafruit Industries.

Creative Commons Attribution/Share-Alike, all text above must be included in any redistribution. 
See license.txt for additional details.
