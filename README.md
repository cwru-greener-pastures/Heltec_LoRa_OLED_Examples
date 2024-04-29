# `Heltec_LoRa_OLED_Examples` 

This package is a quick and basic set of examples to get the newer Heltec development boards (V3 boards) to work without the Heltec libraries.  There is nothing complex are special about these, they simply allow those wishing to use a Heltec device with the most current Espressif ESP32 Board Library to do so quickly and without having to reverse-engineer how the LoRa radio and OLED display are connected.

The Heltec BLE stack in the Heltec Board Library crashes when connecting to certain devices because of a bug that was addressed in the Espressif Board Library.  This effectively renders the devices unusable for BLE.  The Espressif ESP32 Board Libraries are the most current and robust, and the BLE library does not crash when connecting to devices.  The Heltec libraries and the Espressif libraries cannot be used together.  In order to reliably use the Heltec boards with BLE devices, the Espressif libraries must be used, but no examples demonstrate nor is there any documentation describing how to use the LoRa radio or OLED display on the Heltec boards.  This library provides examples from the RadioLib and ESP8266 and ESP32 OLED driver for SSD1306 displays libraries that are adapted to work with the Espressif ESP32 Arduino stack without the need for the Heltec libraries.  These are the libraries Heltec used to develop the Heltec Board Library and demonstration libraries.  A useful feature of the Espressif ESP32 Board Library is that it includes `pins_arduino.h` for Heltec deviecs that use names consistent with the `pins_arduino.h` provided by the Heltec Board Library and demo library.  This compatibility could facilitate migrating away from the Heltec Board Libraries to the Espressif ESP32 Board Libraries for existing sketches needing to switch.  

For completeness, the WiFi101 package works well for WiFi connectivity on the Heltec boards and those examples work without alteration.  For this reason, no WiFi101 examples are included in this repository.

These examples were developed on the Heltec Wireless Stick (V3) and compiled and uploaded using the Espressif ESP32 library (v 2.0.15) using the `Heltec WiFi LoRa 32(V3) / Wireless shell(V3) / Wireless stick lite (V3)` board definition.  The current release candidates for the next release of the Espressif ESP32 library defines the Heltec Wireless Stick (V3) directly.  The pin definitions are the same for these two, though the update will have a few additions specific to the Heltec Wireless Stick (V3).  The size of the display on the Heltec Wireless Stick (V3) is 64x32, but the driver should be set to 128x64.  The new definition contains definitions for the functional screen size.  There is an offset on the OLED that is not addressed in these examples, but the display does work.  Setting the location of display elements remains the responsibility of the developer.

## Dependencies

- [ardiuno-esp32](https://github.com/espressif/arduino-esp32) -- This library can be installed from the Arduino IDE Board Manager.
- [RadioLib](https://github.com/jgromes/RadioLib) -- This library can be installed from the Arduino IDE Library Manager.
- [esp8266-oled-ssd1306](https://github.com/ThingPulse/esp8266-oled-ssd1306) -- This library can be installed from the Arduino IDE Library Manager.


- [WiFi101](https://github.com/arduino-libraries/WiFi101) -- This library is provided by Arduino directly for all architectures, though it must be installed using the Arduino IDE Library Manager.  It is [well documented](https://www.arduino.cc/reference/en/libraries/wifi101/) and the examples work on the Heltec boards without alteration.

The Heltec board and demo libraries are not required for these examples to work.  If it is desired to use them, the repositories containing them must be added to the Arduino Library and Board Manager manually.  Goto the Heltec website for documentation.  Again, the Heltec libraries are *not* required for these examples.

## Sketches

- `SSD1306SimpleDemo` -- Contains code required to get the Heltec boards to turn on the SSD1306 displays derived directly from the Heltec repository.  Tweaks may remain for individual boards with respect to size of display, etc.  This example does not address offsets and functional sizes of the displays.
- `SX126X_Transmit_Interrupt` -- This updates the declaration for the radio to use the pin defintions from the `pins_arduino.h` file.  
- `SX126X_Receive_Interrupt` -- This updates the declaration for the radio to use the pin defintions from the `pins_arduino.h` file.  
- `SX126X_PingPong` -- This updates the declaration for the radio to use the pin defintions from the `pins_arduino.h` file.  

## Support

This code was developed to support research funded by the National Science Foundation (NSF) and the United States Department of Agriculture/National Institute of Food and Agriculture (USDA/NIFA), Award Number 2021-67021-34459.

## Disclaimer

THESE EXAMPLES ARE PROVIDED AS IS AND WITH NO WARRANTY OF SUITABILITY FOR ANY PURPOSE.

