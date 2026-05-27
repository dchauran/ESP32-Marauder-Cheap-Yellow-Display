# ESP32 Marauder — Cheap Yellow Display

<p align="center">
  <img alt="Marauder logo" src="https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/img/readme0.png" width="300">
</p>

<p align="center">
  <img src="https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/actions/workflows/pages.yml/badge.svg" alt="GitHub Actions Badge" />
  <img src="https://img.shields.io/badge/version-1.4.3-000000?style=flat" alt="GitHub Release Version Badge" />
  <img src="https://img.shields.io/github/issues/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display?style=flat&color=2EA44F" alt="GitHub Issues" />
  <br>
  <img src="https://komarev.com/ghpvc/?username=Fr4nkFletcher&label=Views&color=333333&style=flat" alt="Profile Views" />
  <a href="https://twitter.com/Fr4nkFletcher">
    <img src="https://img.shields.io/badge/Follow-%231DA1F2.svg?style=flat&logo=x&logoColor=white&color=1F285E" alt="Follow me on X">
  </a>
</p>

The aim of this project is to port the ESP32-Marauder firmware to the Cheap Yellow Display (CYD), offering powerful WiFi and Bluetooth testing features on an affordable and accessible hardware platform.

---

## 🏴‍☠️ Latest Update Highlights — added wardriving to ESP32-1732S019N (05/18/25) 🏴‍☠️

- Add support for ESP32-1732S019 1.9" ST7789 no touch ESP32-S3
  - **Select button** → `BOOT`
  - **Down button** → `GPIO47`
  - **GPS RX** → `GPIO17`
  - **GPS TX** → `GPIO18`
- Add security check to AP scanning
- Add WPS and Manufacturer check for AP scan
- Add more stats to Raw Capture
- Add WiFi analyzer
- Add quick names to channel analyzer graph
- Fix evil portal AP name character limit
- Add packet count function
- Add AP info
- Add Raw Capture
- Add single scan for AP and Stations
- Add generate random MACs for AP and Station WiFi interface
- Fixed sniffer output overlapping 
- Reduced memory usage
- Add index number to AP scan display
- Add BLE analyzer 
- Add support for ESP32-2432S024C 2.4" ILI9341/CST820 Capacitive Touch
- Add support for ESP32-3248S035C 3.5" ST7796/GT911 Capacitive Touch
- Add support for ESP32-2432S032C 3.2" ST7789/GT911 Capacitive Touch
- Add support for ESP32-2432S032R 3.2" ST7789/XPT2046 Resistive Touch 
- Add support for Guition ESP32-2432S024R 2.4" Resistive Touch
- Recalibrate touch for 3.5" 
- Fix bluetooth attack LED not turning off
- Fix status LED for bluetooth stuff
- Add support for ESP32-3248S035R 3.5" ST7796/XPT2046 Resistive Touch
- Add support for E32R40T 4.0" ST7796/XPT2046 Resistive Touch USB Type-C
- Add support for Adafruit MAX17048 battery monitor
- Update Save/Load Files menu to add for saving and loading AirTags
- Add logging to SD for Flipper/AirTag sniff
- Add Flipper Zero Sniff
- Airtag Sniffing/Spoofing
- Working Pwnagotchi Detect on all models
- Flipper BLE Spam
- Wardriving Menu added
- Added compatibility for ESP32-2432S024R 2.4" Resistive Touch USB Type-C Only
- [Guide for antenna modification](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/AntennaModNew.md) using ESP-WROOM-32U with built-in IPEX/U.FL
- [Evil Portal examples and setup](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/evilportal/)
- [How to add an external antenna](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/AntennaMod.md)

---

## Requirements

1. A compatible CYD module (see [Compatibility](#compatibility))
2. Chrome browser
3. Data-capable USB cable
4. *(Optional)* [GPS](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display?tab=readme-ov-file#gps-functionality) module for enhanced functionality

---

## Installation Steps

### Web Flasher Method (Recommended)

1. Go to the [CYM Web Flasher](https://fr4nkfletcher.github.io/Adafruit_WebSerial_ESPTool/)
2. Hold BOOT on your device, click "Connect" and select
3. Choose the appropriate Model and Version
4. Click "Program" to start flashing

<p align="center">
  <img src="https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/blob/main/assets/sc00000.jpg?raw=true" alt="CYM Web Flasher Screenshot" width="100%" style="max-width:800px; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</p>

### Manual Web Flasher Method (for installing old releases)

1. Visit the [manual flasher](https://fr4nkfletcher.github.io/Adafruit_WebSerial_ESPTool/manual)
2. Hold BOOT, click Connect
3. Set memory offset and upload files
4. Program

<p align="center">
  <img src="https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/blob/main/assets/scman1.png" alt="Manual Flashing">
</p>

| Offset | -> | Bin |
|--------|:--:|------|
| 0x1000  | -> | [Bootloader](https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/raw/refs/heads/main/resources/STATIC/M/CYD/esp32_marauder.ino.bootloader.bin) |
| 0x8000  | -> | [Partitions](https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/raw/refs/heads/main/resources/STATIC/M/CYD/esp32_marauder.ino.partitions.bin) |
| 0x10000 | -> | [Firmware](https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool/tree/main/resources/CURRENT)   |

#### Troubleshooting:

If issues arise, try the following steps:

1. Unplug and restart your CYD module
2. Hold `RST`, tap `BOOT`, release `RST` (the screen should go blank)
3. Refresh the Web Flasher page and click "Connect"

For further details, check out the [Web Flasher repository](https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool).

Alternatively, you can flash using [esptool.py](https://github.com/espressif/esptool) by:
```
cd ~
git clone https://github.com/Fr4nkFletcher/Adafruit_WebSerial_ESPTool
esptool.py --port /dev/YOURSERIALPORT write_flash 0x1000 ~/Adafruit_WebSerial_ESPTool/resources/STATIC/M/CYD/esp32_marauder.ino.bootloader.bin \
0x8000 ~/Adafruit_WebSerial_ESPTool/resources/STATIC/M/CYD/esp32_marauder.ino.partitions.bin \
0x10000 ~/Adafruit_WebSerial_ESPTool/resources/CURRENT/esp32_marauder_ofyourchoice.bin
```
---

### Manual Arduino IDE Method

1. Set up your Arduino environment following the [ESP32 Marauder Arduino IDE Setup Guide](https://github.com/justcallmekoko/ESP32Marauder/wiki/arduino-ide-setup)
2. Update your platform.txt
3. Add the necessary libraries to your Arduino libraries folder
4. Set the upload speed to `115200` in the Arduino IDE (tested on version 1.8.19)
5. Upload the firmware to your CYD module

For a step-by-step guide, refer to [Smoochiee's tutorial](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY)

### PlatformIO Method (4.0" E32R40T)

The `cyd40` PlatformIO environment targets the 4.0" USB Type-C E32R40T board with its `ST7796` display and `XPT2046` resistive touch controller. It selects the compatible local TFT_eSPI setup automatically.

1. Install the PlatformIO extension in VS Code and open this repository folder.
2. Connect the display over USB Type-C.
3. Build with the PlatformIO toolbar or run:

```bash
pio run -e cyd40
```

4. Upload with the toolbar or run:

```bash
pio run -e cyd40 -t upload
```

5. Open a serial monitor at `115200` baud when troubleshooting:

```bash
pio device monitor -e cyd40
```

The environment uses the existing Arduino configuration requirements: `LOLIN D32`, `80MHz` flash frequency, and the Minimal SPIFFS partition table. Touch calibration is configured by `CYD_40_TOUCH_CAL_PORTRAIT` and `CYD_40_TOUCH_CAL_LANDSCAPE` in `esp32_marauder/configs.h`.

The E32R40T battery header and charging circuit are supported through its onboard `BAT_ADC` divider on GPIO34. Its external UART header is shared with the onboard Type-C/CH340 serial bridge. GPS on that header can be compiled in by adding `-D CYD_40_ENABLE_UART_GPS` to the `cyd40` `build_flags`, but USB serial monitoring is not usable at the same time.

For touch calibration, open the serial monitor and run `touchcal` for portrait mode, then `touchcal landscape` for the rotated scan screens. The firmware asks for four corner touches, opens a coordinate test canvas, and prints the generated definition over serial. Copy the generated values into `esp32_marauder/configs.h` and rebuild.

---

## Compatibility

The project has been successfully tested on:

- [1.9" ESP32-S3 No Touch](https://www.aliexpress.us/item/3256807423694742.html)
- [2.4" Capacitive Touch](https://a.co/d/bTSoo9Z)
- [2.4" Resistive Touch](https://a.co/d/fhM7s0J)
- [2.4" Resistive Touch Guition](https://www.aliexpress.us/item/3256806436471011.html)
- [2.8" Resistive MicroUSB-only](https://amazon.com/dp/B0BVFXR313)
- [2.8" Resistive MicroUSB/Type-C 2USB](https://amazon.com/dp/B0CLR7MQ91)
- [3.2" Resistive Touch](https://www.aliexpress.us/item/3256806436888726.html)
- [3.2" Capacitive Touch](https://a.co/d/faB7oVU)
- [3.5" Resistive Touch](https://a.co/d/cxUc73a)
- [3.5" Capacitive Touch](https://a.co/d/2PFDlvL)

No hardware modifications are required, thanks to **@ggaljoen's** fork of the [TFT_eSPI](https://github.com/ggaljoen/TFT_eSPI) library

Support has been added for the [4.0" Resistive Touch USB Type-C module (E32R40T, ST7796/XPT2046)](https://www.amazon.com/dp/B0FGJJ24S1), pending hardware calibration validation. Enable `CYD_40` in `esp32_marauder/configs.h` and use `User_Setup_cyd40.h` with TFT_eSPI. This board has the same `320x480` ST7796 display resolution as the 3.5" ST7796 version, but uses an XPT2046 resistive touch panel with panel-specific calibration. If touch placement still needs adjustment, run TFT_eSPI's `Touch_calibrate` example and replace `CYD_40_TOUCH_CAL_PORTRAIT` and `CYD_40_TOUCH_CAL_LANDSCAPE` in `configs.h` with the generated values for rotations `0` and `1`.

---

## GPS Functionality

GPS functionality is fully supported via the 4-pin connector near the MicroUSB port. For a list of compatible GPS hardware, refer to the [official wiki](https://github.com/justcallmekoko/ESP32Marauder/wiki/gps-modification)

| GPS | -> | CYD |
|-----|:--:|-----|
| VCC | -> | VIN |
| GND | -> | GND |
| TX  | -> | TX  |
| RX  | -> | RX  |

Note: On 2.4" and 3.5" models swap RX/TX

---

## Example Usage

After flashing, you'll boot into the Marauder interface. Refer to the [ESP32 Marauder Wiki](https://github.com/justcallmekoko/ESP32Marauder/wiki) for detailed usage instructions

<p align="center">
  <img src="https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/screenshots/2.gif" alt="Demo 1" width="45%">
  <img src="https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/blob/master/screenshots/swift2.gif" alt="Demo 2" width="45%">
</p>

---

## Acknowledgments

A huge thanks to **@cod5fgzj**, [**smoochiee**](https://github.com/smoochiee), [**ggaljoen**](https://github.com/ggaljoen), [**ATOMNFT**](https://github.com/ATOMNFT), [**jstockdale**](https://github.com/jstockdale), and [**sorinbotirla**](https://github.com/sorinbotirla). And a special mention to [**JustCallMeKoko**](https://github.com/justcallmekoko) for the foundational work on [ESP32Marauder](https://github.com/justcallmekoko/ESP32Marauder).

---

## Disclaimer

This project is for educational purposes only. Always obtain proper authorization before testing on networks you don't own or have explicit permission to test. Don't be a dick!
